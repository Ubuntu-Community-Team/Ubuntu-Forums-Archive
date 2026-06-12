---
title: "Dual boot system keyboard quit working only when booted into XP"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Usually Lurking on 2008-12-01
I've been wanting to explore Linux again and recently started experimenting with Ubuntu 8.10.  I've spent the last week getting the HDD partitions and desktop to my liking so I have not installed many actual programs yet.  As of this last Saturday ( 11-29-2008 ) my Keyboard, PS/2 connection, worked fine in whether booted into Ubuntu or XP and worked in grub as well.  I discovered on Sunday the 30th that when booted into XP my keyboard no longer worked(but my USB mouse works).  The keyboard still works fine in Grub and in Ubuntu but no amount of keypressing works when booted into XP. My device manager indicates the driver has been corrupted or something (Code 39 error) and indicates the driver files are *i8042prt.sys* and *kbdclass.sys*.

Here's a list of the things I've tried so far:
[LIST]
[*]Tried swapping in a USB keyboard;
[*]I've tried updating the drivers in Device Manager; 
[*]uninstalling/reinstalling the drivers in Device Manager; 
[*]I tried the uninstall driver, shutdown, unplug keyboard, reboot, shutdown, plug keyboard back in and reboot routine; 
[*]deleting those two files and letting them be rebuilt at boot;
[*]using the recovery console to copy them from the XP install CD to the System32/Drivers folder 
[*]and as a last resort I tried a repair install only to find when asked to enter the CoA code the keyboard still did not work.
[/LIST]

I obviously borked something on the Ubuntu side that's causing a conflicting with those drivers on the XP side but I'm at a loss as to what that might be.  The only thing I can remember installing since the last time the keyboard worked was maybe Wine, but for sure I did a test install of my Baldur's Gate+ToSC disc and I attempted to install Daemon Tools Lite too.  I've since uninstalled those two programs and even Wine itself without results.  The only other thing I can think of is that I've been messing around with the /fstab file a lot trying to get all my drives/partitions to mount up at boot like I want but I don't know how that would impact the keyboard drivers.  Before I totally wipe everything out and have to start from scratch I'd like to know I've truly tried everything so any advice/insight would be appreciated.

Thanks

---

### Post by Usually Lurking on 2008-12-02
I have effectively solved my issue by removing Ubuntu and re-imaging the Windows OS partition with an older backup image.  I'd like to have figured out what borked the XP keyboard drivers in the first place and how whatever did it was preventing me from fixing the problem but with my backups this turned out to be the far more effective and expedient solution.

---

### Post by sydbat on 2008-12-02
It had nothing to do with Ubuntu. It was completely a Windows XP problem. You could have used the System Restore for XP without removing Ubuntu.

---

### Post by Usually Lurking on 2008-12-02
> **sydbat said:**
> You could have used the System Restore for XP without removing Ubuntu.

I actually tried that and it was unsuccessful at restoring the drivers to working condition.

> **sydbat said:**
> It had nothing to do with Ubuntu. It was completely a Windows XP problem. 

I may not know Ubuntu well and I admit that but I do know _something_ I did while booted _into_ Ubuntu affected those Windows drivers.  It may not have been Ubuntu specifically, and I implied that when I wrote **&#8220;I obviously borked something&#8221;** because I realized it was probably a setting I enabled or disabled or perhaps a program I incorrectly installed/uninstalled in Ubuntu that caused the conflict.  However if as you say it was "completely a Windows XP problem" then a system restore would not be able to accomplish what a Repair install couldn&#8217;t.  So since I realize sarcasm isn't always apparent in written media so I'll give you the benefit of the doubt that you're kidding because otherwise that was a very unhelpful, uninformed and asinine statement to make.

---

### Post by sydbat on 2008-12-02
Sorry. I wasn't using sarcasm. I really mean that Ubuntu had noting to do with the XP problem. 

The only way it could be part of the "borking" would be if you went into the XP partition (while booted into Ubuntu) and worked on XP files directly. Making changes to Ubuntu files would have no effect on XP.

---

