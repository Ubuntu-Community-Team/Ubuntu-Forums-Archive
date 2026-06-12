---
title: "Shared Hard drive"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Ohwii on 2008-05-26
Hi guys, 

i am using a dual boot with my notebook and I like to access a hard drive with both my OS in this case windows and Ubuntu . 

Well I tried this guide [Here]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=(windows)#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971"), but it does not seem to work. could some help please.

Oh Wii 

Here are some outputs 
df ( It is the /dev/sda5 drive) 
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             42291280   8769228  31373760  22% /
varrun                  517100       104    516996   1% /var/run
varlock                 517100         0    517100   0% /var/lock
udev                    517100        68    517032   1% /dev
devshm                  517100        48    517052   1% /dev/shm
lrm                     517100     36048    481052   7% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1             19727784  16399776   3328008  84% /media/sda1
/dev/sda5              9749944       104   9749840   1% /windows

```

and 

fstab 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=624065ff-0159-46f2-9cb6-5f8437b2ad3c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8684325A84324D45 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=D094-6017  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=10B8-4F6D  /windows        vfat    defaults,utf8,umask=007,gid=46,shortname=mixed,user=user,group=group 0       1
# /dev/sda6
UUID=d412f302-65c5-40d2-9c1d-b35f960b7889 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by shifty_powers on 2008-05-26
just create an ntfs partition. both ubuntu and windows will happily read and write to it ;)

---

### Post by Ohwii on 2008-05-26
cant I just leave it as fat32 and then mount it

---

### Post by sisco311 on 2008-05-26
You can leave it as fat. 
Post the output of:
```
sudo mount -a
```

---

### Post by Duck2006 on 2008-05-26
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Ohwii on 2008-05-26
it gives me this :

```
huy@Huy-08:~$ sudo mount -a
[sudo] password for huy: 
mount: special device /dev/disk/by-uuid/D094-6017 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by cdtech on 2008-05-26
Use fdisk -l instead and remove the UUID numbers and try with the /dev/### also.

Just a thought.....

---

### Post by sisco311 on 2008-05-26
Check the uuid of the partition:
```
sudo blkid /dev/sda5
```
and correct it if it's wrong.

---

### Post by Ohwii on 2008-05-26
in the fstab the uuid is the same 

what else could it be??

---

### Post by cdtech on 2008-05-26
Use fdisk -l to see the filesystem type. Just try and remove the UUID and replace with /dev/sda5 to see if you get the same error.

Special devices are listed in the /dev folder such as the sda, sdb ect...

There is a procedure to create these devices if they don't exsist. First you need a process of elimination.

---

### Post by cdtech on 2008-05-26
> Enter any 11-digit prime number to continue... 

Hey sisco311, could I use a Factorial prime:
87178291199

---

### Post by Ohwii on 2008-05-26
after changing uiid  it gives me
```
huy@Huy-08:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/D094-6017 does not exist
mount: special device /dev/disk/by-uuid/\x2fdev\x2fsda5 does not exist

```

---

### Post by cdtech on 2008-05-26
Ok

---

### Post by Ohwii on 2008-05-26
Is there anything i can do to fix it 

I can now see a drive but i can not access it. what else do have to change

---

