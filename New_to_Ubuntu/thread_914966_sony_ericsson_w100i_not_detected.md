---
title: "sony ericsson w100i not detected"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by zalmoxes on 2008-09-09
i've been trying to connect my phone using the usb cable provided. i switched the device mode to usb storage mode. nothing shows up on ubuntu 8.04 at all.

when
```
lsusb
```
output:
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 007: ID 09da:024f A4 Tech Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 008: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 003: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000 
```

when
```
dmesg | tail
```
output:```

[ 4759.435324] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input13
[ 4759.511694] input,hidraw0: USB HID v1.11 Keyboard [A4Tech RF USB Receiver] on usb-0000:00:1d.2-2
[ 4753.530113] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.1/input/input14
[ 4759.654497] input,hidraw1: USB HID v1.11 Mouse [A4Tech RF USB Receiver] on usb-0000:00:1d.2-2
[ 4835.179067] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.183.41 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=16079 DF PROTO=TCP SPT=1403 DPT=135 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 5189.083574] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=24.64.123.158 DST=192.168.1.102 LEN=516 TOS=0x00 PREC=0x00 TTL=62 ID=25627 PROTO=UDP SPT=15826 DPT=1026 LEN=496 
[ 5189.086357] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=24.64.123.158 DST=192.168.1.102 LEN=516 TOS=0x00 PREC=0x00 TTL=62 ID=25629 PROTO=UDP SPT=15826 DPT=1028 LEN=496 
[ 5189.086831] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=24.64.123.158 DST=192.168.1.102 LEN=516 TOS=0x00 PREC=0x00 TTL=62 ID=25628 PROTO=UDP SPT=15826 DPT=1027 LEN=496 
[ 5301.563625] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.19.68 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=656 DF PROTO=TCP SPT=2067 DPT=135 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 5770.039464] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.97.238.202 DST=192.168.1.102 LEN=561 TOS=0x00 PREC=0x00 TTL=49 ID=0 DF PROTO=UDP SPT=42716 DPT=1027 LEN=541 
```

when
```
dmesg | tail -30
```
output
```
[ 3754.652290] usb 5-2: USB disconnect, address 2
[ 3754.652294] usb 5-2.3: USB disconnect, address 6
[ 3754.920091] ehci_hcd 0000:00:1d.7: USB bus 5 deregistered
[ 3754.920184] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 3761.202838] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 3755.343382] usb 1-2: configuration #1 chosen from 1 choice
[ 3755.346248] hub 1-2:1.0: USB hub found
[ 3755.348194] hub 1-2:1.0: 4 ports detected
[ 3755.680694] usb 1-2.3: new full speed USB device using uhci_hcd and address 4
[ 3755.810179] usb 1-2.3: configuration #1 chosen from 1 choice
[ 4046.937189] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.220.15 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=54191 DF PROTO=TCP SPT=1225 DPT=1433 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 4049.924799] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.220.15 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=62892 DF PROTO=TCP SPT=1225 DPT=1433 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 4203.966500] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=218.10.137.139 DST=192.168.1.102 LEN=561 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=51325 DPT=1027 LEN=541 
[ 4400.323182] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.26.170 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=6502 DF PROTO=TCP SPT=3845 DPT=1433 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 4403.159894] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.26.170 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=7179 DF PROTO=TCP SPT=3845 DPT=1433 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 4486.328293] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=211.155.23.224 DST=192.168.1.102 LEN=40 TOS=0x00 PREC=0x00 TTL=101 ID=256 PROTO=TCP SPT=6000 DPT=1433 WINDOW=16384 RES=0x00 SYN URGP=0 
[ 4595.566879] usb 3-2: USB disconnect, address 2
[ 4655.398614] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.19.68 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=51887 DF PROTO=TCP SPT=1807 DPT=135 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 4759.243047] usb 3-2: new low speed USB device using uhci_hcd and address 7
[ 4753.411040] usb 3-2: configuration #1 chosen from 1 choice
[ 4759.435324] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input13
[ 4759.511694] input,hidraw0: USB HID v1.11 Keyboard [A4Tech RF USB Receiver] on usb-0000:00:1d.2-2
[ 4753.530113] input: A4Tech RF USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.1/input/input14
[ 4759.654497] input,hidraw1: USB HID v1.11 Mouse [A4Tech RF USB Receiver] on usb-0000:00:1d.2-2
[ 4835.179067] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.183.41 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=16079 DF PROTO=TCP SPT=1403 DPT=135 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 5189.083574] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=24.64.123.158 DST=192.168.1.102 LEN=516 TOS=0x00 PREC=0x00 TTL=62 ID=25627 PROTO=UDP SPT=15826 DPT=1026 LEN=496 
[ 5189.086357] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=24.64.123.158 DST=192.168.1.102 LEN=516 TOS=0x00 PREC=0x00 TTL=62 ID=25629 PROTO=UDP SPT=15826 DPT=1028 LEN=496 
[ 5189.086831] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=24.64.123.158 DST=192.168.1.102 LEN=516 TOS=0x00 PREC=0x00 TTL=62 ID=25628 PROTO=UDP SPT=15826 DPT=1027 LEN=496 
[ 5301.563625] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.156.19.68 DST=192.168.1.102 LEN=48 TOS=0x00 PREC=0x00 TTL=122 ID=656 DF PROTO=TCP SPT=2067 DPT=135 WINDOW=64240 RES=0x00 SYN URGP=0 
[ 5770.039464] Inbound IN=eth0 OUT= MAC=00:15:c5:24:e9:1b:00:18:39:ff:bf:73:08:00 SRC=202.97.238.202 DST=192.168.1.102 LEN=561 TOS=0x00 PREC=0x00 TTL=49 ID=0 DF PROTO=UDP SPT=42716 DPT=1027 LEN=541
```
when
```
mount -l
```
output:```

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zalmoxes/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zalmoxes)
```

i've looked at many previous threads, and the methods used there dont seem to work in getting me to see my phone at all... btw i have no idea what the smartcard reader is for. i'm using latitude d820. been using using ubuntu for the past 4 months. single boot ubuntu and proud of it.

---

### Post by Thelasko on 2008-09-09
Well, with my w580i you can't access the phone memory by USB, it only allows access to the expansion card (memory stick micro).  To access the phone memory, you have to use bluetooth.

To sync the calendar, etc. you can use Wammu with the USB cord.

I don't know why it's like that, but I hear they are all like that.

---

### Post by zalmoxes on 2008-09-10
but i cant even see anything at all. neither the phone memory or the expansion card. i want to access the expansion card. i dont want to access the phone memory and its an old model with no bluetooth.

---

