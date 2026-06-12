---
title: "wifi card firmware update"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by gulmer on 2012-09-10
Got a question from a friend who is using a laptop with dual operating systems, windows and ubuntu.The ubuntu os needs to update the wifi firmware and he is concerned that if he "flashes"(his words) the wifi card with a firmware update,the card will not work with the windows os. Is his concerns of value or does the firmware update only affect ubuntu's ability to use the wifi card? His wifi card is a Broadcom model.

---

### Post by anewguy on 2012-09-10
Normally with Ubuntu, and Linux in general, it's not flashing the device.  The firmware it is requesting is normally stored as a file on the system.  If you could post back the exact message text and what wireless card is being used (from lspci and lsusb, as well as the output from lsmod), we can go from there.


EDIT:  Forgot to mention - this is very common with Broadcom chipset based adapters.  Please post back the output of lspci and lsusb so we can see exactly which chipset it is using and come up with a solution for you.

---

### Post by gulmer on 2012-09-11
> **anewguy said:**
> Normally with Ubuntu, and Linux in general, it's not flashing the device.  The firmware it is requesting is normally stored as a file on the system.  If you could post back the exact message text and what wireless card is being used (from lspci and lsusb, as well as the output from lsmod), we can go from there.


EDIT:  Forgot to mention - this is very common with Broadcom chipset based adapters.  Please post back the output of lspci and lsusb so we can see exactly which chipset it is using and come up with a solution for you.

I'm going to pass this torch on to my friend and let him communicate directly with you. Thank you.

---

### Post by pschamel on 2012-09-11
[SIZE=2]Thank you... your explanation (plus a few things I came across while studying it) may have sorted some of this out for me (if "firmware" in this environment is system software on the computer, not code actually flashed to the device - which I'm familiar with from old-time PCM/CIA network cards and my routers - I'm much less concerned about OS interoperability), but, since I'm this far, I may as well finish. 

Here's what you requested, along with similar info from the Windows perspective, and my notes...

1) Per WinXP Device Manager & Dell-specified setup s/w for this Latitude D620 laptop:
• Wireless Device Designation: Dell Wireless 1390 WLAN Mini-Card
• BUT: many of the install files are named bcm...
• AND Install ReadMe for Dell Wireless 1390 describes a switch/setting that: "Turns Windows Wireless Zero Configuration Service off and configures the Broadcom tray utility to manage the network." -- so, it may be that the device is by Broadcom and private-labeled for Dell, or simply Broadcom-compatible
• Dell's Install files include wired network device: "Broadcom-Application 57XXGigabitIntegratedController" + driver and diagnostic utility for same device name

2) Ubuntu "System Settings/Network" shows "Wireless - Firmware Missing" -- Previously, the Software Update Manager prompted me to install the wireless firmware. Now, after installing a batch of updates available at logon today (including some Linux "firmware," but not this wireless card's), Settings still show, as above, but I can't find the prompt I saw before to "Install(?) Firmware"

BUT
Ubuntu "Additional Drivers" now wants to "activate" Broadcom STA Wireless Driver -- with additional info:
"This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware."

AND
Based on what's below (esp. lspci, last lines), that would seem appropriate to "Activate"

3) lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

4) lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 003: ID 0480:a006 Toshiba America Info. Systems, Inc. 
Bus 001 Device 005: ID 050d:0413 Belkin Components 
Bus 004 Device 002: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 001 Device 006: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 007: ID 046d:08cb Logitech, Inc. Mic (Notebooks Pro)
Bus 001 Device 008: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader

5) lsmod:
Module                  Size  Used by
nls_utf8               12493  1 
udf                    84466  1 
crc_itu_t              12627  1 udf
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_hda_codec_idt      60251  1 
arc4                   12473  2 
joydev                 17393  0 
b43                   342643  0 
mac80211              436455  1 b43
snd_usb_audio         101566  1 
pcmcia                 39791  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_pcm                80845  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
i915                  414817  3 
drm_kms_helper         45466  1 i915
cfg80211              178679  2 b43,mac80211
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
drm                   197692  4 i915,drm_kms_helper
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
bcma                   25651  1 b43
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27465  0 
usbhid                 41906  0 
ssb                    50691  1 b43
snd                    62064  19 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
lp                     17455  0 
psmouse                72919  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
uvcvideo               67203  0 
pcmcia_rsrc            18367  1 yenta_socket
videodev               86588  1 uvcvideo
hid                    77367  1 usbhid
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
dell_laptop            17767  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
serio_raw              13027  0 
dcdbas                 14098  1 dell_laptop
mac_hid                13077  0 
wmi                    18744  1 dell_wmi
video                  19068  1 i915
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  1 
tg3                   141369  0 
[/SIZE]

---

### Post by pschamel on 2012-09-11
and, after all that, I found:
[http://askubuntu.com/questions/87519/how-to-make-my-dell-1390-wlan-minicard-work](http://askubuntu.com/questions/87519/how-to-make-my-dell-1390-wlan-minicard-work)

Three steps and a rebook, and all is well.

---

### Post by pschamel on 2012-09-11
...rebooT...

---

