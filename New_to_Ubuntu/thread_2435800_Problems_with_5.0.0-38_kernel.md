---
title: "Problems with 5.0.0-38 kernel"
date: 2020-01-26
forum: New to Ubuntu
---

### Post by hk42 on 2020-01-26
It works but booting is very long.
So using the Grub menu I select 5.0.0-37
My main question is how to prevent 5.0.0-37 to be overwritten in a future upgrade ?
To be safe I already made an archive of the actual /boot directory and /lib/modules/5.0.0-37
Will that be enough ?

---

### Post by jeremy31 on 2020-01-26
The last I heard is that Ubuntu 19.04 along with the 5.0 kernels are no longer supported

---

### Post by CatKiller on 2020-01-26
> **jeremy31 said:**
> The last I heard is that Ubuntu 19.04 along with the 5.0 kernels are no longer supported

Even 18.04 with the HWE stack has moved on to 5.3.

---

### Post by hk42 on 2020-01-26
Strange this is the content of my /boot directory:
> /boot$ ls -l
total 304181
-rw-r--r-- 1 root root   224480 Nov 13 20:35 config-5.0.0-37-generic
-rw-r--r-- 1 root root   224509 Nov 13 20:35 config-5.0.0-37-lowlatency
-rw-r--r-- 1 root root   224496 Dec  2 20:25 config-5.0.0-38-generic
-rw-r--r-- 1 root root   224525 Dec  2 20:25 config-5.0.0-38-lowlatency
drwx------ 4 root root     1024 Jan  1  1970 efi
drwxr-xr-x 5 root root     4096 Jan  9 01:14 grub
-rw-r--r-- 1 root root 64197484 Dec 29 22:37 initrd.img-5.0.0-37-generic
-rw-r--r-- 1 root root 64242746 Dec 29 22:36 initrd.img-5.0.0-37-lowlatency
-rw-r--r-- 1 root root 64194162 Jan  6 20:08 initrd.img-5.0.0-38-generic
-rw-r--r-- 1 root root 64238587 Jan 23 22:28 initrd.img-5.0.0-38-lowlatency
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  4440495 Nov 13 20:35 System.map-5.0.0-37-generic
-rw------- 1 root root  4442593 Nov 13 20:35 System.map-5.0.0-37-lowlatency
-rw------- 1 root root  4442280 Dec  2 20:25 System.map-5.0.0-38-generic
-rw------- 1 root root  4444345 Dec  2 20:25 System.map-5.0.0-38-lowlatency
-rw------- 1 root root  8806136 Nov 13 22:36 vmlinuz-5.0.0-37-generic
-rw------- 1 root root  8859384 Nov 13 22:36 vmlinuz-5.0.0-37-lowlatency
-rw------- 1 root root  8802040 Dec  2 20:25 vmlinuz-5.0.0-38-generic
-rw------- 1 root root  8863480 Dec  2 20:25 vmlinuz-5.0.0-38-lowlatency


---

### Post by Impavidus on 2020-01-27
Old kernels are not automatically overwritten during upgrades. At least one old kernel is kept, older than that and they become autoremovable. But even then, they are only automatically removed if your system is configured to automatically remove autoremovable packages. Restoring old kernels from a backup after they have been removed by the package manager is likely to confuse the package manager, which would bring you into more trouble.

The fact that you run a 5.0 kernel tells us there may something wrong with your system. Or maybe you don't install upgrades very frequently. I also see you've both the generic and the low-latency kernel. Which flavour and release of Ubuntu do you run? Can you show us the output of```
sudo apt update
sudo apt upgrade
dpkg --list | grep linux-
```Those commands may install a new kernel, but won't remove one.

---

### Post by guiverc on 2020-01-27
Ubuntu 19.04 is EOL as already mentioned ([http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/))

You can use `apt-mark hold` to hold to a specific package, but I would suggest finding out the actual problem you have and finding another solution, instead of sticking to older potentially insecure unpatched kernels. ([https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto))

---

### Post by hk42 on 2020-01-27
Hi thanks again for the quick replies.
The low latency version comes when installing ubuntu studio.
Maybe it is the reason for being late in versions.
I have studio installed since a moment and each kernel update had the 2 versions.
Since yesterday I managed to install the new version 19.10 on an USB3 SSD
It never worked before.
The *.iso is the same I just checked to get all updates while installing
Thanks for the links about pinning that 's what I was wondering.
My Grub menu looks very impressive now :-)

---

