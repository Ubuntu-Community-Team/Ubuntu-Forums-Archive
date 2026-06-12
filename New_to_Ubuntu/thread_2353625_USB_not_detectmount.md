---
title: "USB not detect/mount"
date: 2017-02-23
forum: New to Ubuntu
---

### Post by sumeetg on 2017-02-23
I formatted my Kingston 32GB otg usb with 3rd party software in windows now it could not detect/mount in windows either Ubuntu. Disk utility detect my usb but shows no media, i also tried g*parted, kde partition manager, KVPM, *but all could not detect my usb.

i also tried *fdisk -l* command but it also could not detect my usb 
and when i run dmesg command then result is 

```
sudo dmesg

[  275.927987] usb 2-1.2: new high-speed USB device number 3 using ehci-pci
[  276.079517] usb 2-1.2: New USB device found, idVendor=13fe, idProduct=5100
[  276.079528] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  276.079534] usb 2-1.2: Product: USB DISK 30X            
[  276.079538] usb 2-1.2: Manufacturer:                         
[  276.079542] usb 2-1.2: SerialNumber: 000000000000
[  276.203602] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[  276.205411] scsi host6: usb-storage 2-1.2:1.0
[  276.205670] usbcore: registered new interface driver usb-storage
[  276.219144] usbcore: registered new interface driver uas
[  277.206362] scsi 6:0:0:0: Direct-Access              USB DISK 30X     1.00 PQ: 0 ANSI: 6
[  277.207671] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  277.211881] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

it detect my usb as sdb
then i also tried to open it with fdisk, but not work

```

sudo fdisk /dev/sdb
unable to open dev/sdb: no medium found

```


I also tried list **ls** command 
```
root@sumit-gehi:~# ls -l /dev/sdb
brw-rw---- 1 root disk 8, 16 &#1601;&#1585;&#1608;&#1585;&#1610; 23 22:11 /dev/sdb

```

also tried sudo blkid but no luck

I think my usb's partition has gone, i need to create partition, so how to create partition on usb?

need help
i have attached screenshots of disk utility

note windows also detect my usb with no media so i try to create partition in windows through ***diskpart*** by following commands *c**reate partition primary, create volume simple, clean, clean attributes*****,** but no luck

[ATTACH=CONFIG]273866[/ATTACH]  [ATTACH=CONFIG]273867[/ATTACH]

---

### Post by guinea2 on 2017-02-25
I would try to format it with the regular windows formatting program that you can do by right clicking on the USB and see if that works. I wouldn't use 3rd party software for formatting a USB because it could mess it up.

---

