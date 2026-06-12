---
title: "[SOLVED] changing permissions"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Stargazer989 on 2008-07-05
ok so, i just installed Xubuntu switching from Ubuntu, Xubuntu didn't auto mount like Ubuntu does, so i had to mount them manually. after i mounted them i took some time to move some files (permissions are fine here) then i partitioned the hard drive so that it'd be only 2 partitions instead of a 40G a 20G and a 14G. now it's composed a 60G and a 14G. the only problem now is that i can't/don't know how to change the permissions for the 60G partition so that i can move files freely.

how do i do it ? i want to make it so that i can freely exchange files in it.

please and thank you

---

### Post by arashiko28 on 2008-07-05
You can see the partition? And access it? If not, try mounting it on computer if you can see it.

---

### Post by Stargazer989 on 2008-07-05
i can see/access the partition but i cannot add/move/delete files

---

### Post by ZabiGG on 2008-07-05
You might need to change owners too. There's this great guide on Psychocats:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I use it ;)

Hope it helps...

Cheers,

Z.

---

### Post by Stargazer989 on 2008-07-05
this is a seperate hard drive:

> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadfcfcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        1267       22061   167034759+   7  HPFS/NTFS
/dev/sda3           22062       30055    64211805   83  Linux
/dev/sda4           30056       30401     2779245    5  Extended
/dev/sda5           30056       30401     2779213+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1854    14892223+   c  W95 FAT32 (LBA)
/dev/sdb2            1855        9729    63255937+  83  Linux

it's the 80GB one

i just need to make it so that i can delete/add files freely
permissions says the Owner is Root

---

### Post by aktiwers on 2008-07-05
```
sudo chmod -R 777 /media/PARTITIONNAME/
```

where partition name is the name of the mountpoint in /media/

You can also change owner like this:
```
sudo chown -R USERNAME:USERNAME /media/partition
```

where username is your Ubuntu username and partition is the name again

---

### Post by ZabiGG on 2008-07-05
You will need to create a directory which will serve as a mount point:

sudo mkdir /80GB

Then, you will have to follow the instructions in the Psychocats guide, but change

/dev/hda5

for 

/dev/sdb

everywhere applicable. 

Also enter the fstab modifications using /dev/sdb instead of /dev/hda

Everything should work without a hitch.

Cheers,

Z.

---

### Post by Stargazer989 on 2008-07-06
Thanks aktiwers it worked just fine :D

---

