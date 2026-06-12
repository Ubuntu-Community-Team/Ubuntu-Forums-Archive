---
title: "[SOLVED] Ubuntu 8.10 - Nvidia Driver &amp;amp;amp;amp; 3D Cube Set Up Solution"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-11-06
These solutions involve downloading the seperate .deb files from the websites listed below, then double clicking the .deb files (once downloaded) to install.

**Nvidia 173 Driver**

Website:[http://packages.ubuntu.com/intrepid/nvidia-173-kernel-source]("http://packages.ubuntu.com/intrepid/nvidia-173-kernel-source")

FILES REQUIRED BY UBUNTU 8.10:

[COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu2_all.deb[/COLOR]
[COLOR="SeaGreen"]nvidia-173-kernel-source_173.14.12-1-0ubuntu4_i386.deb[/COLOR]
[COLOR="SeaGreen"]nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb[/COLOR]

**Nvidia 177 Driver**

Website:[http://packages.ubuntu.com/intrepid/nvidia-177-kernel-source]("http://packages.ubuntu.com/intrepid/nvidia-177-kernel-source")

FILES REQUIRED BY UBUNTU 8.10:

[COLOR="SeaGreen"]dkms_2.0.20.4-0ubuntu2_all.deb[/COLOR]
[COLOR="SeaGreen"]nvidia-177-kernel-source_177.80-0ubuntu2_i386.deb[/COLOR]
[COLOR="SeaGreen"]nvidia-glx-177_177.80-0ubuntu2_i386.deb[/COLOR]

To install these .deb file double click on the icon and click install in the package manager that appears either install the 3 Nvidia 173 (or Nvidia 177) driver files mentioned above, then go to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER VERSION 173 (or VERSION 177 if installed this instead) click enable, an arrow should appear asking you to restart your system.

After restarting your system the driver will enable, select your desktop effects from appearances
and your up and running

**Nvidia Settings (For Both 173 & 177 Drivers)**

Website:[http://packages.ubuntu.com/intrepid/nvidia-glx-177]("http://packages.ubuntu.com/intrepid/nvidia-glx-177") (Green Diamond Link)

Adds System/Administration/NVIDIA X Server Settings (GUI to Ubuntu's Menu Bar)

FILES REQUIRED BY UBUNTU 8.10:

[COLOR="SeaGreen"]nvidia-settings_177.78-0ubuntu2_i386.deb[/COLOR]
[B]
compizconfig-settings-manager[/B]

Website:[http://packages.ubuntu.com/intrepid/x11/compizconfig-settings-manager]("http://packages.ubuntu.com/intrepid/x11/compizconfig-settings-manager")

Adds System/Preferences/CompizConfig Settings Manager (GUI to Ubuntu's Menu bar)

FILES REQUIRED BY UBUNTU 8.10:

[COLOR="SeaGreen"]compizconfig-settings-manager_0.7.8-0ubuntu3_all.deb[/COLOR]
[COLOR="SeaGreen"]python-compizconfig_0.7.8-0ubuntu1_i386.deb[/COLOR]

After installing these 2 files go to System/Preferences/CompizConfig Settings Manager and click "General Options", "Desktop Size" Tab, set Horizontal Virtual Size to 4.

If required click "back" and turn off "Cube Reflection & Deformation" under the effects menu, If you prefer the the 3D Cube effect, switch this on if you prefer the 3D Sphere effect.

**To enable 3D Cube Reflection effects**

If you want 3D cube reflection Effects (requires Compiz Config Setings Manager Installed)

Under SYSTEM>PREFERENCES>COMPIZCONFIG SETTINGS> 

EFFECTS

Click "Cube refelection & deformation" box so tick appears, Then double click on the description part ("Cube refection and deformation" text) on the deformation tag set deformation to "none".

Your 3D cube should now have reflection effects

---

### Post by sharkster2007 on 2008-11-06
If you require the automated internet update version of installing the Nvidia Drivers Automatically, I believe Greyarea2 has found the solution on his thread located at [http://ubuntuforums.org/showthread.php?t=965741]("http://ubuntuforums.org/showthread.php?t=965741") At the 10th posting

---

### Post by sharkster2007 on 2008-11-06
I have looked on the other posts to solve the "grey window title bar" problem that occurs on Ubuntu 8.10, a lot of users report this problem. 

It would appear to be down to the Nvidia driver's (since version 100) as the 169,173 & 177 drivers all have this issue (which Nvidia seems to be aware of now) and as these drivers are not "open-source" the only solution is to wait for Nvidia to make new drivers. 

As Ubuntu/Linux cannot access the source code to them as they are Nvidia's "Closed-source" drivers (unfortunately the "open-source" versions do not yet support 3D Acceleration).

Pity Nvidia hasn't open-sourced their drivers as if they had the Linux community could probably have fixed this rather than us all having to wait :-(

---

### Post by B34ST1Y on 2008-11-06
sticky!

---

### Post by Death5023 on 2008-11-07
I have Geforce 6100 LE and i tryed the 177.80, and i get the error "Desktop effects cannot be enabled. I have been trying many sites and may nvidia things. If you can help me that could be great.

---

### Post by sharkster2007 on 2008-11-07
Sorry Death5023

I too am new to Ubuntu Linux and have little knowledge of it only these instructions have helped myself and others to get it working.

Did you remember to enable the drivers after you installed them? (In the HARDWARE DRIVERS gui)You also need all 3 of the driver files installed to get it working I tried with 2 at first, but didn't work until i found the 3rd one.

eg
> dkms_2.0.20.4-0ubuntu2_all.deb
nvidia-177-kernel-source_177.80-0ubuntu2_i386.deb
nvidia-glx-177_177.80-0ubuntu2_i386.deb

I have heard some Nvidia card drivers are incompatible with the new kernel, whether or not this is the case I do not know.

Does anyone else know how to solve this?

PS: I also would like to know why i've got "amp;amp;amp;" in the thread title as I  did not put it there

---

### Post by loomsen on 2008-12-02
Again I want to point to the HOWTO in my signature.
Missing properties are a big problem almost anyone is aware of.

Further, I'm usually running the newest beta drivers.

So for now this is:
> 
docter[~] nvidia-settings -q all | grep -i driver
  Attribute 'NvidiaDriverVersion' (dhcppc0:0.0): 180.11 
docter[~] 


Actually, this is like always when a new driver is released, it runs very smooth. I've been using the 177 driver from the official repos for comparison purposes, but it just didn't want to work properly.

However, before 180.11 I've been running 180.08 which caused somewhat high system loads, and refused running the PowerMizer properly, as if it was disabled and MaxSpeed set by default. This caused higher Temperatures to max 92°C, where my avg is about 50°C - 60°C.

Well, the newest beta seems to solve this issue, and I can stop hating me for my bleeding-edge-addiction.


Anyway, whichever driver, you should always make sure to have permissions set up properly. 
You may want to read the HowTos in my signature.

Here's an example, without proper permissions X will deny(=not work as intended) access to DRI(=direct rendering infrastructure).
This is equal to passing the indirect rendering option when running compiz for instance. This disables you video devices native direct rendering and 3D enhancements, and uses Xorgs built in indirect rendering infrastructure, which is significantly slower, and as the pictures show, lack the potential your video device offers.

left without proper permissions, just created a user and imported the same profile as the one I use on the right pic, my base account with apropriate permissions:
[[img]http://www.ubuntu-pics.de/thumb/6682/screenshot_wo_dri_AUi7Zh.png[/img]](http://www.ubuntu-pics.de/bild/6682/screenshot_wo_dri_AUi7Zh.png) [[img]http://www.ubuntu-pics.de/thumb/6681/screenshot_22_PyHXfv.png[/img]](http://www.ubuntu-pics.de/bild/6681/screenshot_22_PyHXfv.png)

So, if you experience random crashes of compiz, or same bad aliasing as in the left picture above or any other performance issues, and if you're sure you installed and enabled an apropriate nvidia driver for your device, this should be the first to fix.

As I said, follow links in my sig to read more.

---

### Post by pSYcl0Ne on 2009-03-09
I would just like to say A BIG THANKYOU! Sharkster, I have been tracking down so many threads and you have layed them all out here for me! So far Iam a total linux n0ob. Although I am using hardy not intrepid this is definately a step in the right direction as I have also been trying to figure this out. 

I might suggest you do a little research on a program called Keryx as well though. I haven't got it working yet - as again there are dependancy issues (python) but it looks like a tool to make other installs for us internetless crew a whole lot easier when it works. It's basically a stand-alone apt-get/synaptic pack grabber that creates a project in debian or ubuntu and then can be used on a windows puter on the web to get required packages. 

 [http://keryx.betaserver.org]("http://keryx.betaserver.org")

Yay! My first post!

---

### Post by EXCiD3 on 2009-03-09
> **pSYcl0Ne said:**
> I haven't got it working yet - as again there are dependancy issues (python)

What is the dependency issue with Keryx? 99% of the time the error you get is not using the proper syntax when creating a project. Make sure you used "python keryx.py --create <project name> debian" and it will work just fine.

---

### Post by kijosmith on 2009-09-19
Any suggestions for those of us using jaunty? With Nvidia Geforce Go 6800 Ultra? And getting the cube to work?

---

