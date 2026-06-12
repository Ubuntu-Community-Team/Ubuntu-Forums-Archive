---
title: "Repartitioning HDD"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Zero7 on 2008-11-10
I have 4 primary partitions (NTFS, /, Home, & swap). I would like to repartition the hard drive and try out some other flavor of Linux (Thinking of Puppy). Is there a way to convert some partition to secondary and create one more partition? I do not want to reinstall Ubuntu but I am ready to take the back up as an image or whatever it is called. Thanks in advance!

---

### Post by bumanie on 2008-11-10
I can tell you how to make an image if you like, but puppy, from a live cd will load into ram. You can then take the live cd out and use the cd drive if needed - takes a bit longer to boot off the livecd, but once loaded, it's very quick due to it operating out of ram. I suggest you try the puppy live cd first.

---

### Post by Bartender on 2008-11-10
Zero, this might seem painful, but I'd suggest starting over and doing it right.
 
Use a GParted LiveCD to delete the Linux partitions.  Unformat the entire area so that it's unallocated.  Then create one extended partition out of the entire space.  Then either create a logical partition inside the extended and format it as ext3, then let Ubuntu auto-install to that space, 

or 

create logical partitions inside the extended partition for /, swap, /home, and manually install.  If you partition for manual install format all of them as ext3.  The Ubuntu installer will reformat the swap to "linuxswap" regardless of how you format it beforehand.

You can make several logical partitions inside the extended partition.  You won't run into the "4 partitions and you're done" problem.

If you know or are willing to learn how to manually mount the partitions, one swap partition can be shared by more than one Linux OS.

If you're pretty sure you're going to install another linux OS, you could leave some of the space inside the extended partition unallocated.  Install Ubuntu to whatever space you want, and leave the rest unallocated.

---

### Post by Arlo012 on 2008-11-10
- Zero

I would have to agree with bartender on this one. Reformatting everything and doing it the right way really is the best way to go if you want to install. At the very least make sure you back up all your important documents if you try to resize the partitions. You only have to do that once and lose everything before you never, EVER, want it to happen again.

My two cents,
Arlo012

---

### Post by zvacet on 2008-11-10
Shrink one of your partitions(Ubuntu?) and on that unallocated space make extended partition and inside of it install Puppy.

---

### Post by kansasnoob on 2008-11-10
I'd like to see a screenshot of that! You can install Gparted by going to terminal and:

```
sudo apt-get install gparted
```

It'll then show up in System > Administration > Partition Editor. Although you should almost never use it to change partitions (that's where a Live CD is needed) it's useful to see what's going on.

Anyway if you do indeed have 4 Primary partitions and one of them is Swap, you can resize partitions, delete the swap, create an extended partition, then recreate swap inside the extended partition and create many, many more partitions within that extended partition!

Of course recreating swap will require that you fix some uuid stuff. Look at all of Coffeecat's posts here:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

---

### Post by Zero7 on 2008-11-10
Thanks Bartender and bumanie for replies. I have tried Puppy ind it was pretty fast. I would like to install it and see how it performs. If I have to reinstall Ubuntu my wife will kill me as all her settings will be lost (as I have to format home partition) and will have to install all programs again. That's my worry :(

---

### Post by Zero7 on 2008-11-10
> **kansasnoob said:**
> I'd like to see a screenshot of that! You can install Gparted by going to terminal and:

```
sudo apt-get install gparted
```

It'll then show up in System > Administration > Partition Editor. Although you should almost never use it to change partitions (that's where a Live CD is needed) it's useful to see what's going on.

Anyway if you do indeed have 4 Primary partitions and one of them is Swap, you can resize partitions, delete the swap, create an extended partition, then recreate swap inside the extended partition and create many, many more partitions within that extended partition!

Of course recreating swap will require that you fix some uuid stuff. Look at all of Coffeecat's posts here:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

Thanks Kansasnoob. Let me try this.

---

### Post by ichi@YUKI on 2008-11-10
I already tried resizing and adding new partitions with GParted and my files in both Xp and Gutsy partitions remained intact. I believe that you can shrink and add partitions using GParted without touching the rest of your harddisk, but backing-up is still recommended. 

The Ubuntu live disc usually has GParted, or you can get it using aptitude. Please be warned however that you can edit the partitions except for the one where GParted is installed. Thus it is advisable to use a Live Disc for GParted

---

### Post by kansasnoob on 2008-11-10
> **ichi@YUKI said:**
> I already tried resizing and adding new partitions with GParted and my files in both Xp and Gutsy partitions remained intact. I believe that you can shrink and add partitions using GParted without touching the rest of your harddisk, but backing-up is still recommended. 

The Ubuntu live disc usually has GParted, or you can get it using aptitude. Please be warned however that you can edit the partitions except for the one where GParted is installed. Thus it is advisable to use a Live Disc for GParted

But, what he's up against is the 4 Primary limit!

---

### Post by handydan918 on 2008-11-10
> **Zero7 said:**
> Thanks Bartender and bumanie for replies. I have tried Puppy ind it was pretty fast. I would like to install it and see how it performs. If I have to reinstall Ubuntu my wife will kill me as all her settings will be lost (as I have to format home partition) and will have to install all programs again. That's my worry :(
1) You don't have to format /home if you put it on a serarate partition. So do that, this time.:)

2) Save your wifes settings by backing up /home. That will save your settings, too. 

3) Search the forums for ```
dpkg --set-selections
```
and I feel certain you'll come up with a nice way of reinstalling everything as it was, provided it all went thru the package manager.

---

### Post by Greyed on 2008-11-10
Actually, take a step back and ask what the intended purpose of trying a different distribution is.  If it is to get a feel of the installation process, how it works, how it updates, what it comes with, how easy it is to configure and do some moderate work with it **and** you care not for gaming performance or 3D performance then I suggest not repartitioning.  Get VirtualBox (OSE or PEUL), let it create an 8Gb sparse file for its "drive" and then install the test OS inside that environment.

Pros: No need to mess with partitioning and the dangers to your data associated with it.  Allows you to wipe it clean in a moments notice.  Does allow you to test almost all portions of the OS safely and completely.
Cons: May not be the best for long term use; definately not primary use.  Anything that requires 3D Hardware will not work.

Obviously if you're making a full-time switch then repartitioning would be advisable.  But until you know for sure, why mess with it?

---

