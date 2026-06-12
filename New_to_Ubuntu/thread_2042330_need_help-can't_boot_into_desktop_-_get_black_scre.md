---
title: "need help-can't boot into desktop - get black screen with BusyBox"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by s1baker on 2012-08-14
hi,

When I try to run ubuntu, at boot up, I get a black screen with this on it:
```

mount: mounting /dev/disk/by-uuid/7f56.....(long list of characters) on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
```

Can some one help me?
It worked fine yesterday, but I disconnected from the internet and
reconnected back several just before shutting yesterday, that might
have caused this.
I am using 12.04 with xfce DE 64 bit

When I try to reboot I get a black screen with a list of different
kernel versions to try and recovery kernels to try, but picking recovery kernels or earlier versions doesn't help, I always get back to the black screen with the BusyBox built in shell.


When I type 'init= bootarg' into the BusyBox shell, nothing haoppens.

---

### Post by s1baker on 2012-08-14
I seemed to have fixed this for now.

I just remembered this happening to me some time back and what I did to get the system back up.

for the record:

I ran the install .iso CD that I used to install ubuntu on the HD, and then ran gparted off of the CD and did a check and repair of the partitions. Gparted seemed to have fixed it.

---

