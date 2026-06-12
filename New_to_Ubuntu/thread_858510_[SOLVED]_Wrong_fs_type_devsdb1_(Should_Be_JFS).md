---
title: "[SOLVED] Wrong fs type /dev/sdb1 (Should Be JFS)"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Thee_Baron_ on 2008-07-13
Hello, so I switched my 'data only' drives to JFS. I had to shut my computer down by holding the power off button (it froze when running a screensaver) Now both the drives say this messege in both GParted & PYSDM:
> wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail  or so

Here is my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                                            0  0  
# /dev/sda3
UUID=d885babf-67be-4c9d-8a82-e107dc6dd02a  /                 ext3         relatime,errors=remount-ro                          0  1  
# /dev/sda2
UUID=40abc48d-d27b-4d6a-9829-fe1fc063c740  none              swap         sw                                                  0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8                               0  0  
/dev/fd0                                   /media/floppy0    auto         rw,user,noauto,exec,utf8                            0  0  
/dev/sda1                                  /media/Windows    ntfs         mount,-t,ntfs-3g,/dev/sda1,/media/Windows,-o,force  0  0  
/dev/sda2                                  /media/sda2       swap         defaults                                            0  0  
/dev/sda3                                  /media/sda3       ext3         defaults                                            0  0  
/dev/sdb1                                  /media/Storage    jfs          defaults                                            0  0  
/dev/sdc1                                  /media/Downloads  jfs          defaults                                            0  0
I dont have a clue what to do and cant loose the information on them!

Please help
Thanks.

---

### Post by MDSmith2 on 2008-07-13
Was the partitioner still running when you shut it down?
If not, then sudo apt-get install jfsutils might help

---

### Post by Thee_Baron_ on 2008-07-13
I dont think I had the GParted or PYSDM running
Sadly didnt work because jfsutils is installed

Thanks

---

### Post by logos34 on 2008-07-13
it's not enough to simply install jfsutils--you need to run the jfs fs checker that's included :

sudo jfs_fsck /dev/sdb1

---

### Post by MDSmith2 on 2008-07-13
does your other (/dev/sdc1 i think) work?

---

### Post by Thee_Baron_ on 2008-07-13
jfs_fsck worked! Thanks :)

---

### Post by logos34 on 2008-07-13
ok, great.  mark thread as 'solved' (>thread tools)

enjoy

---

### Post by MDSmith2 on 2008-07-13
congrats.:)

---

### Post by coodtec on 2009-07-17
> **logos34 said:**
> it's not enough to simply install jfsutils--you need to run the jfs fs checker that's included :

sudo jfs_fsck /dev/sdb1


I got same problem with JFS, after force shutdown ubuntu by power off.


[COLOR="Red"][SIZE="4"]
sudo jfs_fsck /dev/sdb1

sudo mount -a[/SIZE][/COLOR]

This is key :P

---

