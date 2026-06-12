---
title: "USB mounted but I'm not the owner, root is."
date: 2014-03-14
forum: New to Ubuntu
---

### Post by tamcphan94 on 2014-03-14
I just mounted my usb flash drive to use part of linux and I can't drag files or copy files into because I don't have permissions to do so. The owner of is root, how do I take ownership of it?

---

### Post by jussi-konttinen on 2014-03-14
My USB works fine (Ubuntu 12.04.4, *Kingston's DataTraveler* USB Flash). Open two filemanagers and try drag&drop.

---

### Post by tamcphan94 on 2014-03-14
> **jussi-konttinen said:**
> My USB works fine (Ubuntu 12.04.4, *Kingston's DataTraveler* USB Flash). Open two filemanagers and try drag&drop.

hmm? i got ubuntu 13.10 the file owner is root and I have no permission to drag and drop to it.

---

### Post by Habitual on 2014-03-14
plug the device in and open a terminal and type
```
df -hT
```

and
```
sudo blkid
``` feed us the output please.

---

### Post by Dennis N on 2014-03-14
I suspect you formatted the filesystem on the flash drive as ext4. In that case root is initially the owner of the new filesystem. That is normal. Just change the owner of the filesystem to yourself.

---

### Post by ajgreeny on 2014-03-14
> **Dennis N said:**
> I suspect you formatted the filesystem on the flash drive as ext4. In that case root is initially the owner of the new filesystem. That is normal. Just change the owner of the filesystem to yourself.Just to clarify that comment, you need to change ownership of the mountpoint of that USB drive partition; you can not actually change ownership of the filesystem.

To make sure that the USB always mounts in the same folder, give the partition on it a label either with gparted, or if it is really ext4, using ```
sudo tune2fs -L *Label* /dev/sdx#
```

---

### Post by tamcphan94 on 2014-03-14
> **Habitual said:**
> plug the device in and open a terminal and type
```
df -hT
```

and
```
sudo blkid
``` feed us the output please.
user@chrubuntu:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda7      ext4      9.8G  7.7G  1.6G  84% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  929M  4.0K  929M   1% /dev
tmpfs          tmpfs     188M  1.4M  187M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     939M   76K  939M   1% /run/shm
none           tmpfs     100M   24K  100M   1% /run/user
/dev/sdb1      ext4       15G   38M   14G   1% /media/user/3f03d33a-059a-42f8-9549-f9b402914fb0
user@chrubuntu:~$ sudo blkid
[sudo] password for user: 
/dev/sda1: UUID="74d5b644-fd38-438c-85de-5bd58429240b" TYPE="ext4" 
/dev/sda3: LABEL="ROOT-A" SEC_TYPE="ext2" TYPE="ext4" 
/dev/sda5: LABEL="ROOT-A" SEC_TYPE="ext2" TYPE="ext4" 
/dev/sda7: UUID="42760710-6f6e-4dc3-aee3-ba1ce5fe9b8c" TYPE="ext4" 
/dev/sda8: LABEL="OEM" UUID="fec31997-286a-416f-ab11-8eaea00236ce" TYPE="ext4" 
/dev/sda12: SEC_TYPE="msdos" LABEL="EFI-SYSTEM" UUID="9919-A5E7" TYPE="vfat" 
/dev/sdb1: UUID="3f03d33a-059a-42f8-9549-f9b402914fb0" TYPE="ext4" 
user@chrubuntu:~$

---

### Post by tamcphan94 on 2014-03-14
> **ajgreeny said:**
> Just to clarify that comment, you need to change ownership of the mountpoint of that USB drive partition; you can not actually change ownership of the filesystem.

To make sure that the USB always mounts in the same folder, give the partition on it a label either with gparted, or if it is really ext4, using ```
sudo tune2fs -L *Label* /dev/sdx#
```

just tried this, but all it did was change the usb drive name to Label as volume

---

### Post by ajgreeny on 2014-03-14
> **tamcphan94 said:**
> just tried this, but all it did was change the usb drive name to Label as volume
Sorry, I didn't explain that very well.

Run that command again but change the word **label** to something that allows you to know which USB drive it is when you insert it, eg if it's the KINGSTON drive call it KINGSTON or something similar.

The USB will now mount automatically when you insert it to either **/media/KINGSTON** or **/media/user/KINGSTON**, depending on which version of ubuntu you have.  Now run the command ```
sudo chown -R user:user /media/KINGSTON
``` or  ```
sudo chown -R user:user /media/user/KINGSTON
```for the appropriate mountpoint you see, and you should now be able to read and write files to that USB as user instead of only as root.

Alternatively, of course, you could simply re-format the drive as fat32 and get rid of any ownership problems entirely.

---

### Post by Dennis N on 2014-03-14
If

/dev/sdb1 ext4 15G 38M 14G 1% /media/user/3f03d33a-059a-42f8-9549-f9b402914fb0

is the USB drive in question, then

sudo chown x:x /media/user/3f03d33a-059a-42f8-9549-f9b402914fb0

**where x is your user name** will make x the owner and group of this folder (even if you unplug it and plug it in again later), and give you the owner's permissions, including write*, allowing you to save and modify files in there.

*assuming the default permissions rwx for the owner.

---

### Post by vasa1 on 2014-03-14
Very useful thread. Lots to learn!

---

### Post by tamcphan94 on 2014-03-15
> **Dennis N said:**
> If

/dev/sdb1 ext4 15G 38M 14G 1% /media/user/3f03d33a-059a-42f8-9549-f9b402914fb0

is the USB drive in question, then

sudo chown x:x /media/user/3f03d33a-059a-42f8-9549-f9b402914fb0

**where x is your user name** will make x the owner and group of this folder (even if you unplug it and plug it in again later), and give you the owner's permissions, including write*, allowing you to save and modify files in there.

*assuming the default permissions rwx for the owner.

worked! thank you very much!

---

### Post by ajgreeny on 2014-03-15
Just an added quick thought.

If you ever need to use that USB drive on a windows machine you will be unlucky if you keep it formatted as ext4; windows can not read ext4 partitions, or not without some extra software to allow it to do so, and that used not to be very effective in the past; perhaps it is better now.

If you do need to be able to use it in windows, format it again as fat32 (or ntfs) using gparted and all will be well for both OSs.

---

### Post by Opti_Rick on 2014-09-19
Done the above and it works, is it necessary to do every time I plug the pendrive in?

And if so, is there a away around it?

Ta.

---

