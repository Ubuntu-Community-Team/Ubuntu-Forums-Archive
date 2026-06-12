---
title: "A little help getting compiz working"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by hithisishal on 2008-09-09
Hi everyone.  I am a complete beginner, so I hope this is the right forum for this.  I recently installed Hardy, and I'm having some trouble getting compiz to run.  I am using a 	Intel 945G chipset with the GMA 950 integrated video.  I saw the other threads about this device, but they all seemed to have trouble running at strange resolutions, and the solution was to download that 915resolution program, not to install a driver of some sort (if I understood correctly).

Now the fun stuff:

If I type compiz, this happens: 

hal@hal-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


I also tried to do something to install xgl, and it told me to log out and in, but I don't think it worked.  And I don't remember what it was, since I tried so much stuff, most of which was even less productive.  If it matters, I needed to boot in "graphics safe mode" off the live DVD when I installed, but then it fired right up without too much tempting.

Thanks!

---

### Post by mike1234 on 2008-09-09
Not sure but it sounds like your video isn't capable of running it. I think Compiz requires quite a bit if video ram. I have a 256 nvidia card and I can tell it slows down my video. Sorry if I'm wrong or it's not wanted you wanted to hear. Everything has limits. I know someone with 64 meg onboard video ram on his Dell. Compiz won't run.

M.

---

### Post by tuxxy on 2008-09-09
How did you install your video driver

---

### Post by hithisishal on 2008-09-09
> **tuxxy said:**
> How did you install your video driver

I didn't.  Everything else just works.  if I go to system...information...hardware drivers, it says that there are no proprietary drivers in use on this system.  I saw a couple of threads referencing [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) for drivers, but I didn't see a neat compiled package available for ubuntu, nor did I see step by step instructions on how to build the drivers for ubuntu.  I don't even know what 75% of the stuff on that site is talking about.  I have no problem learning; I have dabbled in programming a tiny bit (mostly on microcontrollers), but I'm just kinda throwing myself into this, and there seems to be a bit of a learning curve that I'm running into.


As for video memory, the specs say "Up to 224 MB Shared Video Memory." I'm not sure what that means in terms of power.


Thanks so much for your fast replies.

---

### Post by mike1234 on 2008-09-09
> **hithisishal said:**
> I didn't.  Everything else just works.  if I go to system...information...hardware drivers, it says that there are no proprietary drivers in use on this system.  I saw a couple of threads referencing [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) for drivers, but I didn't see a neat compiled package available for ubuntu, nor did I see step by step instructions on how to build the drivers for ubuntu.  I don't even know what 75% of the stuff on that site is talking about.  I have no problem learning; I have dabbled in programming a tiny bit (mostly on microcontrollers), but I'm just kinda throwing myself into this, and there seems to be a bit of a learning curve that I'm running into.


As for video memory, the specs say "Up to 224 MB Shared Video Memory." I'm not sure what that means in terms of power.


Thanks so much for your fast replies.

 224 meg share memory should fulfill that requirement. At the expense of total ram available to the system. Onboard video (to me) is a pain. Hard to believe there is no 3D xgl capability though. Especially if it's Intel.

M.

---

### Post by tuxxy on 2008-09-09
ok well I dont know what you have read but you will need to isntall a video driver for your card before you will be able to run compiz.

To install the driver for ATI you could try this,

> 3D ATI Video Card Driver

Many ATI video cards work well with Ubuntu automatically. To check that 3d acceleration works with your card, see the section called &#8220;Introduction to 3D Video Acceleration&#8221;. If it does not work, this procedure should activate it.

Install the xorg-driver-fglrx package from the Restricted repository (see Chapter 2, Adding, Removing and Updating Applications).

You now need to configure the computer to use the new driver so run this command in a terminal:
sudo dpkg-reconfigure xserver-xorg

When the dialogue appears and asks whether to do automatic detection of your video, pick Yes.

When asked to select a driver, pick fglrx.

Follow the remaining instructions as appropriate.

Restart your machine for changes to take effect.

[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

To test compiz navigate to **system > preferences > visual effects ** , now select the extra setting

---

### Post by mike1234 on 2008-09-09
Do you have this installed in Synaptic?

M.

X.Org X server -- Intel i8xx, i9xx display driver 
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
and i965 series chips.

This package also provides an XvMC (XVideo Motion Compensation) driver
for i810 and i815 chipsets.

More information about X.Org can be found at:
<URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This package is built from the X.org xf86-video-intel driver module.

---

### Post by hithisishal on 2008-09-09
> **mike1234 said:**
> Do you have this installed in Synaptic?

M.

X.Org X server -- Intel i8xx, i9xx display driver 
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
and i965 series chips.

This package also provides an XvMC (XVideo Motion Compensation) driver
for i810 and i815 chipsets.

More information about X.Org can be found at:
<URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This package is built from the X.org xf86-video-intel driver module.

Yup - it looks like I do.  The box is green and it has the ubuntu sign next to it.

---

### Post by mike1234 on 2008-09-09
You could try this. It sounds like what you were referring to. It's an older version but better supported. I get the impression Ubuntu hasn't gotten around to your video card yet. Search for 915 resolution in synaptic. Last idea I can think of.

M.

915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots in order for its changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

The 915resolution package becomes obsolete with the newer xorg,

---

### Post by hithisishal on 2008-09-10
No luck with that.  

Thanks for all your help.  Before installing ubuntu, I was thinking of picking up a PCIe graphics card to squeak a little more performance out of my windows machine.  Now, everything seems really quick, but if I want to make it pretty, looks like I will have to buy one. 

Thanks for all your help.  You guys take this software from cool to awesome ;).

---

