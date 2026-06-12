---
title: "Administrative User &amp; Its Permissions."
date: 2021-09-18
forum: New to Ubuntu
---

### Post by aabedii on 2021-09-18
Hi. Im a new to lubuntu. I installed lubuntu 21 and there were no any problem during installation. It asked me to define a user and password normaly. I made it and checked require password everytime  to login. Now I have 2 problems so far: first, I have a user partition with ext4 fs but I cant open it. Each time I want to open this in any GUI environment and any file manager, an error appears and says : cant mount this. Then second error appears and says you dont have permission to . . . I tried to change the setting in properties/ permission tab of its, but same error happened and when checked the setting again, I see the checkbox es is unchecked after I clicked ok. 
Second problem is about hibernate. I cant hibernate the notebook because I dont have permission. I think there is a big thing I should know about admin user and permissions. Please help me. Thank u all.

---

### Post by ActionParsnip on 2021-09-18
Is it Lubuntu 21.04 or Lubuntu 21.10? Lubuntu 21 doesn't exist. If you are unsure then please run:
```

lsb_release -a

```
And give us the output

---

### Post by ActionParsnip on 2021-09-18
Did you add the file system in /etc/fstab to make it auto-mount at boot? I'm assuming the "user partition" is on an internal system disk.

---

### Post by GhX6GZMB on 2021-09-18
Most likely you selected automatic partitioning during install.
The Lubunutu installer will in that case only make a / partition that contains everything.
You should have selected manual partitioning, then you can define partitions as you like.
Best solution is to redo the installation. Changing fstab is also a possibility, but might not be the complete solution. Other settings also need the partitioning information, eg, initramfs.

---

### Post by grahammechanical on 2021-09-18
Are you the only user on this operating system? Is this "user partition" for you as a user or is it the partition for another user? 

Whether we log in by giving a user name & password or login automatically we will still need to authorize certain actions with our password.  Unlike some operating systems Ubuntu does not have an administrator account which will give anyone sitting at the keyboard the power to do anything to the operating system.

Some user interfaces will ask us to authenticate with our password the action we are trying to take. Are you not getting a dialog box asking you to authenticate the action?

Regards

---

### Post by TheFu on 2021-09-18
On Unix-like OSes, storage management is a task for administrative users, not end-users.  It requires more understanding than "that other OS" requires.  You'll need to understand what these terms mean, exactly, in their correct uses:

**drive** - on "that other OS", you may have learned "C: drive" and "D: Drive" - that is factually incorrect.  Neither C nor D are "drives."  They are partitions.

**partition** - a partition is a sub-section of a total storage device.  Every "drive" can have between 0 and 128 partitions. Partitions are usually split based on contiguous location on the storage media. With flash and SSD storage, that doesn't really exist anymore like it does on older "spinning disks."

**file system** - a file system has to be "formatted" onto a partition before it can be mounted.  In "that other OS", there are effectively just 3 file systems used - NTFS, exFAT, and FAT32.  In Linux, there are 50 file systems from which we can choose in addition to those three from "that other OS".  However, for Linux programs and user's HOME directories, only native Linux file systems can be used.  Examples are ext3, ext4, xfs, btrfs, zfs, f2fs, reiserfs, but there are many, many, others. These are all POSIX file systems, unlike the file systems from "that other OS."  This is a requirement for Unix permissions which include the owner, group, ACLs, xattrs, and file attributes. That is what allows the chown and chmod commands on every Unix-like OS to work.  Those commands do not work on the 3 file systems from "that other OS".  Those file systems can only be used for non-secure data storage, nothing else.

**mount** - only root or a userid that can elevate to root authority can mount storage on Unix systems.  Some Linux distros have hidden that by automatically mounting storage, usually USB/flash/SDHC storage, under /media/{userid}/{Partition LABEL} in what appears to be automatic.  This is for convenience and has many security implications.  _The power to mount, is the power to destroy._  Learn that. It will take some experience, usually years, to understand why that is true.  There are 3 ways to mount a file system into Linux in a way that it is a "real mount".  That last term is mine. There are fake mounts too. More on those later.  Real mounts can be accomplished by:
[LIST]
[*]editing the /etc/fstab file and putting the mount information for the filesystem, location to be mounted onto, and options.
[*]using the "mount" command, using the mount information for the filesystem, location to be mounted onto, and options.
[*]setting up autofs, which can mount storage as-requested, using the mount information for the filesystem, location to be mounted onto, and options.
[/LIST]
This applies to all file systems. Native and from "that other OS".  There is no good way to mount by point-n-click on storage using a GUI.  In general, that creates a "fake mount" which has some liabilities, though there are exceptions in a few specific situations.  For file systems from "that other OS", the GUI fake-mount causes permissions and performance issues on most Linuxen.  Buried deep in the menus of **gnome-disks** (if you setup has that program), it is possible to find a way to mount storage with a real mount that will work fast.

