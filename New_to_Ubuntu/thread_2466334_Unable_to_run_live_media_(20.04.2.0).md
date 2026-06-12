---
title: "Unable to run live media (20.04.2.0)"
date: 2021-08-25
forum: New to Ubuntu
---

### Post by bewildered-newbie on 2021-08-25
My old (but still ticking) HP505 desktop has an integrated Nvidia display adapter on MB and i assume a proprietary Nvidia driver (**GeForce 6150SE nForce 430** probably obsolete). I can boot live media but the resulting screen display cannot be viewed correctly -> distortions, mis-shapen buttons, etc. Clicking on the erratic screen may result in serious problems !!  Apparently there may be a newer driver avail but downloading and installing it is way beyond my Linux newbie skills (i'm a recovering Windows user). Also the BIOS is probably down-level. Any hope for a nice guy like me ??  Thanx.

Bewildered Bob

---

### Post by blackbird34 on 2021-08-25
Hi. Have you checked the "Additional Drivers" section of Ubuntu settings?  (search for "software and updates" and click on the "additional drivers" tab. See [https://itsfoss.com/install-additional-drivers-ubuntu/](https://itsfoss.com/install-additional-drivers-ubuntu/) for more detailed instructions)

If this doesn't work, have you considered one of the other Ubuntu variants? Pop! OS includes Nvidia drivers in its installer,  and most others distros allow you to tick a box and download them while installing too.

---

### Post by grahammechanical on 2021-08-25
Due to a problem with my landline causing a very low internet download rate I gave up waiting for the HP support web site to load. It is useful to us if you give detailed information about your hardware. What CPU? How much RAM? Does the Nvidia graphic adapter have its own memory?

An integrated graphic adapter can mean that it uses memory from the motherboard's allocation of RAM. It could also mean that the CPU might be needed to do the video processing. These things can be the cause of the video problems. So, you might be better off trying one of the flavours of Ubuntu such as Xubuntu or Lubuntu as these distributions require less memory and less video processing power.

Ubuntu and its flavours come with a very good open source video driver. So, if Nvidia no longer supports your Nvidia graphic adapter it is not such a problem. Nvidia often drops support for its older graphic adapters.

I am pasting a link to some Ubuntu boot options. If you can get to the first screen of the installer press any key to access to advanced boot options page. At that page press F6 - other options and from the menu select nomodeset. You will find the instructions at section six of the Changing the CD's Boot Options heading. Selecting nomodeset allows the installer to run without a video mode being set and that may overcome the problem long enough for Ubuntu to be installed.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you get Ubuntu installed and loading to a useable desktop then open Software & Updates>Additional drivers tab. If the OS it connected to the internet it will search for a Nvidia driver if one is available.

Regards

---

### Post by bewildered-newbie on 2021-08-26
Thanx to the 2 posters for their quick response.  Apparently the current driver (Nvidia C61 GeForce 6150SE force 430) is latest one remaining for Linux users. Nvidia is still publishing driver updates but only for Win 10.

As a certified and card-carrying  Linux "newbie" it would help a lot if these thoughtful recommended fixes were prioritized to avoid wasted effort or un-doing a valid fix and making things worse. Will someone consolidate contents of both posts into a single prioritized plan for me ??  Thanx.

Bewildered Bob

ps: before installing Linux the PC successfully ran Win 10 (a known resource hog). Isn't it interesting that altho Linux is believed to run successfully on older machines the damn display adapter & driver are interfering.

---

### Post by bewildered-newbie on 2021-08-26
Does anyone recommend _*Linux Lite*_ as a replacement ??  Using only install media it appears to support 1920x1200 monitor resolution using Nouveau driver without system freeze. Is it worth installing it on HD ?  Thanx.

still Bewildered newbie Bob

---

### Post by Impavidus on 2021-08-26
You mention using the 20.04.2 live disk. The 20.04.3 live disk has been released, which comes with a new kernel (5.11 versus 5.8), which may work better. No guarantees though. At least it will reduce the number of upgrades to install after OS installation. On the other hand, you could try the 20.04.1 image, which comes with the 5.4 kernel. If that works and the 5.11 kernel doesn't, you'll have to configure it not to install the 5.11 kernel, but stick to 5.4.

The Nouveau driver is built into the kernel. How well it works depends on the kernel version. I don't know which kernel version is used by linux Lite, although Google suggests it's 5.4, the same as Ubuntu 20.04.1. I guess the```
uname -r
``` command works there too, telling exactly which kernel version is running. Different Linux distro's come with more or less the same kernel, but not exactly. Different Linux distros may tweak the kernel a bit, but as Linux Lite is based on Ubuntu, I assume it uses basically the same kernel as 20.04.1.

In any case, testing with the Ubuntu 20.04.2 image doesn't tell you how well it handles your hardware, as 20.04.2 has the 5.8 kernel (which is no longer supported), but the installed system will have either the 5.11 kernel (after installing the recommended upgrades) or the 5.4 kernel (after downgrading or starting with the 20.04.1 image).

---

### Post by bewildered-newbie on 2021-08-26
> **grahammechanical said:**
> 

 If you can get to the first screen of the installer press any key to access to advanced boot options page. At that page press F6 - other options and from the menu select nomodeset. You will find the instructions at section six of the Changing the CD's Boot Options heading. Selecting nomodeset allows the installer to run without a video mode being set and that may overcome the problem long enough for Ubuntu to be installed.


Not obvious which is _***FIRST SCREEN***_ since none of the screens responded to "press any key" instruction provided. The install stopped at a purple screen with the head of an animal - too far ??  Thanx.

BB

ps: this is clearly the first choice for debugging since (if it works) it shd be simple

---

### Post by him610 on 2021-08-26
> The install stopped at a purple screen with the head of an animal - too far ?
If it got that far, the installation is complete.

---

### Post by bewildered-newbie on 2021-08-28
> **bewildered-newbie said:**
> Not obvious which is _***FIRST SCREEN***_ since none of the screens responded to "press any key" instruction provided. The install stopped at a purple screen with the head of an animal - too far ??.

_Latest status__ using "live" media _-

(1) ***LOOKING MUCH BETTER*** -  entering <**nomodeset**> appears to allow screen contents to be viewed properly but resulting screen resolution is only 1024x760 which is much lower than optimal. If screen resolution can be increased to current 1920x1200 when Ubuntu is installed on HD how can this chg be made permanent ?

(2) very useful Linux Mint cmd <**inxi**> appears to be missing from Ubuntu. If true is there an alternative ??

(3) driver status is unknown (due to # 2 above) but About -> Graphics shows: **llvm 11.0.0 **(whatever that means)

(4) is/are Nouveau driver(s) avail to replace ancient Nvidia one which apparently fails consistently

BB


=====================================================================
MORE UPDATING - version 20.04.3 was downloaded to USB stick and tested (trial mode only). Apparently there are only 2 choices for monitor resolution: 800x600 and 1024x768 which is best but far away from 1920x1200 which the hardware is capable of supporting. IMHO the bug is caused by inadequate driver rather than "tired iron" system unit.  If so and if a suitable driver was (permanently ?) installed testing could proceed according to an intelligent plan - TRUE ??

---

### Post by bobunderwood99 on 2021-08-28
_Latest status__ using "live" media _-

(1) ***LOOKING MUCH BETTER*** -  entering <**nomodeset**> appears to allow screen contents to be viewed properly but resulting screen resolution is only 1024x760 which is much lower than optimal. If screen resolution can be increased to current 1920x1200 when Ubuntu is installed on HD how can this chg be made permanent ?
 > [https://maketecheasier.com/change-screen-resolution-ubuntu/](https://maketecheasier.com/change-screen-resolution-ubuntu/)

(2) very useful Linux Mint cmd <**inxi**> appears to be missing from Ubuntu. If true is there an alternative ?? 
> [https://howtoinstall.co/en/inxi](https://howtoinstall.co/en/inxi)

(3) driver status is unknown (due to # 2 above) but About -> Graphics shows: **llvm 11.0.0 **(whatever that means)
> [https://askubuntu.com/questions/1276966/ubuntu-20-04-lts-llvmpipe-llvm-10-0-0-256-bits-used-instead-of-nvidia-graph](https://askubuntu.com/questions/1276966/ubuntu-20-04-lts-llvmpipe-llvm-10-0-0-256-bits-used-instead-of-nvidia-graph)

(4) is/are Nouveau driver(s) avail to replace ancient Nvidia one which apparently fails consistently
> [COLOR=#ff0000]You are already using the Nouveau driver since it's in the kernel.[/COLOR]

========================================================
MORE UPDATING - version 20.04.3 was downloaded to USB stick and tested (trial mode only). Apparently there are only 2 choices for monitor resolution: 800x600 and 1024x768 which is best but far away from 1920x1200 which the hardware is capable of supporting. IMHO the bug is caused by inadequate driver rather than "tired iron" system unit.  If so and if a suitable driver was (permanently ?) installed testing could proceed according to an intelligent plan - TRUE ??
>[COLOR=#ff0000] As suggested in Post #3 use nomodeset  with the LiveUSB [COLOR=#ff0000]only [/COLOR]to get Ubuntu installed[/COLOR].

> [COLOR=#ff0000]Further research has revealed widespread issues running a GeForce 6150SE nForce 430 with the Nouveau driver. 
[/COLOR]> [https://www.reddit.com/r/linuxhardware/comments/igke7t/nvidia_geforce_6100_nforce_430/](https://www.reddit.com/r/linuxhardware/comments/igke7t/nvidia_geforce_6100_nforce_430/)

---

