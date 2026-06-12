---
title: "Linux Portability to Another PC - Installation on USB Disk Drive"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-04-17
I recently installed four different versions of Linux on an external USB drive.  The installations included Ubuntu 12.04, Mint 13, Lubuntu LXLE, and Linux Lite.  The system used for the installation was a nine year old PC with Intel Celeron Processor and Gigabyte Motherboard.

Sometime later the USB disk drive was connected to a brand new 64 bit Windows 7 computer.  Only Lubuntu LXLE and Linux Lite booted up and ran.  Ubuntu 12.04 and Mint 13 both failed.

Does anyone have any theories on why those two installations failed to boot on the new hardware?  Perhaps that result is not surprising for those with a better understanding of Linux distributions and hardware compatibility.

---

### Post by oldfred on 2014-04-17
Probably video issues.
IF computer was that old you used a 32 bit version, and new computer could have used 64 bit but that would not have mattered.
The video issue depends on default video card/chip & what driver is being used.

I have nVidia card and have to use nomodeset to get anything to boot until I install nVidia driver. But then with nVidia driver it will only work on systems with nVidia.

What video card/chip was on Windows 7 computer?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by KAWill70 on 2014-04-18
Thanks for the help.  One interesting question is whether booting from Flash and running "Live" is more flexible in adapting to different hardware compared with the same distribution after installation on disk.

The Windows 7 computer has graphics integrated with the Intel i5 Processor.  It may be what is called Haswell HD4600.

The USB Disk was created on the nine year old PC with Gigabyte motherboard which has the often troublesome SIS 661FX graphics.  I have had to use nomodeset and xforcevesa at times to boot certain distributions.

---

### Post by oldfred on 2014-04-18
Your Windows 7 computer then may have needed one or more boot parameters for Intel. Often nomodeset does not work or work best for Intel.
Also the 64 bit version for that computer would be a lot better.

Post above by ubfan1 shows most of the boot parameters that worked with 13.10. Intel made major improvements to kernel, support software and video drivers and most of that is now only in 14.04. Driver improvements now coming along for even future processors are also updating and improving older chips.

       (13.10) Intel graphics driver fails to manage HD 4600 on HP Split x2
[http://ubuntuforums.org/showthread.php?t=2191109](http://ubuntuforums.org/showthread.php?t=2191109)
Needed all the settings??


 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

---

### Post by Mama_Hadija on 2014-04-18
maybe the file system was altered by the windows system
but a side question, why would u need multiple versions of linux distros, i suggest working with one

---

### Post by oldfred on 2014-04-18
Lots of users like to try different things.

I have every install of Ubuntu since 10.10 so I could test each new install, and now only with 14.04 have started to overwrite the obsolete installs. I often have multiple installs so I can experiment with settings and not have to worry that I may mess up my main working install.

---

### Post by KAWill70 on 2014-04-18
Thanks all once again for the help.  On the multiple installs, I was just evaluating different distributions to see what I liked and which one worked best on my older PC.  It was also a learning experience as I am new to Linux.  The intent is to focus on just one after the initial testing.

Oldfred - Many thanks for all the boot information.  That may be a great help for my old PC with the SIS 661FX graphics.  It will not boot Ubuntu and many variants beyond 12.04.0.  The XServer changed around 12.04.2.  I could boot Lubuntu 13.10 using nomodeset and xforcevesa but that did not work with the final Lubuntu 14.04 beta which was quite disappointing.

Hopefully the notes from ubfan1 will provide a solution for SIS 661FX graphics in addition to the new Win 7 computer when using earlier distributions.  I guess one cannot expect a given distribution to necessarily support future hardware that it knows nothing about.  In that case I was using Ubuntu based distributions from two years ago on a brand new Win 7 computer built in 2014.

---

### Post by oldfred on 2014-04-18
I find in my 12.04 lots of old video drivers. 21

fred@fred-Precise:~$ dpkg -l|grep xserver-xorg-video|wc -l
21

And it still shows a SIS driver, but do not know if that is correct for you or not.
fred@fred-Precise:~$ dpkg -l|grep xserver-xorg-video
ii  xserver-xorg-video-sis                 1:0.10.3-3build2                                    X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb              1:0.9.4-2build2                                     X.Org X server -- SiS USB display driver

---

### Post by KAWill70 on 2014-04-18
Thanks very much for the SIS Driver information.  That might be just what I need for the older computer.

Tonight I had quite a surprise when both Ubuntu 14.04 and Lubuntu 14.04 booted on the old computer with SIS 661FX graphics, and no additional boot parameters were needed.  That didn't seem to be the case with version 13.10.  However, I do get the same message that no SIS 630 compatible bus was detected and some module was "not inserted".

Lubuntu 14.04 seems to run fine from what I can tell without that "module".  However, Ubuntu 14.04 runs so slowly that it is unusable.  I can only enter one character every few seconds in the search box.  I suspect my CPU is handling the video card function!

---

### Post by oldfred on 2014-04-18
Unity needs a good video system and more RAM to work well.
My systems from about 2006 do run Unity, but laptop with only internal Intel chip & 1.5GB of RAM barely runs Unity. I change to fallback/flashback and that is acceptable.
I also can run Unity ok on my Desktop with 4GB of RAM and an old nVidia 9600GT which is a decent if older now video card. But I prefer fallback as monitor is 4:3 and panels at top & bottom use space better. Plus I just like the old menus, old dog does not like new tricks. :)

---

### Post by KAWill70 on 2014-04-19
Thanks for the comments on Unity.  Ubuntu 14.04 ran beautifully on my new Win 7 computer but I will not spend any more time trying it on the nine year old low performance computer.

With the good news that I can boot Lubuntu 14.04 live on that system, I installed on disk last night.  It also runs just fine, and I'm now thinking Lubuntu 14.04 will be my primary installation.

The only surprise last night was that I did not pay attention to my boot loader configuration and the first boot attempt failed!  It's good to learn the hard way that new and old distributions don't mix very well on the same disk unless you are handling the boot loaders properly.  By the way, the messages shown during installation of Lubuntu 14.04 differed significantly from the messages displayed by many of the two year old distributions.

---

### Post by KAWill70 on 2014-04-19
One unknown with Lubuntu 14.04 is why it runs so well on the older computer despite the SIS 661FX graphics problem.  A message is displayed during boot that a graphics related module is not inserted.  I intend to pursue that situation and see what I can learn.

---

### Post by KAWill70 on 2014-04-20
Here is an interesting update regarding the SIS Graphics problem on my nine year old PC.

The boot message that no SIS630 Compatible Bus was found does not appear to have anything to do with graphics capability.  The driver that is apparently not loaded is defined as SIS630_smbus.  An Internet search on smbus reveals that it is a 2 wire serial control bus similar to I2C which has widespread use as a low cost and simple interconnect.  The name smbus stands for System Management Bus.

The smbus handles such things as system power (on/off), battery, fans, case sensors, and other similar functions.  This may finally explain why many distros cannot power off that computer at shutdown!

It is possible there are SIS 661FX graphics issues in addition to the smbus problem.  Mint 16 and recent releases of Ubuntu run extremely slow as though the processor was handling the functions of a graphics adapter.

---

### Post by mörgæs on 2014-04-20
Here's some more on SIS if you want to dig deeper:
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

