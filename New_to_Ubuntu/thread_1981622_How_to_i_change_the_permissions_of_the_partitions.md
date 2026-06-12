---
title: "How to i change the permissions of the partitions?"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by soumoks on 2012-05-17
the permissions of the partitions have changed from read and write, to read only,i don't know how this happened,i used a tool called pysdm to automount partitions on startup,is this the trouble maker or what?when i right click on the partitions and go to permissions,it says i need to have root access to change permissions,i did that by typing "sudo su" in the terminal but it still doesn't let me change the permissions,please someone help..,thanks in advance..:)

---

### Post by coffeecat on 2012-05-17
> **soumoks said:**
> i used a tool called pysdm to automount partitions on startup,is this the trouble maker or what?

Yes. It's an old unmaintained app that can cause problems. I suggest you uninstall it, but that won't fix the problem. We need to see what it's done so that whatever it has done can be fixed. We need some terminal output - sorry! :) Open a terminal and post the output of these commands:

```
sudo fdisk -lu
sudo blkid
mount
cat /etc/fstab
```

You can paste these outputs into your post by highlighting it in the terminal with the mouse, right-click -> copy. Please post the terminal output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

We may need some more information after seeing that, but that will be enough to be going on with.

**EDIT**: also - In case these are NTFS partitions you are having problems with, check in Software Centre or in Synaptic package manager (if you have it installed) that you still have the package ntfs-3g installed. Some people have accidentally uninstalled it, and it is needed for read-write access of NTFS partitions.

And - which version of Ubuntu are you using?

---

### Post by soumoks on 2012-05-17
> **coffeecat said:**
> Yes. It's an old unmaintained app that can cause problems. I suggest you uninstall it, but that won't fix the problem. We need to see what it's done so that whatever it has done can be fixed. We need some terminal output - sorry! :) Open a terminal and post the output of these commands:

```
sudo fdisk -lu
sudo blkid
mount
cat /etc/fstab
```

You can paste these outputs into your post by highlighting it in the terminal with the mouse, right-click -> copy. Please post the terminal output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

We may need some more information after seeing that, but that will be enough to be going on with.

**EDIT**: also - In case these are NTFS partitions you are having problems with, check in Software Centre or in Synaptic package manager (if you have it installed) that you still have the package ntfs-3g installed. Some people have accidentally uninstalled it, and it is needed for read-write access of NTFS partitions.

And - which version of Ubuntu are you using?
First of all i would like to thank u for such a quick reply and your interest in my problem,i am running ubuntu 12.04,i recently installed ubuntu on one of my partitions,was running windows 7 initially,generally they were all NTFS partitions..here is the output i got from the terminal after typing your mentioned command

root@sourabh-desktop:/home/sourabh# sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf37af37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   108551204    54275571    7  HPFS/NTFS/exFAT
/dev/sda2       108551266   976751999   434100367    f  W95 Ext'd (LBA)
/dev/sda5       108551268   397946114   144697423+   7  HPFS/NTFS/exFAT
/dev/sda6       397946178   570107418    86080620+   7  HPFS/NTFS/exFAT
/dev/sda7       687341088   976751999   144705456    7  HPFS/NTFS/exFAT
/dev/sda8       570107904   683429887    56660992   83  Linux
/dev/sda9       683431936   687339519     1953792   82  Linux swap / Solaris

Partition table entries are not in disk order
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# sudo blkid
/dev/sda1: UUID="A28674C486749A8D" TYPE="ntfs" 
/dev/sda5: LABEL="Local Disk" UUID="E63054BD30549681" TYPE="ntfs" 
/dev/sda6: LABEL="Local Disk" UUID="68785A4F785A1C5E" TYPE="ntfs" 
/dev/sda7: UUID="46006A9B006A922B" TYPE="ntfs" 
/dev/sda8: UUID="c2bdc7a3-5681-40db-a1cf-7896cece1333" TYPE="ext4" 
/dev/sda9: UUID="f9a06aee-82ff-44dc-bf5f-9eb00b0dd1bb" TYPE="swap" 
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/sda7 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sourabh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sourabh)
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# cat /etc/fstab
,any ideas?will uninstall that program btw..thanks again..:)

---

### Post by soumoks on 2012-05-17
> **soumoks said:**
> First of all i would like to thank u for such a quick reply and your interest in my problem,i am running ubuntu 12.04,i recently installed ubuntu on one of my partitions,was running windows 7 initially,generally they were all NTFS partitions..here is the output i got from the terminal after typing your mentioned command

