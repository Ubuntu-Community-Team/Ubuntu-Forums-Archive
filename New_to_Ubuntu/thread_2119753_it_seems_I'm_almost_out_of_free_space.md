---
title: "it seems I'm almost out of free space"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-24
Hi all, 

it seems I'm almost out of free space: 

user@ubuntu:/host/mama$ df -h
File system      Size   Used  Avail Used% Mounted
/dev/loop0      7,5G  5,5G  1,7G  77% /
udev            1,4G  4,0K  1,4G   1% /dev
tmpfs           552M  840K  551M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,4G   84K  1,4G   1% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2        56G   47G  8,7G  85% /host

 Should I worry about this line 

/dev/loop0      7,5G  5,5G  1,7G  77% /
?

---

### Post by Impavidus on 2013-02-24
5.5GB used is quite normal, but you gave your wubi install a really tiny virtual partition (7.5GB). Besides, the partition on wich you installed is quite full too. If you try to do anything usefull on that system you will get into trouble soon.

---

### Post by bcbc on 2013-02-24
It depends... on what you do with your install. If you run barebones then it's okay. I've run an install at about 90% for a long time - but it's pretty stable because I'm not installing new software or adding personal data - and I make sure my old kernels are removed and package cache cleaned.

You don't really have a lot of space on your /host NTFS partition either, so there's not a lot you can do about it. There are techniques to increase the size of the Wubi install, but since your host is at 85% I would probably just leave it alone.

What's the output of this:
```
ls /boot
```

---

### Post by marchelloUA on 2013-02-25
> **bcbc said:**
> 
What's the output of this:
```
ls /boot
```

As far as I can understand, I may erase old kernels, am I right? But how to do it properly? 

user@ubuntu:~$ ls /boot
abi-3.5.0-17-generic  config-3.5.0-17-generic  grub                         initrd.img-3.5.0-23-generic  System.map-3.5.0-21-generic  vmlinuz-3.5.0-21-generic
abi-3.5.0-21-generic  config-3.5.0-21-generic  initrd.img-3.5.0-17-generic  memtest86+.bin               System.map-3.5.0-22-generic  vmlinuz-3.5.0-22-generic
abi-3.5.0-22-generic  config-3.5.0-22-generic  initrd.img-3.5.0-21-generic  memtest86+_multiboot.bin     System.map-3.5.0-23-generic  vmlinuz-3.5.0-23-generic
abi-3.5.0-23-generic  config-3.5.0-23-generic  initrd.img-3.5.0-22-generic  System.map-3.5.0-17-generic  vmlinuz-3.5.0-17-generic

---

### Post by bcbc on 2013-02-25
I normally keep the most recent 2 kernels - because sometimes the current one can be broken with bad updates (infrequently but it can happen).

This script will keep two kernels and delete older kernels:
[https://raw.github.com/bcbc/utilities/master/clean_kernel.sh](https://raw.github.com/bcbc/utilities/master/clean_kernel.sh)

You can download it with:
```
wget https://raw.github.com/bcbc/utilities/master/clean_kernel.sh
```

And run it (it will still prompt you to confirm before making any changes and you have to enter your password to actually uninstall anything as it uses "sudo" only if there is something to remove):
```
bash clean_kernel.sh
```

Or you could manually identify the older kernels and uninstall them as follows:
```
sudo apt-get remove --purge linux-image-3.5.0-17-generic
```

After the kernel is gone, you can run:
```
sudo apt-get autoremove
sudo apt-get autoclean
```

For more info see "man apt-get":
>  autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed

>  Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

---

