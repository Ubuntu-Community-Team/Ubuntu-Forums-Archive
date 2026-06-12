---
title: "Need patch and permission help"
date: 2007-07-05
forum: Programming Talk
---

### Post by merkel on 2007-07-05
I'm trying to install a patch but I get a permission denied error:

sudo zcat snns-4.2-20040227.patch.gz | patch -p0
patching file SNNSv4.2/configure
patch: **** Can't rename file /tmp/ponJiUJf to SNNSv4.2/configure : Permission denied

root owns everything

$ ls -l
total 11608
-rwxr--r--  1 root   root     304465 2007-07-03 16:43 snns-4.2-20040227.patch
-rw-r--r--  1 root   root      55476 2007-07-05 06:07 snns-4.2-20040227.patch.gz
drwxr-xr-x 10 root   root        616 1998-09-03 09:55 SNNSv4.2
-rwxr--r--  1 merkel merkel 11509760 2007-07-03 16:25 SNNSv4.2.tar

$ ls -l SNNSv4.2
total 224
drwxr-xr-x 2 root root   304 1998-09-03 09:41 configuration
-rwxr-xr-- 1 root root 84830 1998-09-03 09:44 configure
-rw-r--r-- 1 root root  1236 1994-10-06 07:56 default.cfg
drwxr-xr-x 2 root root    48 1998-09-03 09:41 ENZO
drwxr-xr-x 2 root root  4520 1998-09-03 09:53 examples
-rw-r--r-- 1 root root 82224 1998-03-05 08:57 help.hdoc
.
.
.
Any help would be greatly appreciated.

---

### Post by Soybean on 2007-07-05
I believe that when you're using pipes and such, the sudo only applies to the command immediately following it. So ```
sudo zcat snns-4.2-20040227.patch.gz | **sudo** patch -p0
``` might do the trick, or maybe even ```
zcat snns-4.2-20040227.patch.gz | sudo patch -p0
``` if you have read access on the .gz file.

EDIT: Ah... I see that you do have read access. Look at me, responding without reading the whole post. :oops:

---

### Post by merkel on 2007-07-05
Thanks!

zcat snns-4.2-20040227.patch.gz | sudo patch -p0

worked.

---

