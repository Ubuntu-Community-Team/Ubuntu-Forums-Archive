---
title: "Black screen at start up"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by bpl07 on 2008-05-27
This has happened randomly over the last half year that I've been playing with ubuntu.  I'll start up my laptop, choose ubuntu, it'll start to load, then right before it gets to the login window, it'll just go to a black screen.  Nothing I have tried has worked to wake it from this black screen, and I eventually have to power-button shutdown.  I've waited overnight once to see if it would eventually pull itself out, but even 8 hours wasn't enough.

If I'm lucky, I just have to choose recovery mode in grub at start up instead, let it boot normally, then everything is back to normal.  A few times, however, the filesystem has been corrupted due to the hard shutdown and I usually have to start all over and reinstall ubuntu because grub is corrupted.

Is there any other option in this situation?  Any magical key stroke I can do to restart xserver or something?  Any way to recover a corrupted filesystem?  I was always told how much more stable linux was than windows, but so far my experience has been that linux will randomly fail on me and I'll have to start all over, whereas windows just gets slow over time.

---

### Post by spiderbatdad on 2008-05-27
could you run the command```
dmesg > dmesg.txt
```
This will create a text file in your home directory. Right click that file and select 'create an archive.' Upload that archive here using the manage attachment tool below.

---

### Post by pieisgood4589 on 2008-05-27
You could try using your distro cd's or a rescue distro like tomsrtbt to boot to linux and use fsck to try to repair the file system. Also, if you have a Windows XP install CD handy, you can boot it up, enter into the "Repair System" mode, and enter the command "fixmbr" which will clear your probably cluttered master boot record, and then the next time you install GRUB it should be fine.

---

### Post by bpl07 on 2008-05-27
There's my dmesg archive

---

### Post by spiderbatdad on 2008-05-27
looks like a few problems. Unfortunately, I am no expert.
>  No AGP bridge found
[   18.527100] Your BIOS doesn't leave a aperture memory hole
[   18.527140] Please enable the IOMMU option in the BIOS setup
[   18.527180] This costs you 64 MB of RAM
[   18.560409] Mapping aperture over 65536 KB of RAM @ 4000000 

> Could not switch to high resolution mode on CPU 1
[   20.841758]  lapic is not functional.
[   20.841798] Could not switch to high resolution mode on CPU 0 

> APIC error on CPU1: 00(40)
[ 6365.083221] APIC error on CPU0: 00(40) 

I would check for cpu settings in BIOS

Also, I would try these boot parameters by editing the default kernel line in /boot/grub/menu.lst
```
gksu gedit /boot/grub/menu.lst
```Scroll to this section:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=#'s ro **noapic nolapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

```

Change --quiet splash at the end of the line beginning with the word 'kernel' to match the example above. You may have to experiment a little by leaving out one or more of those parameters. You can also try acpi=force nolapic

If you end up unable to boot, don't panic. Boot into recovery mode by pressing esc, if necessary to get the grub menu, at start up, and from the prompt, run ```
nano /boot/grub/menu.lst
```re-edit the kernel line and press ctrl+o to save the file. Hit enter to confirm the filename, and ctrl+x to exit.

---

### Post by bpl07 on 2008-05-28
Ok, I'm pretty sure the high resolution thing has to do with the splash, because it goes away and the boot operations come up instead.  I'm trying to fix that with startupmanager, which appears to just be changing the menu.lst file.  There isn't a widescreen resolution available, which is probably the source of the problem.  I think I'll just turn the splash off.

As for the iommu thing, my bios doesn't have this setting, so I'm trying the kernel parameter iommu=memaper=3 that I found online.  Seems to be an issue wih systems with more than 4gb of ram, which mine has.  I'll keep you guys posted, thanks for the replies.

---

### Post by bpl07 on 2008-05-28
Ok, the iommu=memaper=3 kernel parameter put my boot sequence in a loop where it kept soft resetting SATA to 1.5Gbps, then hard resetting, and some other stuff that happened too fast for me to see.  I eventually had to hard shutdown.  This loop could be what my system gets in when I get the black screen.

Also, eliminating splash didn't get rid of the high resolution error, so still not sure what's going on there.

---

### Post by spiderbatdad on 2008-05-28
> **bpl07 said:**
> Ok, I'm pretty sure the high resolution thing has to do with the splash, because it goes away and the boot operations come up instead.  I'm trying to fix that with startupmanager, which appears to just be changing the menu.lst file.  There isn't a widescreen resolution available, which is probably the source of the problem.  I think I'll just turn the splash off.

As for the iommu thing, my bios doesn't have this setting, so I'm trying the kernel parameter iommu=memaper=3 that I found online.  Seems to be an issue wih systems with more than 4gb of ram, which mine has.  I'll keep you guys posted, thanks for the replies.

Ah not sure Ubuntu supports more than 4gb. Hope you try the above parameters...actually hope you resolve the issue. Good luck. Keep us posted.

---

### Post by bpl07 on 2008-05-28
[Someone else with my same problem]("http://www.nvnews.net/vbulletin/showthread.php?t=83419"), but nvidia graphics instead of ati.

Using iommu=noaperture works for me, no more iommu error in dmesg.  I didn't have a bios setting for iommu, so I would recommend trying that first before this kernel parameter.

---

### Post by bpl07 on 2008-05-29
Apparently it doesn't actually, because it happened again this morning.

---

### Post by bpl07 on 2008-06-17
I think it might have something to do with the forced disk check every 32 boots.  With kernel -19, I now get a notice that X failed to start and that I should restart.  When I do, I cancel the disk check and my system loads fine again.  Any ideas of what the issue might be with the disk check?

---

