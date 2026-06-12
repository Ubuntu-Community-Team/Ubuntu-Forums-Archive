---
title: "Partition &amp; transfer media from windows XP"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by LeeHamo on 2008-10-04
Hi,

Ive used ubuntu now for over a week and I've decide I want to keep it and do away with XP altogether but, I have a lot of photos of my son on XP so I cant just delete it.

Is there a way to transfer all my stuff to my home space on ubuntu?

But before I do that I want to partition this drive so home is seperate from ubuntu...

So basically I have 2 hard drives in pc both 250gb sata, drive 1 is XP and all my photos, personal stuff I want to keep, and on drive 2 is this ubuntu which is pretty much a fresh install still apart from a few progs I can reinstall if need be.

I will want to keep XP on the other drive just for now I think as a backup incase ubuntu breaks, touch wood, but I want it to have nothing on it of any value to me.

Any help would be very appreciated, feel free to reply in terms a total linux noob would understand.

Cheers,

Lee.

---

### Post by LeeHamo on 2008-10-04
Is it because I mentioned XP that nobody wants to help?

---

### Post by Gannon8 on 2008-10-04
In the places menu, there should be an entry that has the number of gigabytes your windows partition it, with "Media" at the end. Click it, and you should get your windows "C:" Directory.

---

### Post by ZhuaSD on 2008-10-04
You can easily see all your photos and stuff in the windows disc while you are in Ubuntu, and just as easy to copy then and move them over.  But from Windows you cannot see the Linux installation.

I am in a similar position, with two physical discs and ubuntu and xp installed with a dual boot.  But I have both installs on one physical disk, not two like you do.  And my installs are all in 20-30 gig partitions.

I use a 30 g swap partition (NOT the 1 gig memory partion for Ubuntu called swap, but a real partition to swap files between the two installations) that is formatted in fat32.  Ntfs will not work so well with the Ubuntu, I understand (but not completely sure about how that works).

I am in the process of reformatting my whole second disk (70 gigs) into fat so that I can leave ALL my files on it, and access them from both OS, and I hope in this way to minimize the chance of data loss.  I also have a big partition that is Ntfs and I guess I am going to have to convert that to fat32 as well, as again its more accessible.

It sounds like you have lots of extra drive space.  You could create a partition on either or both of your disks and format into fat32.

---

### Post by kansasnoob on 2008-10-04
You can add really excellent ntfs read & write support by adding ntfsprogs which is in synaptic. So the answer is yes! You can copy files from ntfs and paste them into folders in your home partition.

Please read the wiki and man pages:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

As with most things really great, it's also very powerful so it can be used to destroy stuff too! And as I said it's in the repos so to install just go to synaptic or:

```
sudo apt-get install ntfsprogs
```

Another option is ntfs-config (also in synaptic). I believe it may be a bit simpler to use, I just use ntfsprogs by personal choice.

**Final warning:** Always make backups before undergoing a data transfer! Bad things can happen! It's well worth the price of DVDs or CDs to have a backup before trying a procedure that's new to you!

---

### Post by gfk on 2008-10-04
What I would do is maybe leave the Windows XP alone, you never know you may need it, and just mount the partition with read and write if it isn't already.

Or skrink the Windows partiton with Gpart and create a new partition to transfer the personal data like pictures, text files and even games in, seperate from any OS.  Keep Windows around 8GB-10GB.


gfk

---

