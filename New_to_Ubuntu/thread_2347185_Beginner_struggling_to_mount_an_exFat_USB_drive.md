---
title: "Beginner struggling to mount an exFat USB drive"
date: 2016-12-22
forum: New to Ubuntu
---

### Post by simapple on 2016-12-22
Here is the output from the terminal...

From sudo fdisk -l:

Disk /dev/sdb: 746.5 GiB, 801569726464 bytes, 1565565872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Size Id Type
/dev/sdb1           1 4294967295 4294967295   2T ee GPT


simon@PMS-BFSH:~$ sudo mount -t exfat /dev/sdb1 /media/external
FUSE exfat 1.2.3
ERROR: failed to open '/dev/sdb1': No such file or directory.

What am I doing wrong?
(thanks for any help in advance)

---

### Post by TheFu on 2016-12-22
The error seems to say that the OS isn't seeing sdb1, but fdisk does?  Odd.  Check what **parted** shows. 

The partition doesn't appear to be a known type. Should see something like:
```
$ sudo fdisk -l /dev/sdh

Disk /dev/sdh: 62.5 GB, 62537072640 bytes
255 heads, 63 sectors/track, 7603 cylinders, total 122142720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008805e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1            2048   122142719    61070336    b  W95 FAT32

```  I don't allow exfat in my house. It is a political statement. Also, see how things line up nicely? Please use "code tags", so that happens.

BTW, the "GPT" at the end means you probably shouldn't use fdisk. Use **sudo parted -l** instead to be safer. It is possible the fdisk version used doesn't correctly support GPT disks.

Looks find to me, assuming /media/external exists.  BTW, I'd mount it anywhere except under /media/.  Perhaps /mnt/ext would be better? That area is controlled by the OS for mounts. Mixing manual and OS auto-mounts might cause issues, though I've never seen it.

---

### Post by karl96 on 2016-12-22
Ok i'm really confused and i've been waiting eagerly for someone to post a solution so i'll have a crack. 

First of all, make sure there is actually a file called /dev/sdb1 in the /dev folder. Make sure it's being mounted (should be unless you have some weird setup where it's mounted separately)

What's the output of ```
 dmesg 
```
And ```
 lsusb 
