---
title: "Question about my kernel version."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Roasted on 2008-10-21
jason@jason-hardy:~$ uname -r
2.6.24-21-server
jason@jason-hardy:~$ 


I'm running 64 bit Ubuntu Hardy Heron. Is there any reason server is listed there?

---

### Post by PointyWombat on 2008-10-21
Just curious, but what's the output of **ls -l /boot**?

---

### Post by Roasted on 2008-10-21
jason@jason-hardy:~$ ls -l /boot
total 48852
-rw-r--r-- 1 root root  420224 2008-08-20 18:15 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  420338 2008-08-25 15:39 abi-2.6.24-21-generic
-rw-r--r-- 1 root root  420338 2008-08-25 15:45 abi-2.6.24-21-server
-rw-r--r-- 1 root root   74164 2008-08-20 18:15 config-2.6.24-19-generic
-rw-r--r-- 1 root root   74188 2008-08-25 15:39 config-2.6.24-21-generic
-rw-r--r-- 1 root root   74193 2008-08-25 15:45 config-2.6.24-21-server
drwxr-xr-x 2 root  999    4096 2008-10-16 19:31 grub
-rw-r--r-- 1 root root 7736345 2008-10-11 21:09 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root  999 8411145 2008-10-11 09:35 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7736907 2008-10-15 20:09 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7736946 2008-10-15 20:08 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root 7455023 2008-10-16 19:31 initrd.img-2.6.24-21-server
-rw-r--r-- 1 root root  103204 2007-09-28 07:03 memtest86+.bin
-rw-r--r-- 1 root root 1152364 2008-08-20 18:15 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1152893 2008-08-25 15:39 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1162836 2008-08-25 15:45 System.map-2.6.24-21-server
-rw-r--r-- 1 root root 1903096 2008-08-20 18:15 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1905624 2008-08-25 15:39 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 1928856 2008-08-25 15:45 vmlinuz-2.6.24-21-server
jason@jason-hardy:~$ 



I don't know if it means anything, but I'm going to bed and figured I'd throw this out there: I have 4 hard drives in my computer, and I'm also running 64 bit. So if those variables have anything to do with it, well, figured I'd speak them before disappearing. Thanks.

---

