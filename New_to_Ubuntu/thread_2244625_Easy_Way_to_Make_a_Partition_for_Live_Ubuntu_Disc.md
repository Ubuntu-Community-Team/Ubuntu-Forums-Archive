---
title: "Easy Way to Make a Partition for Live Ubuntu Disc?"
date: 2014-09-17
forum: New to Ubuntu
---

### Post by Daveski17 on 2014-09-17
I've been running the live version a bit after cold booting it on my x86 laptop running Vista. I looked at the installation wizard for dual-booting but I don't know much about computers to be honest. It seemed to give me the option to replace Vista/Windows with Ubuntu, which is a bloody good idea, but I'd rather dual boot for a while. Is there an easy way to make a partition without using the unreliable and now unsupported Wubi?

Thanks.

---

### Post by deadflowr on 2014-09-17
Best practice when it comes to resizing an existing Windows partition is to use Windows own disk management utilities.
I think the recommended way is to first defragment the partition/drive first (some would argue to defrag the partition two or three times, I don't know, maybe...), then use the disk management feature to resize the drive.


Aside from that, it also helps to know what the disk layout is.
the command
```
sudo parted -l
```
can help in that.

---

### Post by ajgreeny on 2014-09-17
Depending on the specs of your Vista machine, some of which were not very fast to start with (and Vista made them run even slower!) it is possible that you may find Xubuntu runs a lot faster and better than Ubuntu with its unity desktop, which is quite resource hungry.

---

### Post by rolkin on 2014-09-17
I'd highly recommend doing a defrag of the entire drive (maybe twice) first. If you are comfortable doing some partitioning, I'd say to use gparted on a live cd (create it just like you did the ubutnu live cd). You can then follow the installation via ubuntu, and install it on the newly created partition.

Also...backup what you don't want to lose. I'm assuming this is your first time, so please be sure to make backups of anything on your windows side in case you make mistakes.

---

### Post by redrumrogue on 2014-09-17
> Best practice when it comes to resizing an existing Windows partition is to use Windows own disk management utilities.
I think the recommended way is to first defragment the partition/drive  first (some would argue to defrag the partition two or three times, I  don't know, maybe...), then use the disk management feature to resize  the drive.

Just to add to this - I did this a while back when I moved my windows 7 install from a 1TB HDD to a 128GB SSD.  In the windows disk management utility you won't be able to shrink the partition if there are blocks of data near the end / extermity of the partition on the drive.  The shrink function doesn't move data for you.  This is why you have to defrag, to basically move and repack the data at the beginning of the partition so it can be shrunk.  I had issues defragging though because there were some unmovable blocks containing data for the page file, hibernation file and system restore.  I had to disable these three windows features to remove these files and then defrag was able to move all the partition block to fit within the first 128GB.  Only then was I able to shrink the partition down, image the drive and write it onto the SSD.  This was just my experience .... not sure if there's an easier way!  It worked though eventually.

---

### Post by grahammechanical on 2014-09-17
The installer gives us 5 options that include Install along side, Use the entire disk (this will wipe everything on the hard disk) and Something else. Does the installer give you the Install Alongside option? At this point we can still back out of installing. It is important to know if we get the Install alongside option.

I would not agree that Ubuntu + Unity is resource hungry. A lots depends on the power of the graphic adapter and the amount of memory the graphic adapter has. Ubuntu requires that a graphic adapter is able to do 3D hardware acceleration.

Load to a live session. Open the terminal and run this command

```
/usr/lib/nux/unity_support_test -p
```

The result will tell you if your graphic adapter can cope with Unity 3D. Another thing to keep in mind is that the makers of graphic adapters are in the habit of dropping support for older adapters. So, when installing do not tick the box "install third party software" as that will bring in proprietary video driver that may not support your graphic card. We can always install the proprietary driver and the third party software after we get a working OS.

Regards.

---

### Post by Daveski17 on 2014-09-18
OK thank you very much for all of your replies. I'll experiment with the live disc some more and familiarise myself more with OS first. Ubuntu looks really good and I may just waste Vista. My files are backed up anyway and I have another computer. Support ends pretty soon for Vista anyway I think.

Dave

---

