---
title: "Which nvidia drivers to install?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by fedex1993 on 2008-10-12
I have a GeForce MX 4000 and i cant seem to get the default drivers started is there like some outdated or some older drivers that i could use?

---

### Post by tommcd on 2008-10-12
First, make sure the nvidia driver is disabled under system > administration > restricted drivers. 
Then do this:

For the nvidia GeForce MX 4000 you should use the nvidia-glx-legacy driver. See this thread:
[http://ubuntuforums.org/showthread.php?t=483256&highlight=gforce+mx4000](http://ubuntuforums.org/showthread.php?t=483256&highlight=gforce+mx4000)
and this from the nvidia website:
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html)
Scroll all the way down to the section for the legacy driver to find your card listed there.

Just open synaptic package manager and search for nvidia, and then install nvidia-glx-legacy. Or run in terminal:
```
sudo apt-get install nvidia-glx-legacy
```
then run in terminal:
```
sudo nvidia-xconfig
```
to enable the driver. You will need to log out of X with ctrl + alt + backspace for the driver to be loaded. Before you run "sudo nvidia-xconfig", back up your current xorg.conf for safe keeping in case something goes wrong:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Write back if you need more help.

---

### Post by fedex1993 on 2008-10-12
What about on ibex?

---

### Post by tommcd on 2008-10-12
Well, I have not used Ibex yet, but I would think it would still be nvidia-glx-legacy. Search for the nvidia-glx-legacy driver in synaptic and see what synaptic says about it.
EDIT: If nvidia-glx-legacy don't work, you can get rid of it with **sudo apt-get remove --purge nvidia-glx-legacy**. Then replace your old xorg.conf that you backed up with **sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf**.

---

