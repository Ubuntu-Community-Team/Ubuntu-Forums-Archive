---
title: "Why won't this udev script run?"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by mark allyn on 2012-12-13
Hello everyone,

I have been wrestling with udev for a couple of days now, trying to get a simple script to  run when I plug in a flash drive.

Here's the info on the drive as shown by a call to dmesg:[27063.842876] EXT3-fs (sdb1): 
```

mounted filesystem with ordered data mode
[31370.368085] usb 1-3: USB disconnect, device number 26
[31400.672191] usb 1-3: new high-speed USB device number 27 using ehci_hcd
[31400.808046] scsi29 : usb-storage 1-3:1.0
[31401.810491] scsi 29:0:0:0: Direct-Access     SanDisk  Cruzer           1.26 PQ: 0 ANSI: 5
[31401.812880] sd 29:0:0:0: Attached scsi generic sg2 type 0
[31401.818389] sd 29:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[31401.821392] sd 29:0:0:0: [sdb] Write Protect is off
[31401.821405] sd 29:0:0:0: [sdb] Mode Sense: 43 00 00 00
[31401.823205] sd 29:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[31401.834975]  sdb: sdb1
[31401.839039] sd 29:0:0:0: [sdb] Attached SCSI removable disk
[31402.131205] kjournald starting.  Commit interval 5 seconds
[31402.134483] EXT3-fs (sdb1): using internal journal
[31402.134490] EXT3-fs (sdb1): mounted filesystem with ordered data mode

```Here is the udevadm info on the flash drive:
```
looking at device '/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/host29/target29:0:0/29:0:0:0/block/sdb/sdb1':
    KERNEL=="sdb1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{partition}=="1"
    ATTR{start}=="2048"
    ATTR{size}=="15631360"
    ATTR{ro}=="0"
    ATTR{alignment_offset}=="0"
    ATTR{discard_alignment}=="0"
    ATTR{stat}=="      96        0      762      112        1        0        8        0        0      112      112"
    ATTR{inflight}=="       0        0"

  looking at parent device '/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/host29/target29:0:0/29:0:0:0/block/sdb':
    KERNELS=="sdb"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{range}=="16"
    ATTRS{ext_range}=="256"
    ATTRS{removable}=="1"
    ATTRS{ro}=="0"
    ATTRS{size}=="15633408"
    ATTRS{alignment_offset}=="0"
    ATTRS{discard_alignment}=="0"
    ATTRS{capability}=="51"
    ATTRS{stat}=="     174        0     1386      200        1        0        8        0        0      200      200"
    ATTRS{inflight}=="       0        0"
    ATTRS{events}=="media_change"
    ATTRS{events_async}==""
    ATTRS{events_poll_msecs}=="2000"

  looking at parent device '/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/host29/target29:0:0/29:0:0:0':
    KERNELS=="29:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="SanDisk "
    ATTRS{model}=="Cruzer          "
    ATTRS{rev}=="1.26"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x11c"
    ATTRS{iodone_cnt}=="0x11c"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{evt_media_change}=="0"
    ATTRS{dh_state}=="detached"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

```Here is the udev rule:
```
SUBSYSTEMS=="scsi", ATTRS{vendor}=="SanDisk", ATTRS{model}=="Cruzer",SYMLINK+="markyflash", RUN+="/usr/local/bin/flashscript.sh"
```I used the following command to "compile" the rule:
```

sudo service udev restart

```Finally, here is the little teeny scriptfile:

```

str1='Flash attached'
echo $str1 > ~/flashfile

```My understanding is that UDEV can't display on the console (although I gather that ZENITY if given the appropriate DISPLAY env variable can), so all I'm trying to do is write a trivial file.  The symlink is established, by the way.  But the script doesn't run.

I'm really a novice with UDEV, as you can no doubt discern, but I'd like to learn how to use it.

Thank you.

Mark Allyn

---

### Post by steeldriver on 2012-12-13
A couple of things

1. you do have a shebang at the top of that, right? (sorry, have to ask)

2. likely the rule / run action is run as root so I'm not sure ~/flashfile will mean what you think it means

Here's one I *know* works:

```
$ cat /etc/udev/rules.d/21-persistent-local.rules 
ATTR{idVendor}=="0483", ATTR{idProduct}=="2015", SYMLINK+="bioscrypt", GROUP:="usb", MODE:="0660", RUN+="/usr/local/bin/notify-usb"

``````

$ cat /usr/local/bin/notify-usb 
#!/bin/bash
logger "$(whoami) : usb device plugged in" 
$ 

```Then after I plug the device in, I can check syslog and see
```
$ tail -1 /var/log/syslog
Dec 13 15:07:00 lap-t61p logger: root : usb device plugged in
$ 

```Hope this helps

---

### Post by mark allyn on 2012-12-13
Hi Steeldriver,

Your suggestion about where the file would be written using ~/ as the directory was exactly correct.  Changing to /home/administrator/flashdrive produced the desired result.

Oh yes, one other thing.  I had NOT used #! /bin/bash in the script....oh dear.  I kept running it at the term and it ran like topsy, so I assumed it would do the same thing in /usr/local/bin.

Thanks twice over.

Regards,
Mark Allyn

---