root@sourabh-desktop:/home/sourabh# sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf37af37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   108551204    54275571    7  HPFS/NTFS/exFAT
/dev/sda2       108551266   976751999   434100367    f  W95 Ext'd (LBA)
/dev/sda5       108551268   397946114   144697423+   7  HPFS/NTFS/exFAT
/dev/sda6       397946178   570107418    86080620+   7  HPFS/NTFS/exFAT
/dev/sda7       687341088   976751999   144705456    7  HPFS/NTFS/exFAT
/dev/sda8       570107904   683429887    56660992   83  Linux
/dev/sda9       683431936   687339519     1953792   82  Linux swap / Solaris

Partition table entries are not in disk order
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# sudo blkid
/dev/sda1: UUID="A28674C486749A8D" TYPE="ntfs" 
/dev/sda5: LABEL="Local Disk" UUID="E63054BD30549681" TYPE="ntfs" 
/dev/sda6: LABEL="Local Disk" UUID="68785A4F785A1C5E" TYPE="ntfs" 
/dev/sda7: UUID="46006A9B006A922B" TYPE="ntfs" 
/dev/sda8: UUID="c2bdc7a3-5681-40db-a1cf-7896cece1333" TYPE="ext4" 
/dev/sda9: UUID="f9a06aee-82ff-44dc-bf5f-9eb00b0dd1bb" TYPE="swap" 
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/sda7 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sourabh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sourabh)
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# cat /etc/fstab
,any ideas?will uninstall that program btw..thanks again..:)
sorry will paste the output again..

```
root@sourabh-desktop:/home/sourabh# sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf37af37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   108551204    54275571    7  HPFS/NTFS/exFAT
/dev/sda2       108551266   976751999   434100367    f  W95 Ext'd (LBA)
/dev/sda5       108551268   397946114   144697423+   7  HPFS/NTFS/exFAT
/dev/sda6       397946178   570107418    86080620+   7  HPFS/NTFS/exFAT
/dev/sda7       687341088   976751999   144705456    7  HPFS/NTFS/exFAT
/dev/sda8       570107904   683429887    56660992   83  Linux
/dev/sda9       683431936   687339519     1953792   82  Linux swap / Solaris

Partition table entries are not in disk order
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# sudo blkid
/dev/sda1: UUID="A28674C486749A8D" TYPE="ntfs" 
/dev/sda5: LABEL="Local Disk" UUID="E63054BD30549681" TYPE="ntfs" 
/dev/sda6: LABEL="Local Disk" UUID="68785A4F785A1C5E" TYPE="ntfs" 
/dev/sda7: UUID="46006A9B006A922B" TYPE="ntfs" 
/dev/sda8: UUID="c2bdc7a3-5681-40db-a1cf-7896cece1333" TYPE="ext4" 
/dev/sda9: UUID="f9a06aee-82ff-44dc-bf5f-9eb00b0dd1bb" TYPE="swap" 
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/sda7 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sourabh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sourabh)
root@sourabh-desktop:/home/sourabh# 
root@sourabh-desktop:/home/sourabh# cat /etc/fstab

```

---

### Post by Morbius1 on 2012-05-17
There was no output from this command?
```
cat /etc/fstab
```
coffeecat's going to need that to know what to fix.

---

### Post by coffeecat on 2012-05-17
> **soumoks said:**
> ```
root@sourabh-desktop:/home/sourabh# cat /etc/fstab

```


We're missing the output of cat /etc/fstab. By the way, you do not need to run these commands as root. If you are a beginner, it is probably better that you don't. As an aside, I suggest you bookmark this link and read it:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Anyway, to your problem. This:

> **soumoks said:**
> ```
/dev/sda1 on /media/sda1 type fuseblk ([COLOR="Red"]ro[/COLOR],noexec,nosuid,nodev,allow_other,default_permis sions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk ([COLOR="Red"]ro[/COLOR],noexec,nosuid,nodev,allow_other,default_permis sions,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk ([COLOR="Red"]ro[/COLOR],noexec,nosuid,nodev,allow_other,default_permis sions,blksize=4096)
/dev/sda7 on /media/sda7 type fuseblk ([COLOR="Red"]ro[/COLOR],noexec,nosuid,nodev,allow_other,default_permis sions,blksize=4096)
```

Your NTFS partitions are being mounted read-only, so please post the output of cat /etc/fstab. Also - did you check whether or not you have ntfs-3g installed? We need to know this.

Another comment. You have four NTFS partitions mounted, including what might be your Windows 7 boot partition. This seems to be excessive. What are these partitions?

---

### Post by coffeecat on 2012-05-17
> **Morbius1 said:**
> There was no output from this command?
```
cat /etc/fstab
```
coffeecat's going to need that to know what to fix.

@Morbius1, good to see your involvement helping to rescue yet another victim of pysdm. I will value your input as well. :)

---

