---
title: "No sound in Ubuntu 8.04"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by david tutton on 2008-08-08
I have installed Ubuntu 8.04 on a Sony Vaio VGN-B3VP and have no sound. Using the alsa mixer it tells me the volume is 100% on all channels, and displays the volume control as an Intel 82891DB-1CH4. The sound was ok when XP was installed.

---

### Post by Crafty Kisses on 2008-08-08
Post the following output:
```
lspci
```

---

### Post by northern lights on 2008-08-08
Could you please also post the outputs of ```
cat /proc/asound/cards
```
and ```
sudo lshw -C multimedia
```

Thank you.

---

### Post by david tutton on 2008-08-08
> **northern lights said:**
> Could you please also post the outputs of ```
cat /proc/asound/cards
```
and ```
sudo lshw -C multimedia
```

Thank you.
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by david tutton on 2008-08-08
> **david tutton said:**
> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
michelle@Aphrodite:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 9
michelle@Aphrodite:~$ sudo lshw -C multimedia
[sudo] password for michelle: 
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by vjkeito on 2008-08-08
looks like its a known problem [[**1**]("http://ubuntuforums.org/showthread.php?t=267604")] and [[**2**]("http://ubuntuforums.org/showthread.php?p=5547582")]

possibly using OSS for sound instead of ALSA might fix it.

ALSA is in dire need of bringing up-to-speed.

[*here's a useful guide to installing OSS in Ubuntu*]("http://www.ubuntu-unleashed.com/search/label/Better%20Sound%20in%20Ubuntu")

wish I could give you a guaranteed solution but alas I have no experience with this card.

Good Luck

---

### Post by dca on 2008-08-08
Try this (probably won't work, but):  open terminal and at CLI type 'gnome-volume-control' w/o the quotes...
 
On the second tab marked 'switch' I believe make sure there's no check-mark next to 'Headphones'...

---

### Post by david tutton on 2008-08-09
> **vjkeito said:**
> looks like its a known problem [[**1**]("http://ubuntuforums.org/showthread.php?t=267604")] and [[**2**]("http://ubuntuforums.org/showthread.php?p=5547582")]

possibly using OSS for sound instead of ALSA might fix it.

ALSA is in dire need of bringing up-to-speed.

[*here's a useful guide to installing OSS in Ubuntu*]("http://www.ubuntu-unleashed.com/search/label/Better%20Sound%20in%20Ubuntu")

wish I could give you a guaranteed solution but alas I have no experience with this card.

Good Luck

Thanks I tried that but no luck:confused:

---

### Post by david tutton on 2008-08-09
> **dca said:**
> Try this (probably won't work, but):  open terminal and at CLI type 'gnome-volume-control' w/o the quotes...
 
On the second tab marked 'switch' I believe make sure there's no check-mark next to 'Headphones'...

Thanks you were right, it didn't work:confused:

---

### Post by vjkeito on 2008-08-09
yeah, sorry it didn't work.

It would appear that the hardware isn't being picked up correctly.  Reading from [**another thread**]("https://bugs.launchpad.net/ubuntu/+bug/207495") it looks like using another Kernel could help, the issue should get resolved (fingers-crossed) at some point as from that link you can see it has been submitted to launchpad as a bug.

Also, [**this fix might be worth checking first**]("http://ph.ubuntuforums.com/showthread.php?t=161193").

Hope that helps!

Regards,
K3ito

---

### Post by northern lights on 2008-08-10
> **david tutton said:**
> michelle@Aphrodite:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 9
michelle@Aphrodite:~$ sudo lshw -C multimedia
[sudo] password for michelle: 
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
Your sound device appears to be perfectly well installed with the correct driver assigned, also.

This might sound rather banal, but can you check in alsamixer whether nothing's muted?
(MM is muted, OO is a running channel)

---

### Post by vjkeito on 2008-08-22
did you fix this?  using the OSS driver like I said should rectify your problem

hit **alt+F2** (brings up a run dialog box) then in the popup box type

```
gstreamer-properties
```

then in the **default output** section select the **OSS** plugin

---

