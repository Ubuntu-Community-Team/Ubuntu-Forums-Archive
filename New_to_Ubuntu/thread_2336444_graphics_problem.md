---
title: "graphics problem"
date: 2016-09-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-09-08
running ubuntu 16.04. was messing around and messed up graphics. when i get to the logon screen all i get is a bunch of horizontal lines. and control alt f  doesnt work. trying to boot into the recovery also failed  get the message in read only mode. i do have a live cd that works.any ideas/tks

---

### Post by grahammechanical on 2016-09-08
At the recovery menu we can select Network. That will do 2 things. It will set up an internet connection. Which we may need if we are going to download and install software such as a video driver or an alternative window manager to get us to a working desktop. It will also put the file system in read/write mode which we need if we are going to edit system files from the root shell prompt.

There are other recovery menu options that will also put the file system into read/write mode such as fsck. And there is a command that will also do it. But when I need to work from the recovery menu root shell prompt I simply run Network first.

Regards

---

### Post by rburkartjo on 2016-09-08
tks grah

---

### Post by rburkartjo on 2016-09-08
this is how i fixed. took grah advise and reinstalled ubuntu-desktop and unity after i enabled network and the used the root terminal. then booted up normally . this put me in low graphics mode and threw me into a virtual terminal.typed in sudo lightdm stop and this threw me back in normal mode. fixed

---

### Post by rburkartjo on 2016-09-08
ok spoke to soon when i try to start ubuntu the normal way it still throws me into low graphics mode then to a virtual terminal then after i log in while in the virtual and then type sudo lightdm stop it then opens the graphic login screen and i can log in.j

---

### Post by rburkartjo on 2016-09-08
ok really fixed it. ran these commands in virtual terminal

sudo apt-get install gdm
 1062  sudo service gdm restart
 1063  sudo service lightdm restart
 1064  sudo apt-get install --reinstall unity-greeter
 1065  sudo apt-get update
 1066  sudo dpkg-reconfigure lightdm
 1067  sudo dpkg-reconfigure lightdm 
 1068  sudo gedit /etc/lightdm/lightdn.conf
 1069  sudo gedit /etc/lightdm/lightdm.conf
 1070  reboot

---

