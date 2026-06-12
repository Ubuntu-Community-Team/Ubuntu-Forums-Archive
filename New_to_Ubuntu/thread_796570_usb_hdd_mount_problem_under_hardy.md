---
title: "usb hdd mount problem under hardy"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by lman_271860 on 2008-05-16
newbee needs some help

have a usb hard drive that was working under gustsy and now broken under hardy

when plugged in it does not auto mount
i have attached screen shot from the logs and show detection etc etc

lsusb shows that the drive is present and the drive works fine when i plug it in to an xp system

any help would be greatly appreciated many thanks in advance

lman_271860[ATTACH]70338[/ATTACH]

---

### Post by lman_271860 on 2008-05-16
[SIZE="6"]oooopppps wrong screenshot[/SIZE]

---

### Post by Xerp on 2008-06-14
Do you have any information on the USB hardware? Does it have any NTFS partitions on it?

---

### Post by lman_271860 on 2008-06-14
the dive is formatted with ntfs

the controller ic has the following markings

ITE
IT8903CE
0606-CXS
ZM9PGA L

---

### Post by lman_271860 on 2008-06-14
i have just got the data sheet for the controller ic

i know xp reports this ic as a hitachi something i will check on my xp system what hardware is reported

---

### Post by lman_271860 on 2008-06-14
something interesting which may be a clue to fixing the problem

i tried the terminal commands and the usb hard drive was not there

i went back to windows xp safely removed hardware

re booted to ubuntu and LEFT THE DRIVE PLUGGED INTO THE USB PORT

the usb hard drive appeared on the desktop

i can mount and un mount the drive with no problems

*************************************************************************
victor@victor-laptop:~$ sudo fdisk -l
[sudo] password for victor: 

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5937    47688921    7  HPFS/NTFS
/dev/hda2            5938       12161    49994280    5  Extended
/dev/hda5            5938       11901    47905798+  83  Linux
/dev/hda6           11902       12161     2088418+  82  Linux swap / Solaris

Disk /dev/sda: 12.0 GB, 12072517632 bytes
255 heads, 63 sectors/track, 1467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25b625b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1466    11775613+   c  W95 FAT32 (LBA)
victor@victor-laptop:~$ 

**************************************************************************

but when i remove the usb lead and plug it back in again same problem does not auto mount

victor@victor-laptop:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5937    47688921    7  HPFS/NTFS
/dev/hda2            5938       12161    49994280    5  Extended
/dev/hda5            5938       11901    47905798+  83  Linux
/dev/hda6           11902       12161     2088418+  82  Linux swap / Solaris
victor@victor-laptop:~$

---

### Post by lman_271860 on 2008-06-14
more information .............


went back to xp and did not remove the hardware safely ie just umplugged the usb hdd

shut the system down

plugged it back in and re booted to ubuntu

usb hdd is on the desktop and will mount and unmount

unplugged the usb hdd and plugged it back in

same problem as before !!!!!!!

Jun 14 14:07:14 victor-laptop kernel: [  761.761199] usb-storage: device found at 4
Jun 14 14:07:14 victor-laptop kernel: [  761.761209] usb-storage: waiting for device to settle before scanning
Jun 14 14:07:14 victor-laptop NetworkManager: <debug> [1213448834.800718] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_13_2_if0_0'). 
Jun 14 14:07:20 victor-laptop kernel: [  771.625109] usb-storage: device scan complete
Jun 14 14:07:26 victor-laptop kernel: [  313.132825] usb 3-1: reset high speed USB device using ehci_hcd and address 4
Jun 14 14:07:36 victor-laptop kernel: [  802.582256] usb 3-1: reset high speed USB device using ehci_hcd and address 4
Jun 14 14:07:36 victor-laptop kernel: [  802.830220] usb 3-1: reset high speed USB device using ehci_hcd and address 4
Jun 14 14:07:46 victor-laptop kernel: [  813.972745] usb 3-1: reset high speed USB device using ehci_hcd and address 4
Jun 14 14:07:47 victor-laptop kernel: [  814.109216] scsi 1:0:0:0: Device offlined - not ready after error recovery

---

### Post by aktiwers on 2008-06-14
Is it 12gb drive?

Then just add it to your fstab. 

