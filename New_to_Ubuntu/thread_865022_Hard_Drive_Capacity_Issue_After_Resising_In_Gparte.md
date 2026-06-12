---
title: "Hard Drive Capacity Issue After Resising In Gparted"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-07-20
I just did a clean install (I wanted my /home partition on a separate partition...plus it had been a while anyway) everything went fine.  However, I didn't realize until afterwords just how petite the / partition was without /home. In other words the / partition had more room than was necessary.  So, I wanted to give some spare space to /home where it was more needed.  I booted from my livecd and shrank the / partition.  Gparted Wouldn't let me "grow" or "move" the /home partition left whatsoever (formatted ext3). By left I mean that the /home partition was the last partition on the disk. I could grow it to the right (toward the end of the disk) but not to the left (toward the beginning of the disk). So, my workaround was to
1:save partition data w/ partimage.
2:delete /home partition.
3:create new (Larger) partition consisting of the space from the deleted /home partition and the space allocated from resising the / partition.
4:Restore partimage image to the new, larger /home drive

Everything worked as planned...er...almost.  Now both nautilus and gparted say that the /home partition contains the same amount of free space which was there before I added to it (They recognise it as larger, but still only containing the amount of free space which existed prior to the operation), but disk usage analyser reports the correct value. It's as if gparted and nautilus 'think' I just added 20 GB of USED Space, adding more GB to the total, but not to the free space.  I have a somewhat nebulous idea of what may be the problem, but would have no idea how to fix it.

I would guess (correct me if I'm wrong) that partimage restored both the data and MBR in such a way as to put the unused data in such a place where it couldn't be 'found' since it assumed I restored the image to a partition which was the same size as the one from which the image was made.

In my previous life (When I used...<cough> windows /<cough>) I used to create images from disks of size 'a' using Acronis True Image and restore them to disks of size 'b' with no problem. I don't know for sure that partimage is capable of this.
Any help on how to tell Ubuntu that I have 20 Extra Gigs on my /home partition would be appreciated.

---

### Post by unutbu on 2008-07-21
This is my guess as to what's happened:

Think of a partition like a room.
Think of a filesystem like a filing cabinet. 
Partimage saved the filesystem (filing cabinet).
GParted created a bigger partition (room)
Partimage restored the original filesystem (same old small filing cabinet).

So now you have a small filing cabinet in a big room.
The fix I think is to run (changing sda1 (below) to the name of your problem partition):

```

sudo umount /dev/sda1
sudo resize2fs /dev/sda1
```

---

