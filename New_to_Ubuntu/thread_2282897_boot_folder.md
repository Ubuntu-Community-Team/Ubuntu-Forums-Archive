---
title: "/boot folder"
date: 2015-06-17
forum: New to Ubuntu
---

### Post by Paul_Armstrong on 2015-06-17
hi Guys new to this but can you tell me what sort of files are stored in the /boot folder on Ubuntu?

---

### Post by v3.xx on 2015-06-17
> **Paul_Armstrong said:**
> hi Guys new to this but can you tell me what sort of files are stored in the /boot folder on Ubuntu?
Open your file manager and take a look :)
[ATTACH=CONFIG]262665[/ATTACH]

---

### Post by Bashing-om on 2015-06-17
Paul_Armstrong; Hello;

In addition to v3.xx's input;

Here is a look at the directory from terminal:
```

sysop@1404mini:~$ ls -al /boot
total 175720
drwxr-xr-x  4 root root     4096 Jun 16 17:31 .
drwxr-xr-x 25 root root     4096 Jun 16 17:30 ..
-rw-r--r--  1 root root  1164723 Apr 10 16:05 abi-3.13.0-49-generic
-rw-r--r--  1 root root  1164671 Apr 15 08:03 abi-3.13.0-51-generic
-rw-r--r--  1 root root  1164671 May  4 00:09 abi-3.13.0-52-generic
-rw-r--r--  1 root root  1164671 May 20 06:11 abi-3.13.0-53-generic
-rw-r--r--  1 root root  1164806 May 26 15:11 abi-3.13.0-54-generic
-rw-r--r--  1 root root  1164806 Jun 14 14:28 abi-3.13.0-55-generic
-rw-r--r--  1 root root   165773 Apr 10 16:05 config-3.13.0-49-generic
-rw-r--r--  1 root root   165762 Apr 15 08:03 config-3.13.0-51-generic
-rw-r--r--  1 root root   165762 May  4 00:09 config-3.13.0-52-generic
-rw-r--r--  1 root root   165762 May 20 06:11 config-3.13.0-53-generic
-rw-r--r--  1 root root   165762 May 26 15:11 config-3.13.0-54-generic
-rw-r--r--  1 root root   165762 Jun 14 14:28 config-3.13.0-55-generic
drwxr-xr-x  5 root root     4096 Jun 16 17:31 grub
drwxr-xr-x  5 root root     4096 Jun  9  2014 grub_backup
-rw-r--r--  1 root root 19342947 Apr 14 13:24 initrd.img-3.13.0-49-generic
-rw-r--r--  1 root root 19343481 Apr 29 11:30 initrd.img-3.13.0-51-generic
-rw-r--r--  1 root root 19344025 May 21 14:20 initrd.img-3.13.0-52-generic
-rw-r--r--  1 root root 19346748 May 28 12:49 initrd.img-3.13.0-53-generic
-rw-r--r--  1 root root 19346697 Jun 10 11:37 initrd.img-3.13.0-54-generic
-rw-r--r--  1 root root 19346096 Jun 16 17:31 initrd.img-3.13.0-55-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389437 Apr 10 16:05 System.map-3.13.0-49-generic
-rw-------  1 root root  3389875 Apr 15 08:03 System.map-3.13.0-51-generic
-rw-------  1 root root  3389875 May  4 00:09 System.map-3.13.0-52-generic
-rw-------  1 root root  3390132 May 20 06:11 System.map-3.13.0-53-generic
-rw-------  1 root root  3390881 May 26 15:11 System.map-3.13.0-54-generic
-rw-------  1 root root  3390881 Jun 14 14:28 System.map-3.13.0-55-generic
-rw-------  1 root root  5815392 Apr 10 16:05 vmlinuz-3.13.0-49-generic
-rw-------  1 root root  5818368 Apr 15 08:03 vmlinuz-3.13.0-51-generic
-rw-------  1 root root  5818592 May  4 00:09 vmlinuz-3.13.0-52-generic
-rw-------  1 root root  5821152 May 20 06:11 vmlinuz-3.13.0-53-generic
-rw-------  1 root root  5821664 May 26 15:11 vmlinuz-3.13.0-54-generic
-rw-------  1 root root  5821888 Jun 14 14:28 vmlinuz-3.13.0-55-generic
sysop@1404mini:~$

```
Note here that I am behind in system maintenance in that I have several old kernels still installed.

With the aboves as reference, do you now have a specific question ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-06-17
> Note here that I am behind in system maintenance in that I have several old kernels still installed.
And mine is a fresh install, still got that new car smell :biggrin:

---

### Post by monkeybrain20122 on 2015-06-17
You don't need a /boot partition for normal use. So don't make one unless you are using non standard file system and do encryption. You are going to run into issues when it is filled up with old kernels after a few updates (run sudo apt-get autoremove when that inevitably happens)

---

### Post by cooleryawner on 2015-06-17
Just boot up nautilus or your preferred file manager, and check it out, as long as you dont change anything, you won't brake your install.

---

