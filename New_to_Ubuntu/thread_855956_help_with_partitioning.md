---
title: "help with partitioning"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Nickocosmicfatplanet on 2008-07-11
i'm running linux right now, and am currently in the process of installing it on my computer, which has windows xp pro x64 already on it. i'm at the partitioning section of installation, and i'm very confused. everywhere i look, it doesn't give a n00b's perspective of partitioning for ubuntu. the two screenshots are what i've got at the partitioning screen, one after i choose 'manual'. for whatever reasion, i don't have the ability to do the guided partitoning where i can slide the bar to allocate disk space. any help or recommendations will be greatly appreciated.

---

### Post by Dark_Stang on 2008-07-11
Which drive do you want Ubuntu on? If you've got 2 drives, I'd recommend putting windows on one and putting Ubuntu on the other. That would be the absolute easiest way to do it. Just make sure you move all your files over that you'd like.

If you want to just use part of one drive we can walk you through that as well.

---

### Post by Nickocosmicfatplanet on 2008-07-11
one of the drives is an external, connected through usb. it's in fat32 format, so won't that prevent linux from installing there due to the 4gb limit? and there's also a lot of data on there, like music and movies and some programs. will putting linux on there remove all of that?

---

### Post by shp on 2008-07-11
You have two drives that have partitions that are apparent used

You can shrink the /dev/sdb1 to about 100gb (or 100000mb) and then use that created space to install linux

Sorry didn't see your second post but you can still do the above and shouldn't lose any data. But you said it was a usb which your right u probably can't boot off

---

### Post by Dark_Stang on 2008-07-11
Screw it, we'll just do it on the internal then. Close out of the installer first, we want to use a slightly different (actually the same but nicer look) partitioner.

Go System > Administration > Partition Editor. Click on your windows partition on the internal drive and click resize. Shrink it as much or as little as you want, you'll want at least 5gb to run Ubuntu smoothly. I'd suggest 40+ gb if you're going to be keeping a lot of files on Ubuntu. Keep in mind, you will not have to copy all your files over to ubuntu because you can simply access them on the windows partition. After you get your sized picked out click apply.

Fire up the installer and go through it until you get to the partition section again, then select manual.

Now I've got two paths for you.
Path 1. You're playing with Ubuntu and have no real intention of using it a lot. In this case you've only shrank the partition 10 gb or less.

Select your free space, and click &#8220;New partition&#8221;. For type of partition select logical. For new partition size just do 1000. For location select beginning. Use as swap. And click okay. Now click the rest of your free space and create another new partition. Select primary for the type, all the space left for the size, beginning for the location, and use as ext3. Now click your partition you just created, click edit, and select &#8220;/&#8221; as your mount point.


Path 2: You plan to use Ubuntu quite a bit or are thinking about making it your primary operating system. In other words, you left yourself with more than 15 gb.

Go to the free space and click &#8220;New partition&#8221;. For the type select logical, for the size do 1000, for the location select beginning, and use as swap. Now click okay. Create another new partition, for the type select primary, for the size do 75000 to 10000 (this will be the operating system's partition), and use as ext3 (or if you have another preference use it). Now create another partition, for type use primary, use the rest of the available space for your size, and use as ext3. Now we need to go back and edit the partitions. For the first one make the mount point &#8220;/&#8221;, for the second one make the mount point &#8220;/home&#8221;. This keeps all your files on a separate partition so you can reformat the Ubuntu partition without fear if you completely screw something up, or want to do a fresh upgrade/install.
Now go ahead and click forward. Ubuntu is going to tell you there were no users or operating systems suitable for importing from. Go ahead and click forward again.

---

### Post by Nickocosmicfatplanet on 2008-07-11
the only options i get for it are 'unmount', 'manage flags' and 'information'. i read in the 'how to partion' document about unmounting the drive or something.

---

### Post by Dark_Stang on 2008-07-11
You've gotta unmount the drive in order to partition it. Just right click and unmount it. Then resize it.

---

### Post by Nickocosmicfatplanet on 2008-07-11
i'm all up and running. cheers!

---

### Post by Dark_Stang on 2008-07-11
Have fun.

---

