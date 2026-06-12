---
title: "What is the difference between Live and a Full Install?"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by gregoryshock on 2013-04-28
What is the difference between a Live CD system and a full install?  I understand that you can not install software into a Live CD system, and I understand that there are some other limits to the Live CD system, but beyond the limits due to the fact there is no way to record information to the Disc/system, are there any other differences?  It seems to me that when one installs windows to a hard disk, it senses the computer system and attempts to adjust it's self to the hardware, But what I am wondering is How does Linux go about this?  Or does it just simply create a file system and copy it's self over?

---

### Post by hansdown on 2013-04-28
Hi 
gregoryshock.

The live cd essentially runs in your ram, where a complete install is using the hard drive.

You can install apps to a live session, but it will be lost when you shut down.

---

### Post by gregoryshock on 2013-04-28
> **hansdown said:**
> Hi 
gregoryshock.

The live cd essentially runs in your ram, where a complete install is using the hard drive.

You can install apps to a live session, but it will be lost when you shut down.

Thank you for your response.  I am sorry that I forgot to mention that I already knew that.  I am trying to learn if Linux makes any adjustments to it's self during a full installation.

---

### Post by hansdown on 2013-04-28
> **gregoryshock said:**
> Thank you for your response.  I am sorry that I forgot to mention that I already knew that.  I am trying to learn if Linux makes any adjustments to it's self during a full installation.

Ahh. O.K.

A complete install works best, when an internet connection is available.

---

### Post by Mathor on 2013-04-28
Ultimately a CD or a USB is going to have a slower running harddrive, therefore performing a full install will give you a huge speed increase because of faster hard drive and less memory used.

---

### Post by gregoryshock on 2013-04-28
> **Mathor said:**
> Ultimately a CD or a USB is going to have a slower running harddrive, therefore performing a full install will give you a huge speed increase because of faster hard drive and less memory used.

What I am trying to figure out if Linux forms it's self to the machine that it is install on or not.  Example:  If you install Linux to an External Hard Drive and then Moved that drive to another computer, would Linux realize it has been moved and make it's own adjustments to the new computer.  If so then what happens if you move it back to the older system?  In other words what happens when you change from one system to another?

---

### Post by C.S.Cameron on 2013-04-28
As long as you don't install proprietary drivers a Full install or Live Persistent install to HDD, flash disk or SDD should work in any computer they are attached to*, This is not Windows.

* UEFI computers complicate things a bit though.

Full installs boot faster than Persistent instalsl but in my experience they run about the same speed once booted.

---

### Post by Cheesemill on 2013-04-29
Unlike Windows which probes for hardware and sets up specific drivers when you first install, the Linux kernel probes the hardware and loads the correct drivers each time you boot (all hardware drivers are already built into the kernel). This is one of the reasons why it's possible to have a Live CD in the first place.

The only time you will usually run into issues is when you have proprietory drivers installed (usually graphics or networking), for example installing the ATI drivers on your OS and then trying to run it on an Nvidia machine.

---

### Post by mastablasta on 2013-04-29
however despite the fact that linux probes for hardware on boot it still writes down certain settings that are then used on reboot.

for example sound works with live CD any time on my mashcine but upon install it detecs a fake chip (perhaps wrong detection) and it will then use that fake detected chip after boot. then i need to redetect and load all moduels again for it to recognise the correct chip. anyway that "fake" (or should i say false positive) chip is the used on reboot. unfortunatelly. which means i often need to reload the modules to get the sound working.

similary some personal user settings might be used on reboot - for example resolution and driver settings and such. this doesn't happen with live where everytime it will use what it probes for and finds it.

---

### Post by grahammechanical on 2013-04-29
One reason why it takes a Live Session longer to load than Ubuntu installed on a hard is that the live session is probing the hardware. More is required to install Ubuntu (any Linux distribution) than simply copying the contents of the DVD onto the hard disk. A hard disk install is not a live session running from a hard disk. It would be more correct to put it the other way around.

---

