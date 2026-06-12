---
title: "OpenVPN Access Server WebUI Subdomain with SSL"
date: 2015-09-30
forum: New to Ubuntu
---

### Post by Muyiwa on 2015-09-30
[COLOR=#000000][FONT=Lucida Grande]I am using apache server, and I am trying to get my webui client access behind a subdomain but it is not working. No matter my configuration, I get 

502 Proxy Error

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request GET /.

Reason: Error reading from remote server.

Other configurations give me the 503 Service Unavailable message.

I am trying to put it behind the subdomain vpn.mydomain.com, and I want SSL so [https://vpn.mydomain.com]("https://vpn.mydomain.com/").

My current base configuration is:

<VirtualHost *:80>
ServerName vpn.mydomain.com
Redirect permanent / [https://vpn.mydomain.com/](https://vpn.mydomain.com/)
</VirtualHost>

<VirtualHost *:443>

ServerName vpn.mydomain.com
SSLEngine on
SSLCertificateFile /etc/ssl/certs/vpn.crt
SSLCertificateKeyFile /etc/ssl/private/vpn1.key
ProxyPreserveHost on
ProxyPass / [http://localhost:38087/](http://localhost:38087/)
ProxyPassReverse / [http://localhost:38087/](http://localhost:38087/)
</VirtualHost>

I have mapped OpenVpn AS to web port 38087, and I have a SSL certificate for the subdomain. 

I have tried doing a mod_rewrite as I noticed that for the client side, openvpn adds a /?src=connect to the end of the domain, but that didn't work. I tried adding the SSL certificate to the application itself, and that didn't work. I tried changing the connections on the WebUI to monitor both localhost and my ip, but that didn't work, so I need help here. Any ideas?

Thanks[/FONT][/COLOR]

---

