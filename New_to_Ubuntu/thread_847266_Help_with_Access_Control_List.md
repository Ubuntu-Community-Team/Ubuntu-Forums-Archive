---
title: "Help with Access Control List"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by altwo2008 on 2008-07-02
I am in desperate need of some help!  I have inherited a Ubuntu server being used as a proxy.  When trying to connect a new workstation to our LAN, everything works fine until I hit the web browser and try to connect to the Internet.  I then receive an error message:  "Access control configuration prevents your request from being allowed at this time.  Please contact your service provider if you feel this is incorrect."

I think that I understand what it is doing I just don't have a clue as to where to go to resolve the issue.  Forgive me because I come from the "Windows" world.  The last time I used a Linux system it was simply as an end-user.  I can remotely access the server but have not been able to find any file name that may indicate that it is an ACL.  Any and all help would be greatly appreciated.

Thank you.

---

### Post by RealPSL on 2008-07-28
Not sure you will be checking back but the file to start with is /etc/squid/squid.conf. The link will give you some assistance as far as what to look for to find the acl.

[http://doc.ubuntu.com/ubuntu/serverguide/C/squid.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/squid.html")

---

