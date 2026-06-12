---
title: "Multitouch and synaptics-dkms errors"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by Dan Pat on 2012-01-22
I'm running Ubuntu 11.10 on an HP Envy 14 installed with the Desktop CD. I'm also dual booting with Windows 7. This is only my second week using Linux and no other threads I've found online have solved my problem, so hopefully I can get some useful support here. 

When I first installed Ubuntu, my system supported two finger scrolling, two fingers for right click, and three fingers for middle mouse button, but I have since lost that functionality. My only guess as to what happened is that I could have installed a package through another tutorial that is causing problems with these gestures, but I really have no idea. Currently I can right click with two fingers if I'm careful, but it usually requires multiple attempts to keep the dialogue open so that I can select an option. Two finger scrolling does not work at all. If I place one finger on the pad after another, the cursor jumps across the screen. 

One potential fix that I found online on [a blog specific to running Ubuntu on the Envy 14 ]("http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html#comment-form")involves installing "synaptics-dkms_1.1.1_all.deb", but I receive errors when installing it:

```
dan@dan-HP-ENVY-14-Notebook-PC:~/Downloads$ sudo dpkg -i synaptics-dkms_1.1.1_all.deb
Selecting previously deselected package synaptics-dkms.
(Reading database ... 173635 files and directories currently installed.)
Unpacking synaptics-dkms (from synaptics-dkms_1.1.1_all.deb) ...
Setting up synaptics-dkms (1.1.1) ...
Loading new synaptics-1.1.1 DKMS files...

Loading tarball for synaptics-1.1.1

DKMS: ldtarball Completed.

Creating symlink /var/lib/dkms/synaptics/1.1.1/source ->
                 /usr/src/synaptics-1.1.1

DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.0.0-14-generic -C /lib/modules/3.0.0-14-generic/build SUBDIRS=/var/lib/dkms/synaptics/1.1.1/build modules....(bad exit status: 2)
ERROR (dkms apport): binary package for synaptics: 1.1.1 not found
Error! Bad return status for module build on kernel: 3.0.0-14-generic (x86_64)
Consult /var/lib/dkms/synaptics/1.1.1/build/make.log for more information.
dpkg: error processing synaptics-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 synaptics-dkms

```I'm not sure these problems are related, but I can only guess that these errors are hindering my progress. I've tried uninstalling and reinstalling dkms to no avail. I've exhausted all the relevant Google searches I can think of and I've reached the end of my limited knowledge of the topic. I would really just like to be able to use two finger scrolling and three fingers for middle mouse button. 

Thanks in advance for your help! :D

---

### Post by Dan Pat on 2012-01-30
Bump.

I also reinstalled Ubuntu since posting this and experienced the same results. Multitouch worked great for a while but then reverted back to the buggy non-functional state. Does anyone have any clue on this one? Should this thread be in Main Support? I'm not sure what distinguishes the two, but I'm still a Linux beginner!

---

### Post by DustinMoriarty on 2012-08-06
I have similar problems using Ubuntu 12.04.  I have and HP Envy 14 with dual boot with Windows 7.  The touchpad no longer shows up in the settings.  I only have left and right click with no two finger scroll anymore.  

I remember having to do a lot of futsing with drivers when I first did the install, but I can not remember what I did on that late night a few months ago.

I update fairly regularly so it is happened to say if it happened following an update or not.  The problem was actually accompanied by a session where I lost some of my mouse functions in Windows 7.  The functions where restored to Windows 7 after a reboot.  Is it possible that Windows 7 is actually effecting some sort of low level software that would effect Ubuntu's use of the touchpad?

---

