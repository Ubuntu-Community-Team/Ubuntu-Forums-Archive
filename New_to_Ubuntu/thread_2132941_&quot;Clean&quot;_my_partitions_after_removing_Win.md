---
title: "&quot;Clean&quot; my partitions after removing Windows and Leopard"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by TheAmazingKitchen on 2013-04-06
Hi,

I recently installed Kubuntu and uninstalled Windows XP and Leopard using the OS-remover tool. However, after a quick look in the partition manager, I noticed it was kinda messy (or at least it seemed messy to the beginner I am), as you can see on the screenshot below. I'd like to "clean" it and make it so ubuntu uses all the free space, but don't want to mess it up, so I'm asking : what sould I remove/resize/create, and how sould I do it ?

Thanks a lot !

---

### Post by El Tito on 2013-04-06
If you don't have any important data in the extended partition sda5 and 6, fat32 and ntfs, I would wipe the entire extended partition sda2 to reorder the chunks. I would create an extended partition in sda2 with a new partition sda3, 2GB of swap, sda4 20/30GB for / (this is personal, maybe less is enough for you), and for /home depends too on you. As I can see, it seems you have a data partition in fat32 and another one in ntfs, I suppose to enable access between all your OSs. Maybe you want to make a couple of data partitions; in that case you can create a new primary partition (one or two), the filesystem you want/need (fat32, ntfs ...) or as you did in the image, include these new partitions in the logical.

---

### Post by fantab on 2013-04-06
If you have removed Windows then you don't need NTFS and FAT at all. Remove NTFS and FAT altogeter... they are lousy anyways.

My partitioning scheme loos like this:
/dev/sda1  Primary  Ext4  15-20GB  "/" Ubuntu
/dev/sda2  Primary  Ext4  15-20GB  "/" Linux Distro
/dev/sda3  Primary  Ext4  15-20GB "/" Linux Distro
/dev/sda4  Extended Remaining GB
/dev/sda5  Logical   SWAP  2-4GB
/dev/sda6  Logical   Ext4   Remaining GB "/home"

If reinstalling Kubuntu is an option then do consider it. That way you can have your HDD partitioning the way you want/need it. 

EDIT: Do BACK UP your Important DATA first.

---

### Post by DuckHook on 2013-04-06
This is actually not too bad (have seen much worse).

Do NOT delete sda7. This is likely where you have installed Kubuntu itself.

What do you wish to do? Clean things up without reinstalling Kubuntu? If so, then it is just a matter of deleting sda1 and sda6, reinstalling your bootloader and using the freed-up space however you like. You could make new ext4 partitions, move your data to one of the new partitions and then reformat sda5 to ext4 as well for better performance and journalling (better data safety, more efficient use of disk space--fat32 is awful for security, redundancy or efficiency).

If you prefer to have a really neat and tidy partition scheme, with / at the front of the disk, /home next, and a data partition for permanent data that survives across different OSes and installs, then you can either try moving partitions (which is always riskier) or you could use this opportunity to reinstall Kubuntu.

Either way:

*****BACKUP FIRST*****

The single biggest cause of lost data, frantic pleas for help and disappointment on these forums is due to borked partitioning.

All partitioning has to be done from a LiveDVD/USB. Your HDD cannot be mounted while you fiddle around with its partition table.

---

### Post by Impavidus on 2013-04-06
As there is only Linux now on the computer, there is no need for any non-native Linux partitions. Getting rid of the ntfs partitions would be a good idea, as Ubuntu cannot repair them in case they get damaged – only Windows can. So my suggestion would be reformat your /dev/sda1 to ext4, copy the contents of /dev/sda5 there and use it as a general data partition. Then you can either erase everything in your /dev/sda2 (the extended partition) and reinstall (really tidy), or merge your /dev/sda5 and /dev/sda6 into a new ext4 partition and use that for your /home (slightly less tidy, but easy if you don't want to reinstall). If you wish you can shrink your /dev/sda7 and move your /dev/sda8 a bit to the left.

---

### Post by TheAmazingKitchen on 2013-04-06
Thanks for all the quick and detailed answers :) ! I managed to sort it the way I wanted without any major issue.

---

