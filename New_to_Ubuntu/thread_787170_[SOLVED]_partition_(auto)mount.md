---
title: "[SOLVED] partition (auto)mount"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Sain on 2008-05-08
I don't know is it just me, or KDE or whatever, but I never seem to get partition mounting properly under kubuntu...

Anyway, I have Kubuntu and Windows on my machine, each on its own partition. And I also have shared Fat partition on which I keep most documents.... 

Basically it mounts ok, but I need to explicitly click on icon for partition to mount. Can't it automount at computer start?? Cause now Amarok can't access my song library before I click on partition, and wallpaper at startup won't load because it's on that shared partition...

Before you ask; heres output of some commands...

```
sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d9e98b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5354    43005942    7  HPFS/NTFS
/dev/sda2            6631        6723      747022+  82  Linux swap / Solaris
/dev/sda3            6724       14593    63215775    c  W95 FAT32 (LBA)
/dev/sda4            5355        6630    10249470   83  Linux

Partition table entries are not in disk order

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=3afa7527-90b6-44fc-b259-53f03b7be30c / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
# /dev/sda3
# /dev/sda2
UUID=4d0caa74-84ca-11dc-8235-a1976958ae8d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
```

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun               1014M  156K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   48K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   38M  977M   4% /lib/modules/2.6.24-16-generic/volatile
/dev/sda3              61G   55G  6.1G  90% /media/DOCS
```

It shouldn't be too hard, right? :)

---

### Post by gkrules on 2008-05-08
first type this in in the terminal
```
gksudo gedit /etc/fstab
```
at the bottom add this
```
/dev/sda3 /media/[put wat u want the drive to be called here w/o parenthesese] vfat defaults 0 0
```

oh and if u ever want another drive to automount thats fat32...just change the sda3 to watever...like if its sda5 jus change it to sda5

---

### Post by quelx on 2008-05-08
Try these steps

```

sudo vol_id /dev/sda3
sudo mkdir /mnt/windows

```
copy the UUID string and paste it into a new line in /etc/fstab
```
sudo nano -w /etc/fstab
```
make the line look something like this
```
UUID=pasteth-eout-****-fvol-_idhereokay? /mnt/windows vfat user,auto,rw 0 0

```
ctrl-x to save and exit
do this (next reboot it will automount)
```
sudo mount /mnt/windows
```
you will need to point amarok and whatever other apps use that partition to /mnt/windows

---

### Post by Sain on 2008-05-09
Both solutions worked for my problem, but now I cannot write to the partition... :-/

EDIT: To be precise, I can! But only if I open it as Root.

---

### Post by gkrules on 2008-05-09
yea its because of ubuntu's priveleges 
theres prolly a way to bypass it but im not sure 
i hav a ntfs data partition and im using a program that automatically mounts and allows me to write to it

---

### Post by Sain on 2008-05-12
I've used these attributes in fstab for my partition 

```
vfat owner,auto,uid=1000,gid=100,async,rw 0 0
```

Now it works fine. I guess you just need to play with fstab until you get it right.

---

### Post by axor1337 on 2008-05-12
my advise is to create a backup of all data on shared partition and re format it as ntfs (may need to be done from windoze) then from ubuntu load ntfs support from add/remove and load data back.  the ntfs support tool has a easy gui tool to auto mount the ntfs part. had both hardy and gutsy work really well with ntfs  as does widoze.

---

