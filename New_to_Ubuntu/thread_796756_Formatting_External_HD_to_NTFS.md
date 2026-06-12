---
title: "Formatting External HD to NTFS"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Etheredge on 2008-05-16
Im trying to repartition an external HD to NTFS in order to copy more then 4gbs to the drive scince there is a cap at 4 with the fat32 fs

Any ideas?

---

### Post by PinkFloyd102489 on 2008-05-16
Connect the drive then open GNOME Partition Editor under System > Administration >  GNOME Partition Editor.


Oh and if you dont have the option to format to NTFS, open Synaptic and install ntfs-3g, ntfsprogs, ntfs-config and libntfs-3g23.

---

### Post by TeoBigusGeekus on 2008-05-16
System->Administration->Partition Editor
If you don't have it installed, then
```
sudo apt-get install gparted
```

Let it search your volumes, choose the external hd, choose format and apply changes...

---

### Post by Etheredge on 2008-05-16
i have tried this before and i am unable to select NTFS

---

### Post by geoff123 on 2008-05-16
You should do this type of formatting in Microsoft Windows since it's the native format. I assume you have Windows available since you need to use NTFS. Once its formatted it should be usable in Linux.

---

### Post by Etheredge on 2008-05-16
the only reason i was wanting to format it was because i cant xfer files over 4gb to it

well i might be able to but i dont know a way to any help?

---

### Post by PinkFloyd102489 on 2008-05-16
> **geoff123 said:**
> You should do this type of formatting in Microsoft Windows since it's the native format. I assume you have Windows available since you need to use NTFS. Once its formatted it should be usable in Linux.

Windows doesnt come with partitioning tools. Much simpler to format in Ubuntu.


Install the NTFS programs like I indicated in my post.

---

### Post by TeoBigusGeekus on 2008-05-16
> **Etheredge said:**
> i have tried this before and i am unable to select NTFS

How come? Do you get any error messages or something?

---

### Post by Etheredge on 2008-05-16
> **PinkFloyd102489 said:**
> Connect the drive then open GNOME Partition Editor under System > Administration >  GNOME Partition Editor.


Oh and if you dont have the option to format to NTFS, open Synaptic and install ntfs-3g, ntfsprogs, ntfs-config and libntfs-3g23.

Thank you i guess i skipped over that. It worked quite well : )

---

### Post by PinkFloyd102489 on 2008-05-16
Im on a roll today. Mark as Solved please.

---

### Post by Neo0351 on 2008-05-16
> **Etheredge said:**
> Im trying to repartition an external HD to NTFS in order to copy more then 4gbs to the drive scince there is a cap at 4 with the fat32 fs

Any ideas?

i saw that u did get ur harddrive formated, but just so u know, u can have more than 4 gigs on fat32.  i have a 120 gig external HD formated in fat32 with 40+ gigs on it.  i think u are thinking of 4+ gigs of ram on a 32 bit system.

---

### Post by PinkFloyd102489 on 2008-05-16
No, you cant transfer more then 4GB at a time. Of course it can HOLD more than 4GB. :-p

---

