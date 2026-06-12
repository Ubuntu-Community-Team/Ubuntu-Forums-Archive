---
title: "Compiling linux kernel 3.0.0 failing on UBUNTU 10.04"
date: 2011-08-30
forum: Packaging and Compiling Programs
---

### Post by codingfreak on 2011-08-30
HI,

I have followed the steps in [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) and building linux kernel 3.0.0 on UBUNTU 10.04

Compilation of kernel is successful and linux image is created.

But when I try to execute the step 12 in the above mentioned tutorial I am facing some errors

```
sudo update-initramfs -ck 3.0.0-custom/
update-initramfs: Generating /boot/initrd.img-3.0.0-custom/
touch: cannot touch `/boot/initrd.img-3.0.0-custom/.new': No such file or directory
: 3.0.0-custom/ is not a valid kernel version
update-initramfs: failed for /boot/initrd.img-3.0.0-custom/
```

As a result I cant boot with the latest kernel. Can anyone help me through this step ?

---

### Post by howefield on 2011-08-30
Thread moved to "*Packaging and Compiling Programs*"

---

### Post by codingfreak on 2011-08-31
Anbody has any idea about this ?

---

### Post by SevenMachines on 2011-08-31
You need to just use the kernel name from 
```
 $ ls /lib/modules
```you've used the directory by accident, so, not
```
 $ sudo update-initramfs -ck 3.0.0-custom/
```drop the '/'
```
$ ls /lib/modules
3.0.0-custom 
$ sudo update-initramfs -ck 3.0.0-custom
```

---

### Post by codingfreak on 2011-09-02
> **SevenMachines said:**
> You need to just use the kernel name from 
```
 $ ls /lib/modules
```you've used the directory by accident, so, not
```
 $ sudo update-initramfs -ck 3.0.0-custom/
```drop the '/'
```
$ ls /lib/modules
3.0.0-custom 
$ sudo update-initramfs -ck 3.0.0-custom
```

Thanks .. I will make a try tonight

---

### Post by codingfreak on 2011-09-03
Worked like a charm ... thanks ..

---

