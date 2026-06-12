---
title: "Wireless and Audio not working"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by emainieri002 on 2013-01-01
Hi All, 

I love Ubuntu but I have been struggling for 2 days with Quantal Quetzal on my Dell Inspiron 4010.

The problems I am having are two, which I will break down below>

1. My computer is recognizing the Wireless Card as a Bluetooth card. I already searched for the appropriate drivers and I am not able to have the computer make the switch.

2. Usually Ubuntu picks up the Audio configuration and works perfectly reproducing audio (from Youtube, MP3, Wav and all) but for some reason, this time around it's not working.

I am going nuts about this. All your help is appreciated.

Here are the results of lspci and

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

lshw
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)


lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 016: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 001 Device 017: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 018: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 019: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth


Thanks!

---

### Post by squakie on 2013-01-02
If you are thinking that this device:

Bus 001 Device 016: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

is your wireless, everything I have found on the net, including hardware applications of the BCM2046, indicate it is only a bluetooth transceiver.

Please note that the guide for your computer on the Dell site specifically says you had to order a wlan adapter to get wireless on this model - it was not included by default.

However, all may not be lost!  I've been parting out an ancient laptop and have available for FREE - I EVEN PAY THE SHIPPING - a TP-LINK internal minipci 54mbps wireless adapter that should fit your laptop.  I don't remember if Ubuntu finds it out of the box or if you may have to enable a driver for it (people here can help you with that).

So, if you're interested, just PM me with your name and address and I can send it out on Thursday.  Please note - I'm just a private person, I will delete your name and address as soon as I've got it copied for the shipping label.  Nothing will be shared with anyone.

I'm doing this because user lkraemer helped me a few years ago by sending me an external modem for free when I had the need.  I am on disability, so I understand that not everyone can just run out and buy something.  That's it - just trying to follow lkraemer's example - I could never walk in his footsteps, I can only hope to follow.

It might save you $5 or so from buying a used one on EBay.

---

### Post by emainieri002 on 2013-01-02
Hi Squakie,

Thank you very much for the reply. I am a little confused by your insight, as this computer used to have Win 7 and had wireless by default. I read a couple of discussion boards and even the Dell Website, and I found two things:

1. Dell provides the wireless driver for Win 7 online. I downloaded it and installed on this computer before switching to ubuntu. The wireless was never recognized and only Bluetooth was available.

2. After the Bluetooth fiasco, I kept reading, and I found that the card that works for wireless is something of a mix up between wifi and bluetooth. I just cant find how to make it switch to wifi instead of Bluetooth.

I also search for the Broadcom device and I was not able to identify it as part of the Wifi settings.

I was researching for this part>
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)

I am not sure, as I am not that literate, but I believe that this may be the part of the wireless. I think. not quite sure. I am really good with PC parts, but not laptop parts :P
Never the less, thank you very much for your kindness. I will forward you my address and name.

I really appreciate all your help.

---

### Post by squakie on 2013-01-02
Hummmm......I wasn't able to find reference to it as a hybred device.

At any rate - the wireless adapter will be in the mail Thursday.  Hopefully you can use it - if it turns out you can't, please try to forward it on to someone else.

---

### Post by squakie on 2013-01-06
For your original adapter, it does appear it can be a mixed device.  However, if it didn't work in Windows 7 that would indicate at least to me that you don't have wireless.  So, just to test it, I've also been thinking that maybe a new udev rule might need to be created - similar to the 70-persistent-net.rules file in the /etc/udev/rules.d folder. I'm suspecting that maybe creating a new rule file with just a single USB entry similar to those (with the usb manufacturer and product id from your device) with, of course, the address modified to that of your adapter.
 
You may also want to try the following to see if it makes any difference (I think it will only turn on the bluetooth):
 
sudo echo 0x0a5c 0x4500 > /sys/bus/usb/drivers/btusb/new_id

---

### Post by squakie on 2013-01-08
While you're waiting (if it's not there already) for the adapter in the mail, post back this output as well (please note the sudo):

sudo lspci 

sudo lsusb

---

