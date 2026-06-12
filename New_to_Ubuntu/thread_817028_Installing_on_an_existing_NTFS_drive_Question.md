---
title: "Installing on an existing NTFS drive Question?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-03
Hi,

I have a 500Gb drive in NTFS (only MP3's no OS) with half full...I wanna install Microshaft Vista and Ubuntu...

Now in Gparted do i shrink to partition at the end or the Beginning?

Which way?

Thanks..

---

### Post by Sef on 2008-06-03
**Back up** your music.   

Vista needs to be on the first partition.

---

### Post by hopelessone on 2008-06-03
Hi,
Thanks...

Where's a Guide to shrink NTFS ?

Cheers.

---

### Post by hopelessone on 2008-06-04
OK After shrinking the filesytem...

can I use Gparted and move the left hand side and slide it up?

Thanks..

---

### Post by Sef on 2008-06-04
> can I use Gparted and move the left hand side and slide it up?

After shrinking the partition with Vista, you can use GParted to make the Ubuntu partitions. (Root, Shared, Home, and Swap. Only Root and Home are necessary.  The others are good to have.)

---

### Post by hopelessone on 2008-06-04
i haven't installed Vista yet gonna move the whole NTFS to the right to make way for it and Linux..

Wish me luck Moving to the right...!!

---

### Post by hyper_ch on 2008-06-04
I'd recommend to use the VISTA partitioner for shrinking the drive.

Once you shrinked (shrunk?) the drive you can leave the part for Ubuntu "unpartitioned". During the ubuntu install you can then use the "use largest continuous free space" option.

And btw: MAKE BACKUPS FIRST!

---

