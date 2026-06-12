---
title: "novice at IR needs help with receiver set up in Ubuntu"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by squakie on 2013-11-06
I know squat about IR.  I need an IR remote to make using XBMC in Ubuntu easier.  I am in the process of building one of the old serial adapters that a site *claims* will work with lirc, but picked up a USB IR receiver also.  Outside of knowing what lirc stands for and the basics of what it is supposed to do, I am lost.  The IR receiver is listed as:

<code>Bus 009 Device 002: ID 147a:e016 Formosa Industrial Computing, Inc. eHome Infrared Receiver</code>

The light on it is just constantly blinking and I have no idea what to do from here.  I installed the infrared tools and made some changes as suggestion in what is probably an old Ubuntu how-to but I still can't see anything happening.

Can someone tell me:

(1) what do I need to do to be sure a driver, etc., is loaded for the device and that the device is working
(2) verify the device is workiing in some sort of tool

Once I get that far I can go on to try to make it work in XBMC.  I thought it best to take one clear step at a time.

---

### Post by squakie on 2013-11-07
I found [this link]("http://cateee.net/lkddb/web-lkddb/IR_MCEUSB.html") on the net that would seem to indicate something with the kernel, but I don't know anything about any of that either.  If someone "in the know" could look at that and tell me if it pertains to Ubuntu 13.10 and if so how to do whatever it is saying to do.

---

### Post by Lars Noodén on 2013-11-07
I haven't done anything with IR on Ubuntu, but on other systems it is just another serial devices.  There seems to be a package lirc for Ubuntu that works with IR.  Have you tried that one yet?

---

### Post by squakie on 2013-11-07
Thanks Lars.  Yep, tried LIRC.  Dmesg shows it getting recognized but it just isn't working.  The little led on it just constantly flashes, yet when I plug it in to a Raspberry Pi running OpenELEC, the led doesn't flash and the remote works.  I have 2 suspicions but have no idea on what to do:

(1) I need some sort of driver - though dmesg shows it being recognized and using the mceusb driver

(2) I've found other posts on the net that say since an earlier version of the kernel part of the IR functionality (I can't tell if all) that was done in a LIRC module is now being done in the kernel itself.  I don't have a clue if they conflict or what.  I even went so far as to remove LIRC to see if just the kernel "stuff" would do it, buit no such luck.  Since OpenELEC on the Pi is using LIRC, I was hoping perhaps there is some way to turn off the built-in kernel support and go with just lirc, but I don't know enough to even know what to search for.

Thanks again!

EDIT:  here'e the output from dmesg when I plug the adapter in.  I find it interesting that it is going to rc1, when I've seen mention somewhere in the looking I've done of rc0.  Perhaps I need some sort of link or something to tie rc1 to rc0?

```
[43197.121264] usb 6-2: new full-speed USB device number 2 using ohci-pci
[43197.321965] usb 6-2: New USB device found, idVendor=147a, idProduct=e016
[43197.321977] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[43197.321984] usb 6-2: Product: eHome Infrared Transceiver
[43197.321989] usb 6-2: Manufacturer: Formosa21
[43197.321993] usb 6-2: SerialNumber: FM000623
[43197.334953] Registered IR keymap rc-rc6-mce
[43197.335183] input: Media Center Ed. eHome Infrared Remote Transceiver (147a:e016) as /devices/pci0000:00/0000:00:12.0/usb6/6-2/6-2:1.0/rc/rc1/input13
[43197.335462] rc1: Media Center Ed. eHome Infrared Remote Transceiver (147a:e016) as /devices/pci0000:00/0000:00:12.0/usb6/6-2/6-2:1.0/rc/rc1
[43197.335906] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input14
[43197.336550] rc rc1: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[43197.509161] mceusb 6-2:1.0: Registered Formosa21 eHome Infrared Transceiver with mce emulator interface version 1
[43197.509175] mceusb 6-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
dave@davepc:~$ 
```

---

### Post by squakie on 2013-11-09
Well do I feel stupid - turns out the device, while USB, must not be plug-n-play.  When I cycled the power on my PC the device started working.  Tried some tests and indeed if you plug it in while the system is running you have to power cycle.  A reboot won't do it, and it seems to "reset" while the hardware is initializing, long before grub.

---

