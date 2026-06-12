---
title: "Ubuntu does not boot anymore"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2013-06-05
hey,

i am having a big problem .... My ubuntu wont boot. While starting the computer everything seems fine, the Ubuntu load screen appears. Than there is no graphical interface were i usually log in. The terminal is appearing for about 1 or 2 seconds were it orders me to put in my log in information. Than the screen turns black.

I am using the 13.04 Version. I have not changed anything important! I only updated my system with the update manager.

If I use an older Kernel I can use the terminal, log in and update my system with apt-get update and /apt-get dist-upgrade .... BUT there seems to be a problem it tries to install some linux-headers-generic stuff without succeeding. Apt-get tries to do it twice or three times until it finishes the update progress without the installation of the new header. (Switching to the graphical Interface with CTRL+ALT+F7 does not work either!)

The next point is that before the updates it said AMD unsupported hardware as an watermark on my desktop.. I dont know if this has something to do with it. My system was running with the 13.04 version for weeks ....

Thank you !

---

### Post by Krabby.Linux on 2013-06-05
I forgot to mention some things:

1. My windows 7 is running perfectly. Cant be a hardware thing so far!
2. I cant get into failsafex mode! if i start recovery mode than choose failsafeX it asks me that the system needs to mount something. I press yes. Then it says something like dev/sda5/: clean ..... and some numbers of sectors appear
There the system freezes! After 10 Minutes I pressed CTRL+C and I had the option to abort the mounting operation or if i want to manually start recovery it doesnt matter what I chose ... the screen turns black and there is the underline flashing in the upper left corner. No reaction within 15 minutes....

---

### Post by QIII on 2013-06-05
Hello!

When was the last time any portion of the kernel was updated?

Do you use the default open source Radeon driver or the proprietary driver?

If the latter, did you install it from the repo or from the AMD site?


Thanks!

---

### Post by Krabby.Linux on 2013-06-05
Since I can remember I installed the drivers using the synaptic package manager. And I cant remember the last time the kernel has been updated :/.

How can I manage to remove all graphiccard drivers so that I can install new ones using only the terminal?

---

### Post by Krabby.Linux on 2013-06-05
It seems that there are no amd drivers installed. I tried to uninstall them using a tutorial but none of the files were detected so not removed.  I did this from another kernel. It seems that all Kernels do not work except the kernels with "pae".

What should i do ? Always happens if you need something :/

---

### Post by Mark Phelps on 2013-06-06
Just to see what video chipset you have, please open a terminal and enter "lspci" -- and look for the line containing "VGA".  Post that information back here.

---

