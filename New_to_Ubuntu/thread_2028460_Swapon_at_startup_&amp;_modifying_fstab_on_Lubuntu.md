---
title: "Swapon at startup &amp; modifying fstab on Lubuntu 12.04"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by Lyfang on 2012-07-18
Hi, I want to use swapon (part of util-linux) to enable  paging (swapping), however I want to automatically add the disk where swap partition is located at startup to fstab. Any help is greatly appreciated! This works but is done manually. I think a script could be written to  automatically mount the device & enable swap. I'm using Lubuntu 12.04 LTS.

Opened from the Terminal:
```
swapon -s
```
Filename				Type		Size	Used	Priority

No swap is enabled, now I will enable swap on the disk:

```
fdisk -l
```
/dev/sda6       306343936   312580095     3118080   82  Linux växling / Solaris

```
sudo /sbin/swapon /dev/sda6
```

```
swapon -s
```
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	3118076	0	-1

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1495        318       1177          0         32        191
-/+ buffers/cache:         94       1401
Swap:         3044          0       3044
```

Here is my fstab (default Lubuntu 12.04), edit the fstab at your own risk (as usual):
```
gksudo leafpad  /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b99d51d4-b8ce-415f-8a58-3fb6bf318cdf /               ext4    errors=remount-ro 0       1
```

---

### Post by Elfy on 2012-07-18
Hi - run this in a terminal to get the UUID of the swap

```
sudo blkid | grep swap
```

Open fstab as root


```
gksudo leafpad /etc/fstab  
```

and add the line

Mine look like

```
/dev/sda8: UUID="9237bdd4-1976-4532-9c6f-558fb7b4a6f5" TYPE="swap"
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=937c62ee-2a81-4824-877a-b5d77f39f989 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9237bdd4-1976-4532-9c6f-558fb7b4a6f5 none            swap    sw              0       0
```

---

### Post by Lyfang on 2012-07-18
Summary: I cannot mount the swap partition at startup.

Thanks Elfy helping me add this line from 'sudo blkid | grep swap'!

```
sudo blkid | grep swap
```
/dev/sda6: UUID="fda67af6-6e5f-43df-ad87-324ddde184c4" TYPE="swap" 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b99d51d4-b8ce-415f-8a58-3fb6bf318cdf /               ext4    errors=remount-ro 0       1
/dev/sda6: UUID="fda67af6-6e5f-43df-ad87-324ddde184c4" TYPE="swap"
``` 

I installed MountManager for auto mounting the swap partition, is done at your own risk (as usual):

```
sudo apt-get update && sudo apt-get install mountmanager
```

"Mount swap during start of the operating system" was automatically checked.

Then replaced the original fstab configuration by selecting "Apply". Rebooting the system.

```
swapon -s
```
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	3118076	0	-1

"Scary" how MountManager had rewritten the fstab file:

```
/dev/sda6: UUID="fda67af6-6e5f-43df-ad87-324ddde184c4" TYPE="swap" 



UUID=fda67af6-6e5f-43df-ad87-324ddde184c4	swap	swap	sw	0	0
```

At startup I get something like UUID="fda67af6-6e5f-43df-ad87-324ddde184c4" cannot be mounted & I press s to continue. Any help is greatly appreciated!

---

### Post by Elfy on 2012-07-18
If the UUID for your swap is 

fda67af6-6e5f-43df-ad87-324ddde184c4

The line in fstab should be 

```
UUID=fda67af6-6e5f-43df-ad87-324ddde184c4 none swap sw 0 0
```

So edit the file and save it

Then turn off swap 

```
sudo swapoff -a
```

Then see if it turns on again

```
sudo swapon -a
```

---

### Post by Lyfang on 2012-07-18
gksudo leafpad /etc/fstab (edit the fstab at your own risk as usual):

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b99d51d4-b8ce-415f-8a58-3fb6bf318cdf /               ext4    errors=remount-ro 0       1
UUID=fda67af6-6e5f-43df-ad87-324ddde184c4 none swap sw 0 0

```
sudo swapoff -a
sudo swapon -a
swapon -s
```
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	3118076	0	-1

After rebooting the system:
```
swapon -s
```
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	3118076	0	-1

Thank you so much Elfy for all of your help!

---

### Post by Elfy on 2012-07-18
Welcome :)

---

