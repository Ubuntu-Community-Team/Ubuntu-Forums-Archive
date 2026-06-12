---
title: "Computer Sleeping"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by chase321 on 2012-06-30
Hello,
a few weeks ago i installed a screensaver program, due to the lack of screensavers in 12.04, but i did not like the program, and i uninstalled it. however, now when i leave my computer alone for a while, it goes to sleep and my screen shuts off. basically it locks itself. this is annoying for me simply because i have a mapped network drive from my computer that runs to my other computer in my house... and when my computer locks itself, i can no longer access said drive.

all of my setting in the system setting are set so that the pc should never lock...

any ideas??

---

### Post by Frogs Hair on 2012-06-30
If you installed Xscreen saver you need to reinstall the gnome screen saver even though it has no images. Then you can set the sleep time from brightness and Lock. Removing the gnome screensaver is part of installing Xscreen saver so it needs to be installed .```
sudo apt-get install gnome-screensaver
```

---

### Post by lrcaballero on 2012-06-30
Try the following:

On Ubuntu 12.04
Right Click
All Settings
Under Personal
Go to Brightness and Lock

check your settings

good luck,

lrcaballero

---

### Post by chase321 on 2012-06-30
trying it, will post if it works thanks :)

---

### Post by chase321 on 2012-06-30
unfortunatly, i think something in the installation failed, 


chase@Chase-Linux:~$ sudo apt-get install gnome-screensaver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 liboil0.3:i386
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gnome-screensaver
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/107 kB of archives.
After this operation, 422 kB of additional disk space will be used.
Selecting previously unselected package gnome-screensaver.
(Reading database ... 292752 files and directories currently installed.)
Unpacking gnome-screensaver (from .../gnome-screensaver_3.4.1-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up gnome-screensaver (3.4.1-0ubuntu1) ...
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

after running this my computer still goes back to sleep

---

### Post by chase321 on 2012-07-02
ok, so now mysteriously, my computer stays awake all the time now... so thread solved

---

