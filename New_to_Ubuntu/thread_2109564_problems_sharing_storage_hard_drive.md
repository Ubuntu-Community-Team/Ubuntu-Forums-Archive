---
title: "problems sharing storage hard drive"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2013-01-27
Hello all!

Truthfully, I should know this, as I have been using Ubuntu for a few years now, but I seem to be running into a road block. I have a separate HD on my system used for storage. It is formatted as NTFS, as I want to be able to access it from either Ubuntu or Windows (all OSs are installed on separate HDs). I have multiple user accounts on my Ubuntu installation. I want for all users to be able to access this storage HD. The problem I am running into is that if I place files on the storage HD from any user account, it makes the HD inaccessible by other users. Any assistance appreciated.

-Ryan

---

### Post by papibe on 2013-01-27
Hi Ditchdoc7893.

Since NTFS does not support neither ownership and permissions, the only way to share between users is to create relaxed permissions on the mount options.

Take a look a this [thread]("http://ubuntuforums.org/showthread.php?t=2086730&highlight=mount+ntfs") with a similar concern. Adjust the mount options with the proper permissions (I guess 777).

Let us know how it goes.
Regards.

---

### Post by Ditchdoc7893 on 2013-01-29
Ok, another question for ya. Since NTFS does not support either ownership or permissions, I have no problem reformatting the drive. What should I reformat the drive to, to allow sharing permissions between Ubuntu users and still be visible under Windows? And how would I go about sharing the drive in Ubuntu?

Thanks in advance!

---

### Post by DuckHook on 2013-01-29
Problem is, Windows does not play nice with any of the other kids on the block. It is possible to get Windows to read other formats, but this requires special drivers. The "easiest" solution, as far as Windows is concerned, is probably *papibe*'s solution. I've always found that it is easier to accommodate Windows than the other way around. The only formats that Windows will read natively are NTFS, Fat, Fat32 and some cd formats that won't do you any good. I am certain that special Windows drivers will also work, but don't know how to do that. The multi-platform gurus on this forum will be better able to advise you there.

---

### Post by santosh83 on 2013-01-29
> **Ditchdoc7893 said:**
> Ok, another question for ya. Since NTFS does not support either ownership or permissions, I have no problem reformatting the drive. What should I reformat the drive to, to allow sharing permissions between Ubuntu users and still be visible under Windows? And how would I go about sharing the drive in Ubuntu?

Thanks in advance!

Hi. I face the same problem. I've all my files on an external HDD which came formatted as NTFS from the manufacturer. Linux reads and writes to NTFS pretty well, but the permission of all files are set to 777 and unchangeable!

Also I always fear that if and when I read/write to this drive from a Windows system in the future (currently I'm not using any Windows) it might change the NTFS format/metadata in such a way that Linux will read it wrongly later, or both systems interpret NTFS in subtly different ways and in doing so, corrupt my data. As NTFS is Microsoft specification it can change anytime without warning.

Sadly other options are even worse I think. Fat32 is totally inadequate for the sizes of modern drives and files, and I think ISO filesystems are similarly restricted.

On the flip side it's very surprising that while there are decent reverse-engineered NTFS drivers under Linux (which would presumably take a lot of work to track a closed and ever moving format), there are no well-known Windows drivers for ext2/3/4 or btrfs, even though they are open source and all their inner workings are fully known. One would've imagined it'd be easier to make Windows read an open format than Linux read a closed one, but I suppose user pressure forced the NTFS driver to become popular while no one outside Linux considers using ext filesystems.

Maybe when ZFS arrives on Linux it'd change this situation, or even if there's a good btrfs driver written for Windows! Meanwhile I guess we'll have to keep using NTFS for data portability. Sad how technology is nevertheless crippled by human egos.

---

### Post by sudodus on 2013-01-29
> **DuckHook said:**
> Problem is, Windows does not play nice with any of the other kids on the block. It is possible to get Windows to read other formats, but this requires special drivers.[COLOR=Red] The "easiest" solution, as far as Windows is concerned, is probably *papibe*'s solution[/COLOR]. I've always found that it is easier to accommodate Windows than the other way around. The only formats that Windows will read natively are NTFS, Fat, Fat32 and some cd formats that won't do you any good. I am certain that special Windows drivers will also work, but don't know how to do that. The multi-platform gurus on this forum will be better able to advise you there.

Either mount the drive with read/write or read/write/execute permissions or use a linux ext file system and help Windows mount it with

[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

This approach would be preferred, if you are mainly working in linux, since the linux disk drivers for ntfs are not very efficient (slow and need a lot of CPU).
--
An alternative is to have the drive on a separate machine in the local area network  (or a simple NAS), then everybody can connect to it via a network service and never worry about the file system.

---

### Post by Ditchdoc7893 on 2013-01-29
I have found at least a usable workaround for (for now) to share the storage partition between all the users on my Ubuntu installation. I'm still working on the Windows part of it but will post with updates. 

I have re-formatted the partition to ext3.
I used the following commands:
     sudo cd/media/Storage
     sudo chmod -R 777 *

This has allowed all users to read, write, and execute to this partition. Now, I have come across one small issue (that I can deal with if there's no way around it). If a standard user writes something to the partition, it is not accessible by other users unless I go back and use the recursive command above to again change all files to read, write, and execute. This might become a pain if I add files to the drive frequently. Any suggestions?

Also, with regard to accessing the files from Windows, I am going to attempt to find a driver for the ext3 filesystem. Suggestions?

Regards!

---

### Post by sudodus on 2013-01-30
- Driver: see link in post #6

- Permissions: I think the permissions will be 
```
-rw-rw-r--
```
for regular files in directories with
```
drwxrwxr-x
```
This means that the user and group members will have read and write access which should be OK. Others will have read access.

So if you want to share files with write access, make those involved be members of your group.

---

### Post by Ditchdoc7893 on 2013-01-30
Ok,

So I scrapped the whole thing and reformatted AGAIN. This time partitioned the drive into 2 separate partitions, one ext4 and one NTFS. I used the previously described method to enable the folder to be accessed by all users on the Ubuntu system. This is to be used as nothing more than a backup partition for my important stuff in Ubuntu. I can access the NTFS system from Ubuntu and Windows, so I can backup any important Windows files to it and have access to it from Ubuntu if needed. Problem solved for now! 

Thanks everyone!

---

