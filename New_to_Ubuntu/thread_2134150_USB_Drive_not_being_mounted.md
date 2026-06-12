---
title: "USB Drive not being mounted"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by Napes90 on 2013-04-10
I currently have a 4GB USB flash drive which will not automount when inserted into my machine. After reading around and trying a few things i get the output of lsusb:

```

Bus 002 Device 009: ID 1e3d:8246 Chipsbank Microelectronics Co., Ltd 

```

Which shows that the device is being detected at least.

After inserting the drive i ran dmesg and received this output:

```


[ 7465.477608] usb 2-1.1: new high-speed USB device number 10 using ehci_hcd
[ 7465.570698] usb 2-1.1: New USB device found, idVendor=1e3d, idProduct=8246
[ 7465.570708] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7465.570714] usb 2-1.1: Product: V88             
[ 7465.570719] usb 2-1.1: Manufacturer: V88     
[ 7465.570723] usb 2-1.1: SerialNumber: 17205401F37E6C12
[ 7465.571385] scsi11 : usb-storage 2-1.1:1.0
[ 7466.568584] scsi 11:0:0:0: Direct-Access     V88      V88              5.00 PQ: 0 ANSI: 2
[ 7466.570505] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 7466.571206] sd 11:0:0:0: [sdb] 8108032 512-byte logical blocks: (4.15 GB/3.86 GiB)
[ 7466.571699] sd 11:0:0:0: [sdb] Write Protect is off
[ 7466.571707] sd 11:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 7466.572224] sd 11:0:0:0: [sdb] No Caching mode page present
[ 7466.572232] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 7466.576411] sd 11:0:0:0: [sdb] No Caching mode page present
[ 7466.576423] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 7466.577816]  sdb: sdb1
[ 7466.580438] sd 11:0:0:0: [sdb] No Caching mode page present
[ 7466.580446] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 7466.580452] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 7497.111117] usb 2-1.1: reset high-speed USB device number 10 using ehci_hcd
[ 7507.257616] usb 2-1.1: reset high-speed USB device number 10 using ehci_hcd
[ 7523.393801] usb 2-1.1: reset high-speed USB device number 10 using ehci_hcd
[ 7523.561516] usb 2-1.1: reset high-speed USB device number 10 using ehci_hcd
[ 7532.657235] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:b0:b2:dc:43:50:04:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=5452 PROTO=2 
[ 7533.707882] usb 2-1.1: reset high-speed USB device number 10 using ehci_hcd
[ 7533.800363] sd 11:0:0:0: Device offlined - not ready after error recovery
[ 7533.800382] sd 11:0:0:0: [sdb] Unhandled error code
[ 7533.800388] sd 11:0:0:0: [sdb]  
[ 7533.800392] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[ 7533.800396] sd 11:0:0:0: [sdb] CDB: 
[ 7533.800399] Read(10): 28 00 00 7b b7 80 00 00 08 00
[ 7533.800414] end_request: I/O error, dev sdb, sector 8107904
[ 7533.800422] Buffer I/O error on device sdb, logical block 1013488
[ 7533.800451] sd 11:0:0:0: rejecting I/O to offline device
[ 7533.800461] sd 11:0:0:0: killing request


```

I see there are some I/O errors, but I'm not sure how to go about solving them.

Any help would be very much appreciated.

---

### Post by Bashing-om on 2013-04-10
Napes90; Hi ! Welcome to the forum .

I would question the file integrity. What file format is present on the device ?
NTFS, FAT == Windows
ext4 == linux

Windows tools for Windows file systems; ubuntu tools for ubuntu file systems.

Can "fdisk" see the device ?
```
sudo fdisk -l
```
What does GParted (liveCD) show for the file system ?[INDENT=2]
just my thought

[/INDENT]

---

### Post by Napes90 on 2013-04-10
fdisk does not recognise the device at all, and neither does gparted so I'm not quite sure what filesystem is used. It doesn't seemed to be recognised on any windows pc's either. Is it possible that it may be just a hardware fault?

---

### Post by Bashing-om on 2013-04-10
Napes90;
Harware failure is possible, as always; but, as "lsusb" finds the device, indicates to me hardware is good, superblock corrupted ?
Does parted see anything ?
```
sudo parted /dev/sdb unit s print
``` assuming that sda is the hard drive and sdb is the usb device.

And might consider wiping that usb drive with the "dd" command ...see if it can be restored. This will over write all data on the disk and maybe should only be done as a means of last resort (???)[INDENT=2]
nothing lost in look'n

[/INDENT]

---

### Post by leunam12 on 2013-04-10
Has this USB stick been on a windows computer? Sometimes removing the USB drive from Windows without doing a safe removal procedure first will render the drive unreadable or read-only. It has happened to me in the past. Going back to windows, inserting the drive and then removing safely restores the drive to normal operation.

---

### Post by Bashing-om on 2013-04-10
+1 for leunam12; good call !

---

### Post by leunam12 on 2013-04-12
I'm glad it helped; I've been in the same situation many times pulling my hair andtrying to find out what's wrong with the USB stick that was working fine the day before.

---

