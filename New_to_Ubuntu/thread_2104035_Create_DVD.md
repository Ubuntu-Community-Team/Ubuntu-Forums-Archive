---
title: "Create DVD"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by rjh213 on 2013-01-11
I am new to this.  I want to create a Live DVD to run and evaluate a crashed hard drive.  I have downloaded an iso file and want to burn it.  Can I do it with any DVD burner program?  That infra recorder (don't remember the exact name) was confusing and seemed to imply I would be forced to get a toolbar.  I don't want that.  I just want a simple process to create the DVD.  Can someone advise me?  Thanks.

---

### Post by squakie on 2013-01-11
Are you trying to create the DVD in Windows or Linux?  If Windows you should be able to just right-click on the file name for the iso and select burn image.  If Linux, Brasero should be able to burn the image.  Just remember - don't burn the iso FILE to a disk, instead be sure to burn the ISO image as an IMAGE in the software you use.

---

### Post by vegas89 on 2013-01-11
You might try devede, It is in your ubuntu software center. I found it easy to use and not complicated.  \\:D/

---

### Post by leprechaunking on 2013-01-12
the startup disk creator installed in 12.10 (and earlier) is what i use to create livecd's and live usb disks

---

### Post by rjh213 on 2013-01-13
I'm trying to create a live cd in Windows XP.  I think I created one, and I did it with the "burn iso image" in CDBurnerXP.  However, I can't get my Dell PC to recognize it should boot from it.  I even went into the BIOS and changed the boot order to put my drive first.  I see the access light go green, implying the drive is being looked at, but Windows still comes up.  This is an old Dell, about 10 years old.  Is it possible it doesn't recognize a DVD, which is what I burned the iso image to?  Is it possible to burn an older version of Ubuntu to a CD or create a floppy?  With the DVD in the drive, Windows doesn't even see it.  Any thoughts anyone has would be appreciated.  Thanks.

---

### Post by kabukiM0n0 on 2013-01-13
> **rjh213 said:**
> I'm trying to create a live cd in Windows XP.  I think I created one, and I did it with the "burn iso image" in CDBurnerXP.  However, I can't get my Dell PC to recognize it should boot from it.  I even went into the BIOS and changed the boot order to put my drive first.  I see the access light go green, implying the drive is being looked at, but Windows still comes up.  This is an old Dell, about 10 years old.  Is it possible it doesn't recognize a DVD, which is what I burned the iso image to?  Is it possible to burn an older version of Ubuntu to a CD or create a floppy?  With the DVD in the drive, Windows doesn't even see it.  Any thoughts anyone has would be appreciated.  Thanks.


To burn a bootable .iso from Xp use this [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
It works a treat and is simple. 

You can burn older copies of Ubuntu but they have no LTS.
Also try burning onto a flash drive and just changing the boot order in BIOS

---

### Post by rjh213 on 2013-01-13
Thanks.  Sounds easy, but I'm a real beginner and I'm stuck running the USB installer.  It states "Simply choose a Live Linux Distribution".  The drop-down menu has dozens of options.  I'm not sure which one to choose.  Also I'm not sure I have a flash drive that will be big enough.  Can the "flash drive" be a USB external drive?

---

### Post by kabukiM0n0 on 2013-01-13
> **rjh213 said:**
> Thanks.  Sounds easy, but I'm a real beginner and I'm stuck running the USB installer.  It states "Simply choose a Live Linux Distribution".  The drop-down menu has dozens of options.  I'm not sure which one to choose.  Also I'm not sure I have a flash drive that will be big enough.  Can the "flash drive" be a USB external drive?

Look at what it says on the .iso you downloaded. Click from the drop-down menu the same one. 
It cannot if by 'external drive' you mean hard drive, well ... in theory I guess you could if you had a small partition into which install it. A pen drive works, SD Card **with** external adapter, mp3 also works (nothing apple related).

---

