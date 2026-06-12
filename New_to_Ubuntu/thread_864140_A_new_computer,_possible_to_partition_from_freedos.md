---
title: "A new computer, possible to partition from freedos?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by kramer65 on 2008-07-19
Hello,


I just bought a new computer without OS. This because I still have my xp license, because I don't want to support MS any more, and because I am going to run Ubuntu most of the time anyway.. :)

I do want XP on there (for the rare occasions that I still need windows) so I think it is smartest to first install XP, and then ubuntu. Currently it runs only freedos. Is it possible to partition the hard drive in freedos or do I need to first install XP for that?

Also, how do I find out the drive partitioning in freedos?

Any tips and tricks welcome! :)

---

### Post by hAvAAck on 2008-07-19
If you're not keeping freeDOS why not partition when you boot the XP CD, which is the first thing you're installing anyway?

---

### Post by diffuze on 2008-07-19
I agree, partition during XP installation. Make the extra partitions that you will later use for linux. I've done like this; I run XP with NTFS filesystem and I partition my future linux partitions in fat32 so I easily can identify them later while installing linux.

I also keep a fat32 partition for use as a fileshare between windows and linux, full read/write from both OS'es. I keep things like music, firefox-profile folder, downloaded wallpapers and so on there. 

Good luck! :)

---

### Post by Sef on 2008-07-19
> I also keep a fat32 partition for use as a fileshare between windows and linux, full read/write from both OS'es. I keep things like music, firefox-profile folder, downloaded wallpapers and so on there.


Instead of FAT32, you could make it an NTFS.  Then once you have Ubuntu installed, just install NTFS-3g, with which you will be able to read and write to the NTFS partition.  NTFS is more stable than FAT32.

---

### Post by diffuze on 2008-07-19
> **Sef said:**
> Instead of FAT32, you could make it an NTFS.  Then once you have Ubuntu installed, just install NTFS-3g, with which you will be able to read and write to the NTFS partition.  NTFS is more stable than FAT32.

I've had my "fileshare" for a few years, If I was to buy a new hdd and redo this I'd definitely make it ntfs.

---

### Post by kramer65 on 2008-07-19
Allright, there are some good tips.

Some things:

- I've installed XP a couple times, but can you actually partition within the setup? Didn't know..
- I want to make a separate "home" partition for ubuntu. How does this actually work, and can I use the graphical installer to do that? Also, is it possible to encrypt the ubuntu installation?

---

### Post by hAvAAck on 2008-07-20
for #2 see [this]("http://ubuntuforums.org/showthread.php?t=864928") thread :)

---