```

So fdisk says it detects it... So issue is either with (quick brainstorm):
fdisk being a liar
kernel not handling the fs properly
mount gaining intelligence and denying you access for laughs

---

### Post by TheFu on 2016-12-22
Please only post ***relevant parts* of dmesg**. We don't need or want the whole thing.
Also - [https://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working](https://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working) might help, though it is for unsupported releases at this point.

Which ubuntu version/release is being run?

---

### Post by simapple on 2016-12-22
Thank you for looking at this,
unfortunately exFAT is a neccesity (as far as I can tell) as I have files over 4gb on it, and I also need it to work on windows.

parted shows an error when I run the command you suggested
'Error: Invalid argument during seek for read on /dev/sdb' 
have you any idea what might cause this?

---

### Post by TheFu on 2016-12-22
> **simapple said:**
> parted shows an error when I run the command you suggested
'Error: Invalid argument during seek for read on /dev/sdb' 
have you any idea what might cause this?

I can only guess there is something incompatible between the USB port and USB storage. If it isn't a flash drive, convert it to NTFS.  If it is flash, try a different USB port on the box. Maybe it will have a different USB chip?  Try front vs back ports. Try a USB addon card, not the built-in MB ports.  Try USB3 vs USB2 ports.

Also, try a different cable. Not all USB cables are created the same.

That's all I got.  I've seen incompatible flash drives with some of my systems. No way to predict which will or won't work that I've found. Cheap, expensive, no-name, brand-name ... doesn't seem to matter.  

My FAT32 storage sometimes needs to be re-formatted after being used in a dedicated video recorder.  Don't know why, but the device seems to corrupt the file system for some reason.  That device only supports FAT32 or NTFS and only if there is 1 partition on the disk AND only if the disk is externally powered.

Did the disk ever work on this machine running Linux?

---

### Post by simapple on 2016-12-22
The disk works fine in windows, this is my only Linux machine and its never worked on it
I've tried all the USB ports on this machine (its a laptop),
I'm guessing this is not a goer!

---

### Post by TheFu on 2016-12-22
RELEVANT dmesg and lsusb as requested above?

I would prefer **lsusb -t**, if possible.

---

### Post by simapple on 2016-12-22
Sorry, I actually missed that post somehow

Here are what I think may be the relevant parts of dmesg:
```
[ 4736.550175] usb-storage 2-4:1.0: USB Mass Storage device detected
[ 4736.553895] scsi host10: usb-storage 2-4:1.0
[ 4737.553059] scsi 10:0:0:0: Direct-Access     WD       30EZRX External  1.75 PQ: 0 ANSI: 4
[ 4737.554511] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 4737.557178] sd 10:0:0:0: [sdb] 1565565872 512-byte logical blocks: (802 GB/747 GiB)
[ 4737.558052] sd 10:0:0:0: [sdb] Write Protect is off
[ 4737.558061] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4737.558813] sd 10:0:0:0: [sdb] No Caching mode page found
[ 4737.558823] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 4744.437405] sd 10:0:0:0: [sdb] Attached SCSI disk
[ 8574.284162] ------------[ cut here ]------------
[ 8574.284218] WARNING: CPU: 0 PID: 2383 at /build/linux-dcxD3m/linux-4.4.0/drivers/gpu/drm/i915/intel_display.c:12740 intel_modeset_check_state+0x5b3/0x8a0 [i915]()
[ 8574.284221] encoder detached but still enabled on pipe A.
[ 8574.284224] Modules linked in: uas usb_storage uvcvideo videobuf2_vmalloc videobuf2_memops dell_wmi gpio_ich videobuf2_v4l2 sparse_keymap snd_hda_codec_idt videobuf2_core v4l2_common dell_laptop videodev snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec wl(POE) media dcdbas snd_hda_core dell_smm_hwmon snd_hwdep coretemp input_leds joydev serio_raw r852 sm_common nand nand_ecc nand_bch snd_pcm bch nand_ids r592 mtd lpc_ich memstick snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq cfg80211 snd_seq_device snd_timer mac_hid snd soundcore shpchp parport_pc ppdev lp parport autofs4 psmouse firewire_ohci ahci libahci firewire_core crc_itu_t sdhci_pci sdhci pata_acpi sky2 fjes i915 video i2c_algo_bit drm_kms_helper wmi syscopyarea sysfillrect sysimgblt fb_sys_fops drm


```

and here is the output from lsusb -t:

```
simon@PMS-BFSH:~$ lsusb -t
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
    |__ Port 4: Dev 8, If 0, Class=Mass Storage, Driver=usb-storage, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    |__ Port 1: Dev 2, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 1: Dev 2, If 1, Class=Video, Driver=uvcvideo, 480M

```

Also I checked > First of all, make sure there is actually a file called /dev/sdb1 in the /dev folder
There isn't a file called sdb1, however there is a file called sdb

so i tried with that:
```
simon@PMS-BFSH:~$ sudo mount -t exfat /dev/sdb /media/external
FUSE exfat 1.2.3
ERROR: exFAT file system is not found.
```

I've double and triple checked on my windows machine - the file system is exFAT

---

### Post by TheFu on 2016-12-22
Whatever is happening, the USB device isn't being correctly discovered under Linux.  I would look at the USB interface chip for that drive.  **lspci -tv** and **sudo lshw -C storage** might provide more information.

Long term, if the device is a 3TB WD HDD, then it needs a GPT partition table (MS-Dos only allows 2TB to be seen) and I'd switch to NTFS for the better cross-platform support.  The NTFS part is optional and probably will not help discovery.

If this is flash storage (not spinning rust), I don't have a good answer.

---

### Post by Morbius1 on 2016-12-23
This is more of a random thought but I think we all agree that as long as you added support for exfat this usb device should automount to /media/username/something the instant you plug it in the laptop. Shouldn't need to mount it manually.

Since it works in Windows is there any possibility that the partition was encrypted in Windows?

---