### Post by soumoks on 2012-05-17
> **coffeecat said:**
> We're missing the output of cat /etc/fstab. By the way, you do not need to run these commands as root. If you are a beginner, it is probably better that you don't. As an aside, I suggest you bookmark this link and read it:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Anyway, to your problem. This:



Your NTFS partitions are being mounted read-only, so please post the output of cat /etc/fstab. Also - did you check whether or not you have ntfs-3g installed? We need to know this.

Another comment. You have four NTFS partitions mounted, including what might be your Windows 7 boot partition. This seems to be excessive. What are these partitions?
i checked ,and i have ntfs-3g installed,about the excessive partitions,that was done by my computer administrator and have never bothered to change it,the output of the above command is as follows,sorry didn't run it the last time..
```
root@sourabh-desktop:/home/sourabh# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid               0  0  
# / was on /dev/sda8 during installation
UUID=c2bdc7a3-5681-40db-a1cf-7896cece1333  /            ext4  errors=remount-ro                 0  1  
# swap was on /dev/sda9 during installation
UUID=f9a06aee-82ff-44dc-bf5f-9eb00b0dd1bb  none         swap  sw                                0  0  
/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sda7                                  /media/sda7  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
root@sourabh-desktop:/home/sourabh# 

```

---

### Post by soumoks on 2012-05-17
> **coffeecat said:**
> We're missing the output of cat /etc/fstab. By the way, you do not need to run these commands as root. If you are a beginner, it is probably better that you don't. As an aside, I suggest you bookmark this link and read it:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Anyway, to your problem. This:



Your NTFS partitions are being mounted read-only, so please post the output of cat /etc/fstab. Also - did you check whether or not you have ntfs-3g installed? We need to know this.

Another comment. You have four NTFS partitions mounted, including what might be your Windows 7 boot partition. This seems to be excessive. What are these partitions?
one partition contains windows,the others i use them for personal data,is it really too much?,i mean i know how to change the no of partitions(in windows) but never did that as i thought it to be risky..

---

### Post by Morbius1 on 2012-05-17
Only Pysdm ( actually that's not true - all of these fstab editors will do things like this ) will do something goofy like this:
>  /dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,ro,users,umask=000  0  0"ro" means mount the partition as read only.
"umask=000" means make it read / write to everyone and your Aunt Tilly.

So which is it Pysdm? As it turns out ro takes priority.

Anyway, go into fstab and remove the ro and the users option so that it looks like this:
>  /dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,umask=000  0  0Then unmount the partition:
```
sudo umount /media/sda5
```And remount it using this command:
```
sudo mount -a
```And stop logging in a root :)

---

### Post by coffeecat on 2012-05-17
@soumoks, only one suggestion to add to Morbius1's good advice. Your sda1 NTFS partition at about 55GB looks as though it is your Windows C: partition (not the system/boot partition as I mistakenly thought before). It's not a good idea to mount your C: partition routinely. Because Ubuntu will show system files that are hidden in Windows, it is all too easy to damage or delete one accidentally from Ubuntu.  My advice would be not to have that partition mounted on every boot, but to mount it on an as-and-when basis from the Nautilus file manager, and then be careful only to read stuff rather than write. You would need to remove the sda1 line completely from /etc/fstab if you want to follow this advice. To edit /etc/fstab, you need to run this from the terminal:

```
gksudo gedit /etc/fstab
```

Do **not** login as root in the terminal with sudo su before doing this! :wink:

> **Morbius1 said:**
> Only Pysdm ( actually that's not true - all of these fstab editors will do things like this ) will do something goofy like this:

Indeed! :)

---

### Post by soumoks on 2012-05-17
> **Morbius1 said:**
> Only Pysdm ( actually that's not true - all of these fstab editors will do things like this ) will do something goofy like this:
"ro" means mount the partition as read only.
"umask=000" means make it read / write to everyone and your Aunt Tilly.

So which is it Pysdm? As it turns out ro takes priority.

Anyway, go into fstab and remove the ro and the users option so that it looks like this:
Then unmount the partition:
```
sudo umount /media/sda5
```And remount it using this command:
```
sudo mount -a
```And stop logging in a root :)
what about the other partitions,u have mentioned only about sd5,do i have to do the same thing to the other partitions as well?sorry but i didn't understand the part of going into fstab and removing the user settings,can u elaborate on that?thanks..

---

### Post by coffeecat on 2012-05-17
> **soumoks said:**
> what about the other partitions,u have mentioned only about sd5,do i have to do the same thing to the other partitions as well?sorry but i didn't understand the part of going into fstab and removing the user settings,can u elaborate on that?thanks..

To edit /etc/fstab, see my previous post. You use this command:

