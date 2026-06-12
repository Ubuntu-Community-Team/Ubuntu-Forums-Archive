---
title: "List of ports to be kept open"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by kristian3 on 2014-02-14
I'll be running Ubuntu Server with LAMP and Mail installed. 

Being a Windows guy and not having much experience in all of this, I just wanted to know what ports should I keep open for things to run smoothly? 

I know :80 is for Apache/HTTP. What others should I keep open for the site and mail to work? I plan on keeping all others closed as most places tell you.

Also, what's the best way to find/list what ports are open and close them?

Thanks.

---

### Post by TheFu on 2014-02-14
/etc/services

**lsof** will find open ports. **netstat** can too, but isn't as thorough.

---

### Post by slickymaster on 2014-02-14
For SSH --> Port 22
For HTTP --> Port 80
For Mail (if using the server for SMTP) --> Port 25
For SSL --> Port 443

I would advise you to have a read at the following:
[LIST]
[*][https://help.ubuntu.com/community/Servers]("https://help.ubuntu.com/11.10/serverguide/C/index.html")
[*][https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[/LIST]

---

