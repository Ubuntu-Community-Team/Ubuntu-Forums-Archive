---
title: "Instead of dealing with GRUB during install..."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by CompSciSTL on 2008-07-01
Couldn't a person just disconnect the Windows XP Hard Drive, and install Ubuntu on a second Hard Drive?  If the user wanted to boot to either drive, they could just change the boot order in BIOS to have the desired HD boot first.  Is this situation possible?  I have Windows XP on a SATA drive and want to put Ubuntu on a PATA drive if that makes any difference in this scenario.

---

### Post by sea_monkey987 on 2008-07-01
It is very much possible.  In fact, I've done it before.  Just so you know, when you boot from a hard drive by changing the settings in the bios, ubuntu sees it as /dev/sda or /dev/hda no matter how it physically plugged in to the mother board.  This is not the case if you chainload grub from another hard drive.

---

### Post by bluepowder7 on 2008-07-01
you could go totally 80's on your system and boot from a floppy!  have one floppy for booting into win, and another to boot into ubuntu.  i suppose the files on the floppy would only need to be enough to say "go to this drive" or "go to that other drive"...

or use cheap usb flash drives instead of floppies if you're not feeling terribly nostalgic.

---

### Post by arsenic23 on 2008-07-01
Sure.  I did something like this for a while, where I had a 2nd OS on an eSata drive connected to SATA0.  Then I'd just switch on the external drive before the PC to boot that OS.

Grub seems like less work then that though, and I certainly can't image popping into the Bios every time you wanted to switch OSes.  Also some bios setups don't let you specify which indiviual drive you want to boot off of, just wether you want to boot off of one kind of device or another, so it depends on wether your bios suports it as well.

---

### Post by bumanie on 2008-07-01
Yes, you can do that. Some people find it annoying going into bios all the time, but if it suits you, go for it. If you predominantly use one OS more than the other, the amount of bios changes is greatly reduced - so for some people it works fine.

---

### Post by CompSciSTL on 2008-07-01
That's good to hear!  :guitar:

I guess it's possible to install GRUB on the Ubuntu drive at a later point?

Should I put the PATA(Ubuntu) drive to the slave position or would leaving that drive in the master position while having the SATA(XP) drive be my primary drive be ok?  No conflicts would happen even after the order has been set in BIOS?

---

### Post by 4partee on 2008-07-01
> **sea_monkey987 said:**
> It is very much possible.  In fact, I've done it before.  Just so you know, when you boot from a hard drive by changing the settings in the bios, ubuntu sees it as /dev/sda or /dev/hda no matter how it physically plugged in to the mother board.  This is not the case if you chainload grub from another hard drive.

On 8.04, there is a known problem on mixed PATA/SATA systems.  

[http://ubuntuforums.org/showthread.php?t=795362&highlight=grubbish](http://ubuntuforums.org/showthread.php?t=795362&highlight=grubbish)

HTH;
John

---

### Post by CompSciSTL on 2008-07-01
> **4partee said:**
> On 8.04, there is a known problem on mixed PATA/SATA systems.  

[http://ubuntuforums.org/showthread.php?t=795362&highlight=grubbish](http://ubuntuforums.org/showthread.php?t=795362&highlight=grubbish)

HTH;
John

So I have to go with all SATA or PATA in 8.04?  Ugh...:(

---

### Post by CompSciSTL on 2008-07-02
After reading through the posts, I noticed that this issue was for 64-bit systems.  What about 32-bit versions of Ubuntu?  Do they have this problem as well?


(Hopefully it can be fixed sooner than later.)

---

### Post by bumanie on 2008-07-02
I believe the potential conflict between sata and pata drives happens on both 32bit and 64bit systems. Look at [this]("http://users.bigpond.net.au/hermanzone/p15.htm"), it may help with mixed drives.

---

### Post by CompSciSTL on 2008-07-15
Are there any Linux Distros that are more friendly towards a mixed PATA/SATA hard drive setup?

---

### Post by kansasnoob on 2008-07-15
> **CompSciSTL said:**
> Are there any Linux Distros that are more friendly towards a mixed PATA/SATA hard drive setup?

I honestly thought this thread was a joke until I read that.

My suggestion is just stay with Windows.

---

### Post by cariboo on 2008-07-15
Ubuntu is really friendly when using pata and sata drives. I have vista on the first partition of my pata drive hardy on the second, Intrepid on the first sata drive and two sata data drives. I've only had a problem when I was playing with grub2 and for some reason vista would never show up in the boot menu. BTW I run 64bit versions of everything, Vista,Hardy and Intrepid.

Jim

---

