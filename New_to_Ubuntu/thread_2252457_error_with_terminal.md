---
title: "error with terminal"
date: 2014-11-12
forum: New to Ubuntu
---

### Post by cchardonnens on 2014-11-12
Hi everyone, I am trying to install google hearth in ubuntu gnome 14.04 but it does not let me do it and that what a get in the terminal

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 google-earth-stable : Depends: ia32-libs but it is not installable
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to correct problems, you have held broken packages.
```
How can i go about it and fix the problem 
Thanks a bunch.
A newbie Claude

---

### Post by mastablasta on 2014-11-12
install * ia32-libs* and try again. [http://askubuntu.com/questions/359156/how-do-you-run-a-32-bit-program-on-a-64-bit-version-of-ubuntu](http://askubuntu.com/questions/359156/how-do-you-run-a-32-bit-program-on-a-64-bit-version-of-ubuntu)

although th epackage shouldn't be needed anymore. hmm.

or you can try this: [http://askubuntu.com/questions/454253/how-to-run-32-bit-app-in-ubuntu-64-bit/454254#454254](http://askubuntu.com/questions/454253/how-to-run-32-bit-app-in-ubuntu-64-bit/454254#454254)

---

### Post by vasa1 on 2014-11-12
Someone here at Ubuntu Forums had recently (last six months?) written up a very good post about google earth and the 32-bit/64-bit issue but I've lost the link :(

Found it: [http://ubuntuforums.org/showthread.php?t=2248987&p=13147362#post13147362](http://ubuntuforums.org/showthread.php?t=2248987&p=13147362#post13147362)

---

### Post by jimmyh1972 on 2014-11-12
Download the google earth 64 bit version
open the terminal and copy this code:
sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386
cd /tmp && wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)
sudo dpkg -i google-earth-stable_current_i386.deb
sudo apt-get install -f

that should work in Ubuntu 14.04 64bit

---

### Post by Bloodcage on 2014-11-12
but isn't it necessary to first make a sudo apt update? I thought it's important to update the packages after getting new sources.

---

