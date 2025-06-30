# Setting Up

1. Download XAMPP with PHP
- For Mac, PHP v7.3.28 https://sourceforge.net/projects/xampp/files/XAMPP%20Mac%20OS%20X/7.3.28/
- For Windows, PHP v7.3.29 - https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.3.29/
2. Open XAMPP htdocs and delete all it's contents
3. The content of Teamcal folder should be inside htdocs folder
4. Open terminal in XAMPP htdocs
5. Enter the command `git clone repo_link_here .`  (Note the dot in the end)

# Adding to hosts file

### MacOs

1. Open terminal
2. Enter the command `sudo nano /etc/hosts`
3. comment out existing lines by adding hashtag infront of it
4. Add these lines:

```
127.0.0.1    testwebsocket.com
127.0.0.1       marl.tcal.ai
127.0.0.1       unified.tcal.ai
127.0.0.1       rice.ssync.ai
127.0.0.1       maplewood.ssync.ai
127.0.0.1       meet.ssync.ai
127.0.0.1       wmich.ssync.ai
127.0.0.1       api.tcal.ai
127.0.0.1       ace.tcal.ai
127.0.0.1       timebox.tcal.ai
127.0.0.1       solo.tcal.ai
127.0.0.1       alphabgroup.tcal.ai
127.0.0.1       abc.tcal.ai
127.0.0.1       meet.tcal.ai
127.0.0.1       bellivy.tcal.ai
127.0.0.1       go.tcal.ai
127.0.0.1       teamcalai.tcal.ai
127.0.0.1       tmc.tcal.ai
127.0.0.1       zoom.tcal.ai
127.0.0.1       outlook.tcal.ai
127.0.0.1       google.tcal.ai
127.0.0.1       id.tcal.ai
127.0.0.1       connectrajesh.tcal.ai
127.0.0.1       igniter.tcal.ai
127.0.0.1       testingburger.tcal.ai
127.0.0.1       sheely.tcal.ai
127.0.0.1       ninanca.tcal.ai
127.0.0.1       ace.tcal.ai
127.0.0.1       valeriaklimova.tcal.ai
127.0.0.1       acme.tcal.ai
127.0.0.1       prouxreview.tcal.ai
127.0.0.1       prouxr.tcal.ai
127.0.0.1       symbl.tcal.ai
127.0.0.1       team.tcal.ai
127.0.0.1       ateam.tcal.ai
127.0.0.1       ignitersv.tcal.ai
127.0.0.1       tcal.ai
127.0.0.1       demo.tcal.ai
```

4. ctrl+x to save and hit enter once it asks for a filename
5. ctrl+o to exit out of nano

### Windows

1. Navigate to folder "C:\Windows\System32\drivers\etc"
2. Edit hosts file as admin
3. Add these lines:

```
127.0.0.1    meet.tcal.ai
127.0.0.1    go.tcal.ai
127.0.0.1    tcal.ai
127.0.0.1    id.tcal.ai
127.0.0.1    demo.tcal.ai
127.0.0.1    acme.tcal.ai
127.0.0.1    ace.tcal.ai
127.0.0.1    zoom.tcal.ai
127.0.0.1    outlook.tcal.ai
127.0.0.1    google.tcal.ai
```

4. Save and Exit

# Try it out

1. Navigate to one of the links and try logging in
http://go.tcal.ai








### AWS CONFIG ## For IT/aws Admins, Not Meant for Developers

1. Create Instance from the Existing Image
2. Create a Static IP address
3. Create a DNS Zone in Route 53
4. Point the NS to Route 53 DNS Zone
5. Create a SSL Certificate
6. Create a Load Balancer using the SSL Certificate
7. Create Target Group for the instance
8. Setup Targets in the Target Group
9. Setup health check protocol in Targets on 443
10. Make Sure Load Balance Target is https /443 to the Target Group
11. Create an A Record in Route 53 to point to the "Traditional Load Balancer" and point it to the "west zone" load balancer instance

### Custom Form Validation Rules

1. Navigate to application/libraries/MY_FORM_validation.php
2. Create your custom rule here

### Security Headers
Add the following in httpd.conf (bitnami/apache2/conf/httpd.conf needed for Zoom)
From /Applications/XAMPP/xamppfiles/conf/httpd.conf TO /opt/apache/conf/httpd.conf
```
<IfModule headers_module>
    #
    # Avoid passing HTTP_PROXY environment to CGI's on this or any proxied
    # backend servers which have lingering "httpoxy" defects.
    # 'Proxy' request header is undefined by the IETF, not listed by IANA
    #
    RequestHeader unset Proxy early

    Header set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload"
    Header set X-Content-Type-Options nosniff
    Header set Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline' https://www.google.com/ https://www.gstatic.com/ https://maps.googleapis.com/ https://tcal.ai/  https://studentsync.ai/ https://teamshift.ai/ https://id.tcal.ai/ https://id.studentsync.ai/ https://id.teamshift.ai/ https://id.teamcal.ai/ https://id.teamcal.dev/ https://teamcal.ai/ https://studentsync.ai/ https://teamshift.ai/ https://teamcal.dev/ https://unpkg.com/ https://binaries.webex.com; style-src 'self' 'unsafe-inline' https://teamcal.ai/ https://id.tcal.ai/ https://studentsync.ai/ https://teamshift.ai/ https://id.teamcal.ai/ https://id.teamcal.dev/ https://teamcal.dev/  https://tcal.ai/; img-src 'self' https://maps.gstatic.com/ https://teamcal.ai/ https://studentsync.ai/ https://teamshift.ai/ https://teamcal.dev/ https://id.tcal.ai/ https://id.teamcal.ai/ https://id.teamcal.dev/ https://tcal.ai/ https://maps.googleapis.com/ data:; frame-src 'self' https://www.google.com; connect-src 'self' https://maps.googleapis.com/ https://tcal.ai/ https://studentsync.ai/ https://teamshift.ai/ https://id.studentsync.ai/ https://id.teamshift.ai/ https://id.tcal.ai/ https://id.teamcal.ai/ https://id.teamcal.dev/ https://teamcal.ai/ https://teamcal.dev/ ;"
    Header set Referrer-Policy "strict-origin-when-cross-origin"
    Header set X-Frame-Options: "DENY"
    Header set X-Content-Type-Options "nosniff"
    Header set X-XSS-Protection "1; mode=block"
    Header add Access-Control-Allow-Origin  "https://mail.google.com"

</IfModule>
```


    
For More Info: https://codeigniter.com/user_guide/intro/index.html
