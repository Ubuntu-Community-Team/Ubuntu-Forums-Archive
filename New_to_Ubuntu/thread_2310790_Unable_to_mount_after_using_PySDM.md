---
title: "Unable to mount after using PySDM"
date: 2016-01-21
forum: New to Ubuntu
---

### Post by omar36 on 2016-01-21
Hi Guys, 
I have files that I moved from Ubuntu 12.04 to an external drive to add to a windows 10 environment.  The folders show 0kb in Windows, however back in Ubuntu, they open perfectly.  I found a webpage that showed to use PySDM to change permissions to allow Windows to view it. I followed the instructions and when I went back to attempt to remount the drive, I received the following errors, and now I can't mount the drive. 

Error mounting system-managed device /dev/sdb1: Command-line `mount "/media/omar/OC"' exited with non-zero exit status 1: [mntent]: line 12 in /etc/fstab is bad
mount: can't find /media/omar/OC in /etc/fstab or /etc/mtab

I was hoping you guys could please help me.  
My background with Ubuntu is novice at best. 
Thank you for your time,

---

### Post by sandyd on 2016-01-21
Hi, it seems you have errors in your /etc/fstab configuration.
Can you post the output of
```

cat /etc/fstab
```

---

### Post by omar36 on 2016-01-22
Here you go and thanks for helping.

omar@Ubuntu01:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=abdd2a6d-5861-4762-a207-52e0f7af8e34  /            ext3  errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=d1c77916-3a35-4833-9d97-0132f434fac1  none         swap  sw                 0  0  
/dev/sdb1                                  /media/omar/OC Backup/DC Animated Movies  ntfs  nls=iso8859-1,ro,umask=000,gid=omar,uid=omar  0  0  
/dev/sdb1                                  /media/sdb1  ntfs  defaults           0  0  
omar@Ubuntu01:~$

---

### Post by oldos2er on 2016-01-22
Don't use PySDM; it hasn't been maintained in years.

---

### Post by Morbius1 on 2016-01-23
> /dev/sdb1                                  /media/omar/OC Backup/DC  Animated Movies  ntfs  nls=iso8859-1,ro,umask=000,gid=omar,uid=omar  0  0   
/dev/sdb1                                  /media/sdb1  ntfs  defaults           0  0  

*** You or PySDM are mounting the same partition twice.
*** According the to original error message it can't find the "/media/omar/OC" mount point.
Either you or PySDM didn't create the mount point or one of you didn't realize you can't have spaces for a folder in fstab without an escape like \040.
> /media/omar/OC Backup/DC  Animated Movies
Should be written as:
> /media/omar/OC\040Backup/DC\040Animated\040Movies
*** You are specifying the partition with a /dev/sdb1 instead of a UUID or LABEL.
*** And two of your options are contradictory in one of the mounts:
ro = read only
umask=000 = read/write/execute to everyone.

Not sure what the system would do with that. Since the line in fstab is read from left to right I would guess that "umask=000" takes priority.

---

### Post by omar36 on 2016-01-23
Morbius1, 
Firstly, thanks for the reply, Secondly, pretty bitchin name, Lastly, it was a PySDM issue as I'm still an ubuntu novice.  
Would you be so kind as to guide me through the steps needed to fix this issue. I'm comfortable using Terminal but still have not figured out how to remove the error 
Thank you.

---

### Post by sandyd on 2016-01-23
> **omar36 said:**
> Morbius1, 
Firstly, thanks for the reply, Secondly, pretty bitchin name, Lastly, it was a PySDM issue as I'm still an ubuntu novice.  
Would you be so kind as to guide me through the steps needed to fix this issue. I'm comfortable using Terminal but still have not figured out how to remove the error 
Thank you.

```

sudo nano /etc/fstab

```

The file should look like
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda6 during installation
UUID=abdd2a6d-5861-4762-a207-52e0f7af8e34 / ext3 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=d1c77916-3a35-4833-9d97-0132f434fac1 none swap sw 0 0
[COLOR="#FF0000"]/dev/sdb1 /media/omar/OC Backup/DC Animated Movies ntfs nls=iso8859-1,ro,umask=000,gid=omar,uid=omar 0 0
/dev/sdb1 /media/sdb1 ntfs defaults 0 0 [/COLOR]

```
Carefully remove only the two lines in red.

Press control+x to save.

That should remove the mounts for /dev/sdb1, and we can go on to create new proper mounts.

To do that, post the output of
```

sudo blkid
```

---

### Post by omar36 on 2016-01-23
omar@Ubuntu01:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="52EA7665EA76456F" TYPE="ntfs" 
/dev/sda2: UUID="B02A79352A78FA24" TYPE="ntfs" 
/dev/sda5: UUID="d1c77916-3a35-4833-9d97-0132f434fac1" TYPE="swap" 
/dev/sda6: UUID="abdd2a6d-5861-4762-a207-52e0f7af8e34" TYPE="ext3" 
omar@Ubuntu01:~$

---

### Post by sandyd on 2016-01-24
Run
```

## Make sure that drive is actually unmounted
sudo umount /dev/sdb1
## Set permissions of mount point
chown omar:omar /media/sdb1 
sudo nano /etc/fstab
```

Add the following line on a new line to the file```

UUID=B02A79352A78FA24 /media/sdb1 ntfs uid=omar,gid=omar,dmask=027,fmask=137 0 0
```

The file should now look like this (red line was just added):
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda6 during installation
UUID=abdd2a6d-5861-4762-a207-52e0f7af8e34 / ext3 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=d1c77916-3a35-4833-9d97-0132f434fac1 none swap sw 0 0
[COLOR="#FF0000"]UUID=B02A79352A78FA24 /media/sdb1 ntfs uid=omar,gid=omar,dmask=027,fmask=137 0 0[/COLOR]

```
Press control+x to save.

Then, test the mount:
```

sudo mount -a
```

---

### Post by omar36 on 2016-01-26
Thank you very much for your help, the drive now works.  Now I just need to give the folder the correct permissions to be seen and read in Windows.
Thanks so much!

---

