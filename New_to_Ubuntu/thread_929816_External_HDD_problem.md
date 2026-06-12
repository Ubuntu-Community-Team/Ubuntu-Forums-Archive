---
title: "External HDD problem"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by gmarcel on 2008-09-25
Hello Everybody,
I bought a new hard disk to my HP zv5000 laptop. I installed WinXP and Ubuntu. Now I'd like to copy my data from old hard disk to my new hard disk. Unfortunately, none of the system see the external hard disk. Windows shows that there is usb pluging in, but doesn't show any hard disk in the explorer. How can I fix/test this problem under Win or Ubuntu ? Would appreciate any help, since there is a PhD thesis on the old disk which i need within 5 days...... HELP

Lsusb: 
Bus 003 Device 006: ID 058f:6390 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 062a:0003 Creative Labs 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Alcor is my external HDD

DMESG gives:
usb 3-2: new high speed USB device using ehci_hcd and address 3
[  257.432816] usb 3-2: configuration #1 chosen from 1 choice
[  259.713412] usbcore: registered new interface driver libusual
[  259.784563] Initializing USB Mass Storage driver...
[  259.791824] scsi2 : SCSI emulation for USB Mass Storage devices
[  259.794163] usbcore: registered new interface driver usb-storage
[  259.794699] USB Mass Storage support registered.
[  259.795122] usb-storage: device found at 3
[  259.795128] usb-storage: waiting for device to settle before scanning
[  264.792576] usb-storage: device scan complete
[  270.405610] usb 3-2: reset high speed USB device using ehci_hcd and address 3
[  293.151418] usb 3-2: reset high speed USB device using ehci_hcd and address 3
[  316.324225] usb 3-2: reset high speed USB device using ehci_hcd and address 3
[  318.292624] usb 3-2: reset high speed USB device using ehci_hcd and address 3
[  319.447009] scsi 2:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
[  319.460985] sd 2:0:0:0: [sdb] 4206788254 512-byte hardware sectors (2153876 MB)
[  319.461844] sd 2:0:0:0: [sdb] Write Protect is off
[  319.461853] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  319.461858] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  319.463091] sd 2:0:0:0: [sdb] 4206788254 512-byte hardware sectors (2153876 MB)
[  319.463967] sd 2:0:0:0: [sdb] Write Protect is off
[  319.463975] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  319.463979] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  319.463987]  sdb:<6>sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  319.468721] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  319.468738] end_request: I/O error, dev sdb, sector 0
[  319.468744] Buffer I/O error on device sdb, logical block 0
[  319.468751] Buffer I/O error on device sdb, logical block 1
[  319.468756] Buffer I/O error on device sdb, logical block 2
[  319.468762] Buffer I/O error on device sdb, logical block 3


Can somebody help me? Anybody...please ....I'm new to Ubuntu that is why I decided to post this thread here. Dear Moderator, if this is the wrong place, could you be so kind and move it to the proper place of the forum.
Sincerely, 
:-(

---

### Post by Peter09 on 2008-09-25
This is plucking at straws but is the old usb disk running on USB 2? Is your BIOS set up for legacy USB?

---

### Post by gmarcel on 2008-09-25
Now I connect my HDD via usb 2.0. How to check out my BIOS legacy?  I can easily plug in small USB stick (2Gb) and it will be automatically  mounted, and I can read it and write it. But with this HDD I cannot do anything :-( On this HDD (80Gb) Windows and Suse installed. I just want to open it and take my files from there.

---

### Post by Peter09 on 2008-09-25
You can get into most BIOS by hitting the delete key at the beginning of the boot sequence. You need to be careful when you go in there not to change anything else. Look for the USB specification, it will tell you if it supports legacy USB, if not you can enable it.

---

### Post by gmarcel on 2008-09-25
it support legacy.....ok...any other idea ?

---

### Post by Peter09 on 2008-09-25
What filesystem is on this drive?

---

### Post by Yannick Le Saint kyncani on 2008-09-25
Sigh, why oh why don't people ever use backups ... well, obviously those who do don't have to come here for help.

Anyway.

> **gmarcel said:**
> [  319.463987]  sdb:<6>sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  319.468721] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  319.468738] end_request: I/O error, dev sdb, sector 0
[  319.468744] Buffer I/O error on device sdb, logical block 0
[  319.468751] Buffer I/O error on device sdb, logical block 1
[  319.468756] Buffer I/O error on device sdb, logical block 2
[  319.468762] Buffer I/O error on device sdb, logical block 3

This looks like a dying disk. So, you could :

- Make an image of your dying disk using ddrescue (in package gddrescue).

