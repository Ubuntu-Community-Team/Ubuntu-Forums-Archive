---
title: "System Feels Slow"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by EternalDecree on 2012-04-14
Hi, I just installed Ubuntu 11.10 (64 bit) on my Toshiba Satellte P200D and everything feels laggy, as if there is a delay between clicking and the computer responding. Also opening my web browser (and other things) takes longer than I think it should, and longer than it does in Windows. Years ago I had 7.04 on a Satellite and it was very quick. This computer has a 1.9ghz processor and 2GB of ram. I have browsed the forum and it seems the graphics card could be an issue: Mine is the ATI Radeon X1200. Is there a known issue with this card? I have also tried switching to Ubuntu 2d, but this does not increase speed.

Thank you so much for your help! I look forward to being involved as a member of this community!

EDIT: I should also mention, it seems that the processor is working much harder than normal when I do things such as use the launcher or open a new webpage. I say this because I can hear the fan speed increase and the blue light on the front stays lit up much longer normal.

---

### Post by GregA on 2012-04-14
Your system is capable of running with good speed, you have enough ram and processor speed.  

Have you tried to install the proprietary video drivers?  In the pre-Unity ubuntu, there was an option to search & install those drivers.   I assume that option still exists.

---

### Post by jf812 on 2012-04-14
I second the above post, and yes, that feature is still available. Just press alt + F2 and type additional drivers. Then any propreitary drivers should be displayed for you to install, if available.

---

### Post by EternalDecree on 2012-04-14
Thanks for the advice, and thanks for the how-to, jf812. I will try it out and let you know how it goes!

---

### Post by EternalDecree on 2012-04-14
Okay, I found the Addition Drivers section under Dash Home, but when I open it it says "No proprietary drivers are in use on this system."

alt + F2 didn't find anything when I searched for additional drivers.

Any idea where I should go from here? Thanks so much for your help!

