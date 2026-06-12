---
title: "[SOLVED] Antivirus solution"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-06
[FONT="Comic Sans MS"][SIZE="4"]Hi! I'm melvin from Kerala, India.
How about an antivirus in Linux that scans for both Linux and Windows viruses?
Plz let me know which is the best antivirus solution for ubuntu 7.10 and how to install it.[/SIZE][/FONT]

---

### Post by Xerp on 2008-07-06
Hi Melvin,

ClamAV runs on Linux and can be used to scan for Microsoft Windows viruses.

[http://www.clamav.net/](http://www.clamav.net/)

---

### Post by jualin on 2008-07-06
You can check out [ClamAV]("www.clamav.org") which checks for Windows viruses from Ubuntu

---

### Post by jamesapnic on 2008-07-06
Hey there,

There are only two solutions I know of and I wouldn't say the functionality is the same on both windows and Linux.  A commercial solution is F-Secure, [http://www.f-secure.com/security_center/](http://www.f-secure.com/security_center/).  They do a Linux server based scanner and also a windows based desktop application.  Then there is clamav, which you should be able to apt-get, however I don't believe it is a realtime scanner.   You can get the windows version at [http://www.clamwin.com/](http://www.clamwin.com/).
I don't believe there is actually a real time solution for Linux as on windows.

---

### Post by RequinB4 on 2008-07-06
Antivirus is not needed for linux -- There are no linux viruses in the wild.

Just search these forums for virus lots and lots of reasons/articles why... I don't have time write now to write an essay

Windows viruses, however, can be detected through ClamAV (which is in add/remove), but this is only really useful when you are running samba, a mail server, or are otherwise actively sharing files with a windows box/network

---

### Post by jualin on 2008-07-06
However there are hardly any Linux viruses. And the Linux Viruses that exists usually cannot cause any damage to your computer. Check [this out for more information]("http://librenix.com/?inode=21")

---

### Post by alzie on 2008-07-06
I can't say that it is the best,  but I have used AVG free antivirus for windows in the past and it worked fine there.

Added bonus,  they have a deb file for Ubuntu,  basically download and double click.

[http://free.avg.com/ww.download?prd=afl#tba1](http://free.avg.com/ww.download?prd=afl#tba1)

I hope this helps :)

---

### Post by Frak on 2008-07-06
Go with either AVG or ClamAV, though you don't need to worry about Linux virii, since most of them are only developed in labs as proof-of-concept, not for any malicious intent.

---

