---
title: "Shared Data partition format"
date: 2018-05-02
forum: New to Ubuntu
---

### Post by kazakore on 2018-05-02
OK not really new to Ubuntu but this is very much a n00b question, wondering/hoping things have changed in the last few years....

Basically what is now generally considered as the best format for a shared data partition? Years back I used to do FAT32, and generally still do with external drives, as it definitely has support from pretty much any OS you can think of. I have done between using FAT32 and Ext3 for the Data partition of my internal drive depending on conditions....

I have a new 4TB internal drive. I generally run Linux for everything but there's always a chance I may need something from the world of Windows and with some of the work I'm doing at the moment a fairly high chance I'll want to be running Windows in a VM at at least some point and it would definitely want to have access to the same data partition as my main system.

I have ~3.2TB free after allocating multiple OS partitions, EFI and Swap space which I would prefer have as a single data storage partition as I prefer the flexibility of working this way, which in itself basically rules out FAT32.

What would be the best choice of partition format??

---

### Post by Impavidus on 2018-05-02
A data partition to share with multiple Linuxes can be ext4, just like the partition with your installed system or a /home partition. If you want to share a partition with Windows, the best option is NTFS. It's the native system of Windows and Linux can read and write NTFS. However, Linux cannot fix NTFS if broken, you need Windows for that. So it's not a good idea to create an NTFS data partition just in case you want to install Windows at a later date, without actually installing Windows right away.

I've no experience with virtual machines, but I'm not sure they need direct access to the host's file system. Wouldn't they access the files on the host as if it were a file server on the network? In that case, the Windows virtual machine doesn't have to understand the file system of the shared data partition.

---

### Post by kazakore on 2018-05-02
> **Impavidus said:**
> 
I've no experience with virtual machines, but I'm not sure they need direct access to the host's file system. Wouldn't they access the files on the host as if it were a file server on the network? In that case, the Windows virtual machine doesn't have to understand the file system of the shared data partition.

I'm only just getting into the world of VMs but what you say makes a lot of sense.

Maybe I'll just go Ext3 again. Even though it seems support for NTFS on both Linux and OSX are better than they were a few years ago. If at a later date I need to recover data from the drive through somebody else's likely Windows machine I'll just have to make sure to have a Live USB of some kind for that purpose..... ;)

---

