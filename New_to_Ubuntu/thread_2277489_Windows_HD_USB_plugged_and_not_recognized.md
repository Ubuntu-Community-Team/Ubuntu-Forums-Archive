---
title: "Windows HD USB plugged and not recognized"
date: 2015-05-09
forum: New to Ubuntu
---

### Post by kinisia on 2015-05-09
Hi, 

I removed from a damaged HP Pavillon a 250Gb HDD where it was installed Windows Vista on a unique partition. I decided to retrieve some of my data from there because the old laptop was completely gone. Bought a SATA cable i decided to plug it in Ubuntu. However the system did not recognized it, or better, Ubuntu recognized the disk in the Disk Utility app but it did not allow me to go and see what's inside with the file manager. That's what i need to retrieve some old data. 
I will post the log of **lsusb **with the HDD plugged and without:

Without:
```
kinisia@kinisia-Alpha:~$ lsusb 
Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 005: ID 05ac:0246 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 001 Device 008: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

With:

```

kinisia@kinisia-Alpha:~$ lsusb 
**Bus 002 Device 004: ID 174c:55aa ASMedia Technology Inc. ASMedia 2105 SATA bridge**
Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 005: ID 05ac:0246 Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 001 Device 008: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```

Any idea on how to surf what's inside?

---

### Post by ajgreeny on 2015-05-09
Did the damaged Vista computer shutdown properly or did it crash?  NTFS disks/partitions will be shown as "in use" and not mountable in Ubuntu if they have come from a windows system which crashed, or was not shutdown as it should be, allowing the partition to be unmounted.

If there is another Windows computer available, attach the disk to that, then remove it safely, as you must all disks to avoid corruption or loss of files.

---

### Post by kinisia on 2015-05-09
> **ajgreeny said:**
> Did the damaged Vista computer shutdown properly or did it crash?  NTFS disks/partitions will be shown as "in use" and not mountable in Ubuntu if they have come from a windows system which crashed, or was not shutdown as it should be, allowing the partition to be unmounted.
[http://ubuntuforums.org/newreply.php?do=newreply&p=13281982](http://ubuntuforums.org/newreply.php?do=newreply&p=13281982)
If there is another Windows computer available, attach the disk to that, then remove it safely, as you must all disks to avoid corruption or loss of files.

I am not sure that the laptop was turned off properly because it suffered of a GPU damage and the screen was totally black. I suppose that it would be impossible without seeing buttons shutdown it properly. So that can be the first problem. Concerning the other observation i plugged in Windows 8.1 and the system started initializing the hardware reading it and installing drivers. Then it continues to be hide in the file manager but it has been possible to remove it safetly. But it seems very hard to be shown. 
The problem in my opinion is the unique boot partition that make it not understandable as a data HDD but like a system one.

---

### Post by Mark Phelps on 2015-05-09
> as a data HDD but like a system one. Sorry, not correct.  A HDD is a physical device.  Partitions on that device can be created to be system partitions or data partitions.  IF you stick a former Windows-formatted drive in a new PC, it will try to boot from it.

A better approach, if what you want to do is recover data from it, is to boot from the regular HDD in the PC, and connect the other HDD (using an adapter) after the PC has already booted.  This will prevent booting from the second HDD and allow you to do data recovery.

---

### Post by leunam12 on 2015-05-09
It seems from the first post that the kernel recognizes your SATA to USB adapter. Is there a separate power supply for the HDD? is the HDD powered up? What happens when you open Nautilus and try to access the drive? The fact that you cannot access it in Ubuntu nor in Windows is maybe and indication that the drive is damaged. Have you checked this drive for errors? Install gsmartcontrol and run it and see if the drive is in good condition.

Also connect the HDD via USB and then open the terminal and type lsblk and post the result.

---

### Post by leunam12 on 2015-05-09
Found this, it's worth a try

[http://lifehacker.com/192982/geek-to-live--rescue-files-with-a-boot-cd](http://lifehacker.com/192982/geek-to-live--rescue-files-with-a-boot-cd)

---

### Post by kinisia on 2015-05-10
> **Mark Phelps said:**
> Sorry, not correct.  A HDD is a physical device.  Partitions on that device can be created to be system partitions or data partitions.  IF you stick a former Windows-formatted drive in a new PC, it will try to boot from it.

A better approach, if what you want to do is recover data from it, is to boot from the regular HDD in the PC, and connect the other HDD (using an adapter) after the PC has already booted.  This will prevent booting from the second HDD and allow you to do data recovery.


Yes is what i am doing actually. My not proper expression was only to help you understand that is formatted to be bootable

when i tried to plug it in OS X it said that i have to format it. In ubuntu, it can't be read neither.


> **leunam12 said:**
> It seems from the first post that the kernel  recognizes your SATA to USB adapter. Is there a separate power supply  for the HDD? is the HDD powered up? What happens when you open Nautilus  and try to access the drive? The fact that you cannot access it in  Ubuntu nor in Windows is maybe and indication that the drive is damaged.  Have you checked this drive for errors? Install gsmartcontrol and run  it and see if the drive is in good condition.

Also connect the HDD via USB and then open the terminal and type lsblk and post the result.

No separate power supply (only USB cable)
Yes, is powered up with flashing red/green light on Ubuntu while is fixed green while on Windows. 
Nothing i can't see the drive
I did a verify on Mac and the drive seems ok, I will try now with gsmartcontrol

---

### Post by Mark Phelps on 2015-05-11
Having trouble understanding what you're trying to do with the drive ...

You said it was from a Windows PC, Vista to be exact ... but then, you talk about plugging it into a Mac and trying to use it.

In my experience, the best apps to recover former Windows filesystems are Windows apps, not Mac or Linux.  The Windows data recovery apps don't actually read the filesystem, instead, they search the drive for file and folder headers.  So, they are useful when the OS is prompting to reformat the drive.

So basically, you need a working Windows PC to do the data recovery -- if that's your intent.

---

