---
title: "Trying to copy files"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by keymoo on 2008-06-08
Hi there,

I have a 500GB drive in one partition (sdb1) which I use for backups, this has filled up so I've purchased and installed another 500Gb drive and put it in my machine. I have created an LVM logical volume on the new drive with the same filesystem (reiserfs) as sdb1 and added 65Gb from another drive I have to the lv. I have mounted the LVM volume as /var/lib/backuppc and mounted the sdb1 drive as /var/lib/backuppc_old.

sdb1 has 465Gb capacity with 30Gb free
the LVM has 530Gb capacity with 530Gb free (before the copy)

So far so good.

I want to copy the files from old to new, so I used the following command:
```
cp -r /var/lib/backuppc_old /var/lib/backuppc
```This took a few hours to run and caused two problems:

[LIST=1]
[*]A directory called backuppc_old was created in the new LVM volume after the copy. i.e. a directory called /var/lib/backuppc/backuppc_old was created. How do I copy the drive over without creating the directory name? I.e. I want all files from backuppc_old but I don't want to create a directory called backuppc_old
[*]The new LVM drive filled up. Why is that? The old drive has less space than the new one!? I don't understand why this happened.
[/LIST]
Any help gratefully received.

---

### Post by kamaji792 on 2008-06-08
try:

```
cp -r /var/lib/backuppc_old/* /var/lib/backuppc
```

er... test is on a small set of files.

---

### Post by keymoo on 2008-06-08
That doesn't work I get:
```
cp: cannot stat '/var/lib/backuppc_old/*': No such file or directory.
```The directory is there:
```
sudo ls /var/lib/backuppc_old 
```shows the files.

---

### Post by kamaji792 on 2008-06-08
Ok.  Had a little play.

The **-r** option is for recusive but only works with directories.

Can't see an easy way of doing what you want.  Sorry :(

---

### Post by keymoo on 2008-06-08
OK, thanks for looking anyway. Do you think I could use something else other than cp? Maybe rsync?

---

### Post by Barrucadu on 2008-06-08
You could use *mv* to move all the files to the new drive, or even just open a file manager and copy them by hand.

---

### Post by isparkes on 2008-06-08
I'm working on someones crappy Vista PC at the moment, so I can't try it. You'll have to check everything I write here, because I can't do anything right now.

"cp" is a tool that can do this for you, but you're going to have to take a couple of things into account:

If you want a real copy, you might want to use "-a", which is meant for creating backups ("archive"), which is equivalent to "cp -dpR", and means "dereference" (deals with links) "preserve" (keeps the timestamps and ownership) and "recursive". Have a look at the man page by typing

```
man cp
```

which is the online documentation for the command.

Also the path where you have the stuff might not really be the right place. Generally anything called "lib" (including the directories below it) are for program libraries. This might lead to the fact that some of the permissions on the files are not what you would expect. If there are problems, it will tell you.

The second point is that if you want to copy the contents of the directory to a new location, but do not want the directory itself, you should make the command look like this:

```
cp -a /var/lib/backuppc_old/* /var/lib/backuppc
```

this means "look inside the directory "/var/lib/backuppc_old" and copy the contents.

Alternatively, other things for doing this are "tar" or "rsync". I find rsync good, but it's a bit difficult to use.

---

### Post by keymoo on 2008-06-08
Thanks, as I'm using Ubuntu Server I don't have a file manager. I did manage to do it however using the file manager in Webmin. :)

---

### Post by keymoo on 2008-06-08
This is driving me mad. When copying files from the 466Gb disk (with 31Gb free)  to a 531Gb empty LVM, I am running out of space. Why is that? Here's my df -h after copying from /var/lib/backuppc_old to /var/lib/backuppc. This is totally baffling. Both filesystems are reiser 3.

```
> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             7.8G  2.5G  5.1G  33% /
varrun                506M  212K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sdc1             466G  436G   31G  94% /var/lib/backuppc_old
/dev/mapper/backupvg-backuplv
                      531G  531G     0 100% /var/lib/backuppc
```Here's my fdisk -l
```
> fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   82  Linux swap / Solaris
/dev/sda2             244        1275     8289540   83  Linux
/dev/sda3            1276        9729    67906755   8e  Linux LVM

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040576

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28a90443

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
```

Does anyone have any idea how I can fix this weird problem? Thanks!! :confused:

---

### Post by keymoo on 2008-06-08
OK, I've looked into this a bit more. Both filesystems are reiser 3.6.19 and the block size of both is 4096 (I presume this is bytes). I did notice however that the Allocation Block Size of the Logical Volume is 4MB. Would that affect anything? Should I change the Allocation Block Size of the Logical Volume to 4096 bytes? I presume this wouldn't be sensible because this is the defaut Allocation Block Size.

---

