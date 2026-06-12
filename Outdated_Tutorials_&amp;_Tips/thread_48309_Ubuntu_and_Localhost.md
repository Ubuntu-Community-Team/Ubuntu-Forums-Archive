---
title: "Ubuntu and Localhost"
date: 2005-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by SYD2005 on 2005-07-12
Hi guys,

I have a question in relation to running a localhost setup (apache, php, mysql) for prototyping websites on my laptop which is alreadying running standard install of Ubuntu (current release). 

Is there a safe and secure way to set this up properly while still connected to the net? In otherwords, switching back and forwards to emails, live website work and local development while being secure at the time?

I have in the past on Windows been using EasyPHP etc. I figured this will be a good way to learn Ubuntu general operations and security at the same time while keeping everything inside of Linux without booting back to Windows again.

Any thoughts?

Cheers

---

### Post by magoo on 2005-07-12
2 solutions:
- configure the apps to only listen on localhost (127.0.0.1), e.g. for apache it is in the httpd.conf file search for listen and change 0.0.0.0 to 127.0.0.1, and restart apache for mysql, I don't know what the default setup is, check with $ netstat -lntp

- Use a personal firewall like firestarter or simply create your own by disabling connections from outside of the machine to the specific ports of apache (80/tcp or whatever you use) and mysql (usually 3306/tcp) with iptables. But before, RTFM.

---

### Post by SYD2005 on 2005-07-12
Thanks for your reply, Magoo.

[QUOTE=magoo]2 solutions:
- configure the apps to only listen on localhost (127.0.0.1), e.g. for apache it is in the httpd.conf file search for listen and change 0.0.0.0 to 127.0.0.1, and restart apache for mysql, I don't know what the default setup is, check with $ netstat -lntp
[/QUOTE]

Ok, will get in there and have a look...

[QUOTE=magoo]
- Use a personal firewall like firestarter or simply create your own by disabling connections from outside of the machine to the specific ports of apache (80/tcp or whatever you use) and mysql (usually 3306/tcp) with iptables. But before, RTFM.
[/QUOTE]

Firestarter is what I am using now, but for extra measure will disable everything listening as well. 

Cheers

---

