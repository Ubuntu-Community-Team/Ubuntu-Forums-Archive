---
title: "How Do I Install The New Flash Player"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by Cyanarchy on 2012-09-02
I can't see any videos on Youtube or a lot of other content, they all tell me to install the latest version of Flash Player, so I downloaded it, now I don't know how to enable it. The name of the file is: install_flash_player_10_linux.tar.gz.

---

### Post by MG&amp;TL on 2012-09-02
Installing Adobe's version of flash is a pain. You probably want to install Ubuntu's (easier) version by looking for "flashplugin-installer" in the software centre. :)

Unless you've already done that, in which case we have a problem.

---

### Post by pqwoerituytrueiwoq on 2012-09-02
open software-properties-gtk
and enable Canonical Partners
sudo apt-get update;sudo apt-get install adobe-flashplugin adobe-flash-properties-gtk

---

### Post by Cyanarchy on 2012-09-02
> **MG&TL said:**
> Installing Adobe's version of flash is a pain. You probably want to install Ubuntu's (easier) version by looking for "flashplugin-installer" in the software centre. :)

I don't know what software centre refers to, I checked for the "flashplugin-installer" in the Synaptic Package Manager and the Add/Remove Applications thing.

> **pqwoerituytrueiwoq said:**
> open software-properties-gtk
and enable Canonical Partners
sudo apt-get update;sudo apt-get install adobe-flashplugin adobe-flash-properties-gtk

I think I opened the right thing, but I don't know how to enable Canonical Partners. If it's the links in the Third-Party Software, then I did it. And after typing the commands into the Terminal I was presented with this: "E: Couldn't find package adobe-flash-properties-gtk."

---

### Post by critin on 2012-09-02
Adobe flash plugin for Firefox is in the Software Center.  Search for  "flash" and it will come up.  The software center is in the side bar in 12.04.  You can also search in the dash menu.  Software center installs it for you.

---

### Post by NikTh on 2012-09-03
> **Cyanarchy said:**
> And after typing the commands into the Terminal I was presented with this: "E: Couldn't find package adobe-flash-properties-gtk."

Hello , 
forget the properties-gtk and try to install the flashplugin-installer

```
sudo apt-get install flashplugin-installer
``` 

when installation finish , then open Firefox and you will be fine. 

There is another way (better in my opinion) to Install Everything , to play everything in Ubuntu. 

```
sudo apt-get install ubuntu-restricted-extras
``` adobe flash player is included in this package  among others.

Thanks

---

### Post by mlempenau on 2012-09-28
mike@ice-3:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@ice-3:~$ 

It still doesn't work.  What do I do now.  Uninstall?  Try again?

---

