---
title: "using FAT32"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by pandastew on 2008-06-26
so I have set up my partition as suggested by [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
so I have NTFS for window XP, FAT32 for shared. now the guide tells me that FAT32 can be read by both XP and Ubuntu so I went with that for majority of my HD space. but how exactly do I get XP to use this FAT32 partition? cuz I am running out of HD space on my NTFS partition and I cant seem to find the FAT32 partition through XP operating system.

---

### Post by Rocket2DMn on 2008-06-26
In Windows, go to the Control Panel and hit Administrative Tools, then Computer Management (I think it's the same in XP as Vista).  From here click Disk Management on the left side.  You should be able to drives and partitions (some of which won't be recognized because they are linux formatted).  You should be able to see yout FAT32 partition from here and right click it to assign a drive letter.

---

### Post by lunarcloud on 2008-06-26
Y'know, linux will read/write NTFS. It has for a good year or so. Shared fat32 partitions are no longer needed.

---

### Post by bodhi.zazen on 2008-06-26
> **zarquad said:**
> Y'know, linux will read/write NTFS. It has for a good year or so. Shared fat32 partitions are no longer needed.

Well, not exactly.

IMO the drivers for vfat (FAT) are slightly more reliable then ntfs (ntfs-3g). This is not to say ntfs is unreliable, it is just that occasionally the ntfs driver can have issues where, other then frank hardware failure, vfat is solid as a rock.

FAT has another advantage in terms of cross platform compatibility (there are more drivers for FAT on more platforms then ntfs).

---

### Post by pandastew on 2008-06-27
so you know what...I havent touch my big partition yet. so I havent assign it a File system( atleast I hope so, cuz the partition is unknown when read by XP)...should I stay with FAT32 or go with NTFS? and how exactly do you format a partition to whatever file system?

---

### Post by OldTimeTech on 2008-06-27
gparted is the best programs for that

---

### Post by ByteJuggler on 2008-06-27
Personally I would opt for NTFS.

---

### Post by pandastew on 2008-06-27
what program would you use to convert the partition to NTFS?

---

### Post by sydbat on 2008-06-27
Not sure if gparted would do it (probably would because it does everything else). If it doesn't, go into XP and do it from there.

---

### Post by Duck2006 on 2008-06-27
> **pandastew said:**
> what program would you use to convert the partition to NTFS?

You can do that within win xp or use gparted or parted magic.

---

### Post by ByteJuggler on 2008-06-27
> **pandastew said:**
> what program would you use to convert the partition to NTFS?

If the partition is empty, dont bother converting it.  Just reformat it as NTFS.  (Using either Windows preferably or GParted.)

---

### Post by Neo0351 on 2008-06-27
if u use gparted, you will probably need to install ntfsprogs
```
 sudo apt-get install ntfsprogs
```

---

