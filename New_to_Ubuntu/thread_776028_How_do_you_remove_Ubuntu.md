---
title: "How do you remove Ubuntu?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by aNaLpLeAsEr on 2008-04-30
I currently have Ubuntu 7.10 installed on an Acer laptop but need to remove it and install Windows XP. The windows XP disc cant find the hard-drive. Help would be appreciated.

:)

---

### Post by miwaypet on 2008-04-30
If you still have your 7.10 disk you can boot it up and use gparted to wipe the drive. If not, then download gparted and burn it to a disk, then use it to wipe the drive.

XP wil not see the drive because it refuses to recognize linux. Install XP on its own partition then ubuntu. And you will have no problems.

Hope this helps.

---

### Post by OffAxis on 2008-04-30
If you're over-writing the hard disc entirely there's no need to remove ubuntu; the format process of the WinXP install will trash it.
It should still detect and come up as a raw drive in XP regardless of what's on it.

---

### Post by kamitsukai on 2008-04-30
> **aNaLpLeAsEr said:**
> I currently have Ubuntu 7.10 installed on an Acer laptop but need to remove it and install Windows XP. The windows XP disc cant find the hard-drive. Help would be appreciated.

:)

I would use Active killdisk freeware all you do is burn the iso file in [this zip archive]("http://software.lsoft.net/boot-cd-iso.zip") to disk just like with ubuntu and then reboot your computer and follow the screen prompts it will erase everything on the hard drive (so backup what you want!) and then you can install xp

good luck:)

---

### Post by aNaLpLeAsEr on 2008-04-30
> **OffAxis said:**
> If you're over-writing the hard disc entirely there's no need to remove ubuntu; the format process of the WinXP install will trash it.
It should still detect and come up as a raw drive in XP regardless of what's on it.

It doesn't unfortunately and it a genuine disk which has been used for many installs.

---

### Post by lazyart on 2008-04-30
Does ubuntu still boot up?  Sounds like the HD is gone because while XP won't recognize what's on the hard drive, it's smart enough to know that there IS a hard drive.

---

### Post by Calash on 2008-04-30
Is it a SP1 or SP2 disk?  Depending on the laptop you may be running into a SATA issue.  One thing to try would be to go into your BIOS and look for a SATA or Harddrive operation area.  Someplace, if the drive is SATA, there should be a selection for "Compatibility" or "Combination" mode for the drive.  Set it to that and try your install again.

---

### Post by aNaLpLeAsEr on 2008-04-30
Have done that and removed ubuntu. Basically computer wont boot into it now but the grub bit seems to be there still.

Windows still cant find hard drive!!

---

### Post by aNaLpLeAsEr on 2008-04-30
I dont think its the hardrive as ubuntu was working before i just deleted that partition.

---

### Post by fraser_m on 2008-04-30
Steal a Window$ CD. And change your username. It's DIRTY! Lolz. Maybe it's just me that's dirty.

But seriously, try using GParted (on the LiveCD) to format the entire drive as NTFS.

---

### Post by ugm6hr on 2008-04-30
XP sometimes struggles to find Linux partitions.

Try a disk wiping tool from those available on ultimate boot CD:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Once completely wiped, XP should find it.

You could try using GParted to reformat the HD to Fat32 format as an alternative (not sure if that works).  Just make sure you tell XP to reformat prior to installing.

---

### Post by aNaLpLeAsEr on 2008-04-30
i downloaded the zip and used the utility boot disk to erase drive

My genuine windows disk which works on 2 other computers still can not find a hard drive. SP2 version as well

---

### Post by aNaLpLeAsEr on 2008-04-30
i just adjusted harddrive setting in bias and deleted mbr. installation now working.  thanks everyone for the help.

---

### Post by aNaLpLeAsEr on 2008-04-30
> **aNaLpLeAsEr said:**
> i just adjusted harddrive setting in bias and deleted mbr. installation now working.  thanks everyone for the help.


Ok after the disk format finished (ntfs) was fat32 after the recommendation, windows said it cant install on the drive!!!!

---

### Post by Bensky on 2008-04-30
> **aNaLpLeAsEr said:**
> Ok after the disk format finished (ntfs) was fat32 after the recommendation, windows said it cant install on the drive!!!!

If it got changed to FAT32, it will not install. Windows needs a NTFS partition to be installed I'm pretty sure.

---

### Post by aNaLpLeAsEr on 2008-04-30
> **Bensky said:**
> If it got changed to FAT32, it will not install. Windows needs a NTFS partition to be installed I'm pretty sure.

i agree i tried to format it back to ntfs with xp but it failed


maybe there is a problem with the hard drive after all??

but ubuntu was working ok!! 

:confused:

---

### Post by bodhi.zazen on 2008-04-30
Remove Ubuntu (Restore Windows):

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by aNaLpLeAsEr on 2008-04-30
> **bodhi.zazen said:**
> Remove Ubuntu (Restore Windows):

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

I'm not running a dual boot system.

---

### Post by bodhi.zazen on 2008-04-30
> **aNaLpLeAsEr said:**
> I'm not running a dual boot system.

Then there is nothing to remove is there ? You just install what OS you will and format over Ubuntu as you install. If you want to wipe the hard drive you certainly can. If the Windows disk does not recognize the hard drive, you might want to consult windows documentation and/or microsoft.

---

### Post by aNaLpLeAsEr on 2008-04-30
Thats what I tried first but windows could not see the hard drive. but thanks for the help.

I finally got it to work. tempremental hard drive perhaps?? might be on its way out.

After all that i got XP on the laptop (Acer) only to find that the drivers are only available for Vista.  PMSL

Thanks for all the help everyone. I'm gutted i got to run Vista on this thing, but beggers can't be choosers.

---

### Post by phread59 on 2008-04-30
Before downgrading to Vista.  Try going to Acer's site and see if XP drivers are there.  If so download them and install, You should then be golden.  Also if you have XP loaded and only some things don't work like printers or Video ect try going to the manufactuer's web sites and download XP drivers from there.  I would NOT give up on XP and sink to the depths of Vista.  I would rather anything but that trash.

Mark Shuman

---

