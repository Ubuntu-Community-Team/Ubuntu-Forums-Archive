---
title: "USB read only on Ubuntu 12.04"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by radwa.raed on 2013-01-01
Hi
I am using the latest Ubuntu version 12.04 on my hp G72. At the beginning, my USB flash memory was working just fine. But now I can not delete/edit/add anything to it. The Paste/delete is deactivated in the window and all the files open with the words "read-only" in parenthesis. On Windows, it works perfectly fine. From Users and Groups, I added the only username "Radwa" to all the available groups and the account type is: administrator. I go back and forth between root and not root, but this problem is not affected by this?

Here are the outputs of some commands suggested in previous threads:


radwa@Radwa-Notebook:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1947844k,nr_inodes=205344,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=782052k,mode=755 0 0
/dev/disk/by-uuid/934daf58-2be9-4541-b8c4-99318321bb30 / ext4 rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/radwa/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
[COLOR="Red"]/dev/sdb1 /media/usb0 vfat [/COLOR]rw,sync,nodev,noexec,noatime,nodiratime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0

[COLOR="red"]I am guessing this red line is my flash memory? but it is rw, not ro?
[/COLOR]

When I am NOT root:

radwa@Radwa-Notebook:~$ mkdir /media/usb0/test
mkdir: cannot create directory `/media/usb0/test': Permission denied

When I am root:
root@Radwa-Notebook:/home/radwa# mkdir /media/usb0/test
it takes a second and then write back an empty line
[email]root@Radwa.Notebo[/email]ok:/home/radwa#

radwa@Radwa-Notebook:~$ ls -l /media/usb0
total 3984
drwxr-xr-x  2 root root   24576 Dec  6 13:30 2012.12.6 Confocals 08alex488 DFFAapc VZV2drfp
-rwxr-xr-x  1 root root  571118 Dec 14 12:34 Data 1.jpg
-rwxr-xr-x  1 root root  225156 Dec 14 12:37 Data 2.jpg
and a list of the rest of data

I appreciate any help and thanks in advance
Radwa

---

### Post by NikTh on 2013-01-01
Hi , 
of course if you are not root , you cannot create anything  inside /media/ folder , because this folder belongs to root. ```
ls  -ld /media/
``` to see it. 

This is a manual mount. Try 
```
sudo mkdir /media/usb0/ 
sudo mount -t vfat /dev/sdb1/ /media/usb0/ -o uid=1000,gid=1000,umask=022
``` 

Thanks

---

### Post by radwa.raed on 2013-01-01
Thanks for the reply. I tried the manual mount as suggested.

root@Radwa-Notebook:/home/radwa# sudo mount -t vfat /dev/sdb1/ /media/usb0 -o uid=1000,gid=1000,unmask=022
mount: /dev/sdb1 already mounted or /media/usb0 busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/usb0

I repeated this too after re-plugging usb flash memory but same results. Please correct me if I am wrong, but as far as I understand, manual mount means using & accessing the files, right? and since it is already mounted, this would mean it is already in use?  

thank you

---

### Post by NikTh on 2013-01-01
Yes , you have to unmount it first. 
```
sudo umount /dev/sdb1
```

---

### Post by radwa.raed on 2013-01-01
That worked perfectly! Thank you very much :) Hopefully I won't have to repeat it every time ubuntu restarts.

So the final solution for anyone else with this, in the following order: This unmounts then manually mounts the drive

```

sudo umount /dev/sdb1
sudo mkdir /media/usb0/ 
sudo mount -t vfat /dev/sdb1/ /media/[COLOR="Red"]usb0[/COLOR]/ -o uid=1000,gid=1000,umask=022
```

Name in red will probably differ for each case.

---

### Post by radwa.raed on 2013-01-11
There is an issue though. Every time I turn on the computer, I have to do this at the terminal. Isn't there a way, to make the flash stick permanently read and write?

---

### Post by Bashing-om on 2013-01-13
radwa.raed; Hi

>  Isn't there a way, to make the flash stick permanently read and write?Solution: edit /etc/fstab file to mount the device on startup. These links for HOW-TO/tutorials :
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

Post back if you encounter difficulties.
[INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

---

