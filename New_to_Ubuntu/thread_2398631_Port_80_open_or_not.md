---
title: "Port 80 open or not?"
date: 2018-08-15
forum: New to Ubuntu
---

### Post by zapposhusse2 on 2018-08-15
One strange thing that I have discovered.
New installed apache2 server, Ubuntu 16.x. Finally I got it to work BUT:
I can access my web site from internal IP. I can access web site via my fixed IP.
I test open port 80 on canyouseeme.org and it says port 80 closed???
My router responds to fixed IP and redirects to my internal IP.
Does it matter if port 80 is not visible or is that normal?
Port 21 is also not open on canyouseeme.org.
When I try to connect with FTP I get this message: "Connection established, waiting for welcome message..."
Connection times out???
I installed [COLOR=#333333][FONT=monospace]vsftpd.conf and I changed to [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]write_enable=YES an did a restart.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]
[/FONT][/COLOR]):P

---

### Post by wyliecoyoteuk on 2018-08-15
is apache using http or https? (443)
Also, many ISPs block port 80 on home connections.

---

### Post by zapposhusse2 on 2018-08-15
Thanks for answer :D
Only http at the moment
Port 80 and 21 ARE open. 
I have a NAS server up and running for years now. When ask canyouseeme.org both ports are open.
It is a little bit slow, why I try to start up an apache server.

---

### Post by wyliecoyoteuk on 2018-08-15
try 
[https://networkappers.com/tools/open-port-checker](https://networkappers.com/tools/open-port-checker)

It may just be the method they are using to probe the port.

---

