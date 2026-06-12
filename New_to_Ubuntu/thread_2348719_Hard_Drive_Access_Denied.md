---
title: "Hard Drive Access Denied"
date: 2017-01-06
forum: New to Ubuntu
---

### Post by soumyarupchoudhury on 2017-01-06
I have 4 partitions on my hard disk. While one of them is root the other 3 are for data backup and storing. But whenever I try to paste or move any file or folder it says access denied and the paste option is grayed out. Is it something to do with ownership or permission. The three partitions are of XFS format. How do I solve this problem ?

---

### Post by yancek on 2017-01-06
You would generally need to use root (prefix the copy command with sudo) to write anywhere outside your /home/username directory.  You could also change the ownership on the 
mount point directory to your user with the 'chown' command.

---

### Post by ajgreeny on 2017-01-06
If this is a single user machine you can just change ownership of the 3 partitions' mountpoints to your own username and group with ```
sudo chown -R *username:username* mountpoint
``` which will make you, as user, owner of all three mountpoints and should give you read/write permissions to the partitions mounted by /etc/fstab at those folders.

I assume you have all three partitions mounted by /etc/fstab to ensure thay are always named and mounted correctly to the same named folder?

---

### Post by soumyarupchoudhury on 2017-01-07
What is the significance of 'mountpoint' in the command. How do I take ownership of my hard drive partitions. Is there any command to do it ?

---

### Post by leunam12 on 2017-01-07
The mount point is the directory where a partition is mounted Open the terminal and type lsblk and press enter and you will see the mountpoints```
sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0 831.5G  0 part /media/rivasdom/Rivas2
&#9492;&#9472;sdb2   8:18   0   100G  0 part 

```

In the example above (it's not the whole output of lsblk, just a fragment) it shows that the second drive in my machine is sdb and it has two partitions; one is mounted and the other one is not. The mount point for sdb1 is /media/rivasdom/Rivas2

---

### Post by ajgreeny on 2017-01-07
[COLOR="#FF0000"]What is the significance of 'mountpoint' in the command?[/COLOR]
The partitions on the drive will all have mountpoints (a folder in the filesystem somewhere) once mounted, and you can make sure they always mount to the same folder by adding a line to the /etc/fstab file.
[COLOR="#FF0000"]How do I take ownership of my hard drive partitions. Is there any command to do it ? [/COLOR]
Exactly as I showed in my last post.
Figure out the mountpoint you want for each partition then add a line for each to /etc/fstab to mount them at boot at those chosen folders.
I have no idea what you wish their mountpoints to be, so will have to leave you to sort that out, but usually partitions on internal disks are mounted in a subfolder of /mnt, so you may, for example, create three folders with command ```
sudo mkdir /mnt/data1 /mnt/data2 /mnt/data3
```
Now you will need to add 3 lines to /etc/fstab as root in the format ```
UUID=66E53AEC54455DB2 /mnt/data1 xfs defaults 0 1
``` but changing the **/mnt/data1** to the appropriate number each time.
You are advised to use the UUID, not /dev/sda naming as that is always poen to changes depending on the order partitions mount in the boot process.
You can find UUIDs of all partitions from command ```
sudo blkid -c /dev/null
```
Finally you need to change ownership of each mountpoint with ```
sudo chown -R *username:username* /mnt/data1
```

---

### Post by soumyarupchoudhury on 2017-01-07
Thank You, I get it now.

---

