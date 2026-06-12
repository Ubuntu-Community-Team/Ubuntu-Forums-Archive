---
title: "Auto bind a directory to another in startup"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Georgie.Mathews on 2008-09-25
Hello all

Im using Hardy 8.04 LTS Desktop Edition, i set up proftp on our network fine which shares my files from /home/FTP-shared/download.

The folder that i want to share is in /media/disk/Stuff, so what i normally do is type the code 
```

sudo mount -o bind /media/disk/Stuff /home/FTP-shared/download
```

But, this is temporary since after restarting ubuntu, I need to type that command again to bind that directory to the FTP shared directory.

How do i auto bind it in the start of the computer? Another question is how do i automatically mount my ntfs partition to the /media/disk folder, without having to click on Places -> 294.5GB Media to mount it each time i start ubuntu.

Pls help with that, shot.

---

### Post by tonybaqain on 2008-09-25
try this
[LIST]
[*]**sudo -i** or **su -** and enter the password
[*]vim /etc/mtab
[*]enter the folloing code
[*]```
/media/disk/Stuff /home/FTP-shared/download none defaults,bind 0 0 
```
[*]write and quit
[*]mount -a or reboot your pc/laptop
[/LIST]


and have fun :)

---------------------------------------------
if it works for you, please don't forget to mark it as [SOLVED] by changing from thread options up-in-the-page.

---

### Post by Orange_and_Green on 2008-09-25
Hello Georgie,

there is a file in /etc called fstab (= file system table). It contains all the predefined mount points for the system. So, I suppose you could:

1) Make a backup copy of your current fstab (you know, just in case ;))
2) gksu gedit /etc/fstab
3) Add the following line for your autobind:

/media/disk/Stuff /home/FTP-shared/download none bind 0 0

4)For your second question, that depends on where your ntfs is listed under /dev. If you are not sure, please examine (or post) the results of sudo fdisk -l.
Once you have found out, add a corresponding entry to fstab.

Good luck :KS

---

### Post by Orange_and_Green on 2008-09-25
> **tonybaqain said:**
> [*]vim /etc/mtab

Hi tony :)

Are you sure you mean mtab and not fstab? mtab shows the dynamic mount points, dunno if it is 100% safe to modify it... plus are you sure the changes will be carried on to the next bootup?

If mtab is correct too, I apologise for my ignorance and thank you for yet another lesson learned...

Waiting for confirmation on this...

---

### Post by Georgie.Mathews on 2008-09-26
hey guys

Okay will do that, just a question though, will it mount /media/disk/Stuff into /home/FTP-Shared/download even before i click on Places -> 295.8 GB which mounts my ntfs partition into /media/disk?

Ill post the output of sudo fdisk -l when I get home :)

Thanks for the input

---

### Post by Orange_and_Green on 2008-09-26
> **Georgie.Mathews said:**
>  will it mount /media/disk/Stuff into /home/FTP-Shared/download even before i click on Places -> 295.8 GB which mounts my ntfs partition into /media/disk?

Oh I see, /media/disk is the ntfs partition...

Well that depends on fstab. If in fstab there is a line mounting the ntfs partition to /media/disk BEFORE the line with the bind, then it should work. If not, it would try to bind a non-existing location and fail...

If I understand you correctly, I think the entries you need to add to fstab are:
```
/dev/{NTFS_PARTITION} /media/disk ntfs defaults,umask=0003,nls=utf8 0 0
/media/disk/Stuff /home/FTP-shared/download none bind 0 0
```

Where {NTFS_PARTITION} is the identifier for your ntfs partition (like sda1, sda2, sdb1 etc. sudo fdisk -l will tell you this information). Please note that -l is the lowercase letter L, not the digit "one".

This will mount with full read/write/execute permissions for root, read only for _everybody else_. If you need to set specific permissions for some users or groups to access and modify the files, you can change umask setting and/or add uid and gid fields. For example, replacing "umask=0003" with "umask=0037, gid=46" will assign the ownership of the directory to the user who mounted it (group 46 is the plugdev group), give read only permissions to the other users in his group, and deny access to everybody else. [Instructions here]("http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#uid.2Cgid:_mount_as_.28user.2Cgroup.29")
[Another very well-made instructions page]("http://my.opera.com/lounge/forums/topic.dml?id=83440")

I am sticking to fstab as tony didn't reply, and this is the usual advice I find on forums (and also what I always do, anyway).

[EDIT]**Note: It's most likely that fstab already contains an entry for your ntfs partition, so you most likely do not need to add it, just to fix the umask/uid/gid thing.**

Good luck :KS

---

### Post by Georgie.Mathews on 2008-10-02
Here is the output of sudo fdisk -l

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17861785

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021       38913   304375522+   f  W95 Ext'd (LBA)
/dev/sda5            1021       36998   288993253+   7  HPFS/NTFS
/dev/sda6           36999       38822    14651248+  83  Linux
/dev/sda7           38823       38913      730926   82  Linux swap / Solaris

```

Here is my fstab (before making changes)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=bddf0bbf-b19f-4247-9374-b071f884d010 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=9aa1ee36-6c6e-43d1-a6ba-9d9947d46203 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