```
gksudo gedit /etc/fstab
```

Simply edit each of the four ntfs line, changing this part:

```
nls=iso8859-1,ro,users,umask=000
```

To this:

```
nls=iso8859-1,umask=000
```

But read my previous post about sda1. I would not routinely mount my C: partition in my system.

---

### Post by soumoks on 2012-05-17
> **coffeecat said:**
> To edit /etc/fstab, see my previous post. You use this command:

```
gksudo gedit /etc/fstab
```

Simply edit each of the four ntfs line, changing this part:

```
nls=iso8859-1,ro,users,umask=000
```

To this:

```
nls=iso8859-1,umask=000
```

But read my previous post about sda1. I would not routinely mount my C: partition in my system.
I did the above,but still not able to copy anything from my home directory to the other partitions,what do i do?

---

### Post by soumoks on 2012-05-17
> **soumoks said:**
> I did the above,but still not able to copy anything from my home directory to the other partitions,what do i do?

sorry for that but does the same thing apply when i unmount using nautilus and mount it again using the same??sorry but am still not too familier with the command line..

---

### Post by coffeecat on 2012-05-17
> **soumoks said:**
> I did the above,but still not able to copy anything from my home directory to the other partitions,what do i do?

Did you follow all of Morbius1's instructions?

> **Morbius1 said:**
> 
Then unmount the partition:
```
sudo umount /media/sda5
```And remount it using this command:
```
sudo mount -a
```And stop logging in a root :)

---

### Post by coffeecat on 2012-05-17
> **soumoks said:**
> sorry for that but does the same thing apply when i unmount using nautilus and mount it again using the same??sorry but am still not too familier with the command line..

You can't unmount with nautilus if it has been mounted through fstab, and if you remount with nautilus you will not be testing the edits you made to fstab. Use the terminal commands.

---

### Post by soumoks on 2012-05-17
> **soumoks said:**
> sorry for that but does the same thing apply when i unmount using nautilus and mount it again using the same??sorry but am still not too familier with the command line..

okay i tried unmounting it from nautilus and didn't work because it needed root access,so unmounted it using the commands u have mentioned,thanks again for that,but when i try to copy anything from home to any other partition,it still says..the partition is read only,now what do i do?

---

### Post by coffeecat on 2012-05-17
> **soumoks said:**
> okay i tried unmounting it from nautilus and didn't work because it needed root access,so unmounted it using the commands u have mentioned,thanks again for that,but when i try to copy anything from home to any other partition,it still says..the partition is read only,now what do i do?

Did you remount it from the terminal?

Post the output of these commands:

```
mount
cat /etc/fstab
```

We need to see what changes you have made to fstab.

---

### Post by coffeecat on 2012-05-17
I think I see what the problem might be. I think you've only unmounted and remounted one partition. You need to unmount all the ntfs partitions and then remount them.

Just reboot - it'll be quicker!

---

### Post by soumoks on 2012-05-17
> **coffeecat said:**
> Did you remount it from the terminal?

Post the output of these commands:

```
mount
cat /etc/fstab
```

We need to see what changes you have made to fstab.actually its solved now,i did the above mentioned changes and rebooted,reboot was required i guess..:p,still i am pasting the file u asked for,thanks a lot again,go ubuntu!!!!

```
sourabh@sourabh-desktop:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /media/sda6 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7 on /media/sda7 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sourabh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sourabh)
sourabh@sourabh-desktop:~$ cat /etc/fstab



```

---

### Post by soumoks on 2012-05-17
> **coffeecat said:**
> I think I see what the problem might be. I think you've only unmounted and remounted one partition. You need to unmount all the ntfs partitions and then remount them.

Just reboot - it'll be quicker!
actually had mounted all partitions,now rebooted and the problem seems to be fixed.Thanks a lot all of u..loving ubuntu more than ever!!!

---

### Post by soumoks on 2012-05-17
Thanks a lot all of u guys who helped me solve my problem,Go ubuntu  and Go opensource,ok guys last question do i change the thread to solved or leave it like that only?,this is my first thread which got so man replies,so damn excited about it!!!

---

### Post by coffeecat on 2012-05-17
> **soumoks said:**
> last question do i change the thread to solved or leave it like that only?

Only you or a member of staff can mark a thread you started as solved. I've done it for you for this thread, but for the future click on Thread Tools near the top of your thread and you'll see "mark this thread as solved" in the choices.

Good luck!

---

### Post by soumoks on 2012-05-17
> **coffeecat said:**
> Only you or a member of staff can mark a thread you started as solved. I've done it for you for this thread, but for the future click on Thread Tools near the top of your thread and you'll see "mark this thread as solved" in the choices.

Good luck!Thanks again..

---

