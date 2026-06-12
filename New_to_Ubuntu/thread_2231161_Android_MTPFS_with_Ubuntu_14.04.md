---
title: "Android MTPFS with Ubuntu 14.04"
date: 2014-06-23
forum: New to Ubuntu
---

### Post by SupaRice on 2014-06-23
How can I get my Android devices to work with Ubuntu 14.04 without having to go into a long drawn out reinvention of the wheel?

I've already done 

```
apt-get install mtpfs mtp-tools --yes
```

No dice. Sometimes it works, sometimes it doesn't. Mostly doesn't.

Any luck on this for others? I've seen several articles online instructing some third party software source, but wasn't sure if that was safe.

Go-mtpfs
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

Is that the way???

Frustrated, this crap works with WINDOWS! But Android and Linux don't work!? Meh!? There's gotta be an easy way to get this working.... Right?

---

### Post by SupaRice on 2014-06-24
Bueller?

---

### Post by 3rdalbum on 2014-06-25
If you are using Ubuntu 14.04 it should work without you needing to do anything. Do not follow the 12.04 guide, it will only break things.

Try plugging the phone straight into the computer rather than into a hub. Or use a different USB port, or a different cable (my father had trouble with his until he realized that the little locking clips on the cable connector were broken).

Is your phone reporting that it is entering Media Transfer mode when you plug it in? Or PTP mode? What does 'lsusb' and 'dmesg' say when you plug the phone in?

---

### Post by SupaRice on 2014-06-25
Error window pops up and says:
"Unable to mount SAMSUNG ANDROID"
"Unable to open MTP device '[usb:003,007]' "

```

[27648.891596] usb 3-2: new high-speed USB device number 7 using xhci_hcd
[27648.908593] usb 3-2: New USB device found, idVendor=04e8, idProduct=6860
[27648.908595] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[27648.908597] usb 3-2: Product: SAMSUNG_Android
[27648.908598] usb 3-2: Manufacturer: SAMSUNG
[27648.908599] usb 3-2: SerialNumber: ab8f9bf8
[27650.899043] usb 3-2: USB disconnect, device number 7
[27651.293971] usb 3-2: new high-speed USB device number 8 using xhci_hcd
[27651.311234] usb 3-2: New USB device found, idVendor=04e8, idProduct=6860
[27651.311238] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[27651.311240] usb 3-2: Product: SAMSUNG_Android
[27651.311242] usb 3-2: Manufacturer: SAMSUNG
[27651.311243] usb 3-2: SerialNumber: xxxxxxx
[27652.009530] systemd-hostnamed[8157]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b3c8 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]
Bus 003 Device 004: ID 0cf3:311f Atheros Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by SupaRice on 2014-06-25
It does this with my son's Samsung Galaxy Tab3 7" also...

Haven't tried my Asus Transformer yet.

---

### Post by coldraven on 2014-06-28
This is really annoying! I have just been travelling with a notebook running Xubuntu 14.04 and my Moto G connects via USB with no problems.
I got home today and tried to transfer photos to my main laptop running Ubuntu 14.04 and no luck at all. The phone says that it is in MTP mode and lsusb shows the phone but nothing in Nautilus.
I installed mtp-tools and still nothing :(
I tried a different cable and a different usb port and still no joy.
What is going on?

Edit:
If I run SSHDroid on the phone Nautilus can connect using SSH but as both devices are using wi-fi it is very slow. 1.8GB of photos would take over an hour to transfer.

---

### Post by jon-zendatta on 2014-06-28
Same here, so I just plug SD card in to computer

---

### Post by gordintoronto on 2014-06-29
My solution is Airdroid, which is also Wi-Fi.

---

### Post by Vladlenin5000 on 2014-06-29
I guess I'm among the lucky ones: My Meizu MX3 works flawlessly with MTP.

---

### Post by manuelortiz480 on 2014-06-30
I made a bunch of recommended changes to 12.04 trying to get mtp to work with my galaxy tab 2 7.0.  I tried to undo them when I upgraded to 14.04 but I'm sure I missed something.  I have even tried me new phone. It works fine if I boot from a live USB thumb drive.  But when I boot from my hard drive I get

Unable to mount LGE Android Phone
Message did not receive a reply (timeout by message bus)

And the entries in syslog are
```

Jun 29 21:14:24 mortiz-610 kernel: [94827.344604] usb 2-1.6: new high-speed USB device number 6 using ehci-pci
Jun 29 21:14:24 mortiz-610 kernel: [94827.438789] usb 2-1.6: New USB device found, idVendor=1004, idProduct=631c
Jun 29 21:14:24 mortiz-610 kernel: [94827.438797] usb 2-1.6: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Jun 29 21:14:24 mortiz-610 kernel: [94827.438801] usb 2-1.6: Product: LGE Android Phone
Jun 29 21:14:24 mortiz-610 kernel: [94827.438805] usb 2-1.6: Manufacturer: LG Electronics Inc.
Jun 29 21:14:24 mortiz-610 kernel: [94827.438809] usb 2-1.6: SerialNumber: 09a13d169812c6d5
Jun 29 21:14:25 mortiz-610 colord: Device added: sysfs-LG_Electronics_Inc.-LGE_Android_Phone
Jun 29 21:14:25 mortiz-610 colord: Device added: sysfs-(null)
Jun 29 21:17:01 mortiz-610 CRON[14811]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

I'd be glad to show any other log or config files.

manuel

---

### Post by Whoopie on 2014-06-30
If you see the error messages like

"Unable to mount SAMSUNG ANDROID"
"Unable to open MTP device '[usb:003,007]' "

