---
title: "HOWTO: Broadcom 4320 USB wifi drivers"
date: 2008-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Andycas on 2008-07-02
This is a really simple guide, how to obtain and install drivers for broadcom 4320 chipset wifi dongles. The drivers (rndis_wlan) are already included in 2.6.25 kernels and up, so this guide applies to <=2.6.24 kernel.
**NB! Remove the ndiswrapper drivers before you use this guide! Use ndiswrapper -r *yourdrivername*** If you haven't installed ndiswrapper drivers then you can skip this and move on.

You can check what kernel you're running by:
```
uname -r
```
Next we're going to create a dir and download the drivers:
```
mkdir bcm4320drivers
cd bcm4320drivers
wget http://jooz.net/rndis/rndis_wlan-snapshot-20080509.tar.gz
tar -xvzf rndis_wlan-snapshot-20080509.tar.gz
cd rndis_wlan

```
Now that we are in the rndiswlan dir we will use clear.sh command to clean previous drivers from the system and build new ones:
```

sudo ./clean.sh
sudo make
sudo make install

```
**Thats it! Your device should be now recognized by the driver.**

You can monitor syslog with this command to see if it recognizes the device.
```
tail -f /var/log/syslog
```
If it doesnt you might need to add a udev rule to your modules:
```
BUS=="usb", SYSFS{idProduct}=="replace", SYSFS{idVendor}=="replace", RUN+="/bin/sh -c 'echo 1 > /sys/%p/device/bConfigurationValue'
```
Replace product and vendor id with your adapters, you can use *lsusb -vv* to find out these values.

**Devices that use this rndis_wlan driver are:**
Asus WL169gE
Belkin F5D7051
BT Voyager 1055
Buffalo WLI-U2-KG125S (confirmed and tested by me)
Buffalo WLI-USB-G54
Eminent EM4045
Linksys WUSB54GSC
Linksys WUSB54GSv1
Linksys WUSB54GSv2
U.S. Robotics USR5420
U.S. Robotics USR5421

---

### Post by keyz182 on 2008-08-28
Thanks! Been trying to get my Linksys WUSB54GXX working on Mythbuntu 8.04 64-bit for ages, though haven't put any "real" effort in till now.

B.T.W. I put 54Gxx because the case broke a while ago, so I can't find the exact version. I've had to make do without, untill I replace it. It's currently in an old plastic box I found. I also replaced the arial with one of those extending metal ones from an old radio, get's a far better signal now!

---

### Post by ugutugut on 2008-10-10
Thank you for sharing your knowledge. Now I can connect my device (Belkin F5D7051) to wireless network.

---

### Post by D1ZZ4ZZT3R on 2009-04-09
any chance this would work on 8.10? ubuntu, that is.

---

### Post by nanniser on 2009-06-04
Buffalo WLI-U2-KG125S (confirmed and tested by me)
Thanks for your help, I'm trying to start with ubuntu 9.04 with this pen wifi you testede , but I am able to do it.
with lsusb -v I have this answer:
.....
Bus 001 Device 004: ID 0411:00bc MelCo., Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0411 MelCo., Inc.
  idProduct          0x00bc 
  bcdDevice            0.06
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           48
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
.......
Now I don't know wath I can do..
Would you be so kind to help me....??
nanniser

---

### Post by Grundlefleck on 2009-10-20
Thank you, worked a treat!

(Posted with my now-working wireless connection)

---

### Post by feetmaestro on 2009-10-20
OK newbie question. new to ubuntu helping a mate get there wireless working.  I made a text file containing the code provided, thank you, added idProduct and vendor (0x00bc 0x0411) and saved as a .rules with highest priority to /lib/udev/rules.d? Is this what I was supposed to do for I cannot get the Buffalo WLI-U2-KG125S to work :(  Any help much appreciated :) (on 9.04 but wireless not auto detected, was previously using 8.04 with windows wireless drivers which worked for a while now not working, these drivers have been removed).

---

