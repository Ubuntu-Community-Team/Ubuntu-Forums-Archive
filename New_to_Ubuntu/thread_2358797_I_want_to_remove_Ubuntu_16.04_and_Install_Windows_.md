---
title: "I want to remove Ubuntu 16.04 and Install Windows 7"
date: 2017-04-17
forum: New to Ubuntu
---

### Post by rdb3 on 2017-04-17
I have Ubuntu 16.04 installed on a desktop.  I want to remove it and Install Windows 7.  After that is done, I will reinstall Ubuntu 16.04 alongside Windows 7.

Today, I booted from the Windows 7 DVD, clicked on install, selected  custom install, but could not proceed with the installation.  There was a message saying I need to reformat the hard drive to NTFS.

The option to format on that screen was disabled, so could not click on it.

I'm not sure how to proceed at this point. How best to go about this?

Thanks in advance.

---

### Post by Frogs Hair on 2017-04-17
Can you delete and then format from the drive options advanced menu ?

---

### Post by Bucky Ball on 2017-04-17
Boot to a live session from the Ubuntu install media> launch Gparted> right click and unmount partitions (they should already be unmounted)> Devices> Create new partition table.

You will now have a blank drive with unpartitioned space. Right click there and 'New'. Create an NTFS partition.

Might work.

---

### Post by oldfred on 2017-04-17
Is system UEFI or BIOS?
Windows 7 DVD is BIOS boot only, but a copy to flash drive can convert to UEFI boot if desired.

Windows in BIOS mode only installs to MBR(msdos) partitioned drive with a primary(usually sda1, but can be sda1 thru sda4) NTFS formatted partition with the boot flag.

---

### Post by rdb3 on 2017-04-17
Will this work?

1.  Boot with live media....select Try Ubuntu.
2. Open Disks.
3. Select and delete each partition.
4.  Format to NFTS (do I have to create a new partition to do that?)

There are 4 partions on that drive right now:

Filesystem               Partition 1  sda1     56 Gb   Ext 4
Extended Partition   Partition 2   sda2 64 Gb  
Filesystem               Partition 6  sda6      64 Gb   Ext 4
Swap                       Partition 5   sda5   2.1 Gb  Swap

---

### Post by Frogs Hair on 2017-04-17
You can format the entire disk if you don't need anything from those partitions. Did you try the [COLOR=#000000]drive options advanced menu. [/COLOR]

---

### Post by rdb3 on 2017-04-17
I spent the last couple of hours doing it and installed Windows 7 and then Ubuntu 16.04.

Here's what I did:

To delete Ubuntu:
1. Booted from live Ubuntu media (on usb).... selected Try Ubuntu.
2.  Open 'Disks'  (could have used gparted also).
3.  Selected Partition 1 and deleted it.
4.  Created a new partition from that free space (downsized it to 35 GB)  and checked "Compatible with most systems NFTS" selected.

Installed Windows 7.

Installed Ubuntu with option to install alongside Windows 7.  During the install, I was reminded that the other partitions (other than Partition 1) would be formatted.

Thanks for all the replies here.... they were very helpful and I learned a few things along the way.

---

### Post by yancek on 2017-04-17
I'm not familiar with the Advanced Menu referred to in the post above but it seems a bit weird that the windows installer would tell you that you need to format and then not allow it.  There must be an option somewhere.  Formatting is going to remove all data so have backups.  If you can format, you need to format sda1 as that is the only primary partition you currently have.  Might be simpler to overwrite the MBR or delete all partitions once you have your data backed up.

---

### Post by rdb3 on 2017-04-17
> **Frogs Hair said:**
> You can format the entire disk if you don't need anything from those partitions. Did you try the [COLOR=#000000]drive options advanced menu. [/COLOR]

I tried from the advanced menu but it wouldn't let me format.It was like disabled.

---

### Post by rdb3 on 2017-04-17
> **yancek said:**
> I'm not familiar with the Advanced Menu referred to in the post above but it seems a bit weird that the windows installer would tell you that you need to format and then not allow it.  There must be an option somewhere.  Formatting is going to remove all data so have backups.  If you can format, you need to format sda1 as that is the only primary partition you currently have.  Might be simpler to overwrite the MBR or delete all partitions once you have your data backed up.

Yeah, that was strange.

---

### Post by Frogs Hair on 2017-04-17
> **rdb3 said:**
> I tried from the advanced menu but it wouldn't let me format.It was like disabled. 

  In a similar situation I used the delete option in that menu to delete Ubuntu , then the format option became available. After installing Win 7 I shrank the volume from the Windows side and selected install along side from the Ubuntu installer which used the unallocated space created.

---

### Post by rdb3 on 2017-04-17
> **Frogs Hair said:**
> In a similar situation** I used the delete option in that menu to delete Ubuntu , then the format option became available**. After installing Win 7 I shrank the volume from the Windows side and selected install along side from the Ubuntu installer which used the unallocated space created.

The thought of doing that crossed my mind,but I decided to ask on here. Good to know....thanks.  What size did you finally make your Windows 7 partition?

---

### Post by Frogs Hair on 2017-04-17
Subject to change, of course.

---

### Post by rdb3 on 2017-04-17
> **Frogs Hair said:**
> Subject to change, of course.

Got it......thanks!

---

### Post by rdb3 on 2017-04-18
> **oldfred said:**
> Is system UEFI or BIOS?
Windows 7 DVD is BIOS boot only, but a copy to flash drive can convert to UEFI boot if desired.

Windows in BIOS mode only installs to MBR(msdos) partitioned drive with a primary(usually sda1, but can be sda1 thru sda4) NTFS formatted partition with the boot flag.

This was all new to me at the time I first posted. But today, after checking around about where to go to find whether system is UEFI or BIOS, I see this old Compaq Presario (purchased in 2007) is BIOS.  Read your links.... good to know for future reference.... thanks.

---

