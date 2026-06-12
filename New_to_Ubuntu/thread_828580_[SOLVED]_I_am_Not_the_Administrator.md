---
title: "[SOLVED] I am Not the Administrator?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by mgrajeshvkm on 2008-06-13
hi friends,

I am using Ubuntu 8.04,  i am facing a different problem..when i take properties of any folder or drive..it tells that '


"yOU r not the owner and u cannot CHANGE THE PERMISSIONS"

and whenever i place a link to the desktop  it will not work on next restart..i should first open the original file to recoverthe link

plz say why this happend?  on previsos version there was no problem..plz help me!!!


I AM WAINTG FOR YOUR's reply

---

### Post by Joeb454 on 2008-06-13
What folder are you trying to change. By default you'll need root privileges to do anything outside /home

To have a root nautilus session, hit Alt+F2 and enter ```
gksudo nautilus
``` This *should* allow you to edit the properties of files :)

---

### Post by mgrajeshvkm on 2008-06-14
thanx for the reply.

i have created a folder in one of my drive for download data and add a link to it on desktop.  it works and all downloads are go to that folder.   

But when i restart the link will become incative ubuntu tells either cancel or move to trash.  i can relink this by go to that drive and re open the file  just open the original folder on the drive  each time this happens


whats the reason????

as per your direction i entered the root folder and changes the permission  as follows
owner    root
folder access   create and delete files
file access  ----


Group  root
folder access  create and delete files
file access -----

others 
file access  create and delete files
file access----

what should i do?

---

### Post by aysiu on 2008-06-14
So it's a separate drive you're linking to?

Is that drive FAT32 or NTFS?

---

### Post by ChameleonDave on 2008-06-14
Let's make sure that you have the right permissions for your home directory, first of all.

Type this into a terminal:
```

sudo chown -vR **YOURUSERNAME**:**YOURUSERNAME** /home/**YOURUSERNAME**
chmod u+rw -vR /home/**YOURUSERNAME**
```

---

### Post by mgrajeshvkm on 2008-06-14
thanx for the replies

Aysiu,
It is NTFS System

i tried to link a folder from one directory to desktop


ChameleonDave,
i enetered the first line.

ubuntu prompted for password
 and i also changed the me as the owner of the desktop folder in root
chown: cannot access `/home/USERNAME/.gvfs': Permission denied

second line no effect!!!

PLZ HELP

---

### Post by ChameleonDave on 2008-06-14
> **mgrajeshvkm said:**
> thanx for the replies

Aysiu,
It is NTFS System

It is a bad idea to use NTFS with Linux.  NTFS is a Microsoft trade secret.  For interoperability, you ought to use FAT (an old Microsoft filesystem that Linux supports easily) or Ext2/3 (the standard Linux filesystem that Windows can support after you install the drivers).

---

### Post by ChameleonDave on 2008-06-14
> **mgrajeshvkm said:**
> 

chown: cannot access `/home/USERNAME/.gvfs': Permission denied

second line no effect!!!


OK, it had a problem with this special ".gvfs" file, but I imagine that it changed the other files successfully.

It's normal for the line to seem to have no effect.  Messages only come up if there are errors.

To make the command more "talkative", add "-v" to the options.  I've amended my above post to show this.

---

### Post by mgrajeshvkm on 2008-08-03
Any one plz help!!! or say what should be procedure to make me an administrator on next reinstall??


PLZ!!!!!

---

### Post by CatKiller on 2008-08-03
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Xiong Chiamiov on 2008-08-03
> **mgrajeshvkm said:**
> Any one plz help!!! or say what should be procedure to make me an administrator on next reinstall??


PLZ!!!!!
You don't want to run as an administrator (what we call root in the *NIX world) because it is very insecure.  Plus, it gives you all sorts of opportunities to screw something up without meaning to.

I believe there is some confusion as to what exactly you are trying to do.  You have a separate hard drive, yes?  And you are trying to store things on that drive?  And finally, you created some sort of link to it on your desktop?