This is because your screen is locked. Just unlock your screen and you should see the internal device storage and sd card (if plugged in).

---

### Post by lotharmat on 2014-06-30
Alas not so! - Well not on mine anyway!

The only way I can get photos off the S3 is to connect as a camera device (still get errors but at least I can see photos)

---

### Post by SupaRice on 2014-07-07
> **jon-zendatta said:**
> Same here, so I just plug SD card in to computer

Even that doesn't work for me!  This is total nixFail.

---

### Post by eking-x on 2014-07-29
I used gMtp to access my galaxy tab 3. 

```
sudo apt-get install gmtp
```

---

### Post by fataddict on 2014-07-29
My Samsung Galaxy S4 has always worked fine until today. The only thing that has changed is I upgraded to Ubuntu 14.04.1 from 14.04.

mtp-detect produces:
```
Unable to open ~/.mtpz-data for reading, MTPZ disabled.libmtp version: 1.1.6


Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 3, dev 2
Attempting to connect device(s)
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
Error 1: Get Storage information failed.
Error 2: PTP Layer error 02ff: get_handles_recursively(): could not get object handles.
Error 2: Error 02ff: PTP: I/O error
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
Error 7: Found a bad handle, trying to ignore it.
USB low-level info:
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 6860
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 3
      Device number: 2
      Device entry info:
         Vendor: Samsung
         Vendor id: 0x04e8
         Product: Galaxy models (MTP)
         Vendor id: 0x6860
         Device flags: 0x49000207
Configuration 0, interface 0, altsetting 0:
   Interface description contains the string "MTP"
   Device recognized as MTP, no further probing.
Device info:
   Manufacturer: SAMSUNG Electronics Co. Ltd. 
   Model: SHV-E330S
   Device version: E330SKSUCNE2
   Serial number: R33D70H8CM
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMPPD: 11.0; microsoft.com/WMPPD: 10.0; microsoft.com/WMDRMPD:10.1; microsoft.com/playready:1.10;samsung.com/kies:2.1;samsung.com/sidesync3.0
   Detected object size: 64 bits
   Extensions:
        microsoft.com: 1.0
        microsoft.com/WMPPD: 11.0
        microsoft.com/WMPPD: 10.0
        microsoft.com/WMDRMPD: 10.1
        microsoft.com/playready: 1.10
        samsung.com/kies: 2.1
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   100b: Delete object
   100c: Send object info
   100d: Send object
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   101b: Get partial object
   9810: Get object references
   9811: Set object references
   9802: Get object property description
   9801: Get object properties supported
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9201: Report Added/Deleted Items
   9202: Report Acquired Items
   100a: Get thumbnail
   1011: Self test device
   1012: Set object protection
   1017: Reset device property value
   9807: Get interdependent property description
   9808: Send object property list
   9100: Unknown (9100)
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   910b: Send WMDRM-PD Request
   910c: Unknown (910c)
   910d: Unknown (910d)
   910e: Unknown (910e)
   910f: Unknown (910f)
   9110: Unknown (9110)
   9111: Unknown (9111)
   9112: Unknown (9112)
   9113: Unknown (9113)
   9114: Unknown (9114)
   9115: Unknown (9115)
   9116: Unknown (9116)
   9501: Unknown (9501)
   9502: Unknown (9502)
   9503: Unknown (9503)
   9504: Unknown (9504)
Events supported:
   0x4002
   0x4003
   0x4004
   0x4005
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd404: Unknown property
   0xd407: Perceived Device Type
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd103: Revocation Info
   0xd104: Unknown property
   0xd105: Unknown property
Playable File (Object) Types and Object Properties Supported:
   b984: 3GP
   3009: MP3
   b901: WMA
   b981: WMV
   3801: JPEG
   3001: Association/Directory
   ba05: Abstract Audio Video Playlist
   3000: Undefined Type
   3807: GIF
   300a: MS AVI
   300b: MPEG
   300c: ASF
   b982: MP4
   3800: Defined Type
   b980: Undefined Video
   ba10: WPL Playlist
   ba11: M3U Playlist
   ba03: Abstract Audio Album
Special directories:
   Default music folder: 0xffffffff
   Default playlist folder: 0xffffffff
   Default picture folder: 0xffffffff
   Default video folder: 0xffffffff
   Default organizer folder: 0xffffffff
   Default zencast folder: 0xffffffff
   Default album folder: 0xffffffff
   Default text folder: 0xffffffff
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: (NULL)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   Microsoft Windows Media Video
   JPEG file
   Folder
   Abstract Playlist file
   GIF bitmap file
   Audio Video Interleave
   MPEG video stream
   Microsoft Advanced Systems Format
   MPEG-4 Part 14 Container Format (Audio+Video Emphasis)
   Undefined video file
   Abstract Album file
   Ogg container format
   Free Lossless Audio Codec (FLAC)
ERROR: Could not close session!
OK.

```

Then I unplugged the phone and plugged it back in and it produced:
```
Unable to open ~/.mtpz-data for reading, MTPZ disabled.libmtp version: 1.1.6


Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 3, dev 6
Attempting to connect device(s)
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
ignoring libusb_claim_interface() = -6LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
OK.

```


lsusb produces:
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 5986:0400 Acer, Inc 
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 002: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Also, when checking the "USB computer connection" on the GS4 the MTP check box keeps flickering on and off very fast.

Not sure what the problem is. Any ideas?

---

### Post by fataddict on 2014-07-30
So, I edited fuse.conf, rebooted, and now it works like normal.

---

### Post by csinclair0 on 2014-09-12
I am having the same issues. I have tried gmtp, which seems to crash everytime, and I have edited my fuse.conf file. nothing.

---

