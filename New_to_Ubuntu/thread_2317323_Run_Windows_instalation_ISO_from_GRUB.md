---
title: "Run Windows instalation ISO from GRUB"
date: 2016-03-15
forum: New to Ubuntu
---

### Post by notone2 on 2016-03-15
Hi guys,

is it possible to run windows iso file (packed or unpacked and located on root, not new partition) from GRUB 2 menu?

Thanks:KS

---

### Post by oldfred on 2016-03-15
Windows ISO is not designed to be loop mounted by grub. 
You may be able to extract it and use that.

 Windows 7, 8, 10 BIOS or UEFI boot installer from Ubuntu
[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by notone2 on 2016-03-15
hello,

is it possible to extract it on "/" or "/home" partition and then run it from GRUB? (i don't hold big enough USB and i can't make any new partitions on HDD)

i'm burning the DVD right now as last resort, but it would be really neat if i could run windows installation from grub in case of an emergency, thank you

---

### Post by Geoffrey_Arndt on 2016-03-15
Windows does not recognize any Linux filesystem (as far as I know).   So, another physical drive or partition is mandatory.   BUT . . . there is a possible solution - using a VM (virtual machine) technology such as VMware Player or Virtual Box.   Read up about those (plus see youtube videos).   VM's require sufficient RAM and other resources on the PC.   Is there a specific program (or programs) that you need to run in WIndows?

---

### Post by oldfred on 2016-03-15
If you do not have space to create the installer, how are you going to install Windows, it needs lots of space.

---

### Post by yancek on 2016-03-15
> s it possible to extract it on "/" or "/home" partition and then run it from GRUB?

Yes to the first part, no to the second.

You can boot a windows installation media from Grub but as pointed out above, it must be extracted and copied to a location which must an ntfs filesystem and that partition must be labelled as boot or active partition.  This is explained in the link posted above by oldfred.  Given your circumstances, it doesn't look like you will be able to do this.

---

### Post by notone2 on 2016-03-18
Thank you all

@Geoffrey_Arndt, yes, i was using photoshop with wine, but then i needed illustrator and indesign so it was less trouble this way

@oldfred, i had enough space, but already three primary partitions for /,home and swap, and windows was on fourth

---

### Post by yetimon_64 on 2016-03-18
> **notone2 said:**
> ...@oldfred, i had enough space, but already three primary partitions for /,home and swap, and windows was on fourth
Windows must be on a primary partition on a BIOS set up machine, but the other 3 linux partitions can all be placed into the one extended partition (a special primary partition) containing 3 logical partitions for /, /home and swap. Doing so can free up 2 primary partitions with only windows and the extended partition (containing the 3 linux parttions) taking up the other 2 available spots. 

Linux installs can successfully boot from an extended partition set up unlike windows which cannot do so.

---

### Post by notone2 on 2016-03-18
yes but i have linux installed for some time now and didn't planned to install windows, but i need it now for a new job and it was too much trouble backing up data and formatting and installing everything again

---

