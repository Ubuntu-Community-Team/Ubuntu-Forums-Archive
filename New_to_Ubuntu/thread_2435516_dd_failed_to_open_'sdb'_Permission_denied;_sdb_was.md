---
title: "dd: failed to open 'sdb': Permission denied; sdb was created using mknod"
date: 2020-01-22
forum: New to Ubuntu
---

### Post by mittachaitu on 2020-01-22
Attached raw disk to machine and it was detected as `/dev/sdb`
 >Output of lsblk
lsblk 
NAME           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda              8:0    0 931.5G  0 disk  
&#9500;&#9472;sda1           8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2           8:2    0 919.1G  0 part  /
&#9492;&#9472;sda3           8:3    0  11.9G  0 part  
  &#9492;&#9472;cryptswap1 253:0    0  11.9G  0 crypt [SWAP]
sdb              8:16   1  58.8G  0 disk

By using above MAJ:MIN numbers created block file using mknod
> sudo mknod sdb b 8 16 -m=660
sai@sai:~/Desktop/pool_disks$ tree
.
&#9500;&#9472;&#9472; a.txt
&#9492;&#9472;&#9472; sdb


0 directories, 2 files
sai@sai:~/Desktop/pool_disks$ ls -l
total 1048588
-rw-r--r-- 1 root root 1073741824 Jan 21 16:22 a.txt
brw-rw---- 1 root root      8, 16 Jan 22 10:49 sdb

Now, When I tried to run dd on above sdb file I am getting permission denied(Even though I have enough permissions)

> sudo dd if=a.txt of=sdb bs=1M count=1024
dd: failed to open 'sdb': Permission denied




Thanks in advance!!

---

### Post by sudodus on 2020-01-22
It is better to have and use the block devices where the system is normally storing them.

When you used mknod you were doing something very special. I suggest that you remove that 'sdb'.

Instead, you should use the already existing one in the /dev/ directory: /dev/sdb, which is what lsblk is referring to.

What do you want to do with it?

- Format it as a storage device, which means create partition table with one or more partitions and file system(s) in the partitions?

In this case, what file systems do you want?

- Or do you want to install Ubuntu or an Ubuntu community flavour (Kubuntu, Lubuntu, ... Xubuntu) into the drive 'sdb'?

Edit:

What is the content in the file a.txt ? Do you want to store that file in sdb? In that case I think you should format it as a storage device. If you are running Ubuntu, you can install and use gparted or mkusb for this purpose.

See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick#Postrequisites_-_restore_the_USB_stick).

---

### Post by bernard010 on 2020-01-22
&#9500;&#9472;&#9472; a.txt&#9492;&#9472;cryptswap1 253:0    0  11.9G  0 crypt [SWAP]     Did you first open encrypted swap ? password protected
&#9492;&#9472;&#9472; sdb        <--- Could not open                                         

Which did you partition first cryptswap1 or a.txt ----sdb  ?     
I could be wrong. Would it make a.txt ----sdb a tree off of - cryptswap1 partition ?

---

