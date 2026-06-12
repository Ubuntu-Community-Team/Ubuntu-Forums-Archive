---
title: "I think I disabled the swap partition"
date: 2019-11-09
forum: New to Ubuntu
---

### Post by joelnvch on 2019-11-09
So I recently installed ubuntu and I set the swap partition to 7GB.
I wanted to have a bigger swap space so I created a swap file and I did it succesfully, but now I think the swap partition is not being used.

Why? Because when I execute the command **swapon -s **now it displays this:

Filename                Type        Size    Used    Priority
/media/fasthdd/swapfile.img                file        6291452    0    -2

And from what I was reading there it should not only be the file but also the partition (/dev/sda5) that was being used before. 
Could anybody help me please?

**[SOLVED]**: just had to **sudo swapon -a. **I still have the other question tho.


Also just another thing, you guys have any idea why when I use the application GParted I can't operate with the unallocated space? I mean, I can't literally do anything with it, I right click on it and the only options that I can use are "New" and "Information", I can't click on the rest of the options (delete, resize, copy, paste...).

---

### Post by linuxenthusiast on 2019-11-09
Have you tried activating your swap partition with the swapon command?

> sudo swapon /dev/sda5

Also, remember that the swap partition needs to be added to the fstab file, otherwise you won't be able to do it properly.

You can check here in order to [make your swap partition permanent]("https://devconnected.com/how-to-add-swap-space-on-debian-10-buster/#c_Make_your_swap_space_permanent"), this is for Debian but it should work the same way for Ubuntu.

You'll need to have the UUIDs of your partitions in order to make it permanent though.

---

### Post by CatKiller on 2019-11-09
> **joelnvch said:**
> Also just another thing, you guys have any idea why when I use the application GParted I can't operate with the unallocated space? I mean, I can't literally do anything with it, I right click on it and the only options that I can use are "New" and "Information", I can't click on the rest of the options (delete, resize, copy, paste...).

What exactly would you expect to happen with those actions? There **is** nothing to delete, resize, or copy, because it's **unallocated**. There's nothing to paste because you haven't copied anything.

---

### Post by linuxenthusiast on 2019-11-09
> **CatKiller said:**
> What exactly would you expect to happen with those actions? There **is** nothing to delete, resize, or copy, because it's **unallocated**. There's nothing to paste because you haven't copied anything.

Indeed yes, you might want to create a partition first using fdisk or gparted itself for example.

Then you will be able to delete it, resize it etc..

---

### Post by TheFu on 2019-11-09
> **linuxenthusiast said:**
> 
You'll need to have the UUIDs of your partitions in order to make it permanent though.

UUIDs don't make anything permanent, they are just a way to uniquely connect a partition to a mount in the fstab.  A device name, link-to-device by PUUID, UUID, PATH, LABEL also work.  See all the links under /dev/disk/by-* for other methods.  Use **ls -al** in those directories to see how each points to the device.  All of these non-device methods were created because the order that the kernel finds any devices is what determines the device name for many of them.  That order can change from boot to boot, especially with storage.  
Prior to systemd, network cards had a similar issue. On computers with multiple NICs, eth0 and eth1 could swap around from boot to boot, though it didn't happen most of the time, it was always a possibility. Now, systemd names NICs using the MAC, in an attempt to make them unique, consistent, names. enx000ec6c75518, for example. When that change was made, there were lots of very unhappy people, especially for systems with only 1 NIC.  

Have a swap partition or swap file doesn't matter.  Have 1 of each or none or 20 are also options. Just depends on the requirements.  I am not a fan of swap files, but if the HDD has an MBR partition table, there might be no choice if all the partitions are already used up. With GPT (GUID Partition Table), I see no reason ever to use a swap file.

I would question having any swap over 4.1GB in size for a number of reasons.  The goal with servers is to have sufficient RAM to never need swap.  For desktops, the goal should be to have sufficient swap that the OS gets slower as user feedback to know that RAM use is peaking so the user can take steps to free some RAM.
There's 1 exception, but only if security isn't any consideration - hibernation. Then the swap size needs to be slightly larger than the amount of RAM in the system.

IMHO. There are many, many, different opinions about all these things.

---

