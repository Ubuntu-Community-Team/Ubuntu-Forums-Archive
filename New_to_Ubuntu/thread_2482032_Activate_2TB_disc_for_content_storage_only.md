---
title: "Activate 2TB disc for content storage only"
date: 2022-12-16
forum: New to Ubuntu
---

### Post by howz88 on 2022-12-16
I have spent significant time searching for this basic info and could not find it; I hope someone here can help.

The 2TB disc is installed in the computer and shows up in 'Disks'.  It does not show up in 'Files'.

This is not the boot disc.

How do I activate this storage drive?  

How do I format/partition/anything else, to use for Ubuntu content and microsoft content?

Thanks in advance.

---

### Post by TheFu on 2022-12-16
You need to create
a) create a new partition table - use GPT
b) create a partition, sized as you like.  I don't size larger disk file systems beyond what my backup storage can hold
c) create a file system on a partition (probably want to add a unique LABEL at the same time), then 
d) mount that partition somewhere safe using settings in the  /etc/fstab.
e) set the owner of the top directory after mounting to which ever userid you like.  By default, it will be owned by root:root, which is unlikely to be desired.

That's the overview.  'gparted' can do the first 3 items.  'sudoedit /etc/fstab' will let you manually modify the fstab to add a new line with mount information.

There are lots of other options, but because of the question, I'll leave those advanced considerations out and follow the K.I.S.S. method.

If the drive will never be connected MS-Windows directly, use ext4 or any other native Unix file system.  If you don't know, use ext4.  Windows computers can access the storage over the network in many ways, so it is best to have a Unix file system if that's they way the storage will be accessed.  Trust me, you want ext4 for many, many, reasons.

If the computer is dual boot and you're still using MS-Windows, then the best choices is NTFS for the file system. You still need to do all the overview steps and the mount stuff is ugly and chmod/chown will NEVER, EVER, work under linux with NTFS. There are many other drawbacks, like if there is any corruption, then you'll need to use MS-Windows to troubleshoot and correct it.

Since you've asked these questions here - Ubuntu Forums - I'm assuming no MS-Windows, no NTFS, no ugliness.

A mount point is just an empty directory where the file system gets mounted.  While technically, that directly can be anywhere, there are some best practices to avoid problems.  Avoiding problems is what system admins do best, so heed this advice.  
* Don't mount it under any user's HOME directory.  Complications will happen that you want to avoid.
* Don't mount it anywhere that Ubuntu likes to control storage, like where USB flash drives get placed.  Having 2 subsystems screwing around in the same directory area is asking for complications.
* Do mount it somewhere short, say /d/ or /data/ or if you think you'll have more drives added later, you can use something like /d1/ and /d2/ and /d3/ ... you get the idea.

There are multiple ways to specify which file system to be mounted through unique identifiers like a UUID or LABEL.  You may see really, really, really, old guides that say to use /dev/sdb1 (or something like that).  That's a bad idea because the identifier for a disk can change from boot to boot, depending on what storage is connected and the order that the kernel "discovers" the storage.  Complications **will** happen.  I'm a fan of using gparted to place a specific LABEL on the file system, then using a line like this in the /etc/fstab:
```
LABEL=D1    /d1    ext4 nofail,noatime,errors=remount-ro 0 2
```
Simple.  Add a line like that to the bottom of the fstab file.  1 line = 1 mount.  Save the file, and run 
```
sudo mount -a
```
to have the file processed and mount to happen.
Lastly, the owner of the newly mounted storage needs to be set so your user can manage the storage and add directories and files to it.  Run this command, once the mount is there.
```
sudo chown $USER:$USER /d1
```
All this is a 1-time thing.  From this point on, your user had access to the storage and it will be there, already mounted after any reboot.  It doesn't need for you to click on anything. It won't show up as another "disk" or anything like that. It will just be part of the file system.  In your file manager, you can setup a bookmark to it, if you want a button.
From your HOME directory, you can create a symbolic link to make accessing it _slightly_ easier, though 'cd /d1' is pretty damn easy.  Ask if you need help with the command. Symbolic links are powerful.

If there are multiple humans with logins on this system, you might want to create subdirectories for each user in the new storage and setup  the permissions for them to control their areas ... or not.  With NTFS, you can't do that. With normal Unix permissions, it is fairly easy to setup.

I find using UUIDs overly complicated, which is why I've stuck with the "LABEL=" method above.  Much easier for humans, right?

All of this should take under 2 minutes to accomplish, BTW.

---

### Post by howz88 on 2023-01-02
Thanks Fu for the reply.  

I'm a newbie so most of what you stated is over my head.  The disc was already formatted using Windows.  There are 7 partitions and one free space.  

The largest was Partition 3: OS - Basic data partition 450 GB NTFS.  I tried to reduce this size by 50 GB (in case I want to use Windows) using setting in Discs and the got this error message: Error resizing filesystem.  That message won't go away and I can't close Discs.  Any help would be appreciated.

Once that is cleared up, can I divide that in two and have 400 GB in ext4 and 50 GB in NTFS.  BTW, partition 7 is Filesystem (39 GB) in ext4?

I still don't know now to mount.

Do I need gparted if the discs are already partitioned?

---

### Post by oldfred on 2023-01-02
Only use Windows tools on NTFS. It wants chkdsk after any resize.
Also make sure Windows fast start up is off, or it sets hibernation flag locking NTFS in read/only mode from other systems.

Some examples of sharing a data partition. Most are similar.
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by MAFoElffen on 2023-01-03
> **howz88 said:**
> How do I format/partition/anything else, to use for Ubuntu content and microsoft content?

NTFS is my choice of filesystem to share between dualboot OS'es of Windows and Linux on the same machine.

From 2 of your posts, you have a disk installed internally that has 5 existing partions. Your decision to use an existing ntfs partition or to resize one bigger which would require shrinking another, or creating a new prtition formatted as NTFS,  or whatever... Label the one you want to use. I keep it simple, by labeling it how Windows see's it/ For example, something like: "WIN_F".

oldfred gave good advice on changing and partitions in size by using Windows Computer Management > Storage Management.

If you are the sole user on that machine, I find it convenient to mount it inside my home folder...

You need to see and write down how Linux see's you and the partition from these commands:
```

sudo blkid | grep 'TYPE=\"ntfs\"'
id | awk '{print $1 " " $2}'

```
Then from that information, in your terminal type in that information in this format. changing it to the information you got above:
```

DISK="/dev/sdb3"
LABEL="WIN_F"
UID="1000"
GID="1000"

```
Then copy/paste the commands below...
```

mkdir $HOME/$LABEL

sudo echo "/dev/disk/by-uuid/$(blkid -s UUID -o value $DISK) $HOME/$LABEL ntfs defaults,nls=utf8,umask=000,dmask=027,fmask=137,uid=$UID,gid=$GID,windows_names 0 0" >> /etc/fstab
    
sudo mount $HOME/$LABEL
chown -R $USER:$USER $HOME/$LABEL

```
If multiple users, then change the commands to make a folder off from your root, and give it group permissions and group ownership, and change the GID to the gid of the common group...

---

### Post by ActionParsnip on 2023-01-04
What is the output of
```

sudo parted -l; mount

```
Thanks

---

