---
title: "HOWTO:  Install HP Deskjet F4440 All-In-One in Ubuntu 9.10 Karmic Koala"
date: 2010-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by teet on 2010-02-04
This all-in-one is supposed to work out of the box in Ubuntu 9.10 but the scanner didn't work when I plugged it in.  In fact, scanimage -L didn't even list it.

Karmic comes with hplip 3.9.8 which should support the f4440.  I tried installing the newest version of hplip from [http://hplipopensource.com](http://hplipopensource.com) (3.9.12 at the time of writing this) but the script kept aborting due to an error when it was running the make command.  So here is what I did to get the all-in-one working.

1.  Download hplip 3.9.10 here [http://sourceforge.net/projects/hplip/files/hplip/3.9.10/hplip-3.9.10.run/download](http://sourceforge.net/projects/hplip/files/hplip/3.9.10/hplip-3.9.10.run/download)
2.  Open up a terminal and cd into the directory where you downloaded the file ```
cd /home/username/Desktop
```
3.  ```
sh hplip*.run
```
4.  Choose automatic install and answer the few questions it asks you.  It will then automatically remove the 3.9.8 version of hplip which shipped in Karmic (don't worry, you can always reinstall this later through synpatic if you need to), configure, make, and make install the 3.9.10 version.
5.  When it gets done go ahead and hit 'q' to exit the installation.
6.  Reboot your machine.
7.  Open a terminal and type ```
sudo hp-setup
```
8.  Follow the gui setup (I think the defaults are fine).
9.  Everything should be working now.  You can test scanning by running 'xsane'

Note:  I'm not sure if you have to manually add your own user to the 'lp' group or not.  I spent several hours trying to get this stupid all-in-one to work and so I had already done this.  I think the command to do this is ```
sudo useradd -G lp username
``` where username is your username.

Hopefully this will truly work out of the box in Lucid (it's using the 3.9.12 version of hplip).

-teet

Ubuntu 10.04 Lucid Lynx Update:  I upgraded my machine to 10.04 a few weeks ago and just discovered today that my all-in-one didn't "just work".  I am only using the all-in-one for scanning right now (I'm waiting for the ink in an older HP model to run out before switching over fully).  I followed steps 1-9 in the above guide and scanning seems to be working great (I did NOT have to do the sudo useradd -G lp username thing).  I use skanlite for my scanning program.

---

