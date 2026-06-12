---
title: "Avant Window Manger is gone!"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-09-06
I followed the following instructions to get some applets for avant window manager and after i followed the instructions I task killed avant and now its gone. I tried reinstalling it using the add/remove button under the applications menu but it said there was a conflict :
```
 Website: http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html

Installation of Awn applets
To install these applets you have to enable an additional repository from reacocard. For that open the /etc/apt/sources.list file in your favorite editor and append the following line to it.

#FILE: /etc/apt/sources.list
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main

Now update the repository and install the following package. NOTE: It is assumed that you have already installed the Avant Window Navigator.

$ sudo apt-get update
$ sudo apt-get install awn-core-applets-bzr

That is it. Now you can find all the applets in the awn manager which is accessed from GNOME Menu System>Preferences>Awn manager .
```


please help

---

### Post by Bigbob22 on 2008-09-06
Nvm, I figured out how to fix it. I just did this: 
```
 sudo apt-get install avant-window-navigator awn-manager libawn0
```
The applets didn't work.
How do you get the stacking applet for awn?

---

