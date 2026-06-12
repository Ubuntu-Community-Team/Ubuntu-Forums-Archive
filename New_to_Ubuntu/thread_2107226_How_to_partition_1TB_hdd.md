---
title: "How to partition 1TB hdd?"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by bakpinar on 2013-01-21
Hi ppl,

absolute beginner on linux systems. I would like to get a quick suggestion before installing ubuntu, even tough i lost all my data on my D:/ drive while trying to install it last nite.

on windows i use C: and D: as C:/Windows and D:/Movies, Photos, All Personal Data
C:/ around 100-150GB and D:/ 900GB

now how i should partition C: and D: in linux? i guess the filesystem will be ***ext4 ***for both but mounting to? C: can be /root? D: /home? how should i distribute the capacity as well?

And installation was asking to give a swap partition as well.

tia

buri

---

### Post by lukeiamyourfather on 2013-01-21
Yes, use ext4 as the filesystem on both drives. If you plan to erase all of your existing files an all drives and keep nothing, I'd setup what was previously the C: drive as "/" and what was previously D: as "/home". The swap space could be on either drive. I'd put it on the drive that performs better (probably the larger drive).

Depending on how important those files were that were accidentally deleted it might be worth talking to an expert before you do anything else, most of them are probably recoverable but it will cost to have them recovered.

---

### Post by greg_ory on 2013-01-21
[https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html](https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html)

Hope that explains a bit more in detail

-Greg

---

### Post by oldfred on 2013-01-21
Are you dual booting with Windows - on same drive or another drive?

I prefer smaller system files and large data partitions or separate /home. I use 25GB for / root) and keep /home inside /. But then have all data including some of the normally hidden folders in /home in data partitions.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

    
       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

