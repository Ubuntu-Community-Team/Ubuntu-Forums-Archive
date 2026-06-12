---
title: "Installed Ubuntu. Graphics not detected. Errors"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by tausch86 on 2012-06-28
black screen
acould not write bytes: Broken pipe
a * Stopping save kernel messages
aa * Checking battery state... 

* Stopping System V runlevel compatibility 

then it says my graphics can't be detected correctly so i have to do that manually and it takes me to a gui with 4 options

Turn on low-graphics mode for just one session
Reconfigure graphics 
Troubleshoot the error
Exit to console

and it won't let me select any of those options with keyboard or mouse (i've literally hit every button on my laptop)
I'm running along side with windows 7 and this is ubuntu 12.04

---

### Post by mikewhatever on 2012-06-28
Can you post the hardware specs.

---

### Post by Dlambert on 2012-06-28
> What are these options?

[B]nomodeset
[/B]

The newest kernels have moved the video mode setting into the kernel. So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a black screen. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. 

Add that to grub when you boot:)



Then to make it permanent: > How to permanently set kernel boot options on an installed OS (not wubi)

To permanently change the default kernel boot options, press ALT+F2 or open a terminal from system > accessories > terminal. Type in the following command:

Code:
**gksudo gedit /etc/default/grub**
a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
Code:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
**add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:**

Code:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
GRUB_CMDLINE_LINUX=""
Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

Code:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
Now in the terminal, run the following command to update your grub configuration with the new default settings:
Code:
**sudo update-grub**
Thats all. 

---

### Post by Dlambert on 2012-06-28
And if you do not know how to get in grub. Hold shift after you pc boots before the OS would usually start. The hit e to edit the command, then find the line specified about and add nomodeset. ;) Source:[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mapes12 on 2012-06-28
Can you run the Ubu live CD or USB (depending on how your system boots)?

---

### Post by tausch86 on 2012-06-28
system specs:

sony vaio vpcsb190x (don't get this model btw(or vaio))
8gb ram
intel i5-2520 @ 2.50 GHz
AMD Raedon HD 6470M
64 bit

yes. I ran the cd and had no problems with it until I installed.

I'll try that grub thing. Thanks!

---

