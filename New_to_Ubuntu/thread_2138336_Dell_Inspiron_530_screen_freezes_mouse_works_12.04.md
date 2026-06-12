---
title: "Dell Inspiron 530 screen freezes_mouse works_12.04 LTS new install"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by Rekhillbill on 2013-04-23
Hello,

I am exceptionally new to Ubuntu.  I installed 12.04 LTS by itself on the subject Dell and it updated OK.

I can use Firefox for awhile, but at some point the screen freezes and while the mouse works, the only option is to unplug the computer.

12.04 boots right up and all is well again, until the next screen freeze.  When it does freeze, part of the screen is usually black.

I have tried to research this issue before posting, but I am not able to find a solution?

Is it possible the pending release of 13.04 would include the drivers that would work better with the Dell?

By the way I really like 12.10 running in a dual boot with Windows 7 on my Toshiba laptop.  I am only going back to Windows, when I absolutely have to because of software incompatibality.

Appreciate any help.

Thanks,
Bill

---

### Post by Rekhillbill on 2013-04-24
Would like to share the solution I found, after further research.

I have a GeForce 8300 GS VGA, see below:

bill@bill-Inspiron-530:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8300 GS] (rev a1)

When I installed 12.04 LTS, by itself on the HD, I was destracted and decided to not do the updates until the following morning.

I noticed that an option offered via the "Additional Drivers" App was to install third party drivers.  The next morning, I forgot about that offer...

So, I installed Synaptic Packager Manager, but being new to this App I could not immediately figure out how to use it.  I went back to the Additional Drivers App and tried to install the 173 driver that it selected.  That option along with the other 173 and an experimental 310 driver failed to install correctly.

Back to Synaptic Packager Manager and a search for the Nvidia 173 driver.  Managed to "mark for installation" the 173 drivers and the resultant update installed the following:

173.14.36-0ubuntu

So far this seems to have worked?

Hope this helps any one else having problems...I suppose the moral of this thread is don't start an installation of an OS unless you have the time & patience to finish the installation, including all the updates.

---

### Post by Rekhillbill on 2013-04-28
Wanted to provide comments on the update to the VGA Nvidia driver 173.14.36.

I used the Additional Drivers App to install the following update:

304.88-oubuntu0.0 Nividia-current-updates

This driver is working much better that the 173.14.36.

I can't find any thing that I don't like about it's performance.

The Nvidia website does provide a good tool for detecting the drivers required for your hardware.

Good luck.
Bill

---

