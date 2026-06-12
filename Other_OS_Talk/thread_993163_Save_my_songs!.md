---
title: "Save my songs!"
date: 2008-11-25
forum: Other OS Talk
---

### Post by Fzang on 2008-11-25
I'm going to get a new computer in 17 days as they state on the site (how am I ever gonna survive these 17 days?) which is going to be running linux (current computer is stupid and won't run linux, don't ask!) and I can run nearly all my windows programs with a linux alternative, however, iTunes is the only thing that's stopping me...

I have an iPod Touch which isn't happily going to be synced through linux, so I've thought about using iTunes on my winXP install (gonna have that for games still) but I'd love to play music in linux as well. So here's my plan:

Partition 1 - NTFS - winXP
Partition 2 - ext3 - Linux
Partition 3 - FAT32 - contains all my music/video stuff

So if I put up new stuff on the FAT32 partition I could access it from both iTunes in windows and (insert name of linux music player once I've decided) in linux

howzat? Will it work out by having the apps leeching from a different partition?

---

### Post by gn2 on 2008-11-25
Will be very straightforward using Amarok,just point Amarok at the location where your music is stored.

I have Ubuntu 8.10 installed on a USB drive and when it's booted Amarok can use the files on my internal drive's Ubuntu 8.04 installation's /home partition.

---

### Post by Keith Hedger on 2008-11-25
I dont know about thw windows part but most of the music players ive tried on linux allow u to set the location of your music library and as i remember itunes on the mac and so probably on windows too will let you set the location of the itunes library so you should have no problems, just remember that the fat file system does not support full file permissions or symlinks which can sometimes be a problem for linux

---

### Post by prshah on 2008-11-25
> **Fzang said:**
> 
Partition 1 - NTFS - winXP
Partition 2 - ext3 - Linux
Partition 3 - FAT32 - contains all my music/video stuff

So if I put up new stuff on the FAT32 partition I could access it from both iTunes in windows and (insert name of linux music player once I've decided) in linux

Don't know about the rest but you don't need a fat(32) partition; linux has full read/write support for ntfs out of the box from 7.10 onwards.

---

### Post by DeadSuperHero on 2008-11-25
You could always burn your songs onto discs. It might make for a slight drop in quality, but it'd strip away the DRM in the tracks as well.

---

### Post by chris4585 on 2008-11-25
that'll work fine

---

### Post by Fzang on 2008-11-26
> **Mr. Psychopath said:**
> You could always burn your songs onto discs. It might make for a slight drop in quality, but it'd strip away the DRM in the tracks as well.

I have like... 4 songs that are DRM protected, lol :D

So I should just store all songs on windows NTFS?

---

### Post by wolfen69 on 2008-11-26
> **Fzang said:**
> I have like... 4 songs that are DRM protected, lol :D

So I should just store all songs on windows NTFS?

i guess it's a personal choice. i keep all backups and media on fat32. any os can read fat32. ntfs or fat will do.

---

