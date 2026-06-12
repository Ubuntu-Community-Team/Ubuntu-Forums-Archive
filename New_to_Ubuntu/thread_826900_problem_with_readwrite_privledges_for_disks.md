---
title: "problem with read/write privledges for disks"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by ymp on 2008-06-12
I continually run into error messages disallowing me to move folders to or write files to vfat drives on my system.
fstab is below
system is dual ubuntu/winxp, and I must keep some drives in vfat 
I tried changing 'defaults' to 'unmask=000' as advised in some other posts, but that made the drives unreadable
only the ntfs, win system disk is available, but I can't see what is different about it in fstab
also, what do the long strings begining with UUID=..., mean?
assistance appreciated
------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda6
UUID=6bf7d736-789d-4155-b64e-43198ec2c1e7  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda8
UUID=b0004614-7670-40c0-9fce-7113e698c7a0  /home          ext3         relatime                    0  2  
# /dev/sda7
UUID=cd0d92cc-f301-4adc-b93b-06de39129a66  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda9                                  /media/filearc vfat         defaults                    0  0  
/dev/sda10                                 /media/filearc2 vfat        defaults                    0  0  
/dev/sda1                                  /media/winos     ntfs       defaults                    0  1

---

### Post by neurostu on 2008-06-12
have you tried running chown on the disk?  Changing the ownership should give you R/W/X access

---

### Post by NilsE on 2008-06-12
Here is the format for the mount in fstab that works for me for vfat partitions. Might also work for ntfs but I have not tried it.

```
/dev/sdb3   /media/SHARED     vfat  auto,user,sync,exec,uid=1000,gid=1000,umask=007 0 0

just change dev and mountpoint name
```

---

### Post by ymp on 2008-06-13
tried changing fstab to NilsE's settings, this did not change the problem,
unsure how to follow the chown advice, how do I do that? do I only do it once or every time I want to write to the disk? please advise

---

### Post by ymp on 2008-06-13
problem solved
when I changed the mount point to be the same as the /dev name, and used the 'auto,user,sync,exec,uid=1000,gid=1000,umask=007 0 0' permission string it resolved my write and copy problems, strange since I should be able to mount it to any name, anyway, that resolved the problem
thanks for the suggestion

---

