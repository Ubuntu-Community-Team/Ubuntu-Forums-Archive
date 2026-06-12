---
title: "not able to write to 2nd hard drive after install(solved)"
date: 2021-05-16
forum: New to Ubuntu
---

### Post by franklin1k on 2021-05-16
So, I bought a new computer.  Decided to turn my old computer into a Ubuntu lxqt box.  It installed on the first HD.  I partitioned the second HD.  Mounted it.  Can not write to it.  I suspect that it is a permission thing.  
The googling gives me eight different ways to do this, and I did them all wrong!

help!

---

### Post by ajgreeny on 2021-05-16
Assuming the second disk is ext4 filesystem and is for data files only, create a mountpoint folder for it, eg ```
sudo mkdir /mnt/data
``` though you can name it whatever you wish.

Now find the UUID of the partition with ```
sudo blkid -c /dev/null
``` edit **/etc/fstab** with command ```
sudoedit /etc/fstab
``` by adding a couple of lines for the data partition using the UUID you have just found, eg 
```
# Data partition
UUID=2a1a9b57-4d0a-4570-974f-d6114fb25ef1 /mnt/data			ext4	defaults,noatime	0	1
```
You can check all is OK with command ```
sudo mount -a
``` and if no errors show the partition will be mounted at /mnt/data at boot from then on.

Finally you need to change ownership of the mountpoint of that partition to you as user with command ```
sudo chown -R $USER:$USER /mnt/data
``` following which you should be able to write to that partition as user.

---

### Post by Impavidus on 2021-05-16
Best to mount it automatically at boot time using the fstab config file: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Also best to use a native Linux filesystem on it, like ext4.

---

### Post by franklin1k on 2021-05-16
thanks
it worked

---

### Post by ajgreeny on 2021-05-16
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

