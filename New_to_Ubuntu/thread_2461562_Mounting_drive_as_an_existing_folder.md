---
title: "Mounting drive as an existing folder"
date: 2021-05-03
forum: New to Ubuntu
---

### Post by greg00pl on 2021-05-03
Hi. I need to mount new drive, because i'm out of free space... How can i do that? I need to mount new drive as /var (most of space on my current drive). Do i need to copy whole /var content and mount it using fstab or what?
Sorry my english isnt very good, and its problematic for me to write what do i need, but i fully understand your answers. 

My primary drive is using zfs (sda), secondary drive is empty. Is it possible to use zfs on it ? 
Regards P.

---

### Post by ActionParsnip on 2021-05-03
Add an entry in fstab. You may want to rsync the current files over to the new file system but I believe if you just mount it as /var the folders will be made. You can always comment out the line in fstab and re-reboot

---

### Post by CatKiller on 2021-05-03
> **greg00pl said:**
> I need to mount new drive as /var (most of space on my current drive). 
Just as an alternative to consider: is your /var really big because of something that you want, or is your /var really big because a log file has grown out of control? Every now and then some application can sometimes spam the log files, which makes them really big. Worth a look, I'd say.

---

### Post by scorp123 on 2021-05-03
> **greg00pl said:**
>  My primary drive is using zfs (sda) 

Also take a look at ZFS snapshots. Do you have many of those?
```
sudo zfs list -r -t snapshot -o creation,space -s creation
```

If left unchecked then these snapshots can take up lots of space over time.

You can also filter above command and just scan for entries regarding "/var" :
```
sudo zfs list -r -t snapshot -o creation,space -s creation | grep "/var"
```

If I do that on my system I get:
```
> sudo zfs list -r -t snapshot -o creation,space -s creation rpool | grep "/var"

Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var@FreshInstall_WorkingOK_20210301                          -     0B         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/games@FreshInstall_WorkingOK_20210301                    -     0B         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/lib@FreshInstall_WorkingOK_20210301                      -   120K         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/log@FreshInstall_WorkingOK_20210301                      -  2.23M         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/mail@FreshInstall_WorkingOK_20210301                     -     0B         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/AccountsService@FreshInstall_WorkingOK_20210301      -     0B         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/NetworkManager@FreshInstall_WorkingOK_20210301       -    96K         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/apt@FreshInstall_WorkingOK_20210301                  -    56K         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/dpkg@FreshInstall_WorkingOK_20210301                 -     0B         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/snap@FreshInstall_WorkingOK_20210301                     -     0B         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/spool@FreshInstall_WorkingOK_20210301                    -     0B         -       -              -          -
Tue Mar  2  7:18 2021  rpool/ROOT/ubuntu_r07xkn/var/www@FreshInstall_WorkingOK_20210301                      -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var@DataPool_Imported-OK                                     -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/games@DataPool_Imported-OK                               -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/lib@DataPool_Imported-OK                                 -   120K         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/AccountsService@DataPool_Imported-OK                 -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/NetworkManager@DataPool_Imported-OK                  -    96K         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/apt@DataPool_Imported-OK                             -    56K         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/dpkg@DataPool_Imported-OK                            -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/log@DataPool_Imported-OK                                 -  2.31M         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/mail@DataPool_Imported-OK                                -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/snap@DataPool_Imported-OK                                -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/spool@DataPool_Imported-OK                               -     0B         -       -              -          -
Tue Mar  2  7:32 2021  rpool/ROOT/ubuntu_r07xkn/var/www@DataPool_Imported-OK                                 -     0B         -       -              -          -
...
...
(... super long list of snapshots ...)
...
...
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var@autozsys_9o0cxz                                          -     0B         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/games@autozsys_9o0cxz                                    -     0B         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/lib@autozsys_9o0cxz                                      -  32.9M         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/AccountsService@autozsys_9o0cxz                      -    56K         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/NetworkManager@autozsys_9o0cxz                       -    96K         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/apt@autozsys_9o0cxz                                  -  1.30M         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/dpkg@autozsys_9o0cxz                                 -  1.06M         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/log@autozsys_9o0cxz                                      -  1.39M         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/mail@autozsys_9o0cxz                                     -     0B         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/snap@autozsys_9o0cxz                                     -     8K         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/spool@autozsys_9o0cxz                                    -    88K         -       -              -          -
Thu Apr 29 22:41 2021  rpool/ROOT/ubuntu_r07xkn/var/www@autozsys_9o0cxz                                      -     0B         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var@autozsys_7ir0ta                                          -     0B         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/games@autozsys_7ir0ta                                    -     0B         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/lib@autozsys_7ir0ta                                      -  99.7M         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/AccountsService@autozsys_7ir0ta                      -    56K         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/NetworkManager@autozsys_7ir0ta                       -    96K         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/apt@autozsys_7ir0ta                                  -  5.84M         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/lib/dpkg@autozsys_7ir0ta                                 -  2.89M         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/log@autozsys_7ir0ta                                      -  2.25M         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/mail@autozsys_7ir0ta                                     -     0B         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/snap@autozsys_7ir0ta                                     -    72K         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/spool@autozsys_7ir0ta                                    -    88K         -       -              -          -
Sat May  1 18:01 2021  rpool/ROOT/ubuntu_r07xkn/var/www@autozsys_7ir0ta                                      -     0B         -       -              -          -

```

Cleaning out unneeded ZFS snapshots can help reclaim space.

