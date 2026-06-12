---
title: "How To Enable Sound On Presario CQ40"
date: 2009-07-23
forum: Philippine Team
---

### Post by ysNoi on 2009-07-23
Hello..!

How to set my Presario CQ40 to enable sound on it..?

Thanks in advance...!:D

---

### Post by zeroseven0183 on 2009-07-24
Ahhmmm... Excuse me. What's that again?

We need more information please.

---

### Post by kingkalag on 2009-07-25
Could you speak plain Penguin, please :)

---

### Post by ysNoi on 2009-07-25
I mean I could not hear a sound when playing video files on my box. How could I enable it?

I'm using Jaunty and even on my XP guest OS I could not hear any sound when playing any mp3 files and others.

Please help.... :D

---

### Post by loell on 2009-07-25
name of your audio hardware?
```
lspci | grep audio
```

---

### Post by ysNoi on 2009-07-26
Here bro:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controlle

Thanks for the reply... :KS

---

### Post by loell on 2009-07-26
from [https://bugs.launchpad.net/ubuntu/+bug/269586]("https://bugs.launchpad.net/ubuntu/+bug/269586")

try editing **/etc/modprobe** , put an entry **options snd-hda-intel enable_msi=1** 


restart..

---

### Post by stace8383 on 2009-12-30
Thank you for the pointer. However I cannot seem to edit the required file - alsa-base.conf - it's read-only and apparently the owner of the file is "root". I can't change the permissions. Any tips??

Thanks

---

### Post by Samhain13 on 2010-01-01
^^
```
gksu gedit /path/to/file
```

Like that?

---

### Post by ysNoi on 2010-01-12
Im sorry mga bro.. I almost forgot to update this thread..!

Okey na yung sound ko...Hindi ko lang alam how it works pero after ng fresh install ko with Karmic biglang nagkaroon ng sound ang laptop ko..!

Thanks sa mga nagreply... ;)

---

### Post by stormsurge on 2010-01-12
Bro,
 
Piece of advice, do not enable the Software Modem in the Hardware Drivers. My sounds were gone after I activated it. Thanks!

---

### Post by ysNoi on 2010-01-12
On my box, the only enabled driver is Broadcom 802.11 Linux STA wireless driver.

---

