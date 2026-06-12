---
title: "installing nvidia driver - how and queries"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by joey-elijah on 2008-10-04
I downloaded the most "appropriate" driver for my graphics card (8500gt 1gb) from nivida's site.

**NVIDIA-Linux-x86-100.14.09-pkg1.run**

When i run it as root in terminal it says:

[B] ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).
[/B]

...which i do read, but find no helpful hints or suggestions.

I guess what i'd like to know is a) how to install it and b) i've heard that you can only then boot in "low graphics mode" after installing the drivers... which sounds pointless?

any help thanks!

---

### Post by fooman on 2008-10-04
thats a pretty old driver.  the latest from the nvidia site (and envyng) is 173.14.12

have you tried installing with envyng-gtk (a lot easier then the manual method) ?

is it available from synaptic or in a terminal:

```
sudo apt-get install envyng-gtk
```

after it installs,  open it in applications > system tools > envyng

---

### Post by BDNiner on 2008-10-04
Is there a particular reason that u want to use the latest Nvidia driver? Ubuntu should have detected and offered to install a "stable" Nvidia driver when you first turned the computer on with it installed.

---

### Post by Paqman on 2008-10-04
For graphics card drivers, the first place to go isn't the manufacturer's website (that's the Windows way)

In Ubuntu the OS brings the software straight to you. For hardware drivers go to System > Admin > Hardware Drivers.

If you want a (possibly) less stable but more recent driver, one may be available by installing and running EnvyNG, as mentioned.

---

### Post by joey-elijah on 2008-10-04
oh! i just assumed that the driver on Nivida's website was going to be more "efficient" than the 'one size fits all' that i assumed was the linux offerring. But if it's fine, i'll leave as is! thanks!

---

### Post by jaytek13 on 2008-10-04
Just to answer your original question if you did want to install the latest driver from Nvidia's website:

First you have to get youself out of X and into the command line. Do this by pressing ctl-alt-F1. Once there, you need to kill GDM with this command - sudo killall gdm. This will stop the xserver. Then you can run the Nvidia installer.

The installer may complain about some libraries not being installed. If so, install them by using sudo apt-get install build-essential.

Once the driver is installed you can start it up and get back into X by running the command - sudo gdm start. You should see the Nvidia logo.

If you reboot and it goes into low graphics mode, ctl-alt-F1 again and open up this file with this command: sudo nano /etc/default/linux-restricted-modules-common. Then edit the line Disabled_Modules to look like this:  DISABLED_MODULES="nv nvidia_new"

Then reboot or start up X and the low graphics problem should be solved and you will be using the latest driver.

---

