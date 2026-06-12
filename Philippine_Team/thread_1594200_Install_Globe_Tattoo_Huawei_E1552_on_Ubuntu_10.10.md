---
title: "Install Globe Tattoo Huawei E1552 on Ubuntu 10.10"
date: 2010-10-12
forum: Philippine Team
---

### Post by jhaykage on 2010-10-12
Instead of configuring it manually, I used the New Mobile Broadband Connection wizard in Ubuntu 10.10.

Problem now is, how to connect once I've plugged in the USB modem?

---

### Post by TNT1 on 2010-10-12
left click on network manager applet, you should see the connection listed. click it and you should connect.

---

### Post by jhaykage on 2010-10-12
> **TNT1 said:**
> left click on network manager applet, you should see the connection listed. click it and you should connect.

That's why I opened this thread, the connection is not listed in the network manager applet.:confused:

---

### Post by jeffreyvergara.NET on 2010-10-13
have you tried using wammu? i also used it when i tried 10.10 beta

---

### Post by zyperbyte on 2010-10-13
Hi, while the device is unplug, open an terminal and type "tail /var/log/messages". Then try plugging it in. The log file may give us a clue if the device is being detected..

---

### Post by jhaykage on 2010-10-13
> **jeffreyvergara.NET said:**
> have you tried using wammu? i also used it when i tried 10.10 beta

I've installed wammu but each I try to connect using the dongle, it says "GSM Network: Disconnected."

---

### Post by killer_d76 on 2010-10-14
first you have to install usb-mode-switch can be installed from the Software Manager/Center or thru Terminal by typing "sudo apt-get install usb-mode-switch" when you plug your USB modem it would automatically run the Network wizard..

Running the wizard should work fine but you need to configure APN so if you are using GLOBE prepaid use **internet.globe.com.ph** for Post-paid use **http.globe.com.ph** and restart your computer you should be able to connect now using your Globe Tatto USB modem

---

### Post by jhaykage on 2010-10-14
> **killer_d76 said:**
> first you have to install usb-mode-switch can be installed from the Software Manager/Center or thru Terminal by typing "sudo apt-get install usb-mode-switch" when you plug your USB modem it would automatically run the Network wizard..

Running the wizard should work fine but you need to configure APN so if you are using GLOBE prepaid use **internet.globe.com.ph** for Post-paid use **http.globe.com.ph** and restart your computer you should be able to connect now using your Globe Tatto USB modem

the APN configuration is OK. I've checked the Ubuntu Software Center and the following are installed:

usb-modeswitch-data
usb-modeswitch

I tried installing usb-mode-switch via Terminal and I get the following message:

---------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package usb-mode-switch
---------------------------------

The Globe Tattoo dongle now appears in the network manager applet. I try to connect but it still returns with the error message: "GSM network disconnected"

---

### Post by killer_d76 on 2010-10-14
try updating your system and try it again, because that is the exact procedure I did when I installed 10.10 on my friends laptop using same exact Globe Tattoo USB modem but it's the prepaid one, by the way have you tested your Globe Tattoo with other computer to test if it is connecting properly?

---

### Post by jhaykage on 2010-10-14
> **killer_d76 said:**
> try updating your system and try it again, because that is the exact procedure I did when I installed 10.10 on my friends laptop using same exact Globe Tattoo USB modem but it's the prepaid one, by the way have you tested your Globe Tattoo with other computer to test if it is connecting properly?

Now I'm stumped. My system is up-to-date, at least the Update Manager says so. And the Globe Tattoo dongle works fine on my Windows 7 machine.:confused:

Btw, here's the log when I use the "tail /var/log/messages" command after plugging in the dongle

=====================
Oct 14 17:52:53 jhay-laptop kernel: [31459.136043] usb 3-1: new low speed USB device using uhci_hcd and address 5
Oct 14 17:52:54 jhay-laptop kernel: [31459.327959] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input16
Oct 14 17:52:54 jhay-laptop kernel: [31459.328118] generic-usb 0003:046D:C019.0004: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.1-1/input0
Oct 14 17:59:04 jhay-laptop kernel: [31829.544502] lo: Disabled Privacy Extensions
Oct 14 18:35:51 jhay-laptop kernel: [34036.372242] Skipping EDID probe due to cached edid
Oct 14 19:03:38 jhay-laptop kernel: [35703.303471] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3a:6c:d0:c7:00:04:ed:d2:85:5a:08:00 SRC=174.36.58.233 DST=192.168.254.100 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=64771 DF PROTO=TCP SPT=80 DPT=49270 WINDOW=8213 RES=0x00 ACK URGP=0 
Oct 14 19:15:02 jhay-laptop kernel: [36387.368045] usb 1-5: reset high speed USB device using ehci_hcd and address 7
Oct 14 19:22:53 jhay-laptop kernel: [36858.785765] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3a:6c:d0:c7:00:04:ed:d2:85:5a:08:00 SRC=192.168.254.254 DST=192.168.254.100 LEN=340 TOS=0x00 PREC=0x00 TTL=255 ID=2045 PROTO=UDP SPT=1900 DPT=43098 LEN=320 
Oct 14 19:26:24 jhay-laptop kernel: [37069.368048] usb 1-5: reset high speed USB device using ehci_hcd and address 7
Oct 14 19:29:52 jhay-laptop kernel: [37277.368043] usb 1-5: reset high speed USB device using ehci_hcd and address 7
======================

---

