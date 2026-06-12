---
title: "I got a mistake!"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by dewsworld on 2011-12-19
HI,
Today I accdiently executed a command 
```
sudo chmod 0777 /
```
How can I undo previous file permission?

---

### Post by fdrake on 2011-12-19
depending on the files that you have:
```

sudo chmod 755 /
sudo chmod 700 /root /lost+found
sudo chmod 600 /aquota.user /aquota.group
sudo chmod 777 /vmlinuz* /initrd.img* /tmp

```
i am using "Ubuntu 10.04 Lucid Lynx" like you, from your profile info..

you are sure you did not use the recursive method, right? "chmod -R" in that case the problem is more complex
my ls -al looks like this;
> 
drwxr-xr-x  22 root root  4096 2011-12-19 02:46 .
drwxr-xr-x  22 root root  4096 2011-12-19 02:46 ..
-rw-------   1 root root  9216 2011-12-19 02:45 aquota.group
-rw-------   1 root root  9216 2011-12-19 02:45 aquota.user
drwxr-xr-x   3 root root  4096 2011-12-18 20:17 bin
drwxr-xr-x   3 root root  4096 2011-12-19 02:49 boot
drwxr-xr-x   2 root root  4096 2011-08-14 18:42 cdrom
drwxr-xr-x  18 root root  3800 2011-12-19 02:46 dev
drwxr-xr-x 174 root root 12288 2011-12-19 02:36 etc
drwxr-xr-x   4 root root  4096 2011-08-21 14:28 home
lrwxrwxrwx   1 root root    33 2011-12-19 02:46 initrd.img -> boot/initrd.img-2.6.32-37-generic
lrwxrwxrwx   1 root root    36 2011-11-29 17:50 initrd.img.old -> boot/initrd.img-3.1.0-030100-generic
drwxr-xr-x  21 root root 12288 2011-12-19 02:38 lib
drwx------   2 root root 16384 2011-08-14 18:30 lost+found
drwxr-xr-x   8 root root  4096 2011-12-19 02:36 media
drwxr-xr-x   2 root root  4096 2010-04-23 06:11 mnt
drwxr-xr-x   2 root root  4096 2011-07-19 08:02 opt
dr-xr-xr-x 215 root root     0 2011-12-17 08:25 proc
drwx------  21 root root  4096 2011-11-29 21:15 root
drwxr-xr-x   2 root root 12288 2011-12-19 02:38 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 16:55 selinux
drwxr-xr-x   4 root root  4096 2011-09-22 21:53 srv
drwxr-xr-x  12 root root     0 2011-12-17 08:25 sys
drwxrwxrwt  17 root root  4096 2011-12-19 02:49 tmp
drwxr-xr-x  11 root root  4096 2011-08-21 23:27 usr
drwxr-xr-x  17 root root  4096 2011-09-23 07:21 var
lrwxrwxrwx   1 root root    30 2011-12-19 02:46 vmlinuz -> boot/vmlinuz-2.6.32-37-generic
lrwxrwxrwx   1 root root    33 2011-11-29 17:50 vmlinuz.old -> boot/vmlinuz-3.1.0-030100-generic



---

### Post by dewsworld on 2011-12-19
Thanks!

---

### Post by fdrake on 2011-12-19
> **dewsworld said:**
> Thanks!

I edited my commands ..make sure you got the last changes..

---

