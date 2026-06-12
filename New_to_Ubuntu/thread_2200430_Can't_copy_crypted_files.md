---
title: "Can't copy crypted files"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by pisolinux on 2014-01-19
Hello, I hope, this is the right section.
I have a crypted home folder in ubuntu, I can see and open the files inside but not move or copy:

```
/tmp/ecryptfs.3cOae97g
``` 
I create the temporary folder
```
ubuntu@ubuntu:~$ cd /media/ubuntu/cfac8af8-6161-488b-878a-371fec35001a
ubuntu@ubuntu:/media/ubuntu/cfac8af8-6161-488b-878a-371fec35001a$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/ubuntu/cfac8af8-6161-488b-878a-371fec35001a/home/.ecryptfs/hp/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [7cc3a0a835d12515] into the user session keyring
INFO: Success!  Private data mounted at [/tmp/ecryptfs.3cOae97g].
ubuntu@ubuntu:/media/ubuntu/cfac8af8-6161-488b-878a-371fec35001a$
```



I can open and enter the folder:
```
/tmp/ecryptfs.3cOae97g
```
Only after giving
Gksu Nautilus
I can see and open the flies, but not move or copy them to other folders.



If I try Iget :
```
Error while copying &#8220;Untitled 1.odt&#8221;.
There was an error copying the file into /media/ubuntu/D43B-2FD8.
Error opening file: Permission denied
```
[IMG]http://i42.tinypic.com/2dm5kle.png[/IMG]
I don't know what to do.

---

### Post by Dave_L on 2014-01-19
Are you trying to copy a file in /tmp/ecryptfs.3cOae97g to another location within that directory?

By default, ecryptfs-recover-private mounts as read-only. There's a parameter --rw to mount as read-write.

> There was an error copying the file into /media/ubuntu/D43B-2FD8.
Error opening file: Permission denied

Is /media/ubuntu/D43B-2FD8 mounted read-write?

If you're not sure, post the output from:

```
mount
```

---

### Post by pisolinux on 2014-01-19
Hello Dave_L,
I'm using ubuntu live, because i cant log in normally.
```
ubuntu@ubuntu:~$ mount /media/ubuntu/D43B-2FD8
mount: according to mtab, /dev/mmcblk0p1 is already mounted on /media/ubuntu/D43B-2FD8
mount failed

```
May this help?
```
ubuntu@ubuntu:/media/ubuntu$ ls -l
total 28
drwx------  1 ubuntu ubuntu 8192 Jan 19 09:44 80D8F0B7D8F0AD12
drwxr-xr-x 23 root   root   4096 Jan 14 00:01 b621f312-cb36-47a7-87ac-8cd577b5b4a8
drwxr-xr-x 25 root   root   4096 Jan 16 11:44 cfac8af8-6161-488b-878a-371fec35001a
drwx------ 21 ubuntu ubuntu 8192 Jan 19 16:57 D43B-2FD8
drwx------  1 ubuntu ubuntu 4096 May  8  2013 WINRE

```
I think that part of the problem is that ```
/dev/sda6
``` is full:
 ```
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.9G   64M  1.9G   4% /
udev            1.9G   12K  1.9G   1% /dev
tmpfs           386M  868K  385M   1% /run
/dev/sr0        785M  785M     0 100% /cdrom
/dev/loop0      738M  738M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           1.9G  1.2M  1.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   80K  1.9G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sda4       304G  296G  8.6G  98% /media/ubuntu/80D8F0B7D8F0AD12
/dev/sda6       239G  239G     0 100% /media/ubuntu/cfac8af8-6161-488b-878a-371fec35001a
```
Thank you

---

### Post by pisolinux on 2014-01-21
I have found that I can compress files in an external folder (even in other hard disk), so the main problem is solved, i would like to know what happened, so afterhaving recovered the files I will try to delete 
Partition:
```
/dev/sda6
```
and see what happens.
Thank you for the help

---

