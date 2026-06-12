---
title: "USB flash drive force mount/format/..."
date: 2008-08-19
forum: New to Ubuntu
---

### Post by PeeZz on 2008-08-19
Hi all

I had a problem with my ubuntu installation so I thought I could reinstall it via a USB-flash drive. So I followed this guide: [click!]("https://help.ubuntu.com/community/Installation/FromUSBStick"). I used the **UNetbootin** program on Windows (because Ubuntu was broken).
But when the program was copying the files, I got an error saying something about **.exe bla bla use chkdsk*. I removed the flash drive and since then it doesn't work anymore.

When I plug it in under Windows the "safely remove hardware"-icon appears saying a USB-mass storage device is connected. But in *My Computer* when I click **G:** it says **no medium**.

When I do it in Ubuntu dmesg tells me this:
> 
[ 2513.878167] usb 7-2: new high speed USB device using ehci_hcd and address 7
[ 2514.010992] usb 7-2: configuration #1 chosen from 1 choice
[ 2514.011586] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2514.012026] usb-storage: device found at 7
[ 2514.012033] usb-storage: waiting for device to settle before scanning
[ 2515.167576] usb-storage: device scan complete
[ 2515.168458] scsi 8:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 2515.176696] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 2515.176780] sd 8:0:0:0: Attached scsi generic sg3 type 0


But there's nothing I can do with /dev/sdc.

**fdisk -l**
> 
Schijf /dev/sda: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x559f6779

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1291    10364928   27  [onbekend]
/dev/sda2   *        1291       10396    73132884    7  HPFS/NTFS
/dev/sda3           10397       19457    72782482+   5  Uitgebreid
/dev/sda5           10397       11368     7807558+  83  Linux
/dev/sda6           11369       19332    63970798+  83  Linux
/dev/sda7           19333       19457     1004031   82  Linux wisselgeheugen

Schijf /dev/sdb: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x5c74ae42

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS


**fdisk /dev/sdc**
> 
Kan /dev/sdc niet openen

which means 'cannot open /dev/sdc'

**mkfs.ext3 /dev/sdc**
> 
mke2fs 1.40.8 (13-Mar-2008 )
/dev/sdc is het hele apparaat, niet slechts een partitie!
Toch doorgaan? (j,n) j
mkfs.ext3: Geen medium gevonden tijdens bepalen van grootte van bestandssysteem


Any help is welcome! If you think my flash drive is broken, just say it :).

I don't know if I have to post this here or under "hardware & laptops".

Thanks in advance

---

### Post by ggaaron on 2008-08-19
And you have used this commands as root I believe? I'd try gparted - frontend for this commands and see what it has to say - it usually generates some meaningful warnings/errors. Also you could try to format it under Windows. Somewhere in system or something there is a list of all plugged in devices where you can remove/add/resize partitions. Unfortunately (happily?=P) I can't help you in Windows part as I've not used it for a really long time and I don't feel like coming back=)

---

### Post by PeeZz on 2008-08-19
I've used all the commands as root.
And I've tried gparted also but the program doesn't see my drive.
Only the sda and sdb, which are a local and another usb drive.

Formatting under Windows doesn't work because it says there's no medium..

---

### Post by ggaaron on 2008-08-19
Seems hard=/ It is indeed probable that your usb stick is dead. What are permissions on /dev/sdc? Also I'd try to force complete blanking on stick by something like cat /dev/zero > /dev/sdc or dd if=/dev/zero of=/dev/sdc.

---

### Post by PeeZz on 2008-08-19
> **ggaaron said:**
> Seems hard=/ It is indeed probable that your usb stick is dead. What are permissions on /dev/sdc? Also I'd try to force complete blanking on stick by something like cat /dev/zero > /dev/sdc or dd if=/dev/zero of=/dev/sdc.

**cat /dev/zero > /dev/sdc** gives me *access denied*
**dd if=/dev/zero of=/dev/sdc** gives *No medium found*

How can I check the permissions?

I think it's dead too but it's so strange something wrong happened with copying files.. this has 'nothing' to do with the hardware..

---

### Post by ggaaron on 2008-08-19
ls -l /dev/sdc

Possible that hardware broke and this is why copying crashed.

---

### Post by PeeZz on 2008-08-19
> **ggaaron said:**
> ls -l /dev/sdc

brw-rw---- 1 root disk 8, 32 2008-08-19 22:33 /dev/sdc

> **ggaaron said:**
> Possible that hardware broke and this is why copying crashed.

Probably broken then. I'll get a new one then :)

Thanks anyway..

(if someone knows more, don't hesitate to reply!)

---

### Post by zealot_mg on 2008-09-09
please help me, i have the same problem.
[ 4447.947283] usb 3-2: USB disconnect, address 4
[ 4460.056455] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 4460.210508] usb 3-2: configuration #1 chosen from 1 choice
[ 4460.214782] scsi6 : SCSI emulation for USB Mass Storage devices
[ 4460.215307] usb-storage: device found at 5
[ 4460.215309] usb-storage: waiting for device to settle before scanning
[ 4465.210680] usb-storage: device scan complete
[ 4465.213667] scsi 6:0:0:0: Direct-Access     Generic  USB Flash Drive  1.04 PQ: 0 ANSI: 2
[ 4465.219691] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 4465.219740] sd 6:0:0:0: Attached scsi generic sg2 type 0

this is something of the output of dmesg

ls -l /dev/sdb
brw-rw---- 1 root disk 8, 16 2008-09-09 22:15 /dev/sdb

dont know what to do the usb appears at my computer then when i double click it it says there is no media in the drive
:S
anyone

---

### Post by ggaaron on 2008-09-10
Run gparted and see if it discovers the disc. I've had a disc failure myself yesterday, dmesg similar to yours, 'fsisk /dev/sdd' says that it can't read device, gparted don't list the disc. You can't do more=(

---

### Post by zealot_mg on 2008-09-10
so nothing can be done?
its dead?
gparted wont see it :(
ow

---

### Post by ggaaron on 2008-09-10
Test it on other computer, if it is a hard drive connected on usb then it might be the disc, it might be the usb case holding it. So it depends on what you plug in, but test it on other computer, if it's a hard drive then try connecting it directly/in other case. If it doesn't work on multiple machines, then probably it just stopped working...

---

### Post by zealot_mg on 2008-09-10
Noo no, im talking about usb memory stick :S but then I should simply buy another one...

---

