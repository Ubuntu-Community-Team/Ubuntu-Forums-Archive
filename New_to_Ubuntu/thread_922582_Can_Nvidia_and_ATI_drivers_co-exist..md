---
title: "Can Nvidia and ATI drivers co-exist."
date: 2008-09-17
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-09-17
Using switchconf I can boot to different xorg.conf files.
(Ubuntu is installed on USB stick)
I can choose to boot using Nviidia restricted drivers on my office computer or generic drivers on my laptop.
Or I can choose to boot using ATI restricted drivers on my laptop or generic drivers on my office computer.
However installing ATI drivers removes my Nvidia drivers and vice versa.
Is there a way to make both drivers co-exist so that I can boot with either Nvidia, ATI or generic drivers?

---

### Post by Titan8990 on 2008-09-17
They can co-exist but I would not load both of the modules into the kernel at the same time.

---

### Post by Therion on 2008-09-17
I think you're confused.  

What exactly are you referring to when you say "ATI generic" driver, or "nVidia generic" driver?

There is a "generic" VESA driver, but drivers built by nVidia or ATI are either the the open-source binary driver or Restricted driver.  There is no generic ATI or nVidia driver.  

Further, your OS, whatever it is, is going to want to call up (implement) ONE driver for that particular piece of hardware at each boot sequence.  You can use the "generic" VESA driver, OR you can use the manufacturers driver in either restricted or binary flavor.  You can switch xorg config files to change what driver is implemented, but only one driver can be implemented at a time.

Further... if you have an nVidia graphics solution, why would you want to use an ATI driver?  Conversely, if you have an ATI graphics solution why would you want to use an nVidia driver?

---

### Post by C.S.Cameron on 2008-09-17
How to do?
I would like to load the ATI drivers when I boot my laptop and the Nvidia ones when I boot my office computer.
By generic I meant the Vesa ones.

---

### Post by Therion on 2008-09-17
> **C.S.Cameron said:**
> How to do?
I would like to load the ATI drivers when I boot my laptop and the Nvidia ones when I boot my office computer.
By generic I meant the Vesa ones.
Well then your laptop needs to have an ATI video solution installed, either an ATI integrated graphics chipset or an ATI video card.

Your office computer needs to have an nVidia graphics solution.

The hardware that is installed determines the driver that is used.  It's not your decision to use to one or the other, unless you want to stick with the crappy VESA driver.  ATI drivers will not work with nVidia graphics solutions and nVidia drivers do not work on ATI graphics solutions.  Only the crappy VESA driver works on both.

I think the best thing you can do is to boot your PC's and then go to System/Administration and use the Driver Manager to install the correct driver for each PC.  That's the easiest and safest approach.  Open the Driver Manager and follow the instructions.  Once the proper driver is installed you will need to reboot each PC.  After that, you're done.

---

### Post by C.S.Cameron on 2008-09-17
I am booting Ubuntu, Xubuntu from a USB thumbdrive.
My laptop has ATI X700, my desktop has NV 8800GTS.,
When I boot the laptop from the thumbdrive I would like to select the ATI drivers at grub.
When I boot the Desktop I would like to select the Nvidia drivers at grub.

---

### Post by Therion on 2008-09-17
> **C.S.Cameron said:**
> I am booting Ubuntu, Xubuntu from a USB thumbdrive.
My laptop has ATI X700, my desktop has NV 8800GTS.,
When I boot the laptop from the thumbdrive I would like to select the ATI drivers at grub.
When I boot the Desktop I would like to select the Nvidia drivers at grub.
GRUB is not responsible for what graphics driver is loaded at startup.

Even IF it's possible to do what you want - and I'm not sure it is - I certainly can't tell you how to do it; that's way beyond the scope of my limited knowledge/ability.  I have a feeling you're going to have to use the VESA driver for both, if you want to use one driver only for both PC's; or you are going to have to pick either the ATI **or **nVidia driver for one PC and then use the VESA driver for the other.  That's my *guess... *

I wish you good luck... I'll be watching this thread with interest.


EDIT:  Possible solution?  You have both Ubuntu and Xbuntu on your thumb-drive you say...  Install the nVidia driver for one OS (i.e. Ubuntu) and the ATI driver for the other (Xbuntu).  Boot to Xbuntu when using the office computer (with it's nVidia graphics) and to Ubuntu on the laptop with it's ATI graphics solution; or vice versa (Xbuntu on the office PC, Ubuntu on the laptop).  Use whichever distro works best for each PC in question.  Just keep things consistent with what PC boots which distro (based on what video driver you use for each) and you should be good to go.




/I think I just fried a few brain cells re-reading that...

---

### Post by ethoxyethaan on 2008-09-17
well if you don't fill in ether ATI or Nvidia in the  xorg.conf there will be no problems

BUT however never install 2 diffrent Nvidia drivers because i know that fails

---

### Post by C.S.Cameron on 2008-09-17
Therion:
I appreciate your interest. 
Yes, using switchconf, (from the repositories), you can select from multiple xorg.conf files at boot. This is handy for booting multiple computers from a thumbdrive
I currently have one xorg.conf using Nvidia drivers with dual monitors for my office, one for Nvidia drivers with single monitor for the entertainment center and one with vesa drivers for everything else.
I figure there must be a way to make another org.conf with ATI drivers for when I boot the laptop.
I'm wondering if after I install the ATI ones and they delete Nvidia-glx I can just copy it back by hand or anything.
I am only choosing between Xfce or Gnome for session

---

### Post by phidia on 2008-09-17
Interesting question and thread. And this should be very possible otherwise all the livecds that load proprietary drivers couldn't work-but they do work (sabayon for one does it). 
Of course the snag is that live environments set up the xorg on boot. Maybe you could look at how they do that to get some ideas and then expand the knowledge base?

---

### Post by ApatheticLoser on 2009-02-26
dude, I've been looking for the answer to this question for quite awhile myself. If you find a way to get both drivers to exist without one deleting the other on install, please let me know.

As of now I've been keeping the nvidia driver installed (aswell as the intel one, I use it on another laptop) and then for my school computers that have ati graphics cards, I've been forced to use the vesa driver, or take the time to install ati(thus removing nvidia, and requiring me to reinstall it again when I get home)

switchconf is the glue that holds it all together for me (including letting me change some entries in the /etc/modules file for different hardware).

I've opened my own thread, and haven't gotten a response back from anyone that has taken the time to fully read my question either(also having the knowledge to respond of course)

---

### Post by ApatheticLoser on 2009-03-15
This is a great thread, has no one found a solution?

---

