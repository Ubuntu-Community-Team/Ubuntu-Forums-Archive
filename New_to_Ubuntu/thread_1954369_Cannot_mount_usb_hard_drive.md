---
title: "Cannot mount usb hard drive"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by cmanlinux on 2012-04-07
Hi All,

I have been unable to mount a usb hard drive, and I haven't been able to find a solution. Hoping someone can help me out.

I am running Ubuntu 11.10. The usb hard drive in question is a 500G Hitachi hard drive formatted with FAT32.

Here is the output from dmesg:

```

cman@ubuntu-laptop:~$ dmesg | tail -n 50
[  139.604156] usb 2-5: new high speed USB device number 2 using ehci_hcd
[  139.745060] scsi7 : uas
[  139.835483] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[  143.401856] scsi 7:0:0:0: Direct-Access     Hitachi  Touro Mobile Pro A0D0 PQ: 0 ANSI: 4
[  149.824145] scsi 7:0:0:0: uas_eh_abort_handler tag 0
[  149.824156] scsi 7:0:0:0: uas_eh_device_reset_handler tag 0
[  149.824161] scsi 7:0:0:0: uas_eh_target_reset_handler tag 0
[  149.824165] scsi 7:0:0:0: uas_eh_bus_reset_handler tag 0
[  149.936165] usb 2-5: reset high speed USB device number 2 using ehci_hcd
[  150.070071] scsi 7:0:0:0: Device offlined - not ready after error recovery
[  150.070136] scsi 7:0:0:0: rejecting I/O to offline device
[  150.070150] scsi 7:0:0:0: rejecting I/O to offline device
[  150.071896] scsi 7:0:0:1: Enclosure         Hitachi  SES              A0D0 PQ: 0 ANSI: 4
[  150.072092] scsi 7:0:0:2: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
[  150.072713] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  150.072933] scsi 7:0:0:1: Attached scsi generic sg4 type 13
[  180.832158] sd 7:0:0:0: uas_eh_abort_handler tag 0
[  180.832172] sd 7:0:0:0: uas_eh_device_reset_handler tag 0
[  180.832178] sd 7:0:0:0: uas_eh_target_reset_handler tag 0
[  180.832182] sd 7:0:0:0: uas_eh_bus_reset_handler tag 0
[  180.944156] usb 2-5: reset high speed USB device number 2 using ehci_hcd
[  181.078083] sd 7:0:0:0: Device offlined - not ready after error recovery
[  181.078146] sd 7:0:0:0: rejecting I/O to offline device
[  181.078160] sd 7:0:0:0: rejecting I/O to offline device
[  181.078168] sd 7:0:0:0: rejecting I/O to offline device
[  181.078174] sd 7:0:0:0: [sdc] READ CAPACITY failed
[  181.078178] sd 7:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  181.078184] sd 7:0:0:0: [sdc] Sense not available.
[  181.078194] sd 7:0:0:0: rejecting I/O to offline device
[  181.078200] sd 7:0:0:0: [sdc] Write Protect is off
[  181.078205] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  181.078210] sd 7:0:0:0: rejecting I/O to offline device
[  181.078216] sd 7:0:0:0: [sdc] Asking for cache data failed
[  181.078220] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  181.078516] sd 7:0:0:0: [sdc] Attached SCSI disk
[  181.094520] ses 7:0:0:1: Attached Enclosure device

```

I can see that there's a problem - but don't have the experience to figure it out.

Also worth noting that I can mount the same drive with other computers running debian and windows.

Thanks!

---

### Post by Kevin McCready on 2012-04-08
I know very little about this (in fact only learnt of dmesg from your post), but I searched the forums and someone else suggested checking permissions. Would this help?

---

### Post by cmanlinux on 2012-04-09
I'm not sure that I can change the permissions to the disk (or if it would help) since I can't even seem to see it.

None of the suggestions on the wiki seemed to help.

Under normal circumstances, the disk would be visible under /media, which it is not.

fsdisk doesn't yield anything helpful:

```

cman@ubuntu-laptop:/media$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028433

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480153599   240075776   83  Linux
/dev/sda2       480155646   488396799     4120577    5  Extended
/dev/sda5       480155648   488396799     4120576   82  Linux swap / Solaris

```

Output from lsusb:

```

cman@ubuntu-laptop:/media$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 002: ID 4971:1012 SimpleTech

```

One thing that I am curious about - I am running xfce4 which provides a "Disk Utility". When I run that I can see the disk, and it says the device is '/dev/sdc' which I tried mounting from the terminal but it failed (perhaps my mount command was wrong).

---

### Post by kazztan0325 on 2012-04-10
> **cmanlinux said:**
> One thing that I am curious about - I am running xfce4 which provides a "Disk Utility". When I run that I can see the disk, and it says the device is '/dev/sdc' which I tried mounting from the terminal but it failed (perhaps my mount command was wrong).

Since you are running **'Xfce4 Session'** and if your default file manager were set to **Thunar**, please check following points in **'Settings Manager'**.

- Is the item **'Enable Volume Management'** on 'Advanced' tab in 'File Manager Preferences' _Ticked ON_?

- Are the items **'Mount removable drives when hot-plugged'**, **'Mount removable media when inserted'** and **'Browse removable media when inserted'** on 'Storage' tab in 'Removable Drives and Media' _Ticked ON_?

---

### Post by cmanlinux on 2012-04-11
> **kazztan0325 said:**
> Since you are running **'Xfce4 Session'** and if your default file manager were set to **Thunar**, please check following points in **'Settings Manager'**.

- Is the item **'Enable Volume Management'** on 'Advanced' tab in 'File Manager Preferences' _Ticked ON_?

- Are the items **'Mount removable drives when hot-plugged'**, **'Mount removable media when inserted'** and **'Browse removable media when inserted'** on 'Storage' tab in 'Removable Drives and Media' _Ticked ON_?

I have confirmed that 'Enable Volume Management' is on.

I have also confirmed that the other three options are on under the 'Storage Tab' on 'Removable Media and Drives'.

At one point I had even tried to use Nautilus instead of Thunar thinking that might help - it did not.

Something worth adding - the drive is USB 3.0. I did some quick searching and apparently this should be supported by ubuntu (the kernel?). I might of thought it would be a hardware problem with my laptop, but I was able to mount/use the same drive before when I had debian installed on the same machine.

---

### Post by cmanlinux on 2012-04-17
Hi again - I'm marking this as solved.

After searching around some on my dmesg output I found some threads that suggested downgrading/upgrading your kernel.

And I did just that ...

```

cman@ubuntu-laptop:~$ uname -r
3.2.15-030215-generic

```

I am now able to mount the harddrive. Thanks to everyone for your help.

---

### Post by kazztan0325 on 2012-04-17
> **cmanlinux said:**
> After searching around some on my dmesg output I found some threads that suggested downgrading/upgrading your kernel.
...

I am now able to mount the harddrive. Thanks to everyone for your help.

You are welcome, cmanlinux!
However I myself could not help you...

I'm glad to hear you have solved the problem.
I never thought that the problem has to do with downgrading/upgrading kernel.
Your solution would be beneficial for us if we encountered with the same/similar problem.

Thank you!

---