How did you create the link?  Do you have to remount the hard drive everytime you boot up, or did you edit your /etc/fstab to account for it? (if you don't know, you probably didn't)  Could you please post the output of
```

sudo fdisk -l

```

---

### Post by mgrajeshvkm on 2008-08-03
No.. its not solved...plz say how i can overcome this? and now i cant access any drive using the commands given by the user how can i reset it?

---

### Post by northern lights on 2008-08-03
Can you verify that 'ntfs-3g' is installed? Please post the output of ```
aptitude search ntfs
```

---

### Post by Liolikas on 2008-08-03
This is not problem this is security feature. :lolflag:

---

### Post by t0p on 2008-08-03
> **mgrajeshvkm said:**
> No.. its not solved...plz say how i can overcome this? and now i cant access any drive using the commands given by the user how can i reset it?

Look at the posts people have been leaving here for you!  In particular, Xiong Chiamiov's reply should be useful.

The results of your poll should indicate to you that your problem is easily solveable.

---

### Post by mgrajeshvkm on 2008-08-04
Dear friends..  Thanx for your replies..

I will explain the problem deeply..

The importent problem is when i create a link on desktop from a drive..it will become invalid on the next restart

the procedure for creating a link in my way is.. create a link of a file on the particular disk and copy it to the desktop..it works..


i don't know a single line of command

dear Xiong Chiamiov,

i daven,t a seperate hard disk

the result of the gaven command is,,,,

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46415693

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         892     7164958+  83  Linux
/dev/sda2             893       14595   110069347+   f  W95 Ext'd (LBA)
/dev/sda5             893        2804    15358108+  82  Linux swap / Solaris
/dev/sda6            2805        6628    30716248+   7  HPFS/NTFS
/dev/sda7            6629       10452    30716248+   7  HPFS/NTFS
/dev/sda8           10453       14595    33278616    7  HPFS/NTFS


and northern lights, the result for ur command is


p   libntfs-3g-dev                  - ntfs-3g filesystem in userspace (FUSE) lib
i   libntfs-3g23                    - ntfs-3g filesystem in userspace (FUSE) lib
p   libntfs-dev                     - library that provides common NTFS access f
p   libntfs-gnomevfs                - NTFS GNOME virtual filesystem module      
p   libntfs10                       - library that provides common NTFS access f
i   ntfs-3g                         - read-write NTFS driver for FUSE           
p   ntfs-config                     - Enable/disable write support for any NTFS 
p   ntfsdoc                         - documentation about NTFS partitions format
p   ntfsprogs                       - tools for doing neat things in NTFS partit


i dont know why this happens to me..lucky peoples!!!

plz give me a reply

---

### Post by CatKiller on 2008-08-04
```
cat /etc/fstab
``` might be useful too, to show how you have mounted the other partitions. Putting [CODE] tags around the results when you paste them into your message makes it easier to read.

---

### Post by mgrajeshvkm on 2008-08-04
dear friend this is the result

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f1bb9da5-867c-43c6-98b8-68afe7376fd6 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=aafb78ca-da77-4504-970f-9786e8decb47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by CatKiller on 2008-08-04
So the partitions aren't mounted automatically when you start up - you're mounting them by some other method? So when you reboot, the partitions aren't mounted, and so your links to those partitions make no sense, until you manually re-mount those partitions?

The way I would approach it, since you obviously want to access those partitions regularly, is to have those partitions automatically mounted every time you boot up. /etc/fstab (FileSystem Table) is how you control which partitions get mounted, and where they get mounted to. You can edit this file with ```
gksudo gedit /etc/fstab
``` You would put in lines that correspond to the partitions that you want to mount, where you want to mount them, which filesystem is on each partition, and which options you wish to use.

