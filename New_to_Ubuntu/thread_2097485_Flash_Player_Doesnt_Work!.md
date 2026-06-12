---
title: "Flash Player Doesnt Work!"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by V3L1M1R on 2012-12-23
I cant make flash player work. I try adobe-flash player and then flashplugin-installer and nothin. Just open blank screen when opening a SWF of FLV.

I have:
Ubuntu 12.10
Kernel: 3.5.0-21-generic

> r00t@ubuntu:~$ dpkg -l | grep -i flash
ii  flashplugin-installer                     11.2.202.258ubuntu0.12.10.1               i386         Adobe Flash Player plugin installer
ii  get-flash-videos                          1.25~git2012.06.27-1                      all          video downloader for various Flash-based video hosting sites
ii  gnash                                     0.8.11~git20120629-1ubuntu1               i386         GNU Shockwave Flash (SWF) player
ii  gnash-common                              0.8.11~git20120629-1ubuntu1               i386         GNU Shockwave Flash (SWF) player - Common files/libraries
ii  libjs-swfobject                           2.2+dfsg-1                                all          tool to embed Flash content into webpages



Any help? What to do?

---

### Post by Rfdp on 2012-12-23
You could try this:
[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)
didn't work for me, but I found a lot of positive feedback for the Add-on

---

### Post by carl4926 on 2012-12-23
You need to remove gnash

---

### Post by ajgreeny on 2012-12-23
Just out of interest, what graphic card do you have, as some ATI cards will not work at all with flash version 11.2.

The add-on for firefox linked to above is very good if you have some conflicting flash applications on the system, but will not help when used in the default manner if you have the ATI graphic card problem, so if that is your situation have a look at [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") which is the last flash version that works on my computer with an ATI 9200SE card.

---

### Post by V3L1M1R on 2012-12-23
Finaly :) 
I remove gnash, and with FlashAid install 
```
https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz
```and install addon NoScript for security reasons :)

TNX every1 4 suggestion ;-)

P.S. [ajgreeny]("http://ubuntuforums.org/member.php?u=27747")
I have RV350 AS [ ATI Radeon 9550]

---

