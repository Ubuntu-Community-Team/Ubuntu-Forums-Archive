---
title: "I like my dual boot and want to increase the Linux Partition BUT!"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by mtelesha on 2008-08-06
I have shrunk the Windows partition and have given myself room to move my main Linux partition to the left but gparted won't let me move the partition to the left.

Pictures of my issue: My GPart screen shot
[http://www.flickr.com/photos/mtelesha/2737857890/sizes/o/]("http://www.flickr.com/photos/mtelesha/2737857890/sizes/o/")

My Screen shot with a little verbiage to clarify the situation.
[http://www.flickr.com/photos/mtelesha/2737037015/in/photostream/]("http://www.flickr.com/photos/mtelesha/2737037015/in/photostream/")

I thought it was due to the partitions being mounted and I burned the gparted live cd and sit have no ability to move the partition to the left all I can do is shrink from the left or the right.

-Marc

---

### Post by LaRoza on 2008-08-06
sda2 is very full. It cannot be shrunk.

Do you have lots of movies or music on it (usually the cause of full drives)

EDIT:

Never mind. I see you are moving another partition to the left. I am unfamiliar with moving partitions like that, especially ones with data. It may not be possible.

You can install Ubuntu over again and delete the old partition and redo it. 

I noticed you Windows partition (sda2) is almost full. Does it have a lot of media on it? I prefer to have small partitions for my OS's and use the rest of the drive for the data.

---

### Post by Thingymebob on 2008-08-06
Your pics show that dev/sda5 is still mounted at / 
you need to unmount this partition before you can move it. Also your swap is in the same logical partition this will need to be disabled by issuing swapoff then you can resize the logical first then the partitions inside.

I take it these pics are from gparted in ubuntu and not the livecd.

I think the gparted livecd will mount a swap if it finds one (I'm prepared to be corrected on that one)

---

### Post by kansasnoob on 2008-08-06
LaRoza is right about having hardly any room left, but to expand your Linux partition (sda5) to the left and use up that unpartitioned 1.98GB, you first need to expand the extended partition (sda3) to the left. A common "stopper" there is if the swap partition (sda6) is still in "swapon" mode.

You see as long as the "keyring" is visible just to the left of the colored partition "blocks" you can't do anything with any of the partitions in that extended partition. So if swap is "on" that partition is still "locked" so you'll need to right click the swap partition and click on "swapoff".

Then when you're all done remember to click on "swapon".

Hope that helps.

Edit: I almost forgot, but back to what LaRoza said, I really start to panic anytime I have a partition or drive reach about 80% full. The potential for data loss and OS malfunctions seems to increase drastically beyond 80% usage of a drive.

In fact I store no important data at all on my internal drive. Everything is stored on removable drives, placed in Tupperware, and then stuck in my fireproof safe! That might seem like overkill but I treasure my stuff.

---