It's ages since I've edited fstab, but something like this would be what you want. ```
/dev/sda6	    /mnt/sda6/     ntfs-3g     umask=000     0     0
``` Hopefully someone who's done this more recently than I have can tell you if this is correct before you do it. You can (re-)mount all of the partitions in fstab with ```
sudo mount -a
``` Put in an entry for each of the partitions that you want mounted. The second part of the line (/mnt/sda6) tells you where you can find the partition. You can link from there to your Desktop if that's how you find access most convenient, and hopefully the links should continue to work over re-boots.

EDIT: the /mnt/sda6 part can be whatever you want. So if that partition has data on it, you might call it /mnt/data, if it was music, you might call it /mnt/music. These directories need to exist before you can mount anything there. So if you wanted to mount one of your partitions to /mnt/data, you could create that directory with ```
sudo mkdir /mnt/data
```

EDIT 2: If you mount them to /media/whatever rather than /mnt/whatever, you'll automatically get shortcuts on your Desktop. This might be something that you want, rather than making the links yourself.

---

### Post by mgrajeshvkm on 2008-08-05
dear catkiller,
thanx for your reply..

i am purely not familiar with commands

i got a file opened when i typed

gksudo gedit /etc/fstab

and ask for password i ientered it and fot a file..it contains

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f1bb9da5-867c-43c6-98b8-68afe7376fd6 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=aafb78ca-da77-4504-970f-9786e8decb47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


i dont know where i need to change..it only displays the home drive

---

### Post by CatKiller on 2008-08-06
> **mgrajeshvkm said:**
> i got a file opened when i typed

gksudo gedit /etc/fstab

That's right. It opened the file for editing as root, since a normal user doesn't have permission to write to that file.

The results of the *fdisk* command that you ran tells us that you've got 5 [partitions]("http://en.wikipedia.org/wiki/Disk_partition") on that hard drive.

sda1 is the partition that holds all your Ubuntu files. You can tell that because it's [ext2]("http://en.wikipedia.org/wiki/Ext2"), and from your *fstab* we can see that it is [mounted]("http://en.wikipedia.org/wiki/Mount_(computing)") at **/**.

sda5 is your [swap]("http://en.wikipedia.org/wiki/Virtual_memory") partition. We can tell that because it's type is "Linux swap", and it's referenced in your fstab as swap space.

The remaining three partitions - sda6, sda7 and sda8 are all formatted as [NTFS]("http://en.wikipedia.org/wiki/NTFS"). sda6 and sda7 are the same size as each other, and sda8 is slightly larger. Only you know what is on those partitions, and which ones you want to mount when the computer starts up.

Say, for example, that you wanted to mount the sda6 partition so that you could access the files that are on there. You would put a line at the bottom of your /etc/fstab file like the one that I suggested earlier.

The first part of that line, /dev/sda6, determines which **dev**ice it is that you're mounting. If you wanted to mount one of the other partitions, you would put their reference in instead, so /dev/sda7 or /dev/sda8.

The second part of the line, /mnt/sda6, determines where in the filesystem you want that partition to be mounted. This can be wherever is most convenient for you. All that is necessary is that you create a directory with the name that you put in /etc/fstab so that you have somewhere to mount this partition.

If you mount your partition to a directory in /media, you will automatically get a shortcut to that partition on your Desktop. Given that you were making shortcuts on your Desktop anyway, this may be something that you want to do. So you could put /media/sda6, for example. Or, if that partition had a particular purpose, say, data, you could put /media/data instead. It really doesn't matter - it's whatever is most convenient for you that determines where you mount this partition.

The third part of the line, ntfs-3g, tells the *mount* command how that partition is formatted. We already know that these partitions are NTFS, and so you put that in here. ntfs is the older option that didn't let you write to a partition that was formatted as NTFS. ntfs-3g is the newer option that has full read and write support. Since you've said that you interact with these files regularly, you'll probably want to be able to read and write, so you should put ntfs-3g in here.

The fourth part of the line tells mount which options you want to specify when you mount that partition. The option that I gave you specifies that all users should be able to read and write to that partition. There are other options, and if you have a particular type of option in mind, someone will probably be able to tell you how to specify it.

The last part, the two 0s, are to do with how those partitions are checked. You've probably seen the routine disk check every now and then when you start the computer. Since Linux doesn't understand how to check NTFS in this way, it's best to leave these both as 0.

Just put in 1, 2, or 3 new entries at the bottom of your /etc/fstab, one for each of the partitions that you want to mount. Fill in the sections based on how you want to mount each of these partitions. Save the file. Make directories for where you want to mount each of these partitions using the **mkdir** command that I outlined above. Mount all of the partitions that you've decided to mount with the **mount** command that I gave you before.

If there's anything in particular that you aren't sure about just ask, and someone should be able to help you.

---

### Post by mgrajeshvkm on 2008-08-07
dear catkiller,  thanks for the help..but i have some problems

first i typed 

 gksudo gedit /etc/fstab

and it opened fstab

it contains the following as i mentioned earlier

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f1bb9da5-867c-43c6-98b8-68afe7376fd6 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=aafb78ca-da77-4504-970f-9786e8decb47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



i added the following lines at the end

/dev/sda6	    /mnt/sda6/     ntfs-3g     umask=000     0     0
/dev/sda7	    /mnt/sda7/     ntfs-3g     umask=000     0     0
/dev/sda8	    /mnt/sda8/     ntfs-3g     umask=000     0     0

i just need a permement link on the desktop..


is i did anything wrong?i saved and closed...the problem is when i opened my computer all the drives are vanished!!

i got my drives back when i deleted the above lines from the files

what is? 
sudo mount -a

HELP ME!!!!

---

### Post by bodhi.zazen on 2008-08-07
your drives "vanished' because you mounted them in /mnt

Mount them in /media instead.

Also, rather then umask=000 I suggest dmask=027,fmask=137

```
/dev/sda6  /media/sda6/  ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137  0  0
```[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by CatKiller on 2008-08-07
In addition to what bodhi.zazen said, ```
sudo mount -a
``` mounts all of the partitions in fstab.

The drives didn't vanish, as such. When partitions aren't mounted they are represented in the Computer folder of Nautilus as just floating around. They get mounted to default locations if you double-click on them. I'm assuming (since you haven't said) that this is what you were doing before.

When they are mounted, they don't need to be represented so that you can mount them; they are already mounted. Those partitions, and the files they contain, are already integrated into your filesystem tree. You can access them the same as you access any other folder in your computer.

As bodhi.zazen and I have both said, if you mount your partitions in /media you will automatically get shortcuts on your Desktop. If you mount them anywhere else, you'll have to create these shortcuts manually.

Don't forget to create the directories that you want to mount the partitions to.

Read the post that bodhi.zazen linked to. There is lots of information in there.

---

### Post by mgrajeshvkm on 2008-08-07
thanks bodhi.zazen and catkiller..

i just typed as u give me..like
/dev/sda6  /media/sda6/  ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137  0  0
/dev/sda7  /media/sda7/  ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137  0  0
/dev/sda8  /media/sda8/  ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137  0  0

then i can see my drives on my computer...but can't open said

cannot mount volume

then i check details they said

Unprivilaged user can not  mount ntfs block devices using the external FUSE
library, either mount the volume as root or rebuild NTFS-3G with integrated FUSE support and make it setuid root.  please see more information at 
[http://ntfs-3g.org/support.html#unprivilaged](http://ntfs-3g.org/support.html#unprivilaged)

then i typed on terminal
sudo mount -a
then asked for password i entered it and displays the message

fuse: failed to access mountpoint /media/sda6/: No such file or directory
fuse: failed to access mountpoint /media/sda7/: No such file or directory
fuse: failed to access mountpoint /media/sda8/: No such file or directory

what i do next?

---

### Post by bodhi.zazen on 2008-08-07
```
sudo mkdir /media/sda{6,7,8}

sudo mount -a
```

---

### Post by mgrajeshvkm on 2008-08-07
THANX THANX THANX THANX!!!!!

THAnk u all


It Solved my Problem!!!!

---

