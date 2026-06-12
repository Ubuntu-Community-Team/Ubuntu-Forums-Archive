---
title: "External dialup modem not found"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by michael119 on 2014-03-10
While this might fall under the networking section, I'm relatively new to Linux so thought I might have more "newb" oriented answers if posted here. 

I have an HP Pavilion p6823w Desktop PC that I'm saving from Windows. It's my neighbor's computer and they only have dialup. I've installed Ubuntu 12.04 LTS and am using it now via broadband (at my house) to install updates, post to this forum, etc. 

Since they were using Windows they were connecting via a soft modem and I didn't want that headache so I purchased a USRobotics model 5686 external modem off ebay. Since it is a serial device, and this computer doesn't have a serial port, I purchased a Sabrent Serial to USB cable (DB-9 RS-232). The cable has the SBT-FTDI chip so it is supposed to work. I've read other posts from the Ubuntu community where others have had luck using this same setup (modem and cable). 

The problem, as indicated in the title of this post, is that the modem cannot be found. I'm using Gnome PPP and when I go into Setup and go through the device list one at a time and click "detect" I get the "No modem was found on your system" message. 

If I go to terminal and use *lsusb* I get the following:
```
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 005 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 005 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
So it appears that the system is seeing the cable--specifically the chipset if I understand this correctly--but not the modem.

I've done quite a bit of searching on the forums for a similar problem but most of the past posters were using an older verions of Ubuntu and the solutions don't apply (downloading of packages that are installed by default in my case). 

Is there any hope for resolving this using Ubuntu? If not what flavor of Linux do I need to install so that I can get my neighbor back online and surfing at the blazing speed of dialup?

---

### Post by raja.genupula on 2014-03-10
> Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer




what is that  ? 

seems to be you need usb modswitch.

---

### Post by Vladlenin5000 on 2014-03-11
I don't think so. 'modswitch' is for "3G" USB dongle modems which happen to have also a small internal flash memory*.
 
*This mass storage device usually contains Windows drivers/dial-up software intended to run in the first use in a given Windows computer; after that the internal memory is no longer mounted in subsequent sessions, the device working as modem only. 'modswitch' does that in Linux.

The case here is a serial modem connected via an USB-to-Serial adapter cable.
When running the list USB command we should expect to see only the adapter:
```
Bus 005 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
```

This adapter requires drivers and the modem requires configuration, ie, you need to know at least to which COM port it has been assigned to. This link contains specific information for serial modems at the bottom of the page: [https://help.ubuntu.com/community/DialupModemHowto/Modems](https://help.ubuntu.com/community/DialupModemHowto/Modems)

---

### Post by michael119 on 2014-03-11
Raja, Bus 002 Device 004 is a Flash Card Reader. This PC has one preinstalled on the front of the machine. So it is recognizing it as it should. 

Vladlenin5000: 
I've read that page (probably six times) but I'm not sure how that helps me fix the problem. 

> This adapter requires drivers 
I called Sabrent and they told me that Ubuntu comes with all the drivers that are needed. That, > Linux will just see it was what they told me. I have a disc with the following files in a Linux folder:
ftdi_sio.c
ftdi_sio.h
Makefile
Rules.make
I asked the tech support about those files and how I might install them since I was new to Linux and he kept saying they weren't needed. 

> ...and the modem requires configuration, ie, you need to know at least to which COM port it has been assigned to...
So how do I configure the modem and how do I find which COM port it is assigned to?

---

### Post by michael119 on 2014-03-11
Okay. I did a little research regarding my last question to Vladlenin5000 and found [this page]("http://www.cyberciti.biz/faq/find-out-linux-serial-ports-with-setserial/"). Following along I entered this in terminal:
```
$ dmesg | grep tty
``` which returned this:
```
[    0.000000] console [tty0] enabled
[    7.820811] usb 5-2: FTDI USB Serial Device converter now attached to ttyUSB0
```

The next step was to use setserial. Didn't have it. Installed it using the software center since the terminal command for it was returning a not found error. 

Using setserial, and continuing with the directions on the page, I typed the following into terminal:
```
setserial -g /dev/ttyS[0123]
```
Which returned:
```
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
```
After looking at this a second I realised that I needed to be looking at USB (at least that's what I thought, maybe?) so I tried this command:
```
setserial -g /dev/ttyUSB[0123]
```
and got this:
```
/dev/ttyUSB0, UART: unknown, Port: 0x0000, IRQ: 0, Flags: low_latency
```

I have no idea if this gets me any closer but thought I'd do a little work instead of relying totally on your help. But that still leaves me at a standstill. 

What are my next steps?? Thanks.

---

### Post by michael119 on 2014-03-17
At this point I would welcome some advice on whether I should just abandon Ubuntu and load another distro or is there hope for making Ubuntu work with this dialup? Surely someone else has successfully been able to use Linux for dialup. 
TIA.

---

### Post by dretek on 2014-06-13
> **michael119 said:**
> At this point I would welcome some advice on whether I should just abandon Ubuntu and load another distro or is there hope for making Ubuntu work with this dialup? Surely someone else has successfully been able to use Linux for dialup. 
TIA.

Hi Michael, Sorry I am not much help. I am at the same stage as you, except I am actually using an on board serial port. to get any dialer action I had to add my user to the dilout group... Which i think is sudo usermod -a -G dialout username... So I can now get dialing using GNOME PPP but I cannot get it to talk to the modem. Not sure if I have a layer one problem though.

From what I have read Ubuntu has stripped dial-up support since version 11? I am probably wrong, but its not as native as other distros anymore.
If I find anything more helpful I let you know.

---