- Put your dying disk in a safe location and work on the image from now on.

- Use photorec to recover whatever you can. As I understand it, photorec should be able to recover almost everything.

Good luck. And from now on, use backups (a little late for that though).

---

### Post by gmarcel on 2008-09-25
please tell me what exactly i have to do now.......
i installed ddrescue...and now i have to write what? 
ddresue /dev/sd6 /media/data2  ..how to understand that it is sd6?or 5? or 4?

i am reallly sorry for all my problems

---

### Post by gmarcel on 2008-09-25
ok it is working

---

### Post by Yannick Le Saint kyncani on 2008-09-25
> **gmarcel said:**
> ok it is working

Does that mean you're done making an image with ddrescue and are now in the process of recovering your files with photorec ?

---

### Post by gmarcel on 2008-09-25
no no ..it is still copying data....i am just scared that it says rescued: 0B  ,  errsize 87500Mb, and my hard disck in principe 80GB, so where it is come from?

---

### Post by Yannick Le Saint kyncani on 2008-09-25
> **gmarcel said:**
> i am just scared that it says rescued: 0B  ,  errsize 87500Mb

Rescued 0B ? Well that's no good, it means not a single byte has been rescued so far.

If the error size is greater than one percent of the rescue size on a disk, it should mean that the disk is heavily damaged (as far as I'm concerned).

0% rescued is definitely wrong.

So could you :

- Stop the ddrescue'ing thing (0B rescued means you're not getting anything out of it).

- Paste the output of dmesg (the last 20 lines or so), so that we can see why ddescue cannot rescue anything.

- Paste the ddrescue command you used, because 0B rescued is so abnormal that chances are you've made an error.

- Paste the output of sudo fdisk -l ,so that we know what ddrescue command should have been used.

- Unplug the disk, plug it in and paste the last lines of dmesg, because if the usb is not working, that would appear there.

- Slap yourself, because you don't use backups, so you deserve it.

---

### Post by gmarcel on 2008-09-26
Morning everybody, 

Firstly, I started from you last idea..not just slaped...NO MORE CHOCOLATE (for 1 week)!!!!!
 
1. i stopped ddrescue

2.  ddrescue /dev/sdc /media/Bluemedia/obraz.img  
sdc -this is "sick" HDD 
Bluemedia - is external usb 2.0 HDD with 200Gb free space

root@bon:/media/Bluemedia/recover# ddrescue /dev/sdc /media/Bluemedia/obraz.img
rescued:         0 B,  errsize:    255 MB,  current rate:        0 B/s
   ipos:   255197 kB,   errors:    3894,    average rate:        0 B/s
  opos:   255197 kB



3.  This is the output from dmesg:

[ 1999.978153] end_request: I/O error, dev sdc, sector 0
[ 1999.981483] sd 4:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 1999.981492] sd 4:0:0:0: [sdc] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1999.981505] end_request: I/O error, dev sdc, sector 0
[ 1999.985740] sd 4:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 1999.985751] sd 4:0:0:0: [sdc] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1999.985766] end_request: I/O error, dev sdc, sector 2
[ 2036.806561] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode2.fw" not found or load failed.
[ 2036.806575] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).
[ 2177.878658] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode2.fw" not found or load failed.
[ 2177.878678] b43legacy-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 3).


Did I forget something? 
Thank you guys for your good mood :-) It helps a lot !!!!

---

### Post by gmarcel on 2008-09-26
Sorry, here is the rest: 

root@bon:/media/Bluemedia/recover# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06880687

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1913    15366141    7  HPFS/NTFS
/dev/sda2            1914       19457   140922180    f  W95 Ext'd (LBA)
/dev/sda5            1914        2048     1084356   82  Linux swap / Solaris
/dev/sda6            2049        3599    12458376   83  Linux
/dev/sda7            3600       11506    63512946    7  HPFS/NTFS
/dev/sda8           11507       19457    63866376    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb218172

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708832    5  Extended
/dev/sdb5               1       48641   390708831+   6  FAT16

---

### Post by Peter09 on 2008-09-26
Are you sure that legacy support is enabled in your BIOS. Looking at the errors in dmesg there are lines that indicate that it is not.

---

