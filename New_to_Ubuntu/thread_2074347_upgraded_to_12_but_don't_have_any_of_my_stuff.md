---
title: "upgraded to 12 but don't have any of my stuff"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by buzbyx on 2012-10-21
apologies for my ignorance, first and foremost

I upgraded recently to 12.04 and don't know how to migrate my data/fonts/apps from my old system to the new one.   It seems like a pretty massive task to reinstall everything piece by piece:confused:    is this the case?

---

### Post by kc1di on 2012-10-21
Hi buzbyx And welcome to the forums,

When you say you upgraded to you mean you literally upgraded from another Ubuntu version or that you actually did a fresh install?

if the former all of compatible data should have been updated and be there for you.  if you did a clean install from the CD then you may want to just go ahead and re-install the programs because you'll get updated versions if they are available. 

Good Luck,

---

### Post by offgridguy on 2012-10-21
> **kc1di said:**
> Hi buzbyx And welcome to the forums,

When you say you upgraded to you mean you literally upgraded from another Ubuntu version or that you actually did a fresh install?


Hello kc1di; so there is a difference between an up grade and a fresh install, okay so how do I go about an upgrade, say from 12.04 to 12.10. { I don't want to get 12.10}
I just want to know how to upgrade.  Thank you.

---

### Post by MG&amp;TL on 2012-10-21
> **offgridguy said:**
> Hello kc1di; so there is a difference between an up grade and a fresh install, okay so how do I go about an upgrade, say from 12.04 to 12.10. { I don't want to get 12.10}
I just want to know how to upgrade.  Thank you.

Difference is that a fresh install actually wipes all the data and installs a fresh *buntu on your disk/partition, whereas an upgrade just upgrades all the packages. 

There's advantages and disadvantages to both, BUT ALWAYS BACK UP YOUR STUFF. Stuff can and will go wrong, although almost never disastrously.

PS: Make a new thread next time, I've asked for this one to be moved.

---

### Post by buzbyx on 2012-10-21
back folks, and thanks for the replies.   I saw the upgrade in the updater and clicked it...no usb or cd install.   I have a graphic novel in process with a multitude of supporting applications and fonts, but it's all stuck back in 11.whatever on what seems to be a separate partition.   Is there any sudo apt-get kind of command that'll copy the stuff to my new system?

---

### Post by kc1di on 2012-10-21
> **buzbyx said:**
> back folks, and thanks for the replies.   I saw the upgrade in the updater and clicked it...no usb or cd install.   I have a graphic novel in process with a multitude of supporting applications and fonts, but it's all stuck back in 11.whatever on what seems to be a separate partition.   Is there any sudo apt-get kind of command that'll copy the stuff to my new system?

is the partition on the same H.D. ?
or a removable H.D. or other media?
full of question i know.

sounds like if it's on the same H.D. then all you would have to do to have access to it is mount that partition if it's not already mounted.

Then you could copy whatever data you wanted from it.

---

### Post by Old_Grey_Wolf on 2012-10-21
Let us see your partitions by opening a terminal using Ctrl-Alt-t keys combination; then, enter this command in the terminal ```
sudo fdisk -l
```

That is a small letter L not the number 1.

Copy and paste the output of the command in a reply here.

---

### Post by buzbyx on 2012-10-21
here's the result of the fdisk...and thanks for your time

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093519

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   284986075   142492014   83  Linux
/dev/sda2       284987390   488396799   101704705    5  Extended
/dev/sda5       472301568   488396799     8047616   82  Linux swap / Solaris
/dev/sda6       284987392   456202239    85607424   83  Linux
/dev/sda7       456204288   472295423     8045568   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Old_Grey_Wolf on 2012-10-21
You do have 2 Linux partitions. I'm not sure how that happened; however, it is a good thing.

You should be able to use the Nautilus file system browser to copy the files you need to your new OS partition.

---

### Post by buzbyx on 2012-10-21
thank you so much.  I will research this nautilus and, most likely, be back with the questions of a fool.

but if not, you have my profound thanks.

---

### Post by will1982 on 2012-10-21
> **buzbyx said:**
> thank you so much.  I will research this nautilus and, most likely, be back with the questions of a fool.

but if not, you have my profound thanks.

Nautilus is the file manager. It's right under the Ubuntu button (Dash Home) in the launcher

---

