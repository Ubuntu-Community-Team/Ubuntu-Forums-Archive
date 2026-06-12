---
title: "Replacement for ext3 file system"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by yeehi on 2012-05-25
By default Ubuntu uses ext3 as the file system.
There is a more modern file system out that Ubuntu can use, but I forget what its name is. What is it called?
Why isn't Ubuntu using this more modern file system? I remember reading that it was planned to change it.

Have you tried using the new file system? How did it go?

---

### Post by roelforg on 2012-05-25
How about ext4?

---

### Post by zombifier25 on 2012-05-25
Ubuntu is already using this new file system: ext4

---

### Post by yeehi on 2012-05-25
Thanks roelforg.

It wasn't called ext4. It was a new name entirely.

---

### Post by Carborundum on 2012-05-25
Ubuntu uses ext4 as the default file system. The more modern file system you are thinking of is probably btrfs, which isn't yet stable, and [generally performs worse than ext4]("http://www.phoronix.com/scan.php?page=article&item=linux_33_btrfs&num=1").

---

### Post by roelforg on 2012-05-25
> **Carborundum said:**
> Ubuntu uses ext4 as the default file system. The more modern file system you are thinking of is probably btrfs, which isn't yet stable, and [generally performs worse than ext4]("http://www.phoronix.com/scan.php?page=article&item=linux_33_btrfs&num=1").
 
If you want performance, choose xfs.

---

### Post by yeehi on 2012-05-25
Thank you!
btrfs was the one I had in mind.
Can we use btrfs as one of the formatting options when we set up our partitions?

---

### Post by kurt18947 on 2012-05-25
> **yeehi said:**
> Thank you!
btrfs was the one I had in mind.
Can we use btrfs as one of the formatting options when we set up our partitions?

I believe it's offered but

> Carborundum 	 		Re: Replacement for ext3 file system
 		Ubuntu uses ext4 as the default file system. The more modern file  system you are thinking of is probably btrfs, which isn't yet stable,  and [generally performs worse than ext4]("http://www.phoronix.com/scan.php?page=article&item=linux_33_btrfs&num=1"). 

I'm also not sure about the availability of repair and maintenance tools for btrfs equivalent to fsck etc. for ext file systems.

---

### Post by 3rdalbum on 2012-05-25
You can use btfs if you wish, it's an option in the "Something Else" part of the Ubuntu installer. I actually used to use it and never had any trouble (I didn't run benchmarks or anything).

The only problem I had was with using the 12.04 installer to do an "Upgrade" install. The installer doesn't seem to have the smarts to navigate the slightly-different path of a btfs filesystem.

I wouldn't recommend btfs yet; it would be irresponsible of me to recommend a filesystem that hasn't been tested to the ground yet. But I didn't have any data loss or noticable performance issues, if that's any help.

---

