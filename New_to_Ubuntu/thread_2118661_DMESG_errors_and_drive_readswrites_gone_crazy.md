---
title: "DMESG errors and drive reads/writes gone crazy"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-21
From System Log Viewer (in reverse order):

[   129.556648] init: gdm main process (1543) killed by TERM signal

[   127.189767] usb 1-2.2.3: USB disconnect, device number 16

[   79.696771] init: udev-fallback-graphics main process (1154) terminated with status 1

[   78.805763] usb 1-2.2.3: USB disconnect, device number 15

[   19.768457] udevd[330]: renamed network interface wlan0 to wlan2
[   35.797764] usb 1-2.2.3: USB disconnect, device number 14

[   19.539630] cfg80211: Regulatory domain changed to country: CN

I don't live in China. I'm in the USA.

[   11.061496] EXT3-fs (sda3): 6 orphan inodes deleted

[    3.808906] sd 6:0:0:0: [sdb] Asking for cache data failed
[    3.808978] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.813281] sd 6:0:0:0: [sdb] Asking for cache data failed

[    3.275896] usb 1-2.2.1: config 1 interface 0 altsetting 0 has 2 endpoint descriptors, different from the interface descriptor's value: 1

[    1.048054] EISA: Cannot allocate resource for mainboard
[    1.048122] Cannot allocate resource for EISA slot 1 . . .8

7 lines repeat above, EISA slot 1, 2, etc.

As I have never seen the DMESG before, do I have a problem? I ask because the harddrive has been running like crazy for moments during the time the 'puter is on. And when it goes crazy, the mouse won't work, the chrome browser pages ask to kill or wait. I'm sorry to not give enough info, but I'm lost. For example 

mark@Lexington-19:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 001 Device 004: ID 2001:f103 D-Link Corp. DUB-H7 7-port USB 2.0 hub
Bus 001 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 006: ID 03eb:3301 Atmel Corp. at43301 4-Port Hub
Bus 001 Device 007: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 008: ID 3538:0054 Power Quotient International Co., Ltd Flash Drive (2GB)
Bus 001 Device 009: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 010: ID 073a:2330 Chaplet Systems, Inc. 
Bus 001 Device 011: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Bus 001 Device 013: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 019: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0

so the DMESG about the devices I list in this post don't even show up in lsusb.

Also, deleting from the deskto a gedit created text file of 2kb makes the hard disk activity led stay solid color for 30 or more seconds.

Also, from the kernel.log:

[B]Feb 21 17:39:19 Lexington-19 kernel: [ 1767.140404] show_signal_msg: 48 callbacks suppressed
Feb 21 17:39:19 Lexington-19 kernel: [ 1767.140416] mythlogserver[2611]: segfault at 48 ip 00000048 sp ae383bcc error 14 in mythlogserver[8048000+3000]

[/B]

---

### Post by tgalati4 on 2013-02-21
If you haven't already install smartmontools and inspect the output of:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
sudo smartctl -a /dev/sdb
```

You are having issues with both /dev/sda and sdb, so that might be a power supply.

If this is a desktop, has it been cleaned and everything internal reseated?

---

### Post by Mark_in_Hollywood on 2013-02-21
/dev/sdb is a 1 gig usb thumb (jump, pen, flash) drive.

I'm not a sophisticated computer guy, but the only error I see in smartctl is this:


[SIZE="1"]Error 1 occurred at disk power-on lifetime: 17767 hours (740 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle[/SIZE]

smartctl reports the current hours as: 23497

please see attached screenshot of smartctl.

Per previous poster's response: "If this is a desktop, has it been cleaned and everything internal reseated?"

Cleaned? At boot time, choosing GRUB Recovery, fsck, the /sda3 (root) reports as clean, but /sda5 (home) hangs and won't clear without ctrl-c to break into resume loading. As for "internal reseated". I had a big problem with the 12.04 OS 3 weeks ago, but it has been fine since then. I want to think that MythTV is somewhat the culprit here. For that I have 

sudo service mythtv-backend stop

and 'top' does not show myth running.

---

### Post by Mark_in_Hollywood on 2013-02-23
tumblrd, a routine to make "thumbnails" could be the culprit.

See:

[https://bugzilla.xfce.org/show_bug.cgi?id=8377](https://bugzilla.xfce.org/show_bug.cgi?id=8377)

I opened my Thunar and set Edit / Preferences / File Manager Preferences, where it has a drop down menu for "Show thumbnails" to "Never".

I'll update this thread again, in a few days, if the problem seems resolved. And mark this as "Solved" if possible.

---

