---
title: "Building Custom PC"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by john475 on 2015-10-29
I am planning on building a custom PC and am wondering if anyone has any experience with putting the ubuntu OS onto a brand new system.  Specifically: will i need to start the system in a simple text mode to get the graphics drivers in order to run the system properly with the graphics card, or will the system just run the graphics automatically?  Is there a linux OS that can run high end graphics cards without having to download drivers and run them through wine or some such other program?  Any advice on this topic would be much appreciated.

---

### Post by grahammechanical on 2015-10-29
Are you thinking of putting another OS on this machine other than a Linux OS? That is when you will get problems if you do not take steps to avoid them before hand.

Motherboards released over the last few years have UEFI boot systems and not BIOS boot systems. So, read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If Ubuntu is the only OS then things are much simpler. Build the machine, plug it in and switch on and see what the UEFI boot system has to say. The motherboard will have its own basic video mode. Doing this will test if the motherboard is working correctly before installing an OS. You should see the results of some Power On Self Tests (POST) and a message saying something like "Insert disk with OS on." Now you are good to go. 

Now you can restart and put in the Ubuntu install DVD/USB stick. It will load. It has an OS and an open source video driver. So, you can try Ubuntu before installing it. When you decide to install select the Erase disk and install Ubuntu option. And the installer will do its job. If you also tick the box "install third party software" you will get some free but proprietary audio and video codecs and a proprietary video driver installed as well.

Ubuntu will install and run on the open source video driver and we have a utility called Additional Drivers that will find and give us a selection of 4 proprietary video drivers as well as the open source video driver and we can activate whatever one we want.

We can also install the proprietary audio and video codecs after installation by searching the Ubuntu Software Centre for Ubuntu Restricted Extras. So, we are not forced to tick the box "install third party software."

If you plan on using the very latest video cards, then you should plan on using the very latest version of Ubuntu. Each new version of Ubuntu has the newer stable video drivers. That is how Ubuntu keeps update date with the work of Linux developers in keeping up to date with the latest hardware developments.

Regards.

---

### Post by john475 on 2015-10-29
Thanks this helped a lot.

---

### Post by Geoffrey_Arndt on 2015-10-29
Also, the most Linux friendly chipsets are Intel . . . for graphics and for wireless.    Drivers are built into kernel and so users don't need to mess around with proprietary driver searches/installs.   I'm not a gamer, the Intel Iris Pro 5200 graphics system on my laptop will run most anything available - although for serious gamers, Nvidia is the best choice.

---

### Post by Bucky Ball on 2015-10-30
*Thread moved to **New to Ubuntu**.*

Research compatible components (read wireless and graphics in particular), build the machine, install Ubuntu, see what happens re. graphics. 

Depending on the graphics card it will either work 'out of the box' because the drivers are already part of the kernel; you will need to download the appropriate third-party Linux drivers for your card using 'Additional Drivers' app (simple); you will need to download and install the third-party drivers from a third-party site (more time consuming but generally also simple).

No, you don't need Wine to install graphics drivers (definitely not advisable or worth attempting). In fact, you don't need Wine, unless you are planning on using a heap of Windows stuff, much of which will not work that great in Wine anyhow, and if your plan is to use a heap of Windows stuff in Ubuntu using Wine, make a new plan (like look for Linux alternatives to the software apps you are using) or stick to Windows. :)

Good luck.

---

### Post by oldfred on 2015-10-30
I am not a gamer and use either Intel internal video or an older nVidia card.

 22-Way Comparison Of NVIDIA & AMD Graphics Cards On SteamOS For Steam Linux Gaming Oct 2015
[http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1](http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1)

I made the mistake of trying to reuse an older power supply and could not get system to work.New power supply was the solution. 

You cannot load drivers thru .wine.
Ubuntu should have all the drivers you need, but if you build a bleeding edge, i.e. very newest everything you may need to download newer kernels & drivers from ppa. And only use the newest version of Ubuntu as it has newer kernel & drivers. Distributions take a bit to catch up with newest kernel & drives when they are released. 

      
 Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

