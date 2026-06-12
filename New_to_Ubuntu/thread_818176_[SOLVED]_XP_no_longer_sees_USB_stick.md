---
title: "[SOLVED] XP no longer sees USB stick"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-06-04
Hi,

Newbie playing and got in trouble!

I let the heron write to a USB stick and now Windows XP no longer 'sees' it. I don't mind for myself as I'm slowly migrating to the heron. Trouble is, it's not my device and there's data on there that's needed. Any advice as to what to do to get XP reading this again much appreciated.

---

### Post by sweeneytodd on 2008-06-04
if u have a dual boot u could try booting ubuntu and copying data to your winxp partition, might be bit of a long way

---

### Post by Duck2006 on 2008-06-04
Use gparted to format it as fat32 and win should see it.

---

### Post by Tim Silver on 2008-06-04
I do have dual boot. XP is on my internal drive and the heron is on an external USB HDD. I did consider that, but in my total ignorance I'm worried about then making my Windows drive unreadble! Or is my reasoning rubbish?

---

### Post by bumanie on 2008-06-04
Usually an unclean unmount won't worry xp. It may be worth trying to put it back in ubuntu and checking that ubuntu still recognises it, ensuring that you unmount it correctly. If not, may be it has been written to for the last time. Unfortunately, they have a limited lifespan. Once their life is up - it's up. Hopefully someone comes up with a better solution.

---

### Post by Tim Silver on 2008-06-04
Hi Duck,

You've helped me before.

I don't want to format it until I get the data off. Re my above post - if I let the heron write to my Windows drive, will I still be able to boot into XP?

---

### Post by sweeneytodd on 2008-06-04
yes, everything will b fine, ubuntu is everything and more

---

### Post by Paqman on 2008-06-04
> **Duck2006 said:**
> Use gparted to format it as fat32 and win should see it.

USB sticks are all formatted to FAT32 in the factory. My guess is either that the stick has died, or the filesystem is corrupt.

---

### Post by Tim Silver on 2008-06-04
Hi Bumanie,

The heron sees it no problem, but it just flashes away like mad when put into a Windows machine. Very dissapointing if it is knackered as it's only a few weeks old! 1GB for £10 - not a problem, but the data (as always) is irreplaceable!

---

### Post by sweeneytodd on 2008-06-04
boot ubuntu, can u c it, if so , can u copy it, if so paste it, just try it, if it doesn't work, usb is stuffed

---

### Post by Duck2006 on 2008-06-04
> **Tim Silver said:**
> Hi Duck,

You've helped me before.

I don't want to format it until I get the data off. Re my above post - if I let the heron write to my Windows drive, will I still be able to boot into XP?

Yes you will be able to boot to win after you write the files to win from HH.
If it will not write the files to win you need to install ntfs-3g drivers to HH, System -> Administration -> Synaptic Package Manager click on Search and find the drivers, install the drivers from there.

---

### Post by Nessa on 2008-06-04
It's possible that when you wrote to the usb, you changed the format to ext3 which windows cannot read. Copy the data to your heron disk. Format the usb in fat32 and then transfer the files back to it. Forgot how to make sure that it's gonna write in the format of the media. Maybe someone with more knowledge can add something.

---

### Post by Tim Silver on 2008-06-04
OK Chaps,

I'll trust the heron, copy to my Windows drive and then use gparted to try and recover the stick. Thanks for all your input. (It's quite strange feeling so apprehensive at 55!)

---

### Post by bumanie on 2008-06-04
If it works in hardy, can you copy your data somewhere within ubuntu or is seen, but not functioning?

---

### Post by az on 2008-06-04
> **bumanie said:**
> It may be worth trying to put it back in ubuntu and checking that ubuntu still recognises it, ensuring that you unmount it correctly. 

Correct.  Does the device work at all?  I can't see how writing to the device makes it unreadable in one OS and not another.

> **bumanie said:**
> 
If not, may be it has been written to for the last time. Unfortunately, they have a limited lifespan. Once their life is up - it's up. Hopefully someone comes up with a better solution.

They have a theoretical limit to their lifespan, but in practice, they will break before the cells run out of write cycles.  It's more likely that one of the chips or circuitry broke rather than the NAND cells reaching their limit.  It should take way more than ten years of continual use to use up the write cycles.

> **Tim Silver said:**
> Hi Duck,

You've helped me before.

I don't want to format it until I get the data off. Re my above post - if I let the heron write to my Windows drive, will I still be able to boot into XP?

I can assure you that millions of people have written to NTFS filesystems using linux without any problems.  There used to be issues up until a few years ago, but that is long-gone.  Ubuntu would not let you write to a partition if it wasn't safe.

---

### Post by lfaraone on 2008-06-04
```
sudo mkfs.vfat /dev/*device*
```
After the device is unmounted, of course.

---

### Post by Duck2006 on 2008-06-04
> **Paqman said:**
> USB sticks are all formatted to FAT32 in the factory. My guess is either that the stick has died, or the filesystem is corrupt.

Thats true, but if your formated it in HH then you he may have formated it to ext2 or ext3.

---

### Post by sweeneytodd on 2008-06-04
hey, no worries, just a bit of teething, it'll soon pass, put your faith in ubuntu,

---

### Post by Tim Silver on 2008-06-04
That's the confusing thing with forums - messages overlap!

Nessa, when I say I let the heron write to the stick - what actually happened was that I deleted a couple of files that were on the stick and when I went to 'unmount' it I was asked the question did I want to (in Windows terminology) empty the wastebasket. Never come across that before. Anyway, I clicked on 'yes'. Could that have changed the format?

---

### Post by lfaraone on 2008-06-04
> **Tim Silver said:**
> That's the confusing thing with forums - messages overlap!
Too true, but only in the most active ones...

We need some sort of in-thread threading... </offtopic>

---

### Post by Tim Silver on 2008-06-04
Just to let you guys know...

Successfully copied data to Windows drive - no harm done!

Successfully re-formatted stick.

Successfully copied data back to stick.

Successfully returned stick to owner.

Thanks all.

---

### Post by az on 2008-06-04
> **Tim Silver said:**
> what actually happened was that I deleted a couple of files that were on the stick and when I went to 'unmount' it I was asked the question did I want to (in Windows terminology) empty the wastebasket. Never come across that before. Anyway, I clicked on 'yes'. Could that have changed the format?

No.

---

