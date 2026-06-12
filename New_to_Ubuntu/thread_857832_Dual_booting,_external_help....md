---
title: "Dual booting, external help..."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by netq on 2008-07-12
I've done a lot of searching, but am very new to ubuntu, and kinda disoriented with this booting stuff.  I have a 100 gig internal wiht vista on it and came across ubuntu and wanted to try.  So i got an old 12 gig HD and put in an external case and installed it to there.  Went into BIOS and set boot from USB HD.  All went great till i shut down the computer, turned the external off, and tryed to get into windows.  Even with HDD selected in BIOS, it comes up and try to load GRUB? and gives me Error 21 or something.  I want to be able to boot from windows when the external is unplugged, but boot ubuntu when its plugged in.  Did i mess my computer up bad?  Or can i fix is pretty easily?  Im real new.  Sorry if this is dumb and thanks

---

### Post by netq on 2008-07-12
I forgot to mention, whne the external is plugged in, i can get to a grub boot loader and choose vista, but thats only when the external is on and plugged in. thanks

---

### Post by falcon61102 on 2008-07-12
Sounds like you installed the GRUB to your internal HD but the files that the GRUB uses are on the Ubuntu partition.  If you want to restore your windows bootloader back, put your vista cd in and it should have a recovery/restore feature and in there it should say something about restoring your MBR, that's what you want.  Once you get that, then you can reconfigure the GRUB on the External.

---

### Post by steve8track on 2008-07-12
Here is my take on the situation:

By default, grub was installed to let you choose between the installations, but that means your computer is looking for grub each time it boots because installing grub changed the master boot record, and that record is on your internal hard drive, telling it to look for grub on the external hard drive.  So to get it back, I think there is a way with the Windows CD (at least with XP there was) to restore the master boot record using some of the CD's options.  If you do that while the linux hard drive isn't connected, I think that it should fix your problem. 

It will reinstall the master boot record for windows.  Then, it will hopefully use BIOS to determine the boot order, with each hard drive pointing to the correct location, instead of looking for grub immediately.  That means if the external hard drive is on, it should still let you choose windows or linux, but if it is off, it should let you still boot windows.  I could be wrong though, I don't know if you would loose your ability to boot linux after this, but you can just reinstall grub if that happens to get it back, perhaps removing your windows hard drive first to be sure the master boot record is on the external hard drive instead.  Also, gparted lets you select which drives are marked with a boot flag.

Sorry if I'm wrong about any of this, since I am not in the situation, this is just my best guess.

Also, alernatively, you may find this useful for putting linux and windows on the same hard drive without loosing your existing windows installation:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

After doing that, you could set up grub to choose Windows by default by changing the order of options in /boot/grub/menu.lst

Notice they also mention in the guides about a live CD with gparted on it, so you can work on your partitions without booting all of Ubuntu's live CD.

I hope this helps,

Steve

---

### Post by netq on 2008-07-13
Thanks guys, i'm going to find my vista CD and try to repair the windows boot loader and see what that does.  If that goes fine,  the next thing i'll want to try is putting grub on the external only.  But my question to that is, if windows boot loader is running vista normally, how and why would i want grub?  Is the grub boot loader vital to the operation of Ubuntu on my external?  Thanks

---

### Post by netq on 2008-07-13
Thanks for the help, I got super grub boot disk and got the windows mbr back and now it boots great, and i can use the CD to get into ubuntu.  Thanks!

---

