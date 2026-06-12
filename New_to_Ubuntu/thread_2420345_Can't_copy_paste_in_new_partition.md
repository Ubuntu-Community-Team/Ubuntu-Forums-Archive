---
title: "Can't copy paste in new partition"
date: 2019-06-03
forum: New to Ubuntu
---

### Post by yneopany on 2019-06-03
Having Ubuntu 18.04 and partitioned using gparted but can't copy anything in it... Need help

---

### Post by Bashing-om on 2019-06-03
yneopany - hello -

Give us some things to work with :)

What are the file systems ?
How did you make up the new partition ?
How are you mounting the new file system ? - How do you want to mount it ?
What directories did you create ?
"WHO" owns these directories and files ?

These commands will be instructive:
```

sudo parted -l
mount

```
once we know what you have done, we can advise on what can be done to attain what you want done.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by yneopany on 2019-06-05
I actually used gparted to do the partitions, I used as ext4 as new partition which caused the problem. Later i did it with ntfs and the problem is solved.. but I get one pop up Everytime I log in the PC . Error stating some problem has been occurred please report

---

### Post by Dennis N on 2019-06-05
That's a problem when initially creating new ext4 file systems on partitions. gparted will only create ext4 file systems owned by root. The standard set up is that only the owner has both read and write permission for files. If its for your data storage, you need to change the owner of the mount point (root folder of the new file system) to your user. If you plan to install an OS on it, leave it alone and the installer will set the owners and permissions of files correctly.

if your user name is joe and mount point is /mnt/data
```
sudo chown -R joe:joe /mnt/data
```

NTFS is a windows file system (NT filesystem). You can't install Linux on that, even though Linux can read and write to it.

---

### Post by oldfred on 2019-06-05
You should only use NTFS if you have Windows or at least a Windows repair disk. 
It will eventually require chkdsk & defrag and you cannot do that from Ubuntu.

I set ownership & permissions. Sometimes I redo them as I (incorrectly) use root to save a file in /home or my data partition).

You can manually mount the partition, set ownership & permissions. If internal drive you will want to add to fstab (umount if manually mounted already).
 sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab 

Details on fstab entry:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by yancek on 2019-06-05
A general user will usually not have write permissions outside his/her /home/user directory so this is expected behavior and the solution is explained in post 4 above.
Curious as to why you would create an ntfs partition if you are using Linux Ubuntu.  Do you have another OS (windows) and did you have the failure to copy from Ubuntu or windows?

---

### Post by yneopany on 2019-06-06
[COLOR=#000000][[COLOR=#000000]Dennis N[/COLOR]]("https://ubuntuforums.org/member.php?u=321222") [/COLOR]
[COLOR=#000000][/COLOR][IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG] i   i have installed ubuntu only i dnt have any other OS installed.. 
[COLOR=#000000][[COLOR=#000000]yancek[/COLOR]]("https://ubuntuforums.org/member.php?u=1928724") [/COLOR]
[COLOR=#000000][/COLOR][IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]   No actually i did partitions by ext4 but since i could not read nor write anything in it so i was bound to make it in ntfs and added my personal data in it... now if i back it up those files and re do the partitions and need to get permission for read write, what steps should i follow...

---

### Post by drv9977 on 2019-06-06
have you checked for folder permissions???

---

### Post by yancek on 2019-06-06
Before giving detailed instructions, we would need detailed information on your system/partitions from gparted/fdisk/gdisk.  Generally, you would simply create the partition, create a mount point and change ownership on the mount point to the user and/or group you want to access it.

---

