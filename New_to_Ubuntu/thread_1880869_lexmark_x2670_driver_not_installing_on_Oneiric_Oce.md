---
title: "lexmark x2670 driver not installing on Oneiric Ocelot"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by UweBuurman on 2011-11-14
Downloaded file lexmark-inkjet-08-driver-1.0-1.i386.deb.sh from lexmark, but it won't install.

I first put the file on the desktop, and then  brought up term
From term:[INDENT]       cd to the desktop, so that the file could be found.
sudo lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
[/INDENT]entered the  administrator password as sudo requested

sudo responds in term with this:[INDENT]       sudo: lexmark-inkjet-08-driver-1.0-1.i386.deb.sh: command not found
[/INDENT]
[LIST]
[*] What's wrong here?
[*]Should I be in a directory that has broader permissions?
[*]Where is the usual place to put these downloaded driver files?
[*]What kind of file is this ".sh" file that I downloaded?
[/LIST]
     the downloaded file is big, 3MB.   I guess it's some kind of shell script command file that unpacks itself.  

[LIST]
[*] What about tar?  Why isn't it a tar file?
[/LIST]

[LIST]
[*] Is the bash shell trying to interpret some command in the shell file that it doesn't know? is that what it's telling me?
[/LIST]
 
Cheers & thanks,
Uwe Buurman

---

### Post by acrazyplayer on 2011-11-14
You need to right click on the file go to properties and then go to "permissions". Check the box the says "allow this file to be executed" or something like that. This is all for security reasons.

---

### Post by Soulcage on 2011-11-14
You forgot something ```
sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
```
You might also need to give it persmission like acrazyplayer said.
```
chmod +x lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
```
You can use that command if you want to do it in a terminal.

---

