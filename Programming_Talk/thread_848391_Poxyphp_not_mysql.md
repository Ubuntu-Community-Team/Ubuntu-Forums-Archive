---
title: "Poxyphp not mysql"
date: 2008-07-03
forum: Programming Talk
---

### Post by AJB2K3 on 2008-07-03
Im trying to understand this php/mysql crap but for some reason the only php pages that display as web pages are forums. 
FF just keeps asking what to do with a .php and konq just displays it as code.
What am I supposed to to lean php?
Is there a simple front end for building a mysql database?

---

### Post by mssever on 2008-07-03
> **AJB2K3 said:**
> Im trying to understand this php/mysql crap but for some reason the only php pages that display as web pages are forums. 
FF just keeps asking what to do with a .php and konq just displays it as code.
What am I supposed to to lean php?
Is there a simple front end for building a mysql database?
Apparently, you don't have PHP and/or Apache installed and configured correctly, because the proper MIME type isn't getting set. You can verify this:


[LIST=1]
[*]Open up a terminal and type ```
telnet your-hostname-or-ip 80
```
[*]When you're connected, type the following into telnet. Note that if you make any mistakes, you can't correct them; you have to start over from the beginning. ```
HEAD /problem/url HTTP/1.1
Host: your-host-or-ip
Connection: close


``` Notice that you hit enter twice at the end.
[*]The Content-type header should match the type that the URL is supposed to return, generally text/html. I'm guessing that you're getting application/octet-stream or something equally generic.
[/LIST]
Here's an example telnet session. What I typed is in italic. ```
~:$ *telnet scott-desktop 80*
Trying 192.168.1.50...
Connected to scott-desktop.mss.
Escape character is '^]'.
[I]HEAD / HTTP/1.1
Host: www.scott-desktop.mss
connection: close[/I]

HTTP/1.1 200 OK
Date: Thu, 03 Jul 2008 17:36:53 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.6(2007-09-24)
X-Powered-By: PHP/5.2.4-2ubuntu5.1
Connection: close
Content-Type: text/html
```

---

### Post by drubin on 2008-07-03
Hi have you installed a webserver?

---

