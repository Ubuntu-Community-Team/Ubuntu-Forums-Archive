---
title: "Default File System for Ubuntu"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Darksci on 2008-05-23
I noticed that when I first installed Ubuntu, I was given the choice to choose a file system e.g FAT32 etc.

Is the default file system when installing 'guided entire disk' (i think it was called that), the better NTFS file system?

Or did I have to specify that?

---

### Post by vishzilla on 2008-05-23
The default filesystem for Ubuntu is ext3, thats the recommended fs to choose

---

### Post by HunterThomson on 2008-05-23
> **Darksci said:**
> I noticed that when I first installed Ubuntu, I was given the choice to choose a file system e.g FAT32 etc.

Is the default file system when installing 'guided entire disk' (i think it was called that), the better NTFS file system?

Or did I have to specify that?

NTFS is crappy and is used my sindow$. The default is ext3.

---

### Post by fuzzyk.k on 2008-05-23
the default is ext3, NTFS and FAT32 don't compare to it i recommend using it

---

### Post by BlackDragonBE on 2008-05-23
Ext3 is the way to go :)

---

### Post by sayakb on 2008-05-23
Ext3 is the most efficient file system which experiences minimum fragmentation even after prolonged use.

---

### Post by aeiah on 2008-05-23
if you are creating a partition for the purpose of sharing it with windows, you may want to consider FAT or NTFS for that, since windows cannot read or write to the ext3 filesystem without additional windows drivers (available on sf.net). FAT has less issues with it, although NTFS can handle files that are larger than 4Gb in size. i believe problems can arrise with NTFS if windows isnt shut down properly though before booting linux. this only applies for shared partitions between the two OSes on the same PC. for the actual linux stuff, use ext3

---

### Post by reza81 on 2008-05-23
ext3 is tha shizzle for Mac, Linux & Unix users

---