A while ago, I wrote detailed steps to mount storage [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) which also provided tips after over 25 yrs of doing these things. It has the best, easiest, method that I know, which will also be fast and efficient with the storage. I suggest using the LABEL mount method and show specific commands to run.  There are other methods, but those use confusing random identifiers that we humans don't really "get" intuitively like a LABEL name can provide.

---

### Post by TheFu on 2021-09-18
BTW, people often confuse "new" with "better".  With Linux, that isn't necessarily the case.  Anyone new to Ubuntu really should run the most recent LTS release, not the "new"-est release.  Today, that is 20.04.  LTS means a total of 5 yrs of no-hassle, free, support, package updates, etc.  

Non-LTS releases are meant for 6 months of use and Canonical tries out things that often break the OS in those beta releases.  They don't call them "beta", but for most people, there will be issues and do you really want to reload your OS every 6 months when support ends?

There is a valid reason to run a non-LTS release.  That is if your hardware is too new and doesn't work with the current LTS or if you are a professional developer/tester and want to help make Ubuntu better by testing the "new" for bugs, reporting them formally, and getting fixes to be tested. Basically, expect to reload the OS every week.  In the 1990s, I did that stuff.  These days, it isn't how I choose to have my computers setup.  Most of them run the N-1 LTS (18.04) and a few have the current LTS (20.04) as I slowly migrate forward.

**lsb_release -a** is how Debian-based (i.e. Ubuntu) OSes tell use which release they are. Run that command in a terminal.

As for not being able to open an ext4 file system, that is probably because by default, the file system is owned by root and doesn't allow other users access. On a single-user system, the answer is probably to run **sudo chown $USER /path/to/mounted/location** followed by **chmod 700 /path/to/mounted/location**. That will make the current userid the owner and set permissions so that userid has full access, but nobody else can access it.  If you want to allow others to read files/directories from that file system, then use **chmod 755 /path/to/mounted/location** instead.

Sorry, I can't help with hibernation. Never use it due to security issues.  I use standby, but only if I'm near the system or it is at home.  If the laptop will be relocated, then I shut it down for security reasons.  For some reason, I vaguely remember that hibernation got broke when they changed the default from using a swap partition to using a swapfile. I don't recall and didn't pay much attention since I'd never use hibernation.

---

### Post by GhX6GZMB on 2021-09-18
Frankly, forget the Hibernate thing right now. I'll help you with that later.
Getting your basic installation and disk partitioning working is more to the point.
Although those two connect: also define a SWAP partition during install that's a bit larger than your RAM.

---

### Post by aabedii on 2021-09-18
Thank U ActionParsnip. it is 21.04

---

### Post by aabedii on 2021-09-18
> **ActionParsnip said:**
> Did you add the file system in /etc/fstab to make it auto-mount at boot? I'm assuming the "user partition" is on an internal system disk.

No, I did Not. I Use an Internal Disk. How Can I do that ?

---

### Post by aabedii on 2021-09-18
Thank u very much "ml9104".
No, I did it manualy & I created 4 individual partitions for SWAP, /Boot, Root & another one for user. Now, I see just 2 drives in GUI file manager. 

