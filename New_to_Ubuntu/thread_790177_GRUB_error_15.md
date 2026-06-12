---
title: "GRUB error 15"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by estanton on 2008-05-11
When I try and boot up my system I am getting this error
Error 15: file not found

I'm currently running off of a live disk (however it is not up to date with the system). I'd prefer to not have to reinstall the OS from the ground up. I have most of my data backed up but I'm running dual monitors and I'd like to at least salvage my xorg.conf file, because setting it up was a real pain. So what are my options for a restore? If I just tell ubuntu to go ahead and install is it going to mess up my data? Also, how can I access the file system to access my data from a live disk?

---

### Post by ajmorris on 2008-05-11
hi there,
we are going to re-install your bootloader, grub.

First, boot into any linux live cd, then once logged in, mount your ubuntu partition, (you can find the /dev block device by sudo fdisk -l, then do sudo mkdir ubuntu then sudo mount /dev/[I]Block device from sudo fdisk -l)
[/I]
open up a terminal and type in the following commands:
```
      1) sudo grub 
```

```
      2) find /boot/grub/stage1 
```

```
      3) root (hd#,#) Where #,# are the numbers found in step 2) 
```

```
      4) setup (hd0) 
```
```

     5) quit 
```
```

     6) reboot 
```

then, eject the cd, and you should be able to boot back into your system

---

### Post by estanton on 2008-05-11
Had problems mounting I think I have it figured out now.

---

### Post by estanton on 2008-05-11
Worked well, the system is now booting up partly. However I end up in something called BusyBox instead of ubuntu successfully loading. What is that?

---

