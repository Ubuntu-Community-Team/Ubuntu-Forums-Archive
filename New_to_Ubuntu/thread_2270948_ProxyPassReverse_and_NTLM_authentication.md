---
title: "ProxyPassReverse and NTLM authentication"
date: 2015-03-26
forum: New to Ubuntu
---

### Post by leo39 on 2015-03-26
Dear all,

I'm new of Ubuntu Server.
I'm trying to migrate my old services of proxies,configured on an old RHEL 4 with Apache 2.0.52, on the new Ubuntu 14.04.1 LTS with Apache 2.4.7
On my old server I have configured Apache to run as a proxy server to export internal webpages and web applications.
One of this web applications using SSL and NTLM authentication.

On the new server I've replicated the same configuration of the old server.
Now when I try to open the web application, I get the authentication popup window, but when I insert the user/pass, I get back to the same popup window.

Following the apache configuration:

<VirtualHost 192.168.0.10:443>
ServerName name.domain.com
ServerAlias name.domain.com
ProxyPass / [http://internal.web.application/](http://internal.web.application/)
ProxyPassReverse / [http://internal.web.application/](http://internal.web.application/)
CustomLog /var/log/apache2/name.domain_SSL_log combined
SSLEngine on
SSLCertificateFile /etc/ssl/certs/certificate.crt
SSLCertificateKeyFile /etc/ssl/private/private_key.key
HostnameLookups Off
ProxyPreserveHost On
keepalive on
UseCanonicalName Off
ServerSignature On
ProxyRequests Off
</VirtualHost>

Do you have any suggestions?
Regards,

Leo39

---

### Post by SeijiSensei on 2015-03-26
I don't see any entries that impose authentication at the proxy.  Is the authentication happening on the actual webservers themselves? Perhaps you should you be looking there instead.  What do you see in the error logs on both the proxy and the application servers?

---

