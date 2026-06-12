---
title: "Need help with my wireless network card"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by ford08 on 2008-07-11
hi everyone..im new to ubuntu and i need help..

how do i install the driver for my Belkins Wireless G Network Adapter Card?

i have the F5D7000 version 4000..i also downloaded and driver from belkin and try to install it but i wont let me...

can someone pls help me with this as to i am new and just learning ubuntu...

thanks!!

---

### Post by Xerp on 2008-07-11
What happens exactly when you try to install? What steps do you take, and what are the results? Usually a quick "sudo" fixes any "won't let you" problems :)

---

### Post by ford08 on 2008-07-11
well what i do is try to install the driver by double clicking on it..cuz thats how in windows..but apparently its not like that in ubuntu.. can u help me how to install my windows driver for my wireless network card...right now im only using ethernet..

---

### Post by Xerp on 2008-07-11
Try turning off, removing all other usb connections (e.g a printer, usb hub - anything connected via usb) so you just have your belkin adapter attached via USB. Then boot up again and try to scan for networks.

---

### Post by ford08 on 2008-07-11
oh its not a usb wireless network..its a PCI card installed on the motherboard...

---

### Post by Shroomsoup on 2008-07-11
Relevant to my interests, I'm completely new to Ubuntu, and it does not recognize my Broadcom wireless card. I'm on an Acer Aspire 5100, and all works wonderfully except for that.

So... how do I install the driver? I read ndiswrapper might be of use?

---

### Post by Xerp on 2008-07-11
Ok, I checked the Belkin website and they don't appear to have a native downloadable driver:

[http://www.belkin.com/support/article/?lid=en&pid=F5D7000&aid=6001&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D7000&aid=6001&scid=221)

The v4000 is pretty old and I'm having trouble locating its chipset. Can you run

```
lspci
```

and post the output, please?

---

### Post by kidstar64 on 2008-07-11
Ndiswrapper will be needed for your broadcom card. Their is a nice guide on [http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html") for setting it up on a dell 1501. just replace the dell driver files with the broadcom ones.

---

### Post by ford08 on 2008-07-11
sure thing..here you go..

beauford@beauford-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
beauford@beauford-desktop:~$

---

### Post by Xerp on 2008-07-11
As well as the link above there is the non-ndiswrapper way:

[http://ubuntuforums.org/showthread.php?t=424994](http://ubuntuforums.org/showthread.php?t=424994)

Should work on Hardy too :)

Looks like the ndiswrapper way is better for now though... but hey, if one doesn't work try the other!

---

### Post by ford08 on 2008-07-11
ok thanks!!..i think its working now..cuz i see the light at the back came on...i want to set this to share its internet...how do i do that?

when im in windows, this computer is the server, and the wireless NIC in this computer is there so that i can broadcast the connection and have connection on my laptop..

how do i make a wireless home network using ubuntu as my server? i want my laptop to connect to this computer's internet connection(internet sharing)..is it possible?

---

### Post by saskchi on 2008-11-02
Here is what I did to fix the wireless issue in 1501

First install any updates using the update manager or command line

1. Connect your laptop to the Internet using your Ethernet port
2. Click System-> Administration-> Hardware Drivers
3. Let it search for the Broadcom drivers
4. Activated drivers
5. Once installed, click the network icon and choose connect to hidden network
6. The rest is self explanatory

Hope this helps

---