EDIT: I was looking around for a driver and this (long dead) post [http://ubuntuforums.org/showthread.php?t=808583](http://ubuntuforums.org/showthread.php?t=808583) says they are no longer available/don't work on newer versions of Ubuntu. So it looks like I have to stick with the open source driver which I'm currently using? Or are there still other options? Also, could it be something else making everything slow, or is it almost certainly the graphic card driver? Thanks again!

---

### Post by theknightlinux on 2012-04-14
Have you tried to install the drivers for your ATI Radeon X1200 card from an external package like from ATI?

---

### Post by theknightlinux on 2012-04-14
Your processor is working harder because no OpenGL is enabled because your card is not running by the driver is should be using. For what I know your card should support all 3D acceleration.

---

### Post by EternalDecree on 2012-04-14
Hi, the ATI website says the driver for my graphics card will only be supported on linux distributions prior to 2009. Does this mean installing it would be a bad idea? (Sorry for the noob question)

Link: [http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_xp.aspx](http://support.amd.com/us/gpudownload/windows/Legacy/Pages/radeonaiw_xp.aspx)

---

### Post by theknightlinux on 2012-04-14
No problem, I'm a noob too. I don't think that'd be a problem and if it is, it'd be better to try it as you don't have any support at all with the current standard driver you got, right now. If that driver doesn't work, I believe you still got other options.

---

### Post by theknightlinux on 2012-04-14
If you don't want to install the driver provided by ATI... have you read this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It says you can use the Catalyst driver for X1200

---

### Post by EternalDecree on 2012-04-14
Thanks, I'll try it out. If you never hear from me again, it didn't work, destroyed my computer, and somehow killed me too. Otherwise, I will be back.

---

### Post by theknightlinux on 2012-04-14
LOL, it'd be better if you try the Catalyst driver.

---

### Post by EternalDecree on 2012-04-14
Looks like I'm SOL with this graphics card. According to this very thorough guide ([http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)) *"NOTE: If you enter your card information on AMD/ATI's driver page, it will offer you the Catalyst 9-3 driver to download. However, the Catalyst 9-3 driver doesn't support X servers past 1.5, and it will not work with Oneiric (or anything later than Lucid/10,04)! !!!SO BE CAREFUL!!! If you tried to install Catalyst on a system with one of these cards, see the 'Removing the Driver' section to restore the default/pre-installed drivers."*

---

### Post by d4m1r on 2012-04-14
2GB of RAM is plenty to run 11.10 even...Is the CPU dual core?

I'd recommend download 11.10, trying it on a live cd/usb first, and then installing it instead. You'll get better support for it too.

---

### Post by theknightlinux on 2012-04-14
It says it won't give you the latest drivers, but I think it will give you better performance than what you got now if you try what it says. Are you going to try the guide?

---

### Post by theknightlinux on 2012-04-14
The good part here is that you do have some kind of support from a driver for your card, even if it's not the latest, as there are other cards that can only rely on a standard driver. Did you check this page out: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Your card is supported on Ubuntu 11.10.


 o Full support for 8-, 15-, 16- and 24-bit pixel depths;
 o RandR 1.2 and RandR 1.3 support;
 o TV-out support (only on RV/RS1xx, RV/RS2xx, R/RV/RS3xx.  Experimental
 support  on  R/RV5xx,  R/RV6xx,  and  R/RV7xx  through  the **ATOMTvOut**
 option);  TV-out is not supported on cards that use the Rage  Theatre
 chip for TV-out (R100, R200).
 o Full EXA 2D acceleration;        o Full XAA 2D acceleration (only on R/RV/RS1xx, R/RV/RS2xx, R/RV/RS3xx,
 R/RV/RS4xx, R/RV5xx, RS6xx. XAA Render acceleration supported only on          R/RV100, R/RV/RS2xx and RS3xx);
 o Textured  XVideo acceleration including anti-tearing support (Bicubic
 filtering  only  available  on  R/RV3xx,  R/RV/RS4xx,  R/RV5xx,   and
 RS6xx/RS740);
 o Overlay   XVideo   acceleration   (only  on  R/RV/RS1xx,  R/RV/RS2xx,
 R/RV/RS3xx, R/RV/RS4xx);
 o 3D acceleration;
Would be better than just a standard driver.

---

### Post by 3Miro on 2012-04-14
Other people can correct me if I am wrong, but I think AMD recently dropped support for x1200 from their proprietary drivers and the FOSS drivers were never really good. This would slow down your machine.

Try LXDE or XFCE or try going to an older version that has proprietary support for your video card (i.e. 10.04).

---

### Post by EternalDecree on 2012-04-14
If I install 10.04 am I just postponing the problem? I know that distro is LTS but surely it's day is coming soon.

---

### Post by theknightlinux on 2012-04-14
You should try everything that'd work for you; it'd be better than having nothing or a system that's not working to its full performance, or worst yet going back to Windows ;p. You can install Unity in 10.04. And besides, it'd be exactly one year from now for 10.04 to go unsupported; many things can happen in one year, may be support will be available in 12.04 or 11.10 later for you card. Or may be you'll get a new computer to install Linux, and you'd have given the current one you got a good use for now.

---

### Post by EternalDecree on 2012-04-14
Thanks for the encouragement, theknightlinux! I love the support and community here. I'll think about what to do from here, but I'm not giving up on Linux. Would I have the same problem no matter what distro I use (openSUSE, Debian, etc. ?) Not that I want to switch, I'm just curious.

---

### Post by theknightlinux on 2012-04-14
Well, I believe it'd be the same process trying to install the radeon binary driver for any distro, as the Catalyst 9-3 driver is only supported on Linux distros before 2009. If you'd tried to install the radeon open source driver, which is the best bet you got right now in my opinion for a current distro, you'll have to do the same for any distro you try.

---

### Post by theknightlinux on 2012-04-14
By the way, make sure if Ubuntu 10.04 will indeed support your X1200 card with the propietary drivers.

---

### Post by GregA on 2012-04-14
In the past, when Linux users had unsupported video cards or chipsets, an alternate option was to just use the standard "vesa" driver .... the downside being no 3d, or desktop effects.   So, if a person was not especially interested in gaming - - you could have a fast and functional system.

Since I don't run Ubunity/Unity, I don't know if this is still do-able or how to set it up, but perhaps someone else can fill in the blanks.

---

### Post by 3Miro on 2012-04-15
AMD dropped the support for the old ATI cards and this will affect any distro. You may look at 10.04 as a way to "postpone" the problem or as a way to wait until you can get enough money to buy a fully supported computer. If you think that 10.04's extra year of support will not be enough time, you can consider Debian 6. It will be supported for at least another 2 years and possibly more. You can also look at any other distro that has long support and will come with the older version of the AMD driver.

---