Someone correct me if I am wrong or if this approach is wrong for usb drives. I don't use them
myself but have fixed problems with automounting this way. I can see there might be a problem "ejecting" the usbdrive using this method.. donno as I never done it with usbdrives. But anyways, here goes. 

First make a folder to mount it to:
```
sudo mkdir /media/usbdrive
```Then open fstab with text editor:
```
sudo gedit /etc/fstab
```Then add the following linies to the end of that file:
```
/dev/sda1 /media/usbdrive  vfat    noauto,user,umask=0    0 0 
```And save the file.

Now your drive should be mounted all the time.

---

### Post by lman_271860 on 2008-06-14
yes it is the 12 gig drive 

will do and report back

---

### Post by lman_271860 on 2008-06-14
no same problem

will reboot just in case and report back


Jun 14 16:46:12 victor-laptop kernel: [ 3890.949152] Initializing USB Mass Storage driver...
Jun 14 16:46:12 victor-laptop kernel: [ 3890.950683] scsi0 : SCSI emulation for USB Mass Storage devices
Jun 14 16:46:12 victor-laptop kernel: [ 3890.953366] usbcore: registered new interface driver usb-storage
Jun 14 16:46:12 victor-laptop kernel: [ 3890.953375] USB Mass Storage support registered.
Jun 14 16:46:12 victor-laptop kernel: [ 3890.953799] usb-storage: device found at 3
Jun 14 16:46:12 victor-laptop kernel: [ 3890.953801] usb-storage: waiting for device to settle before scanning
Jun 14 16:46:18 victor-laptop kernel: [ 9738.105431] usb-storage: device scan complete
Jun 14 16:46:24 victor-laptop kernel: [ 9745.661701] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:46:34 victor-laptop kernel: [ 9760.562315] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:46:34 victor-laptop kernel: [ 9760.810319] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:46:45 victor-laptop kernel: [ 9772.084602] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:46:45 victor-laptop kernel: [ 9772.217153] scsi 0:0:0:0: Device offlined - not ready after error recovery

---

### Post by aktiwers on 2008-06-14
Yes reboot or restart x (CTRL+ALT+Backspace)

---

### Post by lman_271860 on 2008-06-14
no still the same problem

Jun 14 16:57:46 victor-laptop kernel: [  640.291019] Initializing USB Mass Storage driver...
Jun 14 16:57:46 victor-laptop kernel: [  640.297013] scsi0 : SCSI emulation for USB Mass Storage devices
Jun 14 16:57:46 victor-laptop kernel: [  640.299639] usbcore: registered new interface driver usb-storage
Jun 14 16:57:46 victor-laptop kernel: [  640.300080] USB Mass Storage support registered.
Jun 14 16:57:46 victor-laptop kernel: [  640.300555] usb-storage: device found at 3
Jun 14 16:57:46 victor-laptop kernel: [  640.300562] usb-storage: waiting for device to settle before scanning
Jun 14 16:57:46 victor-laptop NetworkManager: <debug> [1213459066.460858] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6ce_8aa_123456789012_if0'). 
Jun 14 16:57:52 victor-laptop kernel: [  651.098827] usb-storage: device scan complete
Jun 14 16:57:58 victor-laptop kernel: [  263.515706] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:58:08 victor-laptop kernel: [  673.053892] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:58:08 victor-laptop kernel: [  673.301991] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:58:18 victor-laptop kernel: [  684.503970] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 14 16:58:18 victor-laptop kernel: [  684.636436] scsi 0:0:0:0: Device offlined - not ready after error recovery

---

### Post by aktiwers on 2008-06-14
Okay, I suggest you go into fstab again and remove that line again and save the file.
After seaching a little more, I found it is not the right approach to add usb drives in Fstab.

Sorry about that.

That error message sounds a little like the filesystem is damaged or something. Have you tried running:
```
chkdsk /r USBDRIVELETTER
```
From Windows??

---

### Post by lman_271860 on 2008-06-14
scanned it under windows drive is fine

just to highlight previous results

i left the usb hard drive plugged in when rebooting to ubuntu and it appears on the desktop

i can mount and unmount without problems

when i unplug the cable and plug it back in that is when the problem occurs

---

### Post by spiderbatdad on 2008-06-14
:popcorn:

---

### Post by Canis familiaris on 2008-06-14
> **spiderbatdad said:**
> :popcorn:

Isn't this program installed by default?

