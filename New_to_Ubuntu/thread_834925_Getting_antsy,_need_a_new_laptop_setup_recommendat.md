---
title: "Getting antsy, need a new laptop setup recommendation"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by 625 on 2008-06-19
Hey all.

I bought a new laptop a couple weeks ago, and I've been running it with Ubuntu 8.04. It's been working pretty well, but it could perform a little better. Fullscreen video gets a little choppy, flash is just as terrible as it seems to be for everyone, and I haven't even tried any games involving 3d. I installed xubuntu to give that a shot, and while video is much better, fonts are *really* wonky and much too big when they're not too small, plus transparency doesn't seem to work very well at all.

So what would be a good setup I could use? Surely there's some compromise to be made between xfce's performance and the consistency of a plain ubuntu install.

---

### Post by Dynaflow on 2008-06-20
Try installing plain-vanilla Ubuntu, then, though Synaptic, installing the xubuntu-desktop package.  You'll be able to choose whether you'd rather use Ubuntu's GNOME desktop or Xubuntu's XFCE desktop for your current session at login.  You'd have the exact, same underlying OS, programs, home folder, etc., whichever option you choose each time you log in -- just with different "skins" on top, one of which might be better than the other for accomplishing a given task.  It's a much better option than dual-booting two flavors of Ubuntu or wandering off into the wilderness to start over with some other distro.

Choppy video and transparency problems sound like an issue with your graphics card and whatever driver is running it.  What output do you get from ```
lspci
```

Also, what are the general specs of your machine?  Manufacturer, model, processor, RAM, etc.?

---

### Post by 625 on 2008-06-20
Dell Inspiron 1420
Core 2 Duo T8300
4 GB RAM
GeForce 8400M GS, 128mb (a bit of a bottleneck I suppose)
250GB SATA hdd

What all do you want from lspci? The entire thing?

---

### Post by Dynaflow on 2008-06-20
> **625 said:**
> ...

What all do you want from lspci? The entire thing?

Sure.  

With that kind of setup, though, you shouldn't be having these sorts of problems.  Let's figure this out.

Do you have the nvidia-glx-new package installed and enabled?  Also, if you're getting choppy playback from full-screened Flash video, that is a known issue with Adobe's (proprietary) Linux-"friendly" Flash plugin, so there's really nothing we can do about it until Adobe fixes the problem internally and issues a new and improved version of their Flash player.  How's MPEG/AVI/DVD playback?  That would be a better test.

---

### Post by Dynaflow on 2008-06-20
Another important question: I'm assuming you're running Hardy, but are you using the "normal" 32-bit Ubuntu or the 64-bit version? 

Your hardware would clearly be happy running 64-bit Ubuntu, but 64-bit has some multimedia setup steps that differ from the 32-bit version, so you if you're on 64-bit and followed instructions for 32-bit, you may have some misconfiguration issues.

I wouldn't bother with Xubuntu at this point.  Your computer can eat GNOME for breakfast, or maybe even a midnight snack.

---

### Post by mivo on 2008-06-20
Those specs look odd. 4 GB RAM, but a weak video card with 128 MB. Well, I guess it's Vista-centric. It should be fine running Ubuntu with Gnome (though I actually like Xubuntu's setup), but I'd turn off any 3D effects and see how it performs (in *System -> Preferences -> Appearance*). If there is improvement, enable it again but get the Compiz Settings Manager (in the repository) and turn off what you don't need or want. I'd also check for any unwanted background processes like Tracker (*System -> Preferences -> Sessions*). Also run "top" from a terminal and see what eats your performance, if anything.

Another approach is to fix your font problem in Xubuntu. :) I use it on my laptop and it's actually just fine.

---

### Post by 625 on 2008-06-20
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

Yes, I've got nvidia-glx-new installed/enabled.  Viewed in SMplayer, both xvid-encoded avi and softsubbed h264 mkv are watchable, but avis seem to be a bit more smooth, and while there isn't a noticeable drop in framerate, it's still pretty shy of smooth. It's kinda like the playback is out of synch with the screen refresh or something.

And I'm running Ubuntu 8.04, 32-bit.

Yeah, the vid card's a bit weak. I kinda wish I'd gotten something a bit better, but truth be told, it's largely for school anyhow. I figured most of my non-academic use would be video playback and some less demanding games, since I have a fairly powerful PC lying around to cover anything big.

---

### Post by Dynaflow on 2008-06-20
How did you originally go about setting up your multimedia, restricted codecs, etc.?  

This issue is most likely stemming from how all that stuff was configured, and has nothing to do with your hardware.

By way of example, I have a laptop with a Celeron M 1.7-odd GHz processor, a gig of RAM, and an Intel 965 integrated video chipset, Linux support for which has been horribly broken for more than a year.  I still have good video playback and my desktop is a transparent spinning cube.

---

### Post by 625 on 2008-06-20
> **Dynaflow said:**
> How did you originally go about setting up your multimedia, restricted codecs, etc.? 

Largely what I did was install Ubuntu, and go into synaptic, grab smplayer, ubuntu-restricted-extras, and go into hardware drivers and enable nvidia restricted drivers and let that download what it wanted. I've done very little else, so if I'm missing any optimizations, I'm more than happy to hear them.

---

### Post by Dynaflow on 2008-06-20
That would be the root of the problem.  

Follow this guide, and you should definitely see some improvement in how your Ubuntu installation handles multimedia:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I would also recommend, if you're not already too committed to your present installation, reinstalling using 64-bit Ubuntu.  There are, of course, still a lot of kinks with 64-bit (not just in Linux) that are still being worked out, and x86 (32-bit) still seems to be the standard, as it has been for decades, but 64-bit is starting its rise to ascendancy.  Also, to get the full measure of performance out of your particular computer, you'll want to go 64-bit. Read this first, though:  [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

The first link with the multimedia installation guide has instructions for both 64-bit and 32-bit.

---

### Post by 625 on 2008-06-20
Great, thanks! I'll give this a shot. I dunno if I have quite the energy in me for it tonight, since it's getting a little late and all, but I'll burn the disc tonight and install and follow that guide in the morning. I guess I've got nothing to lose, and if this helps, it'll be nice to see this thing more fully meeting its potential. I'll post in here in the morning to report on how it went.

---

