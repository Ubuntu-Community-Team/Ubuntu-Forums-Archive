---
title: "kernel for 12.04 to 14.04 upgrade"
date: 2017-02-21
forum: New to Ubuntu
---

### Post by Nigel_Pain on 2017-02-21
I recently inherited some Ubuntu 12.04 LTS machines, which I want to upgrade to 14.04 LTS. I'm struggling a little because I've come from a Solaris background and, although I've attended some Linux training, it's all still a bit new to me.

I managed to go through the do-release-upgrade process OK but when I rebooted, grub wasn't finding a kernel to use and was looping through memtest. I interrupted the boot process and managed to drop into recovery mode and found all the kernel files still there in /boot:

[FONT=courier new]-rw-r--r-- 1 root root   795365 Jun  6  2013 abi-3.2.0-48-generic
-rw-r--r-- 1 root root   140622 Jun  6  2013 config-3.2.0-48-generic
drwxr-xr-x 3 root root     4096 Nov 10 05:02 grub
-rw-r--r-- 1 root root 14798452 Sep 24  2015 initrd.img-3.2.0-48-generic
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2893287 Jun  6  2013 System.map-3.2.0-48-generic
-rw------- 1 root root  4978416 Jun  6  2013 vmlinuz-3.2.0-48-generic
[/FONT]
 Will this be something to do with the kernel version? Before upgrade uname -r returns 3.2.0-48-generic and according to lsb_release the Ubuntu version is 12.04.5 LTS.

Thanks.

---

### Post by DuckHook on 2017-02-21
I'll be of only limited help because it's literally been years since I've done that upgrade, but&#8230;

From recovery, can you try reinstalling GRUB:```
sudo grub-install
```&#8230;then updating it with:```
sudo update-grub
```

---

### Post by Nigel_Pain on 2017-02-23
That seems to have done it. Luckily it is a VM and I was able to roll back to a snapshot. I installed the latest 3.13 kernel and did the upgrade from that. It still didn't find a kernel so following another roll back and upgrade I ran the grub-install (needed a boot device as an option) and the update-grub. And hey-presto, I had a Ubuntu option in Grub (plus a submenu with a recovery option).
Thanks for your advice, I have a way to go with Linux!

---

### Post by oldrocker99 on 2017-02-23
Since your problem is solved, please use the Thread Tools to mark this thread as [SOLVED].

---

### Post by Nigel_Pain on 2017-02-23
Did that!

---

### Post by DuckHook on 2017-02-23
> **Nigel_Pain said:**
> …Luckily it is a VM…I have a way to go with Linux!Well, you are off to a very good start, and you obviously don't have as long a way to go as you think. Experimenting with Linux in a VM is a *very* smart way to go about it and the safety and versatility that it offers is unparalleled—as you discovered with your easy-as-pie rollback to a good working snapshot.

Glad you worked it out.

Good Luck and Happy Ubuntu-ing!

---

