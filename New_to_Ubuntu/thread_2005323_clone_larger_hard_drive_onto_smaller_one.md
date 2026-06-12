---
title: "clone larger hard drive onto smaller one?"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by Meph1st0 on 2012-06-17
details:
1 TB HDD with one partition using full drive.  Only 39 GB used of the partition.

120 GB SSD unformated, unpartitioned

I've used clonezilla to save a clone of the 1 TB HDD.  I'd like to restore the image to the 120 GB SSD.

Is this possible?  I was thinking that since only 39GB is used on the partition it should be able to be restored to my SSD.  I've attempted to shrink the partition down to be less than 120 GB but the utilities I've used have not been able to shrink it down that much for some reason.

Thoughts? Ideas?...instructions? ;)  Thanks for any consideration.

---

### Post by drs305 on 2012-06-17
If clonezilla can't do it you could use the command line fsarchiver to save a partition and restore it to a smaller one. fsarchiver only saves what's actually on the partition, not the entire partition. It doesn't actually clone so it can restore it to a smaller partition. 

I would guess some GUI backups can do this as well, but if you don't get better solutions fsarchiver can do it.

---

### Post by haqking on 2012-06-17
If the used data is in a single 1TB partition which spans the size of the source drive then no, use gparted to shrink that single partition into close to the used data size then take a clone of that partition.

Technically it is possible, however in a single partition not all data is stored in a contiguous fashion.

In my experience when using clonezilla in this fashion i have got around it through resizing source partition as stated. If the expert option wont allow you too.

Also there is difference between choosing to clone a disk rather than a partition.

Peace

---

### Post by David Andersson on 2012-06-18
> **Meph1st0 said:**
> 
I've used clonezilla to save a clone of the 1 TB HDD.  I'd like to restore the image to the 120 GB SSD.


Maybe I am too ignorant, but I would just copy the files with *sudo cp -a /mount/old/. /mount/new* or maybe *sudo rsync -a /mount/old/ /mount/new*. The only benefit I can see with cloning is that the partition boot record and the uuid will be copied too.

---

