---
title: "[SOLVED] I messed up Grub &amp;quot; error 22&amp;quot; how do I fix Grub"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-09-04
I was having problems with something non related to this post. so I tryed a test by installing Ubuntu again on a separate partition to see if that would cure my original problem ... it didn't so I used gparted to remove that ubuntu , now when I boot grub gives me error 22 and I am wondering how I fix this

---

### Post by Elfy on 2008-09-04
When you installed ubuntu the second time it installed grub - when you deleted that ubuntu it took grub with it. Try to reinstall grub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Error 22: No such partition

---

### Post by Shadowmeph on 2008-09-04
> **forestpixie said:**
> When you installed ubuntu the second time it installed grub - when you deleted that ubuntu it took grub with it. Try to reinstall grub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Error 22: No such partition

thank you for your reply
when I try to "setup (hd0)" I am getting Error 17: Cannot mount selected partition

---

### Post by Elfy on 2008-09-04
Are you running the livecd - can you post ```
sudo fdisk -l
```

---

### Post by Shadowmeph on 2008-09-04
> **forestpixie said:**
> Are you running the livecd - can you post ```
sudo fdisk -l
```

sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a914a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1407       38913   301274977+  83  Linux
/dev/sda2            1276        1406     1052257+  82  Linux swap / Solaris

---

### Post by kansasnoob on 2008-09-04
> **Shadowmeph said:**
> thank you for your reply
when I try to "setup (hd0)" I am getting Error 17: Cannot mount selected partition

Are you running the live CD?

You must be running the live CD and then go to terminal and:

```
find /boot/grub/stage1
```

Post the output from that please.

---

### Post by kansasnoob on 2008-09-04
> **Shadowmeph said:**
> sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a914a91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1407       38913   301274977+  83  Linux
/dev/sda2            1276        1406     1052257+  82  Linux swap / Solaris

According to that you should be able to just run the following in the terminal:

```
sudo grub
```

```
root (hd0,0)
```

```
setup (hd0)
```

```
quit
```

---

### Post by Elfy on 2008-09-04
If you still get the same error can you do this please

```
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/sda1 /media/recovery
cat /recovery/boot/grub/menu.lst
```

---

### Post by Shadowmeph on 2008-09-04
> **kansasnoob said:**
> According to that you should be able to just run the following in the terminal:

```
sudo grub
```

```
root (hd0,0)
```

```
setup (hd0)
```

```
quit
```

thank you it appears to have worked ( havn't rebooted and confimed yet) the funny thing is I followed the instructions that seemed the same as the one you just gave me and it gave me an error 17 . I try it again when you posted and it works weird, thank you so much you made my day :) 
I would like to thank all of you for your help

---

