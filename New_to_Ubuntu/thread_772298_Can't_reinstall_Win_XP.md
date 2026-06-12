---
title: "Can't reinstall Win XP"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by neurostu on 2008-04-28
With the upgrade from Gutsy to Hardy, i thought it would be a good time to do a complete overhaul on my laptop. I resized and reformatted my partitions (to move more space from my NTFS to EXT3 partition).  I went to reinstall XP (I need it for work) and the XP installer said that it could not find a partition to install to.  I rebooted into gparted, and reformatted one of my partitions to NTFS again, but it still said that it couldn't find a valid partition to install to...

Does anybody have any idea as to why this happened, and how to fix it?

---

### Post by Hospadar on 2008-04-28
I've always installed windows first, then shrunk the win partition with gparted, and then installed linux.  But for what you want to do, I would say don't format the partition with gparted, just leave an appropriately sized block of free space, and use the windows installer to format and install to that.

---

### Post by forrestcupp on 2008-04-28
Your NTFS partition needs to be the first one on the hard drive.

---

### Post by neurostu on 2008-04-28
> 
Your NTFS partition needs to be the first one on the hard drive.


It is.  It used to be a working XP partition, I just shrunk it and reformatted it using gparted.

Hospadar:  If I delete the partition completely you think that will work?

---

### Post by bigken on 2008-04-28
delete all your partitions and use windows to create a partition 
whats left use for ubuntu

---

### Post by pro003 on 2008-04-28
the solution is simple:

1. install windows
2. install linux


that's how I always do and I never had a problem...

---

### Post by Calash on 2008-04-28
XP needs to have the blank space, or have it already formatted to NTFS.  GParted can do this for you.  It does not need to be the first partition...on mine it is the 3rd.  As long as XP sets the boot.ini file correctly it will be fine.

Use gparted to resize the drive and format the partition you want for XP to NTFS, then try again.


Just be aware, XP will erase GRUB from the MBR, preventing you from using Ubuntu until you fix it.  It is an easy fix using the Live CD, but this is why many people suggest to install XP first, then Ubuntu.

---

### Post by oedha on 2008-04-28
which gparted ?
did you use gparted liveCD ? 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by bigken on 2008-04-28
is your win xp cd a system restore disc or a normal xp install cd ?
if its a restore cd you will have to select full distructive install
if it a windows xp cd delete all partitons and press C to create your desired 
partition size

---

### Post by neurostu on 2008-04-28
I was using the gparted that is installed with Gutsy.  I erased my original XP partition, so that I could re-install a clean verion of XP

I <B> DO NOT </B> want to get rid of my current ubuntu installation. I spent a lot of time and effort installing special programs and customizations to get it exactly how I <b> NEED </b> it.

That being said this is what I have done:
1 - Erased NTFS Partition, reformatted
2 - Tried to install, got the following error:
```

Setup did not find anyhard disk drives installed in your computer.

Make sure any hard disks drives are powered on and properly connected to your computer, and that and disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program.

Setup cannot continue. To quit setup press F3.

```
3. I deleted the NTFS partition and left it as emptpy space
4. Tried to install XP again, got the same error message.


What is going on?

---

### Post by neurostu on 2008-04-28
BTW, I am using a Lenovo T61

---

### Post by neurostu on 2008-04-28
Bigken, Its a full install cd, again I can't afford to delete my ubuntu partition. (Or my other partition for that matter, a third data storage partition)

---

### Post by bigken on 2008-04-28
ah now I know whats wrong you need to create an extended partition give it a go

tell us what your partitions are

---

### Post by Tux.Ice on 2008-04-28
pop in the windows cd and install xp

Then boot into ubuntu (if your going to use hardy and you dont already have a cd,make sure to use a torrent) and shrink you windows partition and install ubuntu.

---

### Post by neurostu on 2008-04-28
Ok so did you guys even read the previous posts that I made?  

So I did some searching around and it turns out that I had to alter my BIOS settings for my HDD.

I have an SATA drive and the winXP cd did not have the drivers needed to install on this drive.  I had to go into my bios and change my HDD from AHCI to Compatability mode, now windows is installing fine.

These forums can be great but sometimes i wonder how many people actually read the ENTIRE post before they give their advise...

---

### Post by neurostu on 2008-04-28
deleted double post...

---

### Post by Calash on 2008-04-28
I was just about to suggest that....sorry for the delay.

Once you install all the drivers for your system, you should be able to switch it back to where it was, that way you will get more performance out of the system.

Also, you will have to reinstall GRUB after it is installed.

I used this guide...it looks a bit complicated but it is not as bad as it looks ;)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bigken on 2008-04-28
did you tell anybody it was sata drive ?

---

