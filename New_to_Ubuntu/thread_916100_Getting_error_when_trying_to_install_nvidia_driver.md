---
title: "Getting error when trying to install nvidia driver."
date: 2008-09-10
forum: New to Ubuntu
---

### Post by GameGuru on 2008-09-10
This is what happens to me:

The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7333kB of archives.
After this operation, 5939kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted nvidia-glx 1:96.43.05+2.6.24.13-19.45 [7333kB]
Fetched 7333kB in 41s (178kB/s)                                                
(Reading database ... 95186 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)

What can I do?

---

### Post by Titan8990 on 2008-09-10
Try:

sudo apt-get install envyng-gtk


Envy will download and install your drivers for you. It is a handy tool.

---

### Post by vairon on 2008-09-10
hey i got teh same i download envy but nothing i try to do the 3D cube thing but i think is not available fornvidia cards thank you and reply:lolflag::lolflag::lolflag::lolflag:

---

### Post by GameGuru on 2008-09-10
I get an error:

jason@jasonscomputer:~$ sudo apt-get install envyng-gtk
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  envyng-core
The following packages will be REMOVED:
  nvidia-glx-new
The following NEW packages will be installed:
  envyng-core envyng-gtk
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/232kB of archives.
After this operation, 27.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 95186 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)

What can I do?

---

### Post by knix on 2008-09-10
> **vairon said:**
> hey i got teh same i download envy but nothing i try to do the 3D cube thing but i think is not available fornvidia cards thank you and reply:lolflag::lolflag::lolflag::lolflag:

After you download Envy, You have to install the drivers.
Application>> System Tools>> EnvyNG. Mark the right driver for your card. click Install or apply or whatever it is.

Also, install compizconfig-settings-manager in Synaptic and access it via System>> Preferences>> Advanced Desktop Effects Preferences, and enable desktop cube and rotae cube.

For those of you using Apt or Synaptic to install drivers, I highly recommend that you use nvidia-glx-new-envy

---

### Post by TheUbGuy on 2008-09-10
> **vairon said:**
> hey i got teh same i download envy but nothing i try to do the 3D cube thing but i think is not available fornvidia cards thank you and reply:lolflag::lolflag::lolflag::lolflag:

Of course it is - you just need to enable desktop effects, then pick the cube from the CCSM (Compiz Config Settings Manager). IF you have correctly enabled the NVidia drivers, then go to
System ->Preferences->Appearance. Click on the Visual Effects tab then select Extra.

If you don't have CCSM (under System->Preferences->Advanced Desktop Effects), then go to Synaptic Package Manager under System->Administration, search for compiz, and install compizconfig-settings-manager. That will add the entry (Advanced Desktop Effects) that I mentioned above. You should then be able to pick the Desktop Cube.

---

### Post by Kinetic_lord on 2008-09-10
Envy works with ATI and NVIDIA card perfectly, the problem is compiz fusion... you need to install "advanced desktop effects"

Steps:
1. Go to System->administration-> update manager click on it you will get update manager window there click install updates.(it will update all new packages)

2. then go to system-> administration->synaptic package manger click on it.
it will ask you password type your login password and press enter

3. Now you will get a Synaptic package manager window in that click on search button and type compiz then it will show all compiz packages right click on packages name you will see its description and option as mark for installation click it.do it like for all compiz related packages.

4.then click on apply Button, now compiz get installed on your computer.

Now if you want to do setting go to system->preferences then you will see advanced desktop effects click on it to do some settings, before go to system->preferences->appearance click on it in this window click on visual effect button then in that window click on extra.

This way you can enable the compiz cube...
btw, you only have 2 workspaces at first, right click on the "desktop selector" and click preferences. Increase number of colums unil you have 4.

---

### Post by knix on 2008-09-10
> **Kinetic_lord said:**
> Envy works with ATI and NVIDIA card perfectly, the problem is compiz fusion... you need to install "advanced desktop effects"

Steps:
1. Go to System->administration-> update manager click on it you will get update manager window there click install updates.(it will update all new packages)

2. then go to system-> administration->synaptic package manger click on it.
it will ask you password type your login password and press enter

3. Now you will get a Synaptic package manager window in that click on search button and type compiz then it will show all compiz packages right click on packages name you will see its description and option as mark for installation click it.do it like for all compiz related packages.

4.then click on apply Button, now compiz get installed on your computer.

Now if you want to do setting go to system->preferences then you will see advanced desktop effects click on it to do some settings, before go to system->preferences->appearance click on it in this window click on visual effect button then in that window click on extra.

This way you can enable the compiz cube...
btw, you only have 2 workspaces at first, right click on the "desktop selector" and click preferences. Increase number of colums unil you have 4.

Honestly, it's simpler to click the reload button in Synaptic. Compiz is installed by default, but you will need compizconfig-settings-manager to enable the cube (I don't know why it isn't by default).

---

### Post by GameGuru on 2008-09-10
Ok using Envy I believe I have successfully upgraded the nvidia drivers (how do I verify this) but I still can only choose resolutions of 640x480 and 800x600.  It does say UNKNOWN in the big box and when I click Detect Displays it doesn't do anything. 

Please, I need help.

---

### Post by Kinetic_lord on 2008-09-10
simple, configure the display: look on to you're monitors back to see it's version. (Sony, rd 1456 or stuff like that), and just select the monitor you have, the model you have, in the other tab the graphics card you have and that's all. btw, after installing Envy you need to install the video card too using envy (Applications>>System Tools>>envy) :)

---

### Post by GameGuru on 2008-09-10
Where do I configure the monitor at?  I am brand new to Linux.

---

### Post by Kinetic_lord on 2008-09-11
After booting, before log-in, a window will appear (has got to do with low-graphics mode) there are 3 buttons, you press the "Configure" one.

---

### Post by Kinetic_lord on 2008-09-19
It worked? (if yes press blue ribbon:D)

---

