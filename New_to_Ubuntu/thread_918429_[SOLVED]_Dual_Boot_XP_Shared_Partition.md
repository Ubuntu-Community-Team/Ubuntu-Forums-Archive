---
title: "[SOLVED] Dual Boot XP Shared Partition"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by dsurge on 2008-09-12
Sorry for making my 2nd post today, when I figure this stuff out I promise to come back and help people...

So I'm working on dualbooting linux and XP. What I want to do is have a shared partition that both can access and that I can save to (school documents, music, movies, etc...)

I found this guide: 

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=2)

but it seems to be outdated in terms of the linux system. I don't want to use outdated software, so does anyone know how would I make a shared partition for XP and 8.04? 

Again, thank you very much in advance, glad to be part of the community.

-Surge

---

### Post by pi.boy.travis on 2008-09-12
Just create a partition using the GParted partition editing tool. (it's in the repositories, just use synaptic in System-Administration-Synaptic package manager)

FAT32 will suffice as a filesystem.  It is well supported in Ubuntu.

Hope this helps!

---

### Post by Zzl1xndd on 2008-09-12
I would also recommend using Fat32, unless you need it to be able to store files larger then 4 gigs. If you need to be able to store larger then 4 gig files you will need to use EXT3 or NTFS. from my experience its easier to get Linux to Write to NTFS (it can read by default) then it is to get Windows to Read/Write to EXT3.  

If you want to use NTFS just type NTFS into you add remove programs and the only option that will show up will be the one that will allow you to enable writing to NTFS.

---

### Post by akiratheoni on 2008-09-12
Ubuntu can read and write to NTFS, so you could just store the files you want on both Ubuntu and XP on XP's partition because Ubuntu can access it as well as of course Windows.

---

### Post by dsurge on 2008-09-13
> **tweakedenigma said:**
> I would also recommend using Fat32, unless you need it to be able to store files larger then 4 gigs. If you need to be able to store larger then 4 gig files you will need to use EXT3 or NTFS. from my experience its easier to get Linux to Write to NTFS (it can read by default) then it is to get Windows to Read/Write to EXT3.  

If you want to use NTFS just type NTFS into you add remove programs and the only option that will show up will be the one that will allow you to enable writing to NTFS.

Hmm... I'd rather NTFS, but when I type that into add remove programs, nothing comes up.

-Surge

Edit- Sorry, also GParted won't let me make a new partition or resize the ext3 one. Any idea why?

---

### Post by Zzl1xndd on 2008-09-13
Make sure Add/remove is set to All available applications, and The drive can't be mounted when you resize it. If you only have 1 drive perhaps you should try the Gparted live CD.

---

### Post by dsurge on 2008-09-13
I get this error when I try to unmount.

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

But I accidentally unmounted my Windows XP NTFS partition and now it has an ! beside it instead of a set of keys. It won't let me remount it.

---

### Post by dsurge on 2008-09-13
So I think I remounted my XP partition but I'm stil not sure how to unmount and split my ubuntu partition. Thanks everyone for bearing with me.

-Surge

---

### Post by Zzl1xndd on 2008-09-13
Are your Ubuntu and XP partitions on the same drive?

If so Grab the Gparted Live CD and use it to remake your partitions, The whole Drive shouldn't be mounted if you are going to resize it.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by pi.boy.travis on 2008-09-13
I would recommend against keeping any personal files on the same partition as Windows.  It would be better to make a third partition used between the two.

---

### Post by dsurge on 2008-09-13
> **pi.boy.travis said:**
> I would recommend against keeping any personal files on the same partition as Windows.  It would be better to make a third partition used between the two.

Thats exactly what I'm trying to do, but right now I have two partitions. A windows one that is 60 gigs and an ubuntu one that is also 60 gigs. I'm never going to need 60 gigs on ubuntu, so I want to take 40 of those and make it the split partition, but I keep failing :( Rough start eh? Good thing I'm persistent.

And btw, you guys rock! Best forum ever!

---

### Post by pi.boy.travis on 2008-09-13
You have to use a live CD, like the Ubuntu CD, and use GParted with that.  You can't change partitions that are mounted, and you can't unmount a partition that has a running OS on it.  My Ubuntu reads and writes to NTFS by default.

---

### Post by dsurge on 2008-09-13
Thanks everyone, finally got it!

---

### Post by pi.boy.travis on 2008-09-13
Excellent!

Please mark your thread as solved.  It helps with the sorting and such. . .

---