---

### Post by lman_271860 on 2008-06-14
just did a test on the drive under ubuntu

copied 700 meg file from usb hdd to laptop no problems
coped 700 meg file from laptop to usb hdd no problems

---

### Post by Canis familiaris on 2008-06-14
@OP
Did you try what spiderbatdad said?

---

### Post by cheezewiz25 on 2008-06-14
I had a similar problem with a hard drive mounted in a usb aluminum housing.  Whenever I would unplug it from Windows and move it to Ubuntu, it would give me an error message saying that it was still being used by windows.  I ended up having to uninstall it from the device manager of windows before I could move it to my Linux box.  Don't know if this helps or not, but maybe worth a try?

---

### Post by lman_271860 on 2008-06-14
people thanks for all your help so far

and i feel i am making progress

the usb hdd drives works fine as long as i boot ubuntu with it plugged in

so the drivers must work ok

i have copied files back and forward with no problems 700 meg

the problem occurs when i plug the hdd in after i have booted ubuntu

i only discovered that it works when plugged in when booting today

all other usb pens work fine no problems

---

### Post by azimuth on 2008-06-14
edit : Dupe

---

### Post by azimuth on 2008-06-14
I have some observations that may help. These are just from my own machines. but may extend to many others.

USB Hard drives that are not properly unmounted in Windows XP are not available to Ubuntu. This includes just unplugging them, powering them off and if the XP machine was suspended or hibernated rather than shut down.

Internal HHDs with ntfs partitions do not automount in Ubuntu if XP was hibrinated.

Ubuntu is very polite in not using partitions that it thinks are in use by another OS.

There are probably very good reasons for the error messages one gets in either XP or Ububtu, when they "just unplug" a USB Storage device without first unmounting it.

---

### Post by cariboo on 2008-06-14
If you look at the last line of the listing you posted:

```
un 14 16:58:18 victor-laptop kernel: [ 684.636436] scsi 0:0:0:0: Device offlined - not ready after error recovery
```

It will give you a clue what is happening. For some reason the usb drive is not unmounting properly when you diconnect the drive.

You will only get this type of error with an NTFS file system, so other usb storage devices have no bearing on this problem.

Jim

---

### Post by azimuth on 2008-06-14
> **cariboo907 said:**
> 

You will only get this type of error with an NTFS file system, so other usb storage devices have no bearing on this problem.


I have a couple of Kingston Data travelers (1GB) that are formated FAT16 and FAT32. One of them doesn't automount in Ubuntu if it was hibernated in XP. I don't remember which one now, but it doesn't matter since I changed my sloppy ways and now make a habit of unmounting them when I am through with them in either OS.

ps. Jim, I see you are in Williams Lake. I used to have family out in the Nemiah Valley. Beautiful Country!

---

### Post by lswest on 2008-06-15
> **aktiwers said:**
> Is it 12gb drive?

Then just add it to your fstab. 

Someone correct me if I am wrong or if this approach is wrong for usb drives. I don't use them
myself but have fixed problems with automounting this way. I can see there might be a problem "ejecting" the usbdrive using this method.. donno as I never done it with usbdrives. But anyways, here goes. 

First make a folder to mount it to:
```
sudo mkdir /media/usbdrive
```Then open fstab with text editor:
```
sudo gedit /etc/fstab
```Then add the following linies to the end of that file:
```
/dev/sda1 /media/usbdrive  vfat    noauto,user,umask=0    0 0 
```And save the file.

Now your drive should be mounted all the time.

Actually, that entry you give won't work, the device is ntfs, not vfat.  Try replacing vfat with ntfs-3g, it might work then.  Not sure if it will help though, much easier to just remove the device safely (right-click and then "eject"/"unmount" in Ubuntu, or safely remove hardware in XP).

---

### Post by lman_271860 on 2008-06-16
no difference

problem is still the same

i think the biggest clue is that when i re boot ubuntu it sees the usb hdd no problems at all

i can mount and unmount the drive at will

it is only when i unplug the usb cable and then plug it back in again ubuntu has the problems

i have tried to remove hardware safely under xp and it does not make any difference at all

as long as i re boot ubuntu with the us hdd plugged in it works fine

had to remove the line for it to work as described

/dev/sda1 /media/usbdrive  ntfs-3g    noauto,user,umask=0    0 0

---

