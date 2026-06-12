---
title: "cannot download flash player for youtube"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by scientist1971 on 2008-05-12
I went to youtube and where before it was fine now there are no images and when I am asked to download flash player when I go to the link and click on it no dialogue box appears - nothing happens
The only changes I have made to the system are installing foxyproxy and tor but both of these were disabled
any ideas?

---

### Post by scientist1971 on 2008-05-12
I tried to install through the terminal and get this error message
Setting up flashplugin-nonfree (9.0.124.0ubuntu1~gutsy1) ...
Downloading...
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
download failed
The Flash plugin is NOT installed.

anyone know about this?

---

### Post by alzie on 2008-05-12
Thats odd.  You should have got a popup that you were missing plugins.  That is how I installed the flash player in ff3 per psychocats' instructions at [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by scientist1971 on 2008-05-12
hi Alzie, I used that link to install it the first time around
anyway I sorted the parsing proxy problem by system --> preferences --> network proxy
now terminal is telling me flash is already installed (its a shame youtube cannot figure this out!)

richard@richard-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for richard:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
richard@richard-laptop:~$

---

### Post by scientist1971 on 2008-05-12
I installed epiphany and youtube is fine on there - so I have my videos :)
if anyone has any ideas what happened to firefox.....

---

