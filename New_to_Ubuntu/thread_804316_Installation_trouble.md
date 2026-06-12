---
title: "Installation trouble"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by keegs on 2008-05-23
I recently decided to give Ubuntu a try, so I downloaded the latest version (8.04-desktop-i386), checked it with winMD5Sum, and everything checked out.  I burned it with InfraRecorder, then proceeded to nuke my hard drive with Darik's Boot And Nuke (DBAN).  After nuking, I then started up the computer with the Ubuntu disk in the disk drive, it loads for a while, then i get the following:

Boot from CD :

NVIDIA Boot Agent 246.0540
Copyright (C) 2001-2005 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation

CLIENT MAC ADDR: 0004 4B 05 AA 5E GUID: 7343AD1A-064B-0400-0000-000000000000
PXE-E53: No boot filename received

PXE-M0F: Exiting NVIDIA Boot Agent.

NVIDIA Boot Agent 246.0540
Copyright (C) 2001-2005 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation

CLIENT MAC ADDR: 0004 4B 05 AA 5E GUID: 7343AD1A-064B-0400-0000-000000000000
PXE-E53: No boot filename received

PXE-M0F: Exiting NVIDIA Boot Agent.

NVIDIA Boot Agent 246.0540
Copyright (C) 2001-2005 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-E61: Media test Failure, check cable
PXE-MOF: Exiting NVIDIA Boot Agent.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

My specs:
CPU: Intel Core 2 Duo E6750
MB: EVGA 122-CK-NF68-T1 LGA 775 NVIDIA nForce 680i SLI ATX
Video Card: VisionTek X1650 Pro
HDD: Hitachi OA33517 SATA 250gb 7200rpm
Optical: LiteON 20X DVD Writer

Please help, I'm really tired of windows and want to finally make the switch (plus, I need my WoW :wink:). If you need any more info, please let me know.  Thanks.

---

### Post by iaculallad on 2008-05-23
> **keegs said:**
> I recently decided to give Ubuntu a try, so I downloaded the latest version (8.04-desktop-i386), checked it with winMD5Sum, and everything checked out.  I burned it with InfraRecorder, then proceeded to nuke my hard drive with Darik's Boot And Nuke (DBAN).  After nuking, I then started up the computer with the Ubuntu disk in the disk drive, it loads for a while, then i get the following:

Boot from CD :

NVIDIA Boot Agent 246.0540
Copyright (C) 2001-2005 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation

CLIENT MAC ADDR: 0004 4B 05 AA 5E GUID: 7343AD1A-064B-0400-0000-000000000000
PXE-E53: No boot filename received

PXE-M0F: Exiting NVIDIA Boot Agent.

NVIDIA Boot Agent 246.0540
Copyright (C) 2001-2005 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation

CLIENT MAC ADDR: 0004 4B 05 AA 5E GUID: 7343AD1A-064B-0400-0000-000000000000
PXE-E53: No boot filename received

PXE-M0F: Exiting NVIDIA Boot Agent.

NVIDIA Boot Agent 246.0540
Copyright (C) 2001-2005 NVIDIA Corporation
Copyright (C) 1997-2000 Intel Corporation
PXE-E61: Media test Failure, check cable
PXE-MOF: Exiting NVIDIA Boot Agent.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

My specs:
CPU: Intel Core 2 Duo E6750
MB: EVGA 122-CK-NF68-T1 LGA 775 NVIDIA nForce 680i SLI ATX
Video Card: VisionTek X1650 Pro
HDD: Hitachi OA33517 SATA 250gb 7200rpm
Optical: LiteON 20X DVD Writer

Please help, I'm really tired of windows and want to finally make the switch (plus, I need my WoW :wink:). If you need any more info, please let me know.  Thanks.

Did you burn it by using selecting an option which say's "burn image"? You should burn the image to the CD media and not the ISO file on the media.

If that's not the case: Try to open your system BIOS and select the first boot option to CD/DVD drive. Save it then restart your PC with the bootable Ubuntu LiveCD in it. That should do the trick.

---

### Post by keegs on 2008-05-23
I was sure to burn the image, not the ISO file.

Boot order is as follows:
CDROM
Removable
Hard Disk

---

### Post by iaculallad on 2008-05-23
> **keegs said:**
> I was sure to burn the image, not the ISO file.

Boot order is as follows:
CDROM
Removable
Hard Disk

Try testing/booting your newly burned Ubuntu LiveCD using other PC/laptop just to be sure that could really boot.

---

