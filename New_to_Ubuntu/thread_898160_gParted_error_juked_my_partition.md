---
title: "gParted error juked my partition"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by trikster_x on 2008-08-22
I was trying to increase the size of my ubuntu partition on my desktop computer with the live cd and gParted ran into an error while creating the final partition.  Now I have more memory on the new partition, but the same amount of free space.  I finally have ubuntu the way that I want it, so I would like to be able to fix this without having to do a complete wipe and reinstall.  I have another thread with gParted screenshots here:  [http://ubuntuforums.org/showthread.php?t=857714](http://ubuntuforums.org/showthread.php?t=857714) .  I also ran into this problem when installing ubuntu on my new laptop, except it is on the vista partition.  Not that I care for vista, but I would like to be able to access all my hard drive.  On the laptop, this problem eats up about 50 GB.  I am hoping that people will be a little more helpful this time and offer solutions instead of asking for info and never replying again.  Thanks in advance to anyone who can be helpful.

---

### Post by prshah on 2008-08-23
> **trikster_x said:**
> Now I have more memory on the new partition, but the same amount of free space.

From the point that you have said about gparted erroring out before finishing up, I think that either the resize has not been successfully completed, and/or an fsck (file system check) is required.

Both the below command require you to use the live CD to boot, and also you have to ensure that the partition (/dev/sda2) which houses your ubuntu system is UNmounted ```
sudo umount /dev/sda2
sudo resize2fs -p /dev/sda2
sudo fsck -a /dev/sda2

```

If fsck doesn't find anything amiss and you get an error to the effect "nothing to do" with the resize2fs command, then try the resize2fs command again as follows (with force):```
sudo resize2fs -p -f /dev/sda2
```

As always with partition/resizing/disk recovery operations, you must backup or risk your data. The above commands are safe, but inherently dangerous, so you use them at your own risk.

An additional point of advice; your gparted screenshot shows an extended partition sandwiched between two primary partitions. I suggest you to delete the entire extended partition and create a single swap partition in that.

Note that with a new swap partition, swap/hibernate/unhibernate may not work until you tell ubuntu to use the new swap partition rather than the old (non-existent) one.

---

### Post by trikster_x on 2008-08-23
Okay, I'll try that as soon as I can.  Unfortunately, shortly after I started this thread, my desktop died.  Until I fix that I'm at an impass.  Will this fix work with the vista partition on my laptop?  If not, do you have any suggestions for that?  Thank you for the info.

---

### Post by prshah on 2008-08-23
> **trikster_x said:**
> Unfortunately, shortly after I started this thread, my desktop died.  

Tragic. None of what I said is applicable then.

---

### Post by bruno.braga on 2008-09-08
Hi prshah, 

I ran into the same problem, when I tried to delete the Windows partition from my laptop. After running into some problems with the **gparted** to try to delete the Windows and resize the current extended partition (this problem was due to the swap partition which needed to be swapped off before being able to resize the extended partition). Then, the last command of the gparted failed, and the outcome of this was the fact that my 50GB partition, where previously I had Windows installed, was now inside my extended partition, but as a "ghost" space, being considered as **used**.

After reading your post, I could fix it. 

Just one note to you, before running the *resize2fs* command, Ubuntu asked me to run the *e2fsck* command, as follows:

```
sudo e2fsck -f /dev/sda2
```

Cheers!

For reference, I posted it in my [webpage]("http://www.brunobraga.net/miscellaneous/linux-geek/the-drama-of-removing-windows-from-my-laptop").

---

### Post by spectrum on 2009-02-21
> **bruno.braga said:**
> Hi prshah, 

I ran into the same problem, when I tried to delete the Windows partition from my laptop. After running into some problems with the **gparted** to try to delete the Windows and resize the current extended partition (this problem was due to the swap partition which needed to be swapped off before being able to resize the extended partition). Then, the last command of the gparted failed, and the outcome of this was the fact that my 50GB partition, where previously I had Windows installed, was now inside my extended partition, but as a "ghost" space, being considered as **used**.

After reading your post, I could fix it. 

Just one note to you, before running the *resize2fs* command, Ubuntu asked me to run the *e2fsck* command, as follows:

```
sudo e2fsck -f /dev/sda2
```

Cheers!

For reference, I posted it in my [webpage]("http://www.brunobraga.net/miscellaneous/linux-geek/the-drama-of-removing-windows-from-my-laptop").


Got the same problem of your note, i workaround it forcing the resize2fs with

```
sudo resize2fs -f /dev/sda2  
```

The launchpad report is [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/225360](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/225360), but it seems to be solved since gparted 0.3.7


Now, i got a question, it would be wise to ship Hardy with gparted 0.3.7 instead of 0.3.5? I mean, what about the next time i need to rescue and/or resize partition in my installation? Need a separate gparted liveCD?

---

### Post by mkvnmtr on 2009-02-21
The live Gparted just takes a few minutes to download and burn. I believe it will have the latest version on it.

---

