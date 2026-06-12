---
title: "Why Gutsy works but Hardy doesn't in the same computer??"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by gakna on 2008-05-31
I have been using Ubuntu Gutsy in my computer without any major problems, but  i try to use the Hardy Heron Live Cd and can't get into the desktop unless i use the generic VESA option, and when i do this the maximum resolution i get is 800x600 and everything looks huge...so i am afraid of installing it or upgrading to it. Probably is something related to the video card??
Shouldn't Hardy be better at detecting things than Gutsy???

---

### Post by spiderbatdad on 2008-05-31
your video card probably requires a restricted driver from the system administration hardware drivers menu...not available afaik until the system is installed.

---

### Post by IHATEDLINK on 2008-05-31
> **gakna said:**
> I have been using Ubuntu Gutsy in my computer without any major problems, but  i try to use the Hardy Heron Live Cd and can't get into the desktop unless i use the generic VESA option, and when i do this the maximum resolution i get is 800x600 and everything looks huge...so i am afraid of installing it or upgrading to it. Probably is something related to the video card??
Shouldn't Hardy be better at detecting things than Gutsy???

Hardy has been shown to be a buggy upgrade.
I would keep Gutsy ´til Intrepid Ibex comes up but if you desperately want the new features try upgrading anyways and asking for help here at the forums.

---

### Post by gakna on 2008-05-31
I like that last advice...i am so pleased with Gutsy right now, i don't really need more...i will wait for Intrepid then and save my newbie self a headache :)
Thanks anyway!!

---

### Post by kansasnoob on 2008-05-31
No real reason not to stick with Gutsy. It's supported until April 09, so even if Intrepid doesn't suit your fancy you'll still be able to wait for whatever J......... will be :)

---

### Post by SlappyPappy on 2008-05-31
> **gakna said:**
> I like that last advice...i am so pleased with Gutsy right now, i don't really need more...i will wait for Intrepid then and save my newbie self a headache :)
Thanks anyway!!

There is no shame in staying with Gutsy. I'm sticking with Gutsy for a while. It does everything I want a computer to do, does it well, and is extremely stable. Much better than XP, that's for sure.

Enjoy what you have.  :guitar:

---

### Post by brigadoon on 2008-05-31
What driver are you using? Nvidia, ATI, Intel...

---

### Post by gakna on 2008-06-01
Brigadoon, my graphic card is nvidia geforce 6150 SE integrated to the motherboard, and the processor is AMD Athlon 64x2 dual core 4000+.
The acpi=off didn´t work for me, only logging in safe graphic mode but with the problem of the low resolution.
Any ideas? just to know, because maybe it's just something really easy to solve...at least to try Hardy even if i don't upgrade to it :)

---

### Post by PatrickMoore on 2008-06-01
funny i had the exact opposite issue.

---

### Post by bumanie on 2008-06-01
Unfortunately, I think it comes down to some sort of hardware conflict between hardy and your computer. I have had no problem with feisty or hardy, whereas, gutsy barely ran on my computer. With heaps of configuring, it ran, but never very well. I know of other users who have had problems erased by updating to hardy. Unfortunately, in your case, things have occurred the other way around. I'd put in some bug reports to launchpad and hopefully the developers can iron out the issues in future updates. Use gutsy for a while longer and then try hardy again in a couple of months - things may have changed for the better (for you) by then.
As said above somewhere try the hardware driver for the graphics card, you find that it sorts out your graphics issue.

---

### Post by sayakb on 2008-06-01
Thats right. Revert back to gutsy and keep in touch with the Forums. We would let you know if all issues have been neutralized. And ofcourse, Gutsy is supported till April 2009, so there no issue of not getting the latest update either :)

---

### Post by brigadoon on 2008-06-01
> **gakna said:**
> Brigadoon, my graphic card is nvidia geforce 6150 SE integrated to the motherboard, and the processor is AMD Athlon 64x2 dual core 4000+.
The acpi=off didn´t work for me, only logging in safe graphic mode but with the problem of the low resolution.
Any ideas? just to know, because maybe it's just something really easy to solve...at least to try Hardy even if i don't upgrade to it :)

Nvidia drivers seem to have a pattern of not interpreting a monitor's native resolution modes. I have a Toshiba Satellite 1415-S173 laptop with a NVIDIA GeForce4 420 Go with 16 Meg of RAM. I am running Ubuntu 8.04 but had driver resolution issues as well. The driver either locked into a 800x600 screen resolution or went to a choppy 969x768 screen resolution with much tweaking. While running 969x768 resolution I ended up with a black bar on the right side of the screen. My flat panel display didn't have a 969x768 resolution but did have a 1024x768. 1024 - 969 = black bar on right side of the flat panel display.

Fortunately... and you need to know a little about editing a binary file... I was able to fix the problem. My Nvidia X Server Settings console has a switch called ***Acquire EDID***. The Acquire EDID button allows you to save the display device's EDID (Extended Display Identification Data) information to a file. Using a binary editor I was able to modify the EDID file changing the 969 to 1024. I then added the Option "CustomEDID" "/path/to/patched/EDID.file" to the XORG.CONF located in /etc/X11 folder. I placed my edid.bin file in the /etc/X11 folder.

Your resolution issues may be related to the issue I had. You need to know what the resolution modes are for your display and what hexadecimal locations to change. Editing a binary file is not as hard as you might imagine. You can load a hex editor for free through the Synaptic Package Manager. Help on how to edit the xorg.conf and binary files can be found on Wikipedia. I posted the details to my fix at this link...

[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

I find the latest version of Ubuntu to be an improvement over older versions. It's a shame that Nvidia can't get their act together to keep these resolution problems from happening in the first place. I hope this helps. Good luck.

---

