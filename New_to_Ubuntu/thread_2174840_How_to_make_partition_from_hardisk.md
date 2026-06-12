---
title: "How to make partition from hardisk ???"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by gurupal_singh on 2013-09-16
Hi,

I have installed Ubuntu 13.04 but i forgot to make partitions. How can i make partitions from my 500gb Toshiba hardisk. I uses Gparted disk manager, but it won't allowing me to make a single partition. 


Please HELP !!! me out from this.

---

### Post by Kirboosy on 2013-09-16
Welcome to the forums! :D

If I understand correctly you have installed 13.04 but you have installed it to one partition instead of setting up multiple partitions?
[URL="https://help.ubuntu.com/community/HowtoPartition/ResizingPartition"]
How to Partition/Resizing Partitions[/URL]

Hope that helps!
~Caboose

---

### Post by CeejRab on 2013-09-16
Hi gurupal_singh,

If you haven't set up documents and a lot of personal data that you don't want to lose yet, your easiest choice is to reinstall from a live CD. It will give you the option to "install alongside current Ubuntu" or "replace current Ubuntu" or "something else". Choose "Something else" to delete all the partitions so that its free space. Then make one partition that's 3GB less than all the storage space. Choose to make it the EXT4 journaling file system and mount point as "/". The the remaining 3GB of free space you can make into a new partition and select swap from the file system type list. 

Then proceed with the install and you'll be all set, your swap will be set up properly and no more issues. 

Hope this helps!

---

### Post by sandyd on 2013-09-16
> **gurupal_singh said:**
> Hi,

I have installed Ubuntu 13.04 but i forgot to make partitions. How can i make partitions from my 500gb Toshiba hardisk. I uses Gparted disk manager, but it won't allowing me to make a single partition. 


Please HELP !!! me out from this.

Hi, can you post a screenshot of gparted, and the output of
```

sudo fdisk -l
```.

This will allow us to see your current disk configuration, and allow us to help you further.

---

### Post by dshgna on 2013-09-17
Hi...
You cannot make shrink the current partition while you are still using it.
You have two options.
Reinstall as a previous user suggested OR you can burn PartedMagic (or any live cd for that matter) on a cd/usb, boot using it and then resize the current partition and make new partitions.
All the best ;)

---

### Post by cmcanulty on 2013-09-17
I would do the swap as suggested but then a 15-20GB for / and the rest for /Home. That way when you reinstall or mess up system your docs and config files are unaffected and you can just not ever reformat the /hoe partition

---

### Post by whitesmith on 2013-09-17
> **gurupal_singh said:**
> I uses Gparted disk manager, but it won't allowing me to make a single partition. I don't understand. Do you mean gparted puts up an error or that you don't know how to proceed? If it gives an error, please post it. Otherwise follow one of the other answers given here.

---

### Post by grahammechanical on 2013-09-17
You may of forgotten to make partitions but Ubuntu did not forget. When Ubuntu was installed it made 2 partitions - one for Ubuntu and one for Swap partition. If your machine has a boot system called BIOS and not EFI then you will only be allowed to have 4 primary partitions on the hard disk. You may have already had 3 primary partitions. Ubuntu then would have created a fourth primary partition and then turned it into an Extended partition and in the Extended Partition Ubuntu whould have then created 2 Logical partitions - one for Ubuntu and one for swap.

Gparted cannot create any more primary partitions because the allocation of 4 primary partitions have been used up but if we know what we are doing we can use Gparted to create more Logical partitions inside the Extended partitions.

Regards.

---

### Post by CeejRab on 2013-09-17
@grahammechanical - Ubuntu makes itself a swap partition? it didnt do that for me in any of my installs....

Gurupal_singh, Can you upload a screenshot of what you see when you select your HD in gparted please? That would give us an idea of whats going on if we can see how many partitions you have, etc.

The problem may be that you cant edit the partition youre working from, so maybe try booting from a live ubuntu cd and using gparted to resize the partitions. Be careful not to delete though, or you could lose your ubuntu install!

All the best,

---