[https://freeimage.host/i/RPTun4](https://freeimage.host/i/RPTun4)

<a href="https://freeimage.host/i/RPTun4"><img src="https://iili.io/RPTun4.md.jpg" alt="RPTun4.md.jpg" border="0"></a>
[https://freeimage.host/i/RPTaS9](https://freeimage.host/i/RPTaS9)

---

### Post by aabedii on 2021-09-18
Thank U very much " [COLOR=#DD4814][COLOR=#000000][grahammechanical]("https://ubuntuforums.org/member.php?u=1087323") "[/COLOR][/COLOR]
 
I Created only one user. each time I boot the machine, it requires the password.

---

### Post by aabedii on 2021-09-18
> **TheFu said:**
> On Unix-like OSes, storage management is a task for administrative users, not end-users.  It requires more understanding than "that other OS" requires.  You'll need to understand what these terms mean, exactly, in their correct uses:

**drive** - on "that other OS", you may have learned "C: drive" and "D: Drive" - that is factually incorrect.  Neither C nor D are "drives."  They are partitions.

**partition** - a partition is a sub-section of a total storage device.  Every "drive" can have between 0 and 128 partitions. Partitions are usually split based on contiguous location on the storage media. With flash and SSD storage, that doesn't really exist anymore like it does on older "spinning disks."

**file system** - a file system has to be "formatted" onto a partition before it can be mounted.  In "that other OS", there are effectively just 3 file systems used - NTFS, exFAT, and FAT32.  In Linux, there are 50 file systems from which we can choose in addition to those three from "that other OS".  However, for Linux programs and user's HOME directories, only native Linux file systems can be used.  Examples are ext3, ext4, xfs, btrfs, zfs, f2fs, reiserfs, but there are many, many, others. These are all POSIX file systems, unlike the file systems from "that other OS."  This is a requirement for Unix permissions which include the owner, group, ACLs, xattrs, and file attributes. That is what allows the chown and chmod commands on every Unix-like OS to work.  Those commands do not work on the 3 file systems from "that other OS".  Those file systems can only be used for non-secure data storage, nothing else.

**mount** - only root or a userid that can elevate to root authority can mount storage on Unix systems.  Some Linux distros have hidden that by automatically mounting storage, usually USB/flash/SDHC storage, under /media/{userid}/{Partition LABEL} in what appears to be automatic.  This is for convenience and has many security implications.  _The power to mount, is the power to destroy._  Learn that. It will take some experience, usually years, to understand why that is true.  There are 3 ways to mount a file system into Linux in a way that it is a "real mount".  That last term is mine. There are fake mounts too. More on those later.  Real mounts can be accomplished by:
[LIST]
[*]editing the /etc/fstab file and putting the mount information for the filesystem, location to be mounted onto, and options.
[*]using the "mount" command, using the mount information for the filesystem, location to be mounted onto, and options.
[*]setting up autofs, which can mount storage as-requested, using the mount information for the filesystem, location to be mounted onto, and options.
[/LIST]
This applies to all file systems. Native and from "that other OS".  There is no good way to mount by point-n-click on storage using a GUI.  In general, that creates a "fake mount" which has some liabilities, though there are exceptions in a few specific situations.  For file systems from "that other OS", the GUI fake-mount causes permissions and performance issues on most Linuxen.  Buried deep in the menus of **gnome-disks** (if you setup has that program), it is possible to find a way to mount storage with a real mount that will work fast.

A while ago, I wrote detailed steps to mount storage [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) which also provided tips after over 25 yrs of doing these things. It has the best, easiest, method that I know, which will also be fast and efficient with the storage. I suggest using the LABEL mount method and show specific commands to run.  There are other methods, but those use confusing random identifiers that we humans don't really "get" intuitively like a LABEL name can provide.

Thank U very much. Very very good & helpful. This information helps me and others. :P

---

### Post by GhX6GZMB on 2021-09-19
Open a Terminal (Ctrl+Alt+T) and issue the command lsblk.
Show us the output.

---

### Post by TheFu on 2021-09-19
> **ml9104 said:**
> Open a Terminal (Ctrl+Alt+T) and issue the command lsblk.
Show us the output.

Yes, PLEASE.  Text only. Not an image.  We can easily use the text to create the exact line(s) you want in the /etc/fstab ... assuming you can't follow the links I've already posted and do it yourself.  This command would be a little better than just a plain **lsblk**.  It tells us specific things.
```
lsblk -e 7 -o name,size,type,fstype,mountpoint,label
```

---

### Post by GhX6GZMB on 2021-09-19
I think I understand the problem now. aabedii is caught in a DOS/Windows mindset loop.
Trying to explore disks in the file manager (in this case, PCManFM-Qt) makes no sense at all. I get exactly the same error messages when trying to do the same.

@aabedii: there are NO C: or D: or ... drives in UNIX/Linux systems, there is only a directory/file tree.
Disks are called sda, sdb, sdc etc. and you can't access those directly. Partitions are called sda1, sda2, sda3... or sdb1, sdb2... and those can also not be accessed directly.
Those partitions are "mounted" under different directories, meaning that they are storage for those directories (with subdirectories).

The lsblk command will show you where your storage is mounted/allocated.
Here's an example from my very simple laptop:
```
macro@macro-pc:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223,6G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0 188,3G  0 part /home
&#9492;&#9472;sda3   8:3    0     6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom
```  

But what is the file manager you're using? It looks a bit like PCManFM-Qt, but it's not. More like some strange ripoff.

---

