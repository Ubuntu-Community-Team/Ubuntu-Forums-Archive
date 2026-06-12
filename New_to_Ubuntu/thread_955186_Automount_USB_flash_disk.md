---
title: "Automount USB flash disk"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by jesrani on 2008-10-21
When I plugged in my USB flash disk, nothing happens. I think on 7.10 it used to automount and show on the desktop. After I upgraded to 8.04 it doesnt work. What to do.

---

### Post by jesrani on 2008-10-22
An update. When I opened the partition editor with the USB plugged in I could not find it.

---

### Post by kansasnoob on 2008-10-22
In 8.04 I always install pmount from synaptic to auto-mount all of my external drives.

I used to use usbmount but I've come to prefer pmount which depends on hal, so make sure hal is installed also.

The description for pmount in synaptic pretty well explains it all.

---

### Post by jesrani on 2008-10-22
I installed pmount. Hal was already installed. Rebooted. Same problem. The disk does not show up in partition editor either.

---

### Post by jesrani on 2008-10-22
Hello, can anyone help with this please. I need to connect the usb drive to my computer.

---

### Post by OldGrey on 2008-10-22
A flash drive should automount in 8.04. Did you upgrade or do a clean install? In my experience an upgrade sometimes can be problematic.

---

### Post by vanadium on 2008-10-22
Test the drive on another USB port, on another computer. When a drive is not at all recognized, a hardware problem is usually the cause. Check for sure that Ubuntu does not see your drive by plugging it in and issuing the command

```

sudo blkid

```

---

### Post by jesrani on 2008-10-22
I tested on another computer with XP and its working fine. When I put the code "sudo blkid", I get following results:
/dev/sda1: UUID="d3899dc6-d2c3-442d-a679-b026cdb1ba60" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="a1929de1-4d05-4a45-88bb-a5616e979b7c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="e84f16ae-36ad-4e0e-bdff-f6e9046e1cbd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="d56dbda3-f3ad-4d7a-a044-1a5b777aeec7" 

The results are same with or without the USB drive plugged in. It is the 2 harddisks and the partitions only which are showing up as well as the swap. So what is wrong. This used to be ok till 7.10 Ubuntu.

---

### Post by baddnady23 on 2008-10-22
Have you cleanly ejected it from windows before using it in ubuntu?  If not this will cause problems

---

### Post by jesrani on 2008-10-22
> **baddnady23 said:**
> Have you cleanly ejected it from windows before using it in ubuntu?  If not this will cause problems

I just did that, plugged into windows, properly ejected and then back to Ubuntu. No change.

---

### Post by vanadium on 2008-10-22
I probably should have asked you to post the output of 

```

sudo fdisk -l

```

in the first place: only that will tell definitely wether your drive is not seen. The output of blkid shows that no partition is seen. Is this a standard, common USB or does it contain some proprietary file systems?

---

### Post by jesrani on 2008-10-23
Its just a normal 1Gb transcend usb stick which is running OK on my windows PC. The output of fdisk is as under :
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf964f964

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+  83  Linux
/dev/sda2            1959        9729    62420557+   5  Extended
/dev/sda5            1959        9599    61376301   83  Linux
/dev/sda6            9600        9729     1044193+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040d4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux


Is it possible the USB ports are not detected?

---

### Post by vanadium on 2008-10-23
This confirms that the software does not see your USB. I am unfortunately not experienced to do further troubleshooting. Has it ever worked on that PC? Some people might be able to tell something from the output of the kernel. Disconnect the drive, then connect the drive. The command "dmesg" will display all kernel messages, and there it can be seen (by experts) how (and if) the kernel reacted on inserting the USB and eventually what went wrong. However, I wonder if the kernel will see something if the drive is not in the output of fdisk in the first place.

Obviously, you should try also if the problem is there also with another USB, or an USB hard drive as part of your troubleshooting.

---