### Post by gmarcel on 2008-09-26
Please, one more time how I can be sure that it is enable :-( Usually, I'm not that stupid, I'm just nervous now :-((((

---

### Post by Peter09 on 2008-09-26
The trouble is that every BIOS is slightly different, so is difficult to say exactly how to tell.

You need to go into your BIOS. Somewhere in there you will find the specification for USB support. It will specify USB 2, but will also say something like, enable legacy support. You can normally toggle this from off to on and back. Then you need to save and exit.

---

### Post by gmarcel on 2008-09-26
I'm now in Bios, there is nothing about legacy support, or better to say there is nothing about USB. The only thing I have here is Accessibility options: Parallel port mode ECP/EPP. That is it..You think this error message from my dmesg can be a problem? Why do I see then another HDD disk?

---

### Post by Peter09 on 2008-09-26
Think you may have a problem because of lines like

> [ 2036.806561] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode2.fw" not found or load failed.

in dmesg.

Some of the options in your BIOS will have a menu underneath them. You need to go down through each and look for the USB support.

It should be in one of them.

In the event of a screw up just exit without saving.

---

### Post by gmarcel on 2008-09-26
Ok, I have another desktop here, and here is the dmesg message 

sd 7:0:0:0: Attached scsi generic sg3 type 0
usb-storage: device scan complete
usb 6-4: USB disconnect, address 5
usb 6-4: new high speed USB device using ehci_hcd and address 6
usb 6-4: device descriptor read/64, error -71
usb 6-4: configuration #1 chosen from 1 choice
scsi8 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
usb 6-4: reset high speed USB device using ehci_hcd and address 6
usb 6-4: device descriptor read/64, error -71
usb 6-4: reset high speed USB device using ehci_hcd and address 6
usb 6-4: device descriptor read/64, error -71
  Vendor: Generic   Model: USB Disk          Rev: 9.02
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sdc: 4206788286 512-byte hdwr sectors (2153876 MB)
sdc: Write Protect is off
sdc: Mode Sense: 03 00 00 00
sdc: assuming drive cache: write through
SCSI device sdc: 4206788286 512-byte hdwr sectors (2153876 MB)
sdc: Write Protect is off
sdc: Mode Sense: 03 00 00 00
sdc: assuming drive cache: write through
 sdc:<6>sd 8:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
    <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
end_request: I/O error, dev sdc, sector 0
printk: 598 messages suppressed.
Buffer I/O error on device sdc, logical block 0
Buffer I/O error on device sdc, logical block 1
Buffer I/O error on device sdc, logical block 2
Buffer I/O error on device sdc, logical block 3
sd 8:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
    <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
end_request: I/O error, dev sdc, sector 0
Buffer I/O error on device sdc, logical block 0
sd 8:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
    <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
end_request: I/O error, dev sdc, sector 2
Buffer I/O error on device sdc, logical block 1
Buffer I/O error on device sdc, logical block 2
Buffer I/O error on device sdc, logical block 3
 unable to read partition table
sd 8:0:0:0: Attached scsi disk sdc
sd 8:0:0:0: Attached scsi generic sg3 type 0
usb-storage: device scan complete
sd 8:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
    <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
end_request: I/O error, dev sdc, sector 4206788096
Buffer I/O error on device sdc, logical block 2103394048
Buffer I/O error on device sdc, logical block 2103394049
sd 8:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
    <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
end_request: I/O error, dev sdc, sector 4206788096
sd 8:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
    <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
end_request: I/O error, dev sdc, sector 4206788098

---

### Post by gmarcel on 2008-09-26
So it doesn't work anyway :-(

---

### Post by Peter09 on 2008-09-26
OK, found this as a potential solution - try it by copying into a terminal-

```
 
echo N > /sys/module/usbcore/parameters/old_scheme_first


```
If you unplug the USB Disk and plug it in again you should be able to mount it.

---

### Post by Peter09 on 2008-09-26
if that does not work reboot and try

```
echo -1 >/sys/module/usbcore/parameters/autosuspend
```

---

### Post by gmarcel on 2008-09-26
This a response to ur first command:

[ 2879.564431] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.564440] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.564451] end_request: I/O error, dev sdb, sector 0
[ 2879.566808] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.566816] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.566828] end_request: I/O error, dev sdb, sector 1
[ 2879.566848] ldm_validate_partition_table(): Disk read failed.
[ 2879.569179] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.569189] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.569200] end_request: I/O error, dev sdb, sector 0
[ 2879.571556] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.571565] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.571577] end_request: I/O error, dev sdb, sector 1
[ 2879.573935] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.573944] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.573956] end_request: I/O error, dev sdb, sector 0
[ 2879.576310] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.576319] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.576332] end_request: I/O error, dev sdb, sector 1
[ 2879.578839] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.578849] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.578863] end_request: I/O error, dev sdb, sector 0
[ 2879.581181] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.581191] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.581203] end_request: I/O error, dev sdb, sector 1
[ 2879.583555] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.583565] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.583576] end_request: I/O error, dev sdb, sector 0
[ 2879.585927] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.585936] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.585948] end_request: I/O error, dev sdb, sector 1
[ 2879.585968] Dev sdb: unable to read RDB block 0
[ 2879.588302] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.588311] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.588323] end_request: I/O error, dev sdb, sector 0
[ 2879.590676] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.590685] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.590697] end_request: I/O error, dev sdb, sector 1
[ 2879.593049] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.593058] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.593070] end_request: I/O error, dev sdb, sector 0
[ 2879.595425] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.595434] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.595446] end_request: I/O error, dev sdb, sector 1
[ 2879.597923] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.597932] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.597944] end_request: I/O error, dev sdb, sector 24
[ 2879.600299] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.600308] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.600320] end_request: I/O error, dev sdb, sector 25
[ 2879.602672] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.602681] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.602693] end_request: I/O error, dev sdb, sector 24
[ 2879.605048] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.605057] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.605069] end_request: I/O error, dev sdb, sector 25
[ 2879.607421] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.607430] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.607441] end_request: I/O error, dev sdb, sector 0
[ 2879.609797] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.609806] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.609818] end_request: I/O error, dev sdb, sector 1
[ 2879.612170] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.612179] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.612190] end_request: I/O error, dev sdb, sector 0
[ 2879.614546] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.614555] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.614567] end_request: I/O error, dev sdb, sector 1
[ 2879.614586]  unable to read partition table
[ 2879.614682] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 2879.614777] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 2879.857136] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.857150] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.857170] end_request: I/O error, dev sdb, sector 0
[ 2879.860493] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.860502] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.860514] end_request: I/O error, dev sdb, sector 0
[ 2879.863618] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.863627] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.863639] end_request: I/O error, dev sdb, sector 1
[ 2879.959736] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.959750] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.959769] end_request: I/O error, dev sdb, sector 0
[ 2879.963100] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.963109] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.963121] end_request: I/O error, dev sdb, sector 0
[ 2879.965475] sd 3:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[ 2879.965484] sd 3:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2879.965496] end_request: I/O error, dev sdb, sector 1

