---
title: "502 Bad Gateway - Nginx"
date: 2019-01-23
forum: New to Ubuntu
---

### Post by valecloudtk on 2019-01-23
[FONT=Ubuntu]Hi,
[/FONT]I start using ubuntu some weeks ago and I have a problem.

[FONT=Ubuntu]I've installed on Ubuntu 18.02 the web application OnlyOffice Document Server using this tutorial: [https://serenity-networks.com/how-to-install-onlyoffice-document-server-for-nextcloud-fast-easy/](https://serenity-networks.com/how-to-install-onlyoffice-document-server-for-nextcloud-fast-easy/)[/FONT][FONT=Ubuntu].[/FONT]

[FONT=Ubuntu]I've obtained a free TLS certificate with certbot and edit the file [/FONT][FONT=Ubuntu]/etc/nginx/conf.d/onlyoffice-documentserver.conf[/FONT][FONT=Ubuntu] as explained in the tutorial[/FONT][FONT=Ubuntu].[/FONT]

[FONT=Ubuntu]I've restarted both nginx and supervisor, but when I try to access to the OnlyOffice welcome page via browser I have this error: [/FONT][FONT=Ubuntu]**502 Bad Gateway - Nginx**[/FONT][FONT=Ubuntu].[/FONT]

[FONT=Ubuntu]In the log file, this is the line related to the error:[/FONT]
[FONT=Ubuntu]*2019/01/23 12:02:38 [error] 4852#4852: *12 connect() failed (111: Connection refused) while connecting to upstream, client: XXX.XXX.XXX.XXX, server: onlyoffice.example.com, request: "GET /welcome/ HTTP/2.0", upstream: "http://127.0.0.1:8000/welcome/", host: "onlyoffice.example.com"*[/FONT]

[FONT=Ubuntu]How to fix the issue?[/FONT]

[FONT=Ubuntu]Thanks[/FONT]

---

