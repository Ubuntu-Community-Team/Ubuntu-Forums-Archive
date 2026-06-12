---
title: "Upgrade Question"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by pirate_steve on 2008-08-27
I recently installed Ubuntu Edgy on my computer alongside WindowsXP.  I would like to upgrade to Hardy but would rather not go through all the upgrades and just do a clean install. I am having some trouble doing this since I am so new to ubuntu and still have the partitioning with WindowsXP.  What would be the best way to go about doing this?

Any help appreciated, thanks.

---

### Post by zamadatix on 2008-08-27
if oyu want to just get rid of ubuntu and do a fresh instlal and keep xp delete the ubuntu partiton (from a gparted live cd) and then reinstall the new ubuntu and hte now blank partition.

---

### Post by Scunge on 2008-08-27
I did this, the only difference being that the clean install was over Dapper.

When you installed Edgy, do you remember selecting "manually edit the partition table", and putting "/" and "swap" (and probably "/home") on partitions which were not already taken up with Windows stuff?

Then when you commited the changes to disk, you saw that no Windows partitions were going to be reformatted or anything?

Then at the end, when it asked you what to do with the grub boot loader, it told you it found a Microsoft Windows XP operating system and that it was safe to install the boot loader in the master boot record, and you said "yes" to that?

And then it just worked, with a boot menu with Ubuntu, memtest and Windows in?

Well, just do the exact same thing again.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by Ryadt on 2008-08-27
Try this [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

---

### Post by pirate_steve on 2008-08-27
Thanks to everyone for their help, I got Hardy installed alongside XP just fine. :)

---

