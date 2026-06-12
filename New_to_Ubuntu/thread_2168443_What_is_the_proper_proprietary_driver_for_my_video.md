---
title: "What is the proper proprietary driver for my video?"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by mawil10132 on 2013-08-17
I'm trying to figure out, what is the proprietary driver for my laptops video chip?/card?,, I have an acer aspire 5336-2524. Using; ubuntu-13.04-desktop-amd64, off a USB until it can be determined that the video can be fixed.

I have the blank screen issue which has a work around but has to be worked around each time I start up, see: [http://ubuntuforums.org/showthread.php?t=2167962](http://ubuntuforums.org/showthread.php?t=2167962)

I was advised that in order to find a more permanent solution that I need to get the proprietary driver for my video hardware.

ubuntu@ubuntu:~$ sudo lshw -C video
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d3400000-d34fffff

FYI: The laptop is running Win7 Home Premium 32bit.

Michael

---

### Post by SweetAurora on 2013-08-17
You are already using the proper Intel Driver. Intel dosen't provide proprietary drivers because they have a fondness of Linux and open source all their chipset drivers. :)

---

### Post by mastablasta on 2013-08-18
you can set that nomodeset is used automaticly on each boot: [http://ubuntuforums.org/showthread.php?t=1675337](http://ubuntuforums.org/showthread.php?t=1675337)

---

### Post by r_avital on 2013-08-18
Michael,

Forgive a silly question, but you mention that you're running this off a USB - Is that an external USB Hard Drive?  Or a USB flash-drive/pen-drive/memory-stick?

And second, how was the installation created on that USB?  Did you use "Startup Disk Creator" from another Ubuntu system?  If so, did you use the "permanence" option?  How large is the permanence area?

I could be completely off-track, but this might help diagnose the problem.

---

### Post by driftpost on 2013-08-18
Regarding your question about nomodeset if that works for you from grub but would like to make it permanent then do this:

Open a terminal and get root. Eg: $sudo su
Then as root type #nautilus go to to filesystem /etc/default/grub find the line that says; GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and change it to "quiet splash nomodeset" save and exit. Then in a terminal type #update-grub That's it reboot done!

---

### Post by mawil10132 on 2013-08-18
For now it's running off a USB thumb drive/pen.  I formatted the pen drive, made it bootable then copied the ubuntu ISO onto the pen drive.  But, I've done this before and installed directly onto the laptops hardrive with same result.  I created it while in win7 OS. Haven't a clue as to what permanance area is? I'm waiting on a restore to factory diskettes from acer to win7 at which time I will see if BIOS is latest, I keep hearing the issue is primarily due to BIOS.  It will be another 7 days from today before I can restore the laptop to factory and review BIOS as well as make sure all other drivers are latest too. Then I'm going to set up dula boot win7/ubuntu 13.04 at which time I will try out the other posters suggestion if all else fails.


> **r_avital said:**
> Michael,

Forgive a silly question, but you mention that you're running this off a USB - Is that an external USB Hard Drive?  Or a USB flash-drive/pen-drive/memory-stick?

And second, how was the installation created on that USB?  Did you use "Startup Disk Creator" from another Ubuntu system?  If so, did you use the "permanence" option?  How large is the permanence area?

I could be completely off-track, but this might help diagnose the problem.

---

### Post by r_avital on 2013-08-18
Michael,

Good detail, thanks.

Starting with your USB drive:  The Ubuntu iso image is intended to be burned (expanded) onto a DVD, which then becomes bootable, and lets you do two things:  Install to your HDD, and/or experiment and test that version of Ubuntu on your PC without affecting anything on it, before you make the commitment to actually install on your HDD.

Without affecting anything on it means, you don't get to save any files you created or settings you changed.  That would make sense for read-only media like a DVD, which is how it was intended to be used.  I could be wrong, but I don't believe it's different for a USB drive, since that "Try/Install" arrangement was never designed to allow the user to save anything permanently without actually installing.  When you play with "try Ubuntu" after booting from the DVD, settings and files you save are written to some temporary area, and as soon as you shut-down/reboot, your changes are gone.

A good way to experiment with Ubuntu on a USB drive such as yours, is to use an existing installation of Ubuntu, to use a "Statup Disk Creator" utility on it, to put a working Ubuntu operating system of your choice, onto a USB, make it bootable, AND if you want to, have a permanence area.  What that means is, not only will you have a working Ubuntu OS on your USB thumb-drive, you will also be able to keep changes in your settings and files you create from one bootup to the next.

To do this you would need a pc with a fairly recent version of Ubuntu, the original ISO image on either the same HDD on the pc or on a DVD, and your USB thumb drive.  That utility is under the System>Administration menu and it's called "Startup Disk Creator."

The second part, is windows.  Dual-booting Windows and Ubuntu is fine, it's done all the time, and here's a good source of info once you get your Windows-recovery disk(s).
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Since you're waiting for a week for those factory-reset disks anyway, IF you have a Windows7 disk you can use for installation, here's what you could do (if you don't have a Windows install disk, keep reading below):

1. Install Ubuntu on your system.  Allow for a large-enough area on the HDD to remain free, so you can later install Windows on it.
2. Experiment with Ubuntu all you want.  Try everything recommended by all the posts above, try different drivers etc., and if at that point, you're satisfied, install Windows into the free area on the HDD.
3. If you're not satisfied with the setup of Ubuntu, but would like to keep plugging at it later on, use that "Startup Disk Creator" utility that is part of Ubuntu, to create an installation of Ubuntu on your USB thumb drive, **and make sure you use the option to store documents and settings in "reserved extra space" (this would be the permanence area).**  You have two radio buttons to pick from, one for this option, the other to discard all your changes when you shut down, and there's a slider for how large you want that reserved extra space to be (permanence area).  The limit right now is 4MB, which is not much, but more than adequate for experimenting with settings and drivers.

IF 4MB on your USB thumb drive is not enough (you will probably run out of space on it if it turns out that you need a whole bunch of updates), and your thumb drive is larger than 4MB, there is another way to prepare a USB thumb drive to install a full-blown Ubuntu OS on it that will save everything you create or change, and there's a good procedure on how to do that in this post (It talks about Lubuntu, but it will work with Ubuntu as well):[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Last, I know you may not have a straight Windows DVD, since OEMs like Acer and others never bother to provide one.**  There is a way you can get one for a nominal fee from Microsoft, IF you have your COA (Certificate of Authenticity)** which should be on a sticker somewhere on the outside of your PC.  Here's the Microsoft link to the form you have to fill out for that: [https://om.one.microsoft.com/opa/Validation.aspx?StoreID=b19f4ce9-dfcb-44e4-9abe-1c9dfbad47d0&LocaleCode=en-us&JavaScriptOn=yes](https://om.one.microsoft.com/opa/Validation.aspx?StoreID=b19f4ce9-dfcb-44e4-9abe-1c9dfbad47d0&LocaleCode=en-us&JavaScriptOn=yes)

Sorry for the very long post, but I think this gives you the widest array of options.  Feel free to come back if you have more questions.

Good luck :)

---

### Post by vasa1 on 2013-08-18
> **r_avital said:**
> ..., this works best when Windows is installed **last, not first** ...
I didn't read the entire post but are you sure about this? All my installs have Windows pre-existing and *buntu installed later.

---

### Post by r_avital on 2013-08-19
> **vasa1 said:**
> I didn't read the entire post but are you sure about this? All my installs have Windows pre-existing and *buntu installed later.
vasa1,

I stand corrected, and I'll edit my post above.  Good catch, thanks!

---

