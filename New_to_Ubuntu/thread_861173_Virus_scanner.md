---
title: "Virus scanner"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Unotforme on 2008-07-16
How important are a virus scanner, and a firewall to Ubuntu? In windows, of course, it's damn near mandatory.

---

### Post by muteXe on 2008-07-16
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

nice quick read :)

---

### Post by appi2012 on 2008-07-16
A virus scanner is practically useless, unless you're checking for windows viruses or removable media. I'm pretty sure that linux has all ports closed by default, but if you want to block certain IPs or other stuff, ubuntu has a commandline firewall called ufw (standing for uncompilated firewall)

If you want a GUI, then look at gufw, which is a gui that uses ufw:
[http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)

---

### Post by muteXe on 2008-07-16
I believe it becomes more of a concern if you're dual-booting with windows.  Your linux partition can act as a virus "carrier" for windows ones.

---

### Post by Sef on 2008-07-16
> A virus scanner is practically useless, unless you're checking for windows viruses or removable media. I'm pretty sure that linux has all ports closed by default, but if you want to block certain IPs or other stuff, ubuntu has a commandline firewall called ufw (standing for uncompilated firewall)

If you want a GUI, then look at gufw, which is a gui that uses ufw:
[http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)

It uses IPTables as a firewall, which is a command line based.  If you want a GUI for it, download firestarter from Add/Remove.

If you have a mail client, then you would want a anti-virus, so you wouldn't send any viruses to your Window using friends.  Clam A-V is in the repositories too.

---

### Post by Ryadt on 2008-07-16
Anti-virus is not needed in ubuntu. But if you share files with windows then you might consider installing, Avast is a good one.
Ubuntu manages your firewall. You can install Firestarter as an alternative if you want.

---

### Post by Kevbert on 2008-07-16
The only other reason for using AV software is if you're emulating windows or DOS (using such programs as DosBox).  In this case it's possible to get viruses but they are written only for Windows/DOS and will not effect Linux.  Linux viruses are virtually unknown of.  ClamAV will only find Windows and DOS viruses.

---

