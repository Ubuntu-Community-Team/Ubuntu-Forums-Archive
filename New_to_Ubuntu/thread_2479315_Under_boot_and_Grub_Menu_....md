---
title: "Under /boot and Grub Menu ..."
date: 2022-09-20
forum: New to Ubuntu
---

### Post by cwmoser2 on 2022-09-20
Under the Grub Menu during boot, the default Linux that boots is my *-125-generic OS but that OS lacks my Sound Drivers.
I can cursor down and select *-124-generic OS and I do have sound and Sound Drivers.

How can I get update-grub command to ignore the *-125-generic and make *-124-generic the default during boot up?
Can I just delete the *-125-generic files under /boot and run update-grub????

Here is the contents of /boot :

```

-rw-r--r-- 1 root root   237947 Aug  3 21:48 config-5.4.0-124-generic
-rw-r--r-- 1 root root   237947 Aug 10 04:17 config-5.4.0-125-generic
drwxr-xr-x 4 root root     4096 Sep 19 06:13 grub
lrwxrwxrwx 1 root root       28 Sep 19 06:11 initrd.img -> initrd.img-5.4.0-125-generic
-rw-r--r-- 1 root root 90239721 Sep 19 06:10 initrd.img-5.4.0-124-generic
-rw-r--r-- 1 root root 90243114 Sep 19 06:11 initrd.img-5.4.0-125-generic
lrwxrwxrwx 1 root root       28 Sep 19 06:11 initrd.img.old -> initrd.img-5.4.0-124-generic
-rw-r--r-- 1 root root   182704 Aug 18  2020 memtest86+.bin
-rw-r--r-- 1 root root   184380 Aug 18  2020 memtest86+.elf
-rw-r--r-- 1 root root   184884 Aug 18  2020 memtest86+_multiboot.bin
-rw------- 1 root root  4758850 Aug  3 21:48 System.map-5.4.0-124-generic
-rw------- 1 root root  4758850 Aug 10 04:17 System.map-5.4.0-125-generic
lrwxrwxrwx 1 root root       25 Sep 19 06:11 vmlinuz -> vmlinuz-5.4.0-125-generic
-rw------- 1 root root 13660416 Aug  3 21:54 vmlinuz-5.4.0-124-generic
-rw------- 1 root root 13660416 Aug 10 04:24 vmlinuz-5.4.0-125-generic
lrwxrwxrwx 1 root root       25 Sep 19 06:11 vmlinuz.old -> vmlinuz-5.4.0-124-generic


```

---

### Post by tea for one on 2022-09-21
> **cwmoser2 said:**
> How can I get update-grub command to ignore the *-125-generic and make *-124-generic the default during boot up?
Assuming that *-124 is the second of two kernels installed, you can edit Grub to boot this kernel as default.
```
GRUB_DEFAULT="[COLOR="#0000FF"]1[/COLOR]>[COLOR="#FF0000"]2[/COLOR]"
```

Grub counts from 0 hence GRUB_DEFAULT=0 is the first line of the Grub menu, which will boot the latest installed kernel.
The 1 in blue is the second line of the Grub menu i.e. Advanced Options for Ubuntu.
The 2 in red is the third option from the second line I.e the previous kernel.
Don’t forget to run [COLOR="#0000FF"]sudo update-grub[/COLOR] after editing the file.
> Can I just delete the *-125-generic files under /boot and run update-grub????
If you remove the latest kernel packages, you'll also remove the metapackages associated with them. Future kernel installation becomes more difficult.
I would wait until a new kernel arrives and see if your sound improves.

Of course, if a new kernel works OK, you will have to change Grub again.
```
GRUB_DEFAULT=0
```

---

