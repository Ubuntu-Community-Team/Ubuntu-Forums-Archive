---
title: "Gparted not resizing as wished"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by olhat on 2008-09-23
I have made a mirror image of my ubuntu OS hard drive (Seagate 40g and the mirror image Samsung 500g).  After an endless list of various Linux solutions giving me error messages or graphics problems etc I gave up and booted up on a Winxp hdd and tried Norton ghost that could not read ext3 drives but after that I tried some other Symanteccy that did the job on the first go.  The first time could really have been way easier and faster.

Now, I would like to resize my Seagate40 ubuntu hdd os partition because I don't need the ntfs on that drive.  I wish to make 

1) hda1 as small as possible, 

but my grub is obviously on that drive so I guess I cannot delete it entirely.  Secondly I would like to increase the size of 

2) hda6 swap to about 4-6 gig.

3)And the rest for hda5.

I'm running my mirror image right now and GParted cannot see the used part of my ext3 on original OS.  I need to do more setup, install programs etc and if I start using my mirror image I cannot do any more backuping on smaller hds because this one is 500g and most of my old hds are way smaller.  So I reckon that I need to keep on using the seagate40 as original and use other hds as backup-mirror image.
And I would like to have my OSs on dedicated hdds so that I can have my personal data on those bigger hdds clean from os and programs.


The problem now is GParted that is giving only one option to do things and that is delete.  I hope that this is not another root thingy, I typed “gksudo gparted” in terminal.  Must I go back to my Windows hdd and try to do everything on Norton?:confused:


BTW the screenshots are taken as windowshots but that function has decided to be a desktopshot instead.:lolflag:

---

### Post by Pro-reason on 2008-09-24
That's all a bit confusing.  Why do you need GRUB on that NTFS partition?  I don't understand that.

---

### Post by Tatty on 2008-09-24
Your grub will be on hda5 not hda1, hda1 is your windows partition.

6Gb is a massive amount for swap, are you sure you need that much?

To edit your partitions you need to boot with a liveCD, as you cannot alter the partitions of a mounted system.

I am afraid that I cant help much more unless you clarify what you are doing a little better, as your post seems a little muddled.

---

### Post by sneeks on 2008-09-24
> **Tatty said:**
> Your grub will be on hda5 not hda1, hda1 is your windows partition.

6Gb is a massive amount for swap, are you sure you need that much?

To edit your partitions you need to boot with a liveCD, as you cannot alter the partitions of a mounted system.

I am afraid that I cant help much more unless you clarify what you are doing a little better, as your post seems a little muddled.

are you sure the 6 gig partition is your swap???
run gparted from live cd and look a little further.

---

### Post by olhat on 2008-09-26
> **Pro-reason said:**
> That's all a bit confusing.  Why do you need GRUB on that NTFS partition?  I don't understand that.
I really don't need GRUB to be there but since the ntfs is the only place that shows as boot partition in GParted so I was in the belief that the GRUB had located itself there.  If it is not there and it's in hda2 then I naturally can wipe out the entire ntfs partition.

---

### Post by olhat on 2008-09-26
> **Tatty said:**
> Your grub will be on hda5 not hda1, hda1 is your windows partition.

6Gb is a massive amount for swap, are you sure you need that much?

To edit your partitions you need to boot with a liveCD, as you cannot alter the partitions of a mounted system.

I am afraid that I cant help much more unless you clarify what you are doing a little better, as your post seems a little muddled.


Since the hda5 was not flagged as boot so I thought that grub was in the partition marked as boot. My bad.

I'd like to use Hibernation and lots of apps open.  Even my raw bare-bones Ubuntu of last week could not hibernate on 1G so I just took a figure that should be enough.  Maybe something in between is more appropriate but since hdd real estate is even cheaper than Peoria so why skimp.

I booted from my mirror image, I did not boot from the partition I was going to resize, I've done this in Winxp a few times.  But is there a difference between booting from liveCD or another hdd?  I might try the liveCD I just could not think there being any difference?

I guess that my problem was that both the booting hdd (samsung500) and the original os (sg40) showed as booted (keypic) in GParted.  Must try to umount the resizee.

Must make a new mirror image on a third hdd just before I try to actually do this resizing:)

---

### Post by Pro-reason on 2008-09-26
> **olhat said:**
> I really don't need GRUB to be there but since the ntfs is the only place that shows as boot partition in GParted so I was in the belief that the GRUB had located itself there.  If it is not there and it's in hda2 then I naturally can wipe out the entire ntfs partition.

Unless you have specified otherwise, the GRUB bootloader is normally installed to the MBR (Master Boot Record) of an entire device, rather than the boot sector of a partition of that device.

In any case, reinstalling the bootloader takes an instant.

---