---

### Post by gmarcel on 2008-09-26
after rebooting:

  286.213009] end_request: I/O error, dev sdb, sector 0
[  286.215360] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  286.215369] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  286.215380] end_request: I/O error, dev sdb, sector 1
[  286.215891]  unable to read partition table
[  286.215994] sd 2:0:0:0: [sdb] Attached SCSI disk
[  286.216076] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  286.438703] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  286.438718] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  286.438737] end_request: I/O error, dev sdb, sector 0
[  286.442563] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  286.442573] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  286.442585] end_request: I/O error, dev sdb, sector 0
[  286.444937] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  286.444948] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  286.444962] end_request: I/O error, dev sdb, sector 1
[  287.140355] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  287.140369] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  287.140386] end_request: I/O error, dev sdb, sector 0
[  287.143653] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  287.143663] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  287.143677] end_request: I/O error, dev sdb, sector 0
[  287.146028] sd 2:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
[  287.146038] sd 2:0:0:0: [sdb] Device not ready: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  287.146052] end_request: I/O error, dev sdb, sector 1

---

### Post by gmarcel on 2008-09-26
Btw, did I make ddrescue in a right way?

---

### Post by Peter09 on 2008-09-26
Is this for the second command line?

That may need a reboot anyway to get it to work. I have more hope for the second command than the first.

---

### Post by Peter09 on 2008-09-26
Also look here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54273](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/54273)

---

### Post by gmarcel on 2008-09-26
yes message #25 is after 2nd command ....but i think, if it is a problem with usb, then it will not work just on my laptop.  But on the other machine it must work, so it is a really problem with the hard disk. Any other solutions?

---

### Post by Peter09 on 2008-09-26
Well finally out of solutions apart from - have a good look at the usb cable, make sure its in good condition.

Sorry I could not help

---

### Post by gmarcel on 2008-09-26
Wait, so you think it is a problem with the HDD? Anyway, thanks a lot for you r time and help :-) I do appreciate it :-)

---

### Post by Peter09 on 2008-09-26
Error -71 which you are getting is an interface error, but what the problem is exactly I don't know. If the other machine is a windows machine then it must be somewhere in the H/W of the drive.

---

### Post by Yannick Le Saint kyncani on 2008-09-26
> **gmarcel said:**
> Btw, did I make ddrescue in a right way?

Yeah, you did.

Man, does this look bad or what ...

( I don't see any solution )

---

