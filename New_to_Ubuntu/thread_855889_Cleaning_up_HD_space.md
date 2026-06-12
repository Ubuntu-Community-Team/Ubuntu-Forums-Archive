---
title: "Cleaning up HD space"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by echo314 on 2008-07-10
I've had the same /home partition for some time now. 68.1gb capacity, with 29.1gb free. The thing is, I can't approach having a few gigs free anymore without the system freezing up and not starting any new apps, at which time I delete some stuff and hope for the best upon reboot. 

It seems to happen most often when I am downloading files via torrent. Again, I don't come near filling the folder, and the download speed is quite small, but I get the feeling the files are badly fragmented and thats causing my disk space to seem artificially small. 

I have tried running fsck at startup, but this does not seem to help much in the long run. Is there a more comprehensive disk operation I can use to clean up my home dir, or other suggestions?

btw, I have 2.2gb free in my / partition, so I don't think thats related.

---

### Post by ChameleonDave on 2008-07-11
Clean up?

Well, there's checking a filesystem for errors, and there's deleting unwanted files when space is low.  Those are two different things.

Use *fsck* for error checking.

To examine your drives to see what is taking up so much space, try using *filelight*.

You should indeed strive to keep plenty of free space, in order to avoid fragmentation.

P.S. Another thing you can do to save space is to delete user configuration files for software you don't use.  This is usually negligible, but for apps such as Google Earth or VirtualBox they can be large.

---

### Post by echo314 on 2008-07-11
I used filelight and freed up a few more gigs. What is the approx. threshold that I should keep for free space? 

Since my home partition is potentially badly fragmented, do I need to stay above 'a few' gigs'? Would re-partitioning likely help?

I only ask because I don't think I come anywhere near filling up the folder when this occurs, at *least* 8 gigs left, most likely around 15-20. (this is counting hidden folders. (Right clicking-properties does take that into account, right?)

---

### Post by ChameleonDave on 2008-07-11
Drives should be at least 10% empty, perhaps more.

Provided they have enough space, they will defragment themselves with time.  Moving files to and from partitions increases fragmentation if there is little space, and decreases fragmentation if there is a lot of space.

You're using an Ext3 filesystem, right?  See [http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