### Post by killer_d76 on 2010-10-14
does the Globe Tattoo logo show up on your desktop when you plug your usb modem on your 10.10?.. as this would mean that your 10.10 has detected your usb modem properly.

---

### Post by killer_d76 on 2010-10-14
can you pull up Terminal and type **lsusb** and post the result here.

---

### Post by killer_d76 on 2010-10-14
did a quick research... and I found this **[BAD NEWS]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2480190.html")** it seems that I have installed 10.09 on my friends lappie then.. aawww! and I told her that it was the latest version! :oops:

---

### Post by jhaykage on 2010-10-14
Here's what lsusb returns:

=========
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 04f2:b057 Chicony Electronics Co., Ltd integrated USB webcam
Bus 001 Device 007: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jhay@jhay-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 022: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 008: ID 04f2:b057 Chicony Electronics Co., Ltd integrated USB webcam
Bus 001 Device 007: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
=========

The Globe Tattoo logo doesn't show up on the desktop when the dongle is plugged in.

---

### Post by jhaykage on 2010-10-14
> **killer_d76 said:**
> did a quick research... and I found this **[BAD NEWS]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2480190.html")** it seems that I have installed 10.09 on my friends lappie then.. aawww! and I told her that it was the latest version! :oops:

Oh crap!:(

---

### Post by killer_d76 on 2010-10-15
> **jhaykage said:**
> Here's what lsusb returns:

=========
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 04f2:b057 Chicony Electronics Co., Ltd integrated USB webcam
Bus 001 Device 007: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jhay@jhay-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**[COLOR="Red"]Bus 001 Device 022: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem[/COLOR]**
Bus 001 Device 008: ID 04f2:b057 Chicony Electronics Co., Ltd integrated USB webcam
Bus 001 Device 007: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
=========

The Globe Tattoo logo doesn't show up on the desktop when the dongle is plugged in.

It seems that your the Ubuntu recognized your USB Modem it's just that 10.10 is relatively new!, there are a few more bugs to fix for 10.10 just wait for a few more updates and this should work properly on your Linux machine ;), that's why I wait for a few months before I install the latest version of Ubuntu :D

---

### Post by jhaykage on 2010-10-15
It's a waiting game for now then.

Thanks for all the help!:)

---

### Post by bill.denbigh on 2010-10-19
I have exactly the same problem with my globe tattoo ZTE 626 modem. This i understand is a problem with modeswitch 1.1.4 that is now included in ubuntu 10.10

A similar problem is reported in:
[https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568)

I have been trying to find help with this here:

[http://ubuntuforums.org/showthread.php?t=1595964](http://ubuntuforums.org/showthread.php?t=1595964)

and:

[http://ubuntuforums.org/showthread.php?t=1594029](http://ubuntuforums.org/showthread.php?t=1594029)

but to date have had no help...

Sorry to not give you a solution, just misery loves company ;-)

---

### Post by junetrinidad on 2010-10-30
hello to all, i have globe tattoo huawei e1552 and using it right now in ubuntu 10.10, i haven't installed anything, i just plugged it in and was auto detected. a wizard then asked my provider (globe) and just changed the settings:

1.) Mobile Broadband Tab > Number > *99#
2.) Mobile Broadband Tab > APN > internet.globe.com.ph
3.) Mobile Broadband Tab > Type > Any
4.) PPP Settings > Configure Methods > PPP (uncheck others)
5.) Tick Connect automatically check box

Hope this helps.

---

### Post by aljoriz on 2010-10-30
A correction, Sir, If I may

4.) PPP Settings > Configure Methods > **PAP** (uncheck others)

not PPP

---

### Post by junetrinidad on 2010-10-31
> **aljoriz said:**
> A correction, Sir, If I may

4.) PPP Settings > Configure Methods > **PAP** (uncheck others)

not PPP

you're right, its **PAP**, thanks for the correction. my problem now is how to receive/send text messages using the usb dongle (huawei e1552) to check my balance without having to insert it's sim in my cellphone. i already installed wammu, but i don't know the right configurations yet. searching for info right now.

---

### Post by aljoriz on 2010-11-01
^
sudo apt-get install wammu

---

### Post by junetrinidad on 2010-11-01
i installed wammu using the add/remove software, i just have to configure the settings. thanks.

---

### Post by nfaustin on 2010-11-03
> **junetrinidad said:**
> i installed wammu using the add/remove software, i just have to configure the settings. thanks.

junetrinidad, 
Have you successfully configure the wammu?
I tried mine using Smartbro but it failed.

---

### Post by junetrinidad on 2010-11-05
> **nfaustin said:**
> junetrinidad, 
Have you successfully configure the wammu?
I tried mine using Smartbro but it failed.

Here is what i did:

1. Insert Huawei E1552 to USB port and in the Wammu file menu, click Settings

2. Connection Tab > Phone Connection > click Add

3. There will be a Guided Configuration wizard, here is my selection:
> USB Cable
> I don't know
> AT based
> Generic AT over serial line or it's emulation
> Device Name of USB port = /dev/ttyUSB0

4. I checked my settings in Wammu file menu Settings > Connection Tab:

> Phone Connection = huawei (position 1)
> Name = huawei
> device = /dev/ttyUSB0
> connection = at
> model = auto

5. Then on the phone file menu click connect

6. After my device is connected, go to Retrieve file menu:
> Contacts(SIM)
> Messages

Sorry if it is long, I just hope it will work for you too

---

