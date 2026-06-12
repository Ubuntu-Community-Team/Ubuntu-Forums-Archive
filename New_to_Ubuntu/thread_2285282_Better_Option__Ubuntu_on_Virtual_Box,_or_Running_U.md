---
title: "Better Option:  Ubuntu on Virtual Box, or Running USB Live?"
date: 2015-07-04
forum: New to Ubuntu
---

### Post by Jdanniel on 2015-07-04
Hello, everyone and happy 4th.

I'd like to experiment with Ubuntu, and would like your opinion about how to install it.  I'd prefer not to install it as the sole OS on my computer, and I'm not ready to set up a dual boot system, because I need access to Windows for work.  I'd need to multi-task.

So, that leaves me with two options:  Install Ubuntu on a virtual machine (I am familiar with Virtual Box, and am using it to test Windows 10), or run it live from a USB stick.

Which would you consider the better of these two alternatives?  I know the virtual machine will probably be slow, but I can multi-task while experimenting with Ubuntu.

Can I install software on my computer with Ubuntu just running live?  Will WINE work on Ubuntu if I run it just live?

Thank you for your feedback!   Jack D.

---

### Post by ajgreeny on 2015-07-04
If you machine is of high enough spec, particularly amount of RAM and at least a dual core CPU, I would suggest that VBox is the better choice than a live USB.  It is worth saying, however, that a full dual boot would be even better.

I have several VMs of various versions of *ubuntu family OSs, and several other Linux distros, plus an old WinXP that I need to update a satnav machine, running very well on a Xubuntu 14.04 64bit host, the guests generally using all 4 cores of my i5-3570K CPU and 4GB out of my 8GB ram.  Video memory is set to the max of 128MB in all of them.  With that sort of resource made available they all run as fast as they do on the hard metal of the computer.

You can't really add software to a live system in the normal way, though a persistent live USB will help to some extent if you make changes to configuration and allows you to save files to the live home..

---

### Post by limbenjamin on 2015-07-04
I would recommend running it in virtual box instead of live. Ubuntu does not require a lot of RAM and most CPUs today would have no problems running a guest OS.

One advantage of virtualbox is that the installation is persistent. That means that you only need to configure and install packages once.

When running off a live CD, you need to reconnect to Wifi network (if applicable) and reinstall all packages every reboot. Yes, WINE will work, but you need to reinstall WINE every time you reboot. It is possible to boot off the live CD and still maintain persistence but the setup might be slightly more complicated.

---