### Post by neurostu on 2008-04-28
Calash,

So I tried switching it back to AHCI but when I booted into windows it gave me a BSOD and rebooted...

Any ideas?

I also didn't realize that my drive was sata until after I did my searches

---

### Post by kolisikepu on 2008-04-28
> **bigken said:**
> did you tell anybody it was sata drive ?

LOL :lolflag:

> These forums can be great but sometimes i wonder how many people actually read the ENTIRE post before they give their advise... 	

The forums great and helpful when people give ALL info needed to trouble shoot. ](*,):biggrin:

---

### Post by kolisikepu on 2008-04-28
> **neurostu said:**
> Calash,

So I tried switching it back to AHCI but when I booted into windows it gave me a BSOD and rebooted...

Any ideas?

I also didn't realize that my drive was sata until after I did my searches

If possible, install Vista (all you need is Basic) and then roll back to XP.  See if that helps.

---

### Post by Calash on 2008-04-28
Hmm...did you install all the drivers for the laptop?  You may need to get it up to SP2 as well.

We had similar issues with a Dell where I work.  After downloading the drivers and updating all the patches it worked fine.



> 
These forums can be great but sometimes i wonder how many people actually read the ENTIRE post before they give their advise... 


I believe this comment was in reference to the OP stating he wanted to keep the current Ubuntu install, yet getting several suggestions to wipe it out after the fact..not about SATA drives.

---

### Post by Zralou on 2008-04-28
> **Calash said:**
> 
I believe this comment was in reference to the OP stating he wanted to keep the current Ubuntu install, yet getting several suggestions to wipe it out after the fact..not about SATA drives.

I also noted the original thread title was "Can't reinstall Win XP", but had one poster who advised:
> pop in the windows cd and install xp

Then boot into ubuntu (if your going to use hardy and you dont already have a cd,make sure to use a torrent) and shrink you windows partition and install ubuntu.
So the OP's comment about "actually reading the whole thread" was a valid one.

Sara Lou

---

### Post by kolisikepu on 2008-04-28
> **Calash said:**
> Hmm...did you install all the drivers for the laptop?  You may need to get it up to SP2 as well.

We had similar issues with a Dell where I work.  After downloading the drivers and updating all the patches it worked fine.





I believe this comment was in reference to the OP stating he wanted to keep the current Ubuntu install, yet getting several suggestions to wipe it out after the fact..not about SATA drives.

I think when he's saying he can't install XP, I don't think he has it installed for him to install SP2.

---

### Post by forrestcupp on 2008-04-28
> **kolisikepu said:**
> 
The forums great and helpful when people give ALL info needed to trouble shoot. ](*,):biggrin:

Guys, he's talking about the fact that time and time again he stated that he **could not** install Windows, and a lot of people gave him the advice to install Windows.  I was thinking the same thing.  People should read the whole post and comprehend it before they post.

---

### Post by fiddledd on 2008-04-28
Boot into Bios, change HDD back to IDE mode (what I assume it was when You installed XP)
Reboot back into XP
Download and install all motherboard drivers (especially the SATA drivers)
Reboot into BIOS, change back to ACHI
Reboot and you should be back into XP (without getting a BSOD)

After that you can reinstall Grub (which has been described in previuos replies)

---

### Post by neurostu on 2008-04-28
I'll try getting the XP sata drivers installed, thanks fiddledd.

I can't believe how HARD windows is to use.  After using linux exclusively now for almost a year I shutter to think that I used to use windows.  Its so clunky and disorganized.  

Thanks for all your help.  I'll check out the AHCI fix and post back if I have problems.

---

### Post by bigken on 2008-04-28
the way to install it is press f6 when prompted and install the sata drivers 1st using a floppy then continue to install windows

---

### Post by fiddledd on 2008-04-28
> **bigken said:**
> the way to install it is press f6 when prompted and install the sata drivers 1st using a floppy then continue to install windows

I agree, but he said he was installing on a Laptop, and I assumed he had no Floppy. Appollogies if I assumed wrong :)

---

### Post by bigken on 2008-04-28
> **fiddledd said:**
> I agree, but he said he was installing on a Laptop, and I assumed he had no Floppy. Appollogies if I assumed wrong :)

yep thats why its always handy to have usb floppy but in honesty windows xp if its sp2 should not need drivers for sata hdd its pain when this sort of thing happens

---

### Post by forrestcupp on 2008-04-28
> **bigken said:**
> the way to install it is press f6 when prompted and install the sata drivers 1st using a floppy then continue to install windows

You mean people still have floppies?

---

### Post by bigken on 2008-04-28
> **forrestcupp said:**
> You mean people still have floppies?


yep when you need to install drivers before a windows install its the only way :lolflag:

---

