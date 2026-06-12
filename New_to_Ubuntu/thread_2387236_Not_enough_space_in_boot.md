---
title: "Not enough space in boot?"
date: 2018-03-16
forum: New to Ubuntu
---

### Post by rdandrimont on 2018-03-16
Hi guys,
It sounds that I have the same problem. I have upgraded my Ubuntu 17.04 to Ubuntu 17.10 and since I did it, I have the same type of error and cannot install program anymore.
If I try to install sth, I have the following error.
```
~$ sudo apt-get install ...
Removing linux-image-extra-4.10.0-19-generic (4.10.0-19.21) ...
depmod: FATAL: could not load /boot/System.map-4.10.0-19-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-19-generic /boot/vmlinuz-4.10.0-19-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-19-generic /boot/vmlinuz-4.10.0-19-generic

```

It seems that before installing anything, the installer tries to remove an unexisitng image of my system in my /boot folder. Here is what I have in my boot folder.


```
~$ ls -la /boot

total 125236
drwxr-xr-x  3 root root     4096 mar  7 11:05 .
drwxr-xr-x 27 root root     4096 mar  5 10:10 ..
-rw-r--r--  1 root root  1443962 dic  4 15:04 abi-4.10.0-42-generic
-rw-r--r--  1 root root  1501359 feb 16 18:49 abi-4.13.0-36-generic
-rw-r--r--  1 root root   204962 dic  4 15:04 config-4.10.0-42-generic
-rw-r--r--  1 root root   213212 feb 16 18:49 config-4.13.0-36-generic
drwxr-xr-x  5 root root     4096 mar  7 11:05 grub
-rw-r--r--  1 root root 42833675 mar  5 10:12 initrd.img-4.10.0-42-generic
-rw-r--r--  1 root root 58376815 mar  7 10:59 initrd.img-4.13.0-36-generic
-rw-r--r--  1 root root   182704 gen 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 gen 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 gen 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root     2860 feb 16 18:49 retpoline-4.13.0-36-generic
-rw-------  1 root root  3722463 dic  4 15:04 System.map-4.10.0-42-generic
-rw-------  1 root root  3880918 feb 16 18:49 System.map-4.13.0-36-generic
-rw-------  1 root root  7587600 dic  4 15:04 vmlinuz-4.10.0-42-generic
-rw-------  1 root root  7870224 feb 16 18:49 vmlinuz-4.13.0-36-generic


```
Can anyone help me solving this?

---

### Post by QIII on 2018-03-16
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2381960](https://ubuntuforums.org/showthread.php?t=2381960)

Please do not horn in on the threads of other users.  Aside from being impolite, your similar symptoms may have entirely different underlying causes.  Threads often get tangled and confusing for both the OP, the interloper and everyone trying to help.

Thanks.

---

### Post by wildmanne39 on 2018-03-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by SeijiSensei on 2018-03-17
Since you only have two kernel images and associated files in /boot, I'm guessing the partition is just too small.  256 MB is the minimum I'd use with the enormous hard drives available today.  512 MB will never be filled.

If you cannot repartition the drive, then the only suggestion I can make is to remove the older set of kernel files manually before updating.  That should free up enough space for the new kernel and its files to be written.

```

cd /boot
sudo rm -f *4.13.0-36*

```

would work with the listing above.  Remove the "-f" if you want to see exactly what's being deleted and confirming each file.

---

### Post by deadflowr on 2018-03-17
Not sure this is the same issue as the one that this thread was pulled from.
Seems more like a busted package removal.
The only similarities are the FATAL error outputs.

Since this was a release upgrade from 17.04 to 17.10 it might be that the clean up failed and only removed part of what it should have.
Probably a good starting point would be to look at the current status of the installed (or not installed, or other) kernels is

Post back what
```
dpkg -l linux*
```
shows
(Hint: for full results, please run the command in a maximize terminal window, or else the command gets cut off)

Also, please use code tags.

---

