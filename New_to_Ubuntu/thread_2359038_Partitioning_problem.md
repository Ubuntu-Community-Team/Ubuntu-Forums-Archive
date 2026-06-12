---
title: "Partitioning problem"
date: 2017-04-20
forum: New to Ubuntu
---

### Post by jelich on 2017-04-20
Hello,

I have a question regarding the partitions and previous instalations of linux... I've been testing linux for a while now and i run into something i cant explain :)

I used linux mint, then switched to lubuntu on an older laptop, today i found 2 directorys on partition, i had no idea that was there. I think it might be from previous linux mint instalation, one directory is named "jimi" as a user name from that instalation and other one is lost+found. That "jimi" dir contains regular user files, e.g. documents, pictures, downloads + hidden files, .adobe . cache .cinamon etc... so i have swap - sda1, then sda3 has two "subpartitions" -> sda5 - PROBLEM and sda6 - root.
Sda5 i think should contain my home folder that i use now on lubuntu, and it containst those two directorys "jimi" and lost+found.

If anyone can tell me what to upload here, some info from terminal, or pictures. I would really like to understand what happened with my partitions.

o and I'm new to the forum, so Hi ubuntu community!

Thank you

---

### Post by Dennis N on 2017-04-20
Welcome to the forum!

A partition's ext4 file system gets a top level lost+found folder upon creation, so we expect to see that. 

Top level folders (and a couple of symbolic links here too):
```
dmn@Roxanne:/$ ls
bin    dev   initrd.img  lost+found  opt   run   srv  usr
boot   etc   lib         media       proc  sbin  sys  var
cdrom  home  lib64       mnt         root  snap  tmp  vmlinuz

```
The partition containing jimi sounds like it was created as a separate home partition, and you are seeing the home folder for that one user. Like any partition, when it was created so was the lost+found folder.

---

### Post by jelich on 2017-04-20
Thank you for answering... though i'm still not certain whats happening. This partition is mounted in media/user/"bunch of letter and numbers" and in those bunch of letters and numbers i have dir "jimi" and that lost&found. Whats that jimi? Should i delete that? is my partitioning ok?

---

### Post by oldfred on 2017-04-20
Was jimi your name in  mint? And you used a different name with new install?
And then did you reuse sda5 for /home without formatting.

If mounted at /media/$USER/UUID it is not your /home.
Post this:
cat /etc/fstab
That will show if /home is separately mounted at sda5.

Do you have data in jimi that you want to keep.

Or do you want to make that partition /home. If brand new install may be easier to reinstall.
But  you can copy files from /home inside / to sda5 and convert sda5 to /home. 
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by ajgreeny on 2017-04-20
Your partitioning seems to be absolutely normal, so whatever you do, DO NOT start deleting folders from anywhere other than your own home.

It sounds as if you previously had a separate /home partition which you have now mounted by clicking on its icon in the file manager.  That will automatically mount it in /media/username which I assume in your case means /media/jimi and is exactly what I would expect.

The **lost and found** folders that you find are usually empty, and if your system is running cleanly they will stay empty, but if things should go wrong you may find files and folders within **lost and found** that can be restored to where they should be.

---

### Post by jelich on 2017-04-21
fstab result:> /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=81833465-f9a2-4456-b96e-055a60b335d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=97b84f6b-270c-4e75-88b0-e88332033e9b none            swap    sw              0       0



Yes, jimi was username on mint, new user name is "user". I dont remember did i use sda5 as home without formating.
No, i dont have any data on jimi, i can remove that. I would like to "merge" that partition containing jimi&lost+found, with my current home partition, if
that is possible.

---

### Post by jelich on 2017-04-21
could this be helpful maybe:
```
user@user-HP-625:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            851M     0  851M   0% /dev
tmpfs           175M  5,6M  169M   4% /run
/dev/sda6        19G  5,5G   12G  32% /
tmpfs           871M   52M  819M   6% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           871M     0  871M   0% /sys/fs/cgroup
tmpfs           175M   16K  175M   1% /run/user/1000
/dev/sda5       274G  5,1G  255G   2% /media/user/3d9a119f-5834-4077-b351-2d22fab23552
```
this sda5 is the one I'm talking about.

---

### Post by ajgreeny on 2017-04-21
If you want to reuse that sda5 partition as your /home you should be able to do so relatively easily but it will be easiest I believe if you can reinstall but this time use the previous username of **jimi**, not **user** as you have at present.

You will need to use the Something Else option in the installation which will show you all the partitions on the hard disk, and you can opt to reuse the current root partition as the new root by highlighting that partition, choosing to use as ext4, select the Format tick-box, and select / in the mountpoint drop-down box.  For the swap just leave it as it is, but for sda5, the old home, choose to use it as ext4, **DO NOT TICK** the format tick-box, and finally use /home as the mountpoint.

If for some reason you have to keep user as your new username come back and we can figure out how to proceed in that situation, where I think perhaps automounting sda5 in fstab and using symbolic links to the folders and files in /sda5 may be the way forward, treating it as a data partition.

---

