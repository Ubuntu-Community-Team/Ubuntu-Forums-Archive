---
title: "Need some help partitioning for a dual book"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by purplegromit on 2008-05-03
Hi chaps, I've been utterly failing to install ubuntu for the last hour.

I'd like to dual boot (xp and ubuntu 8.04)on a 120gb hard drive with a large partition for data used by both (movies mp3s etc)

Now after reading a few guides I know what partitions I need but not how to set them up. I dont know about the "mount" and am unsure about the file system for ubuntus space.

This is the plan:  
10GB XP NTSF
10GB Ubuntu OS
2GB Swap space  
The rest for data (Fat 32?)

Can someone PLEASE tell me what mount for the big partition (to be used by XP and Ubuntu) and what file system and mount for the ubuntu partition.
Ive been looking through a few "guides", but they seem to have a blind spot for this information.


The secret to life the universe and everything for the first useful reply..

Cheers

---

### Post by aheckler on 2008-05-03
Ubuntu will use the ext3 filesystem, and the shared data section will probably use NTFS. Ubuntu can read/write NTFS very well.

EDIT: As far as what to keep in "the big partition", that would be stuff like music, movies, pictures, etc. that Windows and Ubuntu can both access without interfering with the other OS.

---

### Post by purplegromit on 2008-05-03
Thanks for the quick reply,

so what do I need to mount things as?

is "/" for the ubuntu os partition?

p.s. there doesnt seem to be an option for ntfs. I'm doing the setup screens on a live cd.

---

### Post by aheckler on 2008-05-03
> **purplegromit said:**
> is "/" for the ubuntu os partition?

Yes. You'll need about 10 GB for that.


As far as how to set up the shared partition, you could do it like this:

[IMG]http://www.psychocats.net/ubuntu/images/partitioning4.png[/IMG]

So set up the partition as FAT32 first. But then right after you install, boot to a GParted LiveCD and format the partition to NTFS. Or you could leave it as FAT32, I guess it doesn't really matter.

---

### Post by purplegromit on 2008-05-03
I have been looking at that very diagram on a guide.

So the mount options for the large partition are "windows" or "dos". Which should it be? Neither seems logical

Cheers again

---

### Post by aheckler on 2008-05-03
> **purplegromit said:**
> So the mount options for the large partition are "windows" or "dos". Which should it be? Neither seems logical

That doesn't sound right. What exactly are you looking at?

---

### Post by purplegromit on 2008-05-03
Im trying to do the setup with a live CD.

Im in the partition bit.

If I choose file system FAT32 the only mount options are windows or dos.

---

### Post by aheckler on 2008-05-03
> **purplegromit said:**
> If I choose file system FAT32 the only mount options are windows or dos.

Hmm, that is weird, I've never heard about this before. 

I would imagine you would just pick Windows. After all, the mount point is just the folder in which it can be found in ubuntu. My guess it that, when you tell Ubuntu to format the partition as fat32, it just guesses that's where Windows is, but I'm not sure.

So, if you format that partition as fat32 and choose windows, then in Ubuntu you'll be able to acces the large partition via the /windows folder.

I'm just making educated guesses here though, I might wait until someone with a bit more experience comes along to help you out.

---

### Post by purplegromit on 2008-05-03
Well it just crashed while I was trying to do the partitions, so I need to reformat the drive again. I'm getting a "blue screen of death" when loading windows with a mount error.

Trying the live CD with fingers crossed.

---

### Post by Moop on 2008-05-03
I would suggest skipping the fat32 partition and using a ntfs partition for shared data. Ubuntu can read and write to ntfs, so you really don't need fat32. If you create a ntfs partition separate from the one windows is on you can give it a mount point of /storage or just name it anything you want like  /mystuff

---

