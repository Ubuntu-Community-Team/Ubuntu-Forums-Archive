---
title: "Low disk space warning in wubi install / converting to full install"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by brctad on 2013-03-21
Hello,

Currently I am dual booting Win7 and 12.10.
 I installed Ubuntu on a 25g partition I created yet a “Low Disk Space” warning has been appearing.
After some research I have learned this may be due to the limitations of a Wubi install.
```
/dev/loop0      9.4G  8.5G  415M  96% /
```
 How can I correct this?

Should I uninstall from Windows and install fully on the 25g partition?

Is 25g large enough for regular use of Ubuntu?

Can it be done without losing all my customizations and apps (reset from backup)? 


Thanks

---

### Post by ibjsb4 on 2013-03-21
I have not ran wubi, but found what looks to be a fairly easy process to migrate your wubi to a partition.  Give you something to read while you wait for a wubi expert to come along :)

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=migrate+move+wubi+to+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=migrate+move+wubi+to+partition&sa=Search&cof=FORID:9)

A 25G partition is ok.  It really depends on what your planing on running and storing on it.

---

### Post by Impavidus on 2013-03-21
You may have wubi installed on a 25GB ntfs partition, but Ubuntu doesn't use that 25GB partition. Instead, it uses a 9.4GB virtual ext4 (or ext3) partition existing as a file in that 25GB ntfs partition. You can resize wubi to make more use of the 25GB partition (for which there wasn't really much need to create it, but since it's there it's easier to just leave it until you decide to do a full install).

Wubi resize instructions can be found here: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)
If you want to migrate to a full installation read this: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by brctad on 2013-03-21
Thanks **ibjsb4** and **Impavidus**.

It looks like [ResizeWubiDisk ]("https://help.ubuntu.com/community/ResizeWubiDisk")is what I need.

My question now is how do I know the correct NTFS partition to mount?

---

### Post by Impavidus on 2013-03-21
Find the one that's 25GB. The commands **df**, **sudo fdisk -l** or **sudo parted -l** may be useful. Don't worry, if you get the wrong one the commands will just complain they can't find the root.disk file, so you can unmount the partition and try another one.

---

### Post by Mark Phelps on 2013-03-21
One of the key reasons for using Wubi in the first place is to avoid partitioning -- as that can corrupt your filesystem if not done correctly, rendering your PC unbootable in the process.

You've already done that -- by creating the 25GB partition.

Wubi was not intended for long-term installations, hence the 30GB size limit.  If you're really intending to use Ubuntu for the long haul, I would do the following:
1) As long as the NTFS partition is NOT the Windows OS partition, then erase it
2) In place of the previous NTFS partition, use the Ubuntu LiveCD to create an extended partition'
3) Inside the extended partition, create two Linux partitions, both Logical, one for the root file system the other for swap
4) Once that is done, boot from the Ubuntu installer media and, using Something Else, install Ubuntu to the partitions you just created.

And, just in case you're tempted to shrink the Win7 OS partition to leave more room for Ubuntu, do NOT, repeat NOT, use GParted or the Ubuntu installer to do that. Instead, use only the Win7 Didk Management tool to do that.  Using Linux partitioning tools to resize Win7 partitions is asking for trouble.

---

### Post by bcbc on 2013-03-21
You can find the /host partition by entering the following while the Wubi install is booted:
```
df -h
```
At the bottom you'll see something like:
```
bcbc@14:10:50:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0        15G   12G  2.3G  84% /
...
/dev/sda3        25G   15G  10.0G  65% /host
```

That shows the /host partition as /dev/sda3.

There are lots of ways to clean up space. Removing old kernels, browser cache, downloads etc. Here are some...[http://askubuntu.com/a/107476/14916](http://askubuntu.com/a/107476/14916)

---

### Post by brctad on 2013-03-25
Mission accomplished.
Thanks all!

---

