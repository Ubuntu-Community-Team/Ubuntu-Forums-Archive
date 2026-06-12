---
title: "How do I get my wirless usb stick working?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Shuko on 2008-06-21
Hi,

I have a dell latitude laptop on which I've installed the latest Ubuntu release. I can access the internet fine when its plugged into my netgear router.

I have a Belkin usb wireless stick - chipset Zydas 1211B. I understand this should work with driver zd1211rw which I understand comes ready installed? But I can't get any sites with firefox when I'm not plugged in to the router. i.e. I don't know how to get the laptop to use the usb stick.

Because I saw it on a very techy thread I tried the following on a terminal window which presumably means the driver is there?.

 dmesg | grep zd
[ 2986.150961] zd1211rw 1-1.4:1.0: eth1
[ 2986.151000] usbcore: registered new interface driver zd1211rw
[ 2107.885479] zd1211rw 1-1.4:1.0: firmware version 4725
[ 2987.386083] zd1211rw 1-1.4:1.0: zd1211b chip 050d:705c v4810 full 00-17-3f AL2230_RF pa0 g--NS

Can someone tell me how to get the usb wireless working?
How do I tell when it is working (other than trying firefox)?

Cheers

---

### Post by geo909 on 2008-06-21
Sorry, that's not to answer your question but take a look at [this]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), it may help.

---

### Post by Shuko on 2008-06-21
I get:
Bus 001 Device 006: ID 050d:705c Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705c 
  bcdDevice           48.10
  iManufacturer          16 
  iProduct               32 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1

---

### Post by marcomangiante on 2008-08-24
Hello,

sincerely I have the same problem and I don't know in what I can resolve it: can someone help us?

--
Regards,

Marco Mangiante

---

### Post by Donkinator on 2008-10-14
You probably either gave up or have your solution already, but check these links out. Someone at puppy managed to get their zd1211b device working by downloading the vendor supplied zd1211b driver, and not using the zd1211rw ones. 
It may work, or could just be a shot in the dark...

([http://www.murga-linux.com/puppy/viewtopic.php?t=11277&start=96&sid=d11436b496b8e3fef8f614355617a13e](http://www.murga-linux.com/puppy/viewtopic.php?t=11277&start=96&sid=d11436b496b8e3fef8f614355617a13e))

And the download is in this post.

[http://www.murga-linux.com/puppy/viewtopic.php?p=145745#145745](http://www.murga-linux.com/puppy/viewtopic.php?p=145745#145745)

Please note that he tells you,

"After installing zd1211+b-2.21.0.0-k2.6.21.7.pet do this - 
Code: 
rmmod zd1211rw 
modprobe zd1211b "

Keep in mind this was written for puppy linux, so you won't be able to use any installation scripts in the archive. Manually copy zd1211b.ko to /lib/modules/(your kernel build number)/kernel/drivers/net/wireless.

Good luck :guitar:

---

