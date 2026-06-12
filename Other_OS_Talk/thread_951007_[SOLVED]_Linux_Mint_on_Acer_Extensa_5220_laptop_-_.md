---
title: "[SOLVED] Linux Mint on Acer Extensa 5220 laptop - no sound capture"
date: 2008-10-17
forum: Other OS Talk
---

### Post by Rytron on 2008-10-17
Hi,
I am unable to capture sound in sound recorder or GTK RecordMyDesktop.
Does anyone have a solution?
I use Linux Mint Elyssa.

I tried alsamixer in the command prompt but still no luck.

Please help.

Thanks.

---

### Post by Rytron on 2008-10-18
```
lspci
```


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by NoWayBill on 2008-10-19
To get sound working properly on my Extensa 5620 (Ubuntu 8.04), same chips as yours, I had to edit alsa-base file.

> sudo gedit /ect/modprobe.d/alsa-base

Add the line

**options snd-hda-intel model=acer**

Restart X, or reboot.

Internal mic is noisy here, but that's probably because it's sitting on a cooler pad.

---

### Post by Rytron on 2008-10-19
> **NoWayBill said:**
> To get sound working properly on my Extensa 5620 (Ubuntu 8.04), same chips as yours, I had to edit alsa-base file.



Add the line

**options snd-hda-intel model=acer**
alsa-base file
Restart X, or reboot.

Internal mic is noisy here, but that's probably because it's sitting on a cooler pad.

Hi,
I added that line. 
I tried to capture sound in Audacity, I just get noise.
Should it have been added at the end of the alsa-base file, or does it matter where the line is added?

---

### Post by NoWayBill on 2008-10-19
I have only recorded off of Line In previously.
After playing around a bit I found a possible solution.
Dbl click the sound icon, opening ALSA Mixer.
Be sure you have the correct input devices enabled.
See screen shots.
Select "Edit" "Preferences".
Go to the Edit tab and select the correct input device.
The levels must be set now.
Then "File" "Change Device" and select either of the capture devices.
Both worked noiselessly for me.

---

### Post by NoWayBill on 2008-10-19
After select Capture the only level device you will have is the Master.

---

### Post by Rytron on 2008-10-19
Thank you so much NoWayBill.
You are a genius.

:popcorn:

---

### Post by Rytron on 2008-10-20
Just one more thing(as Columbo used to say):

What are your settings for the pictures attached?

Thanks again.

---

### Post by NoWayBill on 2008-10-20
I leave everything maxed as you have it.
If the recording starts clipping, distortion because input levels are too high, you'll simply have to adjust to suit.

Also, if you're getting too much ambient noise from the room with Audacity, or what ever program you're using...
Turn down the input gain in ALSA Mixer and turn up the recording gain in the program.
It becomes a balancing act.
Ideally, you want the recorded level to almost clip, but stop just short.

The discerning ear knows that every room has different acoustic qualities.
Even moving the microphone(s) within a given room will effect the end recording.

I don't know if Mint offers a real-time kernel.
If so I recommend installing and booting it to do recording.
Then return to the generic kernel for normal PC use.
Or dual boot Mint and UbuntuStudio:)

An audiophile is born.

---

