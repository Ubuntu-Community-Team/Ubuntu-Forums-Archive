---
title: "Installing OS Issue"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by xcvcx on 2008-04-26
Long story straight I reform mated to Linux to find that it wasn't for me, so i'm going to keep testing it on my desktop computer and use windows on my laptop. I tried to install windows by putting in the cd but i got an error saying it could not find my hard drive. So i completely nuked both my hard drives. Now i can install Linux but when i put in the windows cd i still get the same error which is

Setup did not find any hard disk drives installed in your computer

Make sure any hard drisk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program.

Setup cannot continue. To quit Setup, press F3

Any ideas?

And my hard drives do work since installing Linux is possible.

It's a laptop HP DV8000

---

### Post by Joeb454 on 2008-04-26
Boot from the Ubuntu Live CD. And then when it loads up the Desktop environment, click System>Administration>Gparted

And format your drive to an NTFS partition. It may take a while, but it should allow the Windows disc to see it :)

---

### Post by frup on 2008-04-26
> **Joeb454 said:**
> Boot from the Ubuntu Live CD. And then when it loads up the Desktop environment, click System>Administration>Gparted

And format your drive to an NTFS partition. It may take a while, but it should allow the Windows disc to see it :)

Do you have to do that much? Shouldn't plain unformatted disc space or fat32 be good enough for windows?

---

### Post by xcvcx on 2008-04-26
i did that but it still says device is dev/sda then under filesystem it says NTSF and it still doesn't recognize.

---

### Post by xcvcx on 2008-04-27
also this is the same windows cd i've used 10000 of times.

---

### Post by thisiam on 2008-04-27
can you see the HDD from the BIOS?
if you have used that windows cd that many times you might want to try a different one.

---

### Post by xcvcx on 2008-04-27
i did check them and I've tried other cd's.

---

### Post by xcvcx on 2008-04-27
I've tried to nuke my hard drives and completely erase them. I've tried the gparted. I changed the file system to NTSF. Nothing seems to work. I know the windows cd's I've tried work. What I do notice is that the partition is always dev/sda1, maybe that plays a part. Could someone please help this is getting very aggravating.

---

### Post by southernman on 2008-04-27
When you boot the livecd and get into gparted, how many partitions do you see on the drive in question?

Simply deleting the partition (or all of them) *should* make your drive readable by MS. If not rinse and repeat with the livecd, except setup your drive how you want it - making them ntfs.

Should take nothing more than that to get you going again... as long as your drive didn't decide to puke on you.

Good luck

---

### Post by Chilli Bob on 2008-04-27
I had a similar problem last night setting up a Win2K/Hardy dual boot.  I partitoned the hard drive with the live cd, then rebooted with the windows cd, but it couldn't see the drive at all.  Turns out I had partitoned the drive,but not actually formatted the partitions.  I re-did it and all was well.

---

### Post by xcvcx on 2008-04-27
Okay. I'm trying to reformat the drives by reinstalling Linux only manually changing them to ntsf. But it automatically changed them back to ext3.

---

### Post by xcvcx on 2008-04-27
I really don't understand why this has to be so hard. I've done everything you guy's have told me but nothing is working.

Gparted changed the partition to ntsf but it doesn't format it so it still doesn't see it. What is really pissing me off is that i actually did a nuke of my hard drive but it still! wasn't found but Linux did.

---

### Post by southernman on 2008-04-27
Linux can not install to a ntfs partition, that's not possible so forget that path.

When your in gparted and you setup the partitions as ntfs, are you clicking the "apply" button. They don't get formatted until then. 

If all else fails, use gparted to just delete every partition you have, then click apply. 

reboot with your MS cd

---

### Post by Paqman on 2008-04-27
> **xcvcx said:**
> 
Setup did not find any hard disk drives installed in your computer


Do you have SATA hard drives, and are trying to install XP? 

XP doesn't have SATA drivers by default. You have to put them on a floppy, then when the setup says "Press F6 to install third party or SCSI drivers" you can hit F6 and it'll give you the chance to add your drivers.

---

### Post by xcvcx on 2008-04-27
THank you Paqman you're answer was the closest to being right. All i had to do was disable the SATA in the BIOS.

Thanks every for the help

---