---

### Post by greg00pl on 2021-05-03
Thanks for answers.
#CatKiller -> my /var its really big, because it will hold many files for samba and www shares (it will be IPTV server / home monitoring, VPN server, private website, cloud storage for my mobiles backup, sama server and domain controller for syncing most important data from my laptops)... for now i'm using only 1,5TB total HDD space, but i'm planning to build RAID 10 of 4 x 2TB HDDs, and use it under ZFS...
#scorp123 -> i have fresh Ubuntu install, so i dont have many snapshots ;) but i found out that under ZFS i can just add drive to a zfs pool... its a very nice option and i think i will use zfs for all my devices [Here]("https://unix.stackexchange.com/questions/530968/adding-disks-to-zfs-pool") is an useful article about zfs functions and usage.
Regards P.

---

### Post by scorp123 on 2021-05-03
> **greg00pl said:**
>  i found out that under ZFS i can just add drive to a zfs pool.. 

Yes, I'd recommend to do that. I've been using ZFS since at least 2007 on good old SUN/Oracle Solaris. The fact that it was ported over to Ubuntu is one of the best things ever, it was the one thing that I felt was missing here.  I just wish other distributions (e.g. Red Hat and its clones) implemented it too.

---

### Post by TheFu on 2021-05-03
> **greg00pl said:**
>  
My primary drive is using zfs (sda), secondary drive is empty. Is it possible to use zfs on it ? 
Regards P.
Yes.  I haven't any clue, but I'd think if you don't care at all abot daa protection, then add the new drive to the zfs pool.
ZFS is "experiential" on Ubuntu for the OS, but you know that already.

---

### Post by greg00pl on 2021-05-04
> **TheFu said:**
> Yes.  I haven't any clue, but I'd think if you don't care at all abot daa protection, then add the new drive to the zfs pool.
ZFS is "experiential" on Ubuntu for the OS, but you know that already.

ZFS as i  read is much safer file system than ext or ntfs... its new on ubuntu, yes, but even when ubuntu crash my data will be intact 
ZFS seems to be much comfortable to use than other file systems especially when drive replace is needed.

The only inconvinence (with ubuntu) is that i cannot add all disks to pool at once during installation...

---

### Post by TheFu on 2021-05-04
> **greg00pl said:**
> ZFS as i  read is much safer file system than ext or ntfs... its new on ubuntu, yes, but even when ubuntu crash my data will be intact 
ZFS seems to be much comfortable to use than other file systems especially when drive replace is needed.

The only inconvinence (with ubuntu) is that i cannot add all disks to pool at once during installation...

ZFS should be safer, but like a hammer isn't safe in the hands of everyone, neither is ZFS. Don't have a false sense of extra security.  ZFS validates that data sent to the storage is actually placed onto the storage, but if you don't use ECC RAM and don't build the storage with redundancy - RAIDz or RAIDz2 or at least mirroring, then there is little that ZFS can do above what EXT4 can accomplish.  

ZFS, ext4, NTFS are all "journaled" file systems. This means that writes are atomic and if there is a failure, the current write in progress can be rolled forward or back, as needed.  In the last 20 yrs, most new file systems are journaled in that way. The exceptions are flash-based file systems - so exFAT, FAT32 aren't journaled to avoid the extra writes.

ZFS includes a volume manager. This is lacking in all the other file systems except btrfs, so if you want a volume manager too, then LVM needs to be part of the storage architecture.  LVM+ext4  or LVM+xfs are the typical enterprise storage stacks used when ZFS isn't.  

ZFS use for data on Ubuntu is a great idea when you have sufficient disks to support RAIDz or RAIDz2. No question about that and only for data. It is further improved if the system has (and actually uses) ECC RAM.  Some motherboards support ECC RAM, but don't actually make use of the parity checks.  All storage systems benefit from working ECC RAM, not just ZFS.

So let me google how to add a HDD to a storage pool on ZFS.
[https://ubuntu.com/tutorials/setup-zfs-storage-pool](https://ubuntu.com/tutorials/setup-zfs-storage-pool) - much too basic to be useful.
[https://wiki.ubuntu.com/ZFS/ZPool](https://wiki.ubuntu.com/ZFS/ZPool) - all the examples are for mirrored or RAIDz1/2 setups.
[https://unix.stackexchange.com/questions/530968/adding-disks-to-zfs-pool](https://unix.stackexchange.com/questions/530968/adding-disks-to-zfs-pool) - uses the **zpool add** command. This is effectively like using LVM to concatenate storage into a VG.  

**WARNING/DANGER:** About 20 yrs ago, I was setting up LVM storage at home and couldn't be bothered to setup RAID or ... backups ... when I got some new HDDS.  I concatenated 2 new HDDs onto existing LVM storage. Great, until it wasn't. One disk failed about 1 yr into use.  At the time, my LVM-fu was weak (clearly), and all the data on the last 2 HDDs added was lost. Gone. Never to be recovered again.

There is no replacement for daily, automatic, versioned, backups.

---

### Post by garye on 2021-05-05
If you are doing this for the time, this is by far the best way to start!

[https://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/](https://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/)

---

### Post by TheFu on 2021-05-06
> **garye said:**
> If you are doing this for the time, this is by far the best way to start!

[https://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/](https://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/)

That guide isn't for zfs and is 11 yrs old. ZFS mounts don't use the fstab.
Suggesting 777 permissions causes repercussions  that many people wouldn't desire.

---

