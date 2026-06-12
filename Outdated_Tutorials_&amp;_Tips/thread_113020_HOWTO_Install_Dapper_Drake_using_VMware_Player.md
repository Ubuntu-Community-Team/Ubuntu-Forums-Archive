---
title: "HOWTO: Install Dapper Drake using VMware Player"
date: 2006-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Jammy_Stuff on 2006-01-05
Firstly follow the instructions [here]("https://wiki.ubuntu.com/InstallingVMWare") to install VMware player (download VMware player from [here]("http://download3.vmware.com/software/vmplayer/VMware-player-1.0.1-19317.tar.gz") though rather than VMware Workstation. Also, when it starts talking about using a vmware-any-any-update script you need to stop. It's installed

Quite a bit of this has been taken from [this]("http://www.ubuntuforums.org/showthread.php?t=84275") HOWTO.

Let's begin. Firstly open Synaptic and make sure that Qemu is **NOT** installed. Get the latest version from [http://fabrice.bellard.free.fr/qemu/....2-i386.tar.gz](http://fabrice.bellard.free.fr/qemu/....2-i386.tar.gz) .

```
mkdir UbuntuDapperDrake
cd /
sudo tar -zxf /path/to/download/qemu-0.7.2-i386.tar.gz
cd ~/UbuntuDapperDrake
qemu-img create -f vmdk UbuntuDapperDrake.vmdk 2G/CODE]

You can change the 2G to the size of virtual hard drive you want Dapper to have in gigabytes eg. 4G = 4 Gigabytes.

Now you need to create a text file in you UbuntuDapperDrake directory called UbuntuDapperDrake.vmx Copy and paste the following into it.

[CODE]#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "UbuntuDapperDrake.vmdk"
memsize = "192"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
floppy0.startConnected = "TRUE"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Ubuntu Dapper Drake"
guestOS = "other26xlinux"
nvram = "UbuntuDapperDrake.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
uuid.bios = "56 4d cd 3f 59 5b 61 43-fd 73 ef 46 56 4c 23 7b"
ethernet0.generatedAddress = "00:0c:29:4c:23:7b"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "UbuntuDapperDrake.vmss"
tools.remindInstall = "TRUE"
```

Save it. Now if you don't have a CD of Dapper Drake download the newest one from [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

Put the CD in your CD drive and then open VMware player (Applications > System Tools > VMware Player and open your virtual machine. Install Dapper as usual and enjoy :).

---

