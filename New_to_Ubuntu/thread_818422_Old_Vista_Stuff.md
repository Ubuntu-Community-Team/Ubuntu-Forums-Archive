---
title: "Old Vista Stuff"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Gingerman on 2008-06-04
I like Ubuntu, and want to keep it.  I have some files on my computer from my previous OS, Windows Vista.  I can't figure out how to find it.  Much of it, particularly applications, I would like to un-install to free up space, and some of the files I would like to use without repeating them.

For example, I now have two versions of Open Office installed; All of the Windows Office stuff.  A lot of big applications that could be gone.

How do I find them, and how can I remove them?

---

### Post by strongboww on 2008-06-04
well, generally speaking, if you want to stay with ubuntu only, you can mount your vista partitions in ubuntu, then copy all your important data and erase the vista partition

if you want to stay dual boot, you should uninstall your programs in windows, but the problem is the free space will be still assigned to the ntfs-partition, i once tried to shrink a partition with partition-magic and it totally went wrong ending up in a complete data loss, so i dont know if i can recommend to uninstall programs and then resize the partition

---

### Post by sayakb on 2008-06-04
Your post is not quite clear to me. You must have had Vista on a separate partition. Did you look there. Also, how can you possibly "uninstall" programs you had in Vista? You have to just delete them I guess.

---

### Post by Oldsoldier2003 on 2008-06-04
> **Gingerman said:**
> I like Ubuntu, and want to keep it.  I have some files on my computer from my previous OS, Windows Vista.  I can't figure out how to find it.  Much of it, particularly applications, I would like to un-install to free up space, and some of the files I would like to use without repeating them.

For example, I now have two versions of Open Office installed; All of the Windows Office stuff.  A lot of big applications that could be gone.

How do I find them, and how can I remove them?

If you are wanting to clean up your vista installation the best bet is to clean it up from Vista. If you plan on keeping/using Vista then that is the way to go. If you don't want Vista anymore then the thing to do would be to save your data files (not applications) then remove the vista partition and remove the partition from your /etc/fstab and update your grub to remove the Vista entry from the boot loader.

If removing Vista from your system is what you want to do then post back with your /etc/grub/menu.lst and the result from ```
sudo fdisk -l
``` and someone here will be able to help you clean it up.

---

### Post by twright on 2008-06-04
> **strongboww said:**
> well, generally speaking, if you want to stay with ubuntu only, you can mount your vista partitions in ubuntu, then copy all your important data and erase the vista partition

if you want to stay dual boot, you should uninstall your programs in windows, but the problem is the free space will be still assigned to the ntfs-partition, i once tried to shrink a partition with partition-magic and it totally went wrong ending up in a complete data loss, so i dont know if i can recommend to uninstall programs and then resize the partition
you could easily resize the partition in GParted (free is always better) but it might be wise to backup important stuff 1st

---

### Post by django0909 on 2008-06-04
What I would do is, as strongboww said, mount the Windows partition in Ubuntu, transfer your files from Vista into your Ubuntu partition. Then I would use gparted to wipe the Vista partition. You will have to use the gparted live CD, (google it), as far as I am aware as you cannot alter/resize partitions while you are using them.

Hope that helps?

---

### Post by Oldsoldier2003 on 2008-06-04
> **strongboww said:**
> well, generally speaking, if you want to stay with ubuntu only, you can mount your vista partitions in ubuntu, then copy all your important data and erase the vista partition

if you want to stay dual boot, you should uninstall your programs in windows, but the problem is the free space will be still assigned to the ntfs-partition, i once tried to shrink a partition with partition-magic and it totally went wrong ending up in a complete data loss, so i dont know if i can recommend to uninstall programs and then resize the partition

resizing a vista partition is best achieved using the partitioning tool in Vista

---

### Post by twright on 2008-06-04
> **django0909 said:**
> What I would do is, as strongboww said, mount the Windows partition in Ubuntu, transfer your files from Vista into your Ubuntu partition. Then I would use gparted to wipe the Vista partition. You will have to use the gparted live CD, (google it), as far as I am aware as you cannot alter/resize partitions while you are using them.

Hope that helps?just use the ubuntu liveCD, it has gparted

---

### Post by Oldsoldier2003 on 2008-06-04
> **twright said:**
> just use the ubuntu liveCD, it has gparted

why would he want to use a live cd? simply unmounting The partition and wiping from within Ubuntu is not a problem and doesn't require a reboot. Just wipe/reforamt the Vista partition, add it back to the fstab and ```
sudo mount-a
```(if thats what the OP wants to do)

---

### Post by twright on 2008-06-04
> **Oldsoldier2003 said:**
> why would he want to use a live cd? simply unmounting The partition and wiping from within Ubuntu is not a problem and doesn't require a reboot. Just wipe/reforamt the Vista partition, add it back to the fstab and ```
sudo mount-a
```(if thats what the OP wants to do)
but to make use of any space gained he would have to resize the Ubuntu partition

if you just want to reduce the size of Vista not remove it you need to boot in to Vista to do it, I would uninstall some programs then run CCleaner

---

### Post by Oldsoldier2003 on 2008-06-04
> **twright said:**
> **but to make use of any space gained he would have to resize the Ubuntu partition**

if you just want to reduce the size of Vista not remove it you need to boot in to Vista to do it, I would uninstall some programs then run CCleaner

nope. once reformatted he could mount the partition and use it as a data partition. no need to mess with the / partition

---

### Post by twright on 2008-06-04
> **Oldsoldier2003 said:**
> nope. once reformatted he could mount the partition and use it as a data partition. no need to mess with the / partitionmultiple partitions means multiple places to loose stuff, much better to just add space to the existing directory structure

---

### Post by Oldsoldier2003 on 2008-06-04
a difference of opinion :) Since i often run multiple versions of different distributions i find having a separate data partition extremely and immensely useful. It allows data sharing between the different operating systems. For a single OS user it means a reinstall is relatively painless and a no brainer since all the data files are safely placed on a nonsystem partition.

I guess I'll just have to agree to disagree with you since I am a firm believer that just extending the / partition in size is not the best or safest option.

---

