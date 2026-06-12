---
title: "loss of sound"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by zirgut on 2012-06-23
Hi,
In an uninformed attempt to remove a fire fox add-on package, an autoform filler, I deleted a package called libwww-mechanize-formfiller-perl(0.10-2). Along with that quite a few other packages were deleted, all of which are listed in removals in USC. I think it is from that point that the sound disappeared. I am wondering how it might be possible to reload those files and also if that is the real cause of the sound loss. I am on Ubuntu Pangolin.
Thanks for the anticipated help

---

### Post by idoitprone on 2012-06-23
> **zirgut said:**
> Hi,
In an uninformed attempt to remove a fire fox add-on package, an autoform filler, I deleted a package called libwww-mechanize-formfiller-perl(0.10-2). Along with that quite a few other packages were deleted, all of which are listed in removals in USC. I think it is from that point that the sound disappeared. I am wondering how it might be possible to reload those files and also if that is the real cause of the sound loss. I am on Ubuntu Pangolin.
Thanks for the anticipated help

post the output of

```
sudo cat /var/log/dpkg.log | tail -n 100
```


it should give you the history of your upgrading

---

### Post by zirgut on 2012-06-23
Hi,
Thanks for your reply idiotprone.
This is what came up
2012-06-22 14:45:37 status unpacked gnome-settings-daemon 3.4.2-0ubuntu0.1
2012-06-22 14:45:37 trigproc man-db 2.6.1-2 2.6.1-2
2012-06-22 14:45:37 status half-configured man-db 2.6.1-2
2012-06-22 14:45:44 status installed man-db 2.6.1-2
2012-06-22 14:45:44 trigproc bamfdaemon 0.2.118-0ubuntu0.1 0.2.118-0ubuntu0.1
2012-06-22 14:45:44 status half-configured bamfdaemon 0.2.118-0ubuntu0.1
2012-06-22 14:45:44 status installed bamfdaemon 0.2.118-0ubuntu0.1
2012-06-22 14:45:44 trigproc desktop-file-utils 0.20-0ubuntu2 0.20-0ubuntu2
2012-06-22 14:45:44 status half-configured desktop-file-utils 0.20-0ubuntu2
2012-06-22 14:45:44 status installed desktop-file-utils 0.20-0ubuntu2
2012-06-22 14:45:45 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2012-06-22 14:45:45 status half-configured gnome-menus 3.4.0-0ubuntu1
2012-06-22 14:45:45 status installed gnome-menus 3.4.0-0ubuntu1
2012-06-22 14:45:45 trigproc libglib2.0-0 2.32.3-0ubuntu1 2.32.3-0ubuntu1
2012-06-22 14:45:45 status half-configured libglib2.0-0 2.32.3-0ubuntu1
2012-06-22 14:45:46 status installed libglib2.0-0 2.32.3-0ubuntu1
2012-06-22 14:45:47 trigproc gconf2 3.2.5-0ubuntu2 3.2.5-0ubuntu2
2012-06-22 14:45:47 status half-configured gconf2 3.2.5-0ubuntu2
2012-06-22 14:45:47 status installed gconf2 3.2.5-0ubuntu2
2012-06-22 14:45:48 trigproc hicolor-icon-theme 0.12-1ubuntu2 0.12-1ubuntu2
2012-06-22 14:45:48 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2012-06-22 14:46:01 status installed hicolor-icon-theme 0.12-1ubuntu2
2012-06-22 14:46:02 startup packages configure
2012-06-22 14:46:02 configure libwbclient0 2:3.6.3-2ubuntu2.3 <none>
2012-06-22 14:46:02 status unpacked libwbclient0 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:02 status half-configured libwbclient0 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:03 status installed libwbclient0 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:03 status triggers-pending libc-bin 2.15-0ubuntu10
2012-06-22 14:46:03 configure libsmbclient 2:3.6.3-2ubuntu2.3 <none>
2012-06-22 14:46:03 status unpacked libsmbclient 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:03 status half-configured libsmbclient 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:03 status installed libsmbclient 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:03 configure firefox 13.0.1+build1-0ubuntu0.12.04.1 <none>
2012-06-22 14:46:03 status unpacked firefox 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:03 status unpacked firefox 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:03 status unpacked firefox 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:04 status unpacked firefox 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:04 status unpacked firefox 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:04 status half-configured firefox 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:08 status installed firefox 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:09 configure firefox-globalmenu 13.0.1+build1-0ubuntu0.12.04.1 <none>
2012-06-22 14:46:09 status unpacked firefox-globalmenu 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:09 status half-configured firefox-globalmenu 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:09 status installed firefox-globalmenu 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:09 configure firefox-gnome-support 13.0.1+build1-0ubuntu0.12.04.1 <none>
2012-06-22 14:46:09 status unpacked firefox-gnome-support 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:10 status half-configured firefox-gnome-support 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:10 status installed firefox-gnome-support 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:10 configure firefox-locale-en 13.0.1+build1-0ubuntu0.12.04.1 <none>
2012-06-22 14:46:10 status unpacked firefox-locale-en 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:10 status half-configured firefox-locale-en 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:10 status installed firefox-locale-en 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:11 configure samba-common 2:3.6.3-2ubuntu2.3 <none>
2012-06-22 14:46:11 status unpacked samba-common 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:11 status unpacked samba-common 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:11 status unpacked samba-common 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:11 status unpacked samba-common 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:11 status half-configured samba-common 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:14 status installed samba-common 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:15 configure smbclient 2:3.6.3-2ubuntu2.3 <none>
2012-06-22 14:46:15 status unpacked smbclient 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:15 status half-configured smbclient 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:15 status installed smbclient 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:15 configure samba-common-bin 2:3.6.3-2ubuntu2.3 <none>
2012-06-22 14:46:15 status unpacked samba-common-bin 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:15 status half-configured samba-common-bin 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:15 status installed samba-common-bin 2:3.6.3-2ubuntu2.3
2012-06-22 14:46:16 configure thunderbird 13.0.1+build1-0ubuntu0.12.04.1 <none>
2012-06-22 14:46:16 status unpacked thunderbird 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status unpacked thunderbird 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status unpacked thunderbird 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status unpacked thunderbird 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status half-configured thunderbird 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status installed thunderbird 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 configure thunderbird-globalmenu 13.0.1+build1-0ubuntu0.12.04.1 <none>
2012-06-22 14:46:16 status unpacked thunderbird-globalmenu 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status half-configured thunderbird-globalmenu 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status installed thunderbird-globalmenu 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 configure thunderbird-gnome-support 13.0.1+build1-0ubuntu0.12.04.1 <none>
2012-06-22 14:46:16 status unpacked thunderbird-gnome-support 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:16 status half-configured thunderbird-gnome-support 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:17 status installed thunderbird-gnome-support 13.0.1+build1-0ubuntu0.12.04.1
2012-06-22 14:46:17 configure xserver-xorg-input-evdev 1:2.7.0-0ubuntu1.2 <none>
2012-06-22 14:46:17 status unpacked xserver-xorg-input-evdev 1:2.7.0-0ubuntu1.2
2012-06-22 14:46:17 status half-configured xserver-xorg-input-evdev 1:2.7.0-0ubuntu1.2
2012-06-22 14:46:17 status installed xserver-xorg-input-evdev 1:2.7.0-0ubuntu1.2
2012-06-22 14:46:17 configure xserver-xorg-input-vmmouse 1:12.9.0-0ubuntu0.1 <none>
2012-06-22 14:46:17 status unpacked xserver-xorg-input-vmmouse 1:12.9.0-0ubuntu0.1
2012-06-22 14:46:17 status half-configured xserver-xorg-input-vmmouse 1:12.9.0-0ubuntu0.1
2012-06-22 14:46:17 status installed xserver-xorg-input-vmmouse 1:12.9.0-0ubuntu0.1
2012-06-22 14:46:17 configure gnome-settings-daemon 3.4.2-0ubuntu0.1 <none>
2012-06-22 14:46:17 status unpacked gnome-settings-daemon 3.4.2-0ubuntu0.1
2012-06-22 14:46:17 status unpacked gnome-settings-daemon 3.4.2-0ubuntu0.1
2012-06-22 14:46:17 status unpacked gnome-settings-daemon 3.4.2-0ubuntu0.1
2012-06-22 14:46:17 status unpacked gnome-settings-daemon 3.4.2-0ubuntu0.1
2012-06-22 14:46:18 status half-configured gnome-settings-daemon 3.4.2-0ubuntu0.1
2012-06-22 14:46:18 status installed gnome-settings-daemon 3.4.2-0ubuntu0.1
2012-06-22 14:46:18 trigproc libc-bin 2.15-0ubuntu10 <none>
2012-06-22 14:46:18 status half-configured libc-bin 2.15-0ubuntu10
2012-06-22 14:46:18 status installed libc-bin 2.15-0ubuntu10
adrian@adrian-Dell-DM051:~$ 
 
Is this just a record of my last update? The mistaken deletions I did was done about a week ago.

---

### Post by HiImTye on 2012-06-23
try this:
```
sudo cat /var/log/dpkg.log | grep 'remov' | tail -n 20
```

---

### Post by zirgut on 2012-06-23
Thanks HilmTye
This is what came up which looks like the list of packages I inadvertently removed
 2012-06-16 23:58:17 remove icc-profiles-free 2.0.1+dfsg-1 <none>
2012-06-16 23:58:18 remove libattica0 0.2.80-0ubuntu2 <none>
2012-06-16 23:58:19 remove libwww-mechanize-formfiller-perl 0.10-2 <none>
2012-06-16 23:58:20 remove libdata-random-perl 0.06-1 <none>
2012-06-16 23:58:21 remove libgd-gd2-perl 1:2.46-3build1 <none>
2012-06-16 23:58:22 remove libgtkspell3-0 2.0.16-1ubuntu2 <none>
2012-06-16 23:58:22 remove libwww-mechanize-perl 1.71-1 <none>
2012-06-16 23:58:23 remove libhttp-server-simple-perl 0.44-1 <none>
2012-06-16 23:58:24 remove libid3tag0 0.15.1b-10build2 <none>
2012-06-16 23:58:25 remove libindicator3-6 0.4.1-0ubuntu1 <none>
2012-06-16 23:58:25 remove libindicator6 0.4.1-0ubuntu1 <none>
2012-06-16 23:58:26 remove libllvm2.9 2.9+dfsg-3ubuntu4 <none>
2012-06-16 23:58:26 remove libminiupnpc5 1.5-2ubuntu2 <none>
2012-06-16 23:58:27 remove libnatpmp1 20110808-3ubuntu1 <none>
2012-06-16 23:58:28 remove libnl3 3.0-1.1ubuntu1 <none>
2012-06-16 23:58:28 remove libx264-116 2:0.116.2042+git178455c-1ubuntu1 <none>
2012-06-16 23:58:29 remove linux-headers-3.0.0-12-generic 3.0.0-12.20 <none>
2012-06-16 23:58:35 remove linux-headers-3.0.0-12 3.0.0-12.20 <none>
2012-06-16 23:58:39 remove nvidia-settings 295.33-0ubuntu1 <none>
2012-06-16 23:58:40 remove screen-resolution-extra 0.14ubuntu2 <none>
adrian@adrian-Dell-DM051:~$

---

### Post by zirgut on 2012-06-27
The struggle continues and I am now looking for new suggestions on solving this problem. I have reinstalled as many of those packages as possible but it has had no effect on returning the sound.
Does anyone have any new suggestions, apart from learning to lip read?
In anticipation
zirgut

---

### Post by jmfal on 2012-06-27
HI Zirgut
Open a terminal and run
```
 lspci -v      
```
 And post the results using the code tag  "#"  it makes it easier to read.

Before you do that in a terminal run
```
  alsamixer    
```

IS there a sound card listed in the top left
press F5 and turn up all volumes using the arrows on your keyboard , look for pcmand turn that uo also.

---

### Post by zirgut on 2012-06-28
Hi,
Thanks for your help.
Here is what has emerged
The card came up as HDA Intel and the  chip as Sigma Tel STAC 9221 A1.
I turned everything up and still no sound though could here the very faintest trace of sound at maximum volume. Not enough to actually here what someone was saying.
So here is the output from lspci -v
#00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: Dell Device 01d2
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ec000000-efefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 01d2
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: ebf00000-ebffffff
    Prefetchable memory behind bridge: 0000000040100000-00000000402fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: ebe00000-ebefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 01d2
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fea0 [size=16]
    Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Dell Device 01d2
    Flags: medium devsel, IRQ 9
    I/O ports at ece0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ec000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc80 [size=128]
    Expansion ROM at efe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs SB0570 [SB Audigy SE]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at cca0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: snd_ca0106
    Kernel modules: snd-ca0106

03:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
    Subsystem: Dell Device 01ab
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at ebeff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ccc0 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100
I look forward to hearing your analysis.
With appreciation
zirgut

---

### Post by jmfal on 2012-06-28
Can you get sound out of the onboard card.

---

### Post by jmfal on 2012-06-28
Try this it should load the sound module till you log out or restart
```
 sudo modprobe snd-hda-intel      
```

to use your onboard sound
To use the sound blaster try

```
 sudo modprobe snd-ca0106      
```

 if that works and your satisfied then run this
```
 sudo nano /etc/modules snd-ca0106     
```

For the S/B card,  or replace "ca0106" with "hda-intel" , make sure you leave the hyphen in after  "snd"..
Also open up sound settings and click on the card that says "analog" if there  are two listed.

---

### Post by jmfal on 2012-06-28
Try this it should load the sound module till you log out or restart
```
 sudo modprobe snd-hda-intel      
```

to use your onboard sound
To use the sound blaster try

```
 sudo modprobe snd-ca0106      
```

 if that works and your satisfied then run this
```
 sudo nano /etc/modules snd-ca0106     
```

For the S/B card,  or replace "ca0106" with "hda-intel" , make sure you leave the hyphen in after  "snd"..
Also open up sound settings and click on the card that says "analog" if there  are two listed.
You can try the other chip (SIGMA)  for onboard sound , select that card in the sound settings

---

### Post by zirgut on 2012-06-29
Much thanks for all your help.
I do now have sound! hooray. Well I have sound on Banshee and on the test on sound settings. However I do not have sound on videos that I play on Yahoo news for instance. Also I notice that when I try to turn the video on to full screen it stays the same. Could this be related to another issue which is running in low graphics mode. On starting up the computer this message comes up about not being able to detect the graphics card and then I select the option to run in low graphics mode for this one session.
This problem arose when I deleted the guest log-in and I overcame it one time by installing loads of updates that were due, This brought the guest log-in back as well. So I tried deleting again,thinking that this time I was wiser and knew how to manage the process. Alas the graphics card problem returned although the guest log-in has vanished.
Also do you have any cures for a touch of arthritis in the right hand middle finger?
With much appreciation
zirgut

---

### Post by jmfal on 2012-06-29
GOOD!
Using which sound card??

Ubuntu-restricted-extras  should help with the video sound. If it doesn't you might need to get the medibuntu repositiry.

lspci -v shows that you are using the newvuea driver 

Try rebooting to normal and see what happens or you can try to reinstall the nvidia driver in low graphics.

---

### Post by zirgut on 2012-07-01
Hi again,
I found the Ubuntu restricted extras and downloaded and also the medibuntu repositiry. But so far to no avail. I am not sure what you mean when you say about rebooting to normal and I don't know how to reinstall the nividia driver. Sorry but step by step help is needed on that.
Thanks for your patience.
zirgut

---

### Post by jmfal on 2012-07-01
Thats a plain old restart your pc

Try installing  from medibuntu 
1.non-free codecs
2.w64 codecs
3.libavcodec-extra-53
4.libavutilit-extra-51

You should get the graphics problem fixed , them worry about watching videos.

---

### Post by jmfal on 2012-07-01
Take a look at this:

[http://ubuntuforums.org/showthread.php?t=1771806](http://ubuntuforums.org/showthread.php?t=1771806)

I istalled this ppa and the driver and it fixed the problems that I was having, stable, no problems.
I f you decide to add this ppa and use the driver, do one command at a time, don't try to copy/paste the whole thing at once.

Open the Update center and go to "other software" and make sure that the lines for the ppa and medibuntu have a check in the box.

---

### Post by zirgut on 2012-07-02
Hi again,
I have tried this and everything has gone a bit haywire. Have to say that I did not read your instructions carefully and did try to install by paste the whole command line together but then went back and did it line by line. Now when I start up the log-in screen does not come up. I eventually got into ubuntu by using a previous version. The low graphics mode warning was still there.  Medibuntu has a check in it but not sure what the ppa is?
Will check back later.
Thanks
zirgut

---

### Post by jmfal on 2012-07-02
I think you need to enable "nomodeset"  till you can get a driver installed;
Read this, all of it, there is a section on how to enable with existing OS .....follow the instructions there.

Once you get to the desktop run

```
 lspci -v
```

and see which kernal being used
If it shows none in use then you can install the driver from the ppa  using synaptic >>click on origin (bottom left) >>> click on the x-swat ppa >>> and install nvidia-current.

The ppa should be in the same section as medibuntu, in the "Other Software" tab of the Update Manager..

---

### Post by zirgut on 2012-07-02
Hi,
This is what came up when I entered lspci -v
#
~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
    Subsystem: Dell Device 01d2
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ec000000-efefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Dell Device 01d2
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: ebf00000-ebffffff
    Prefetchable memory behind bridge: 0000000040100000-00000000402fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: ebe00000-ebefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 01d2
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 01d2
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fea0 [size=16]
    Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Dell Device 01d2
    Flags: medium devsel, IRQ 9
    I/O ports at ece0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])
    Flags: fast devsel, IRQ 11
    Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ec000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc80 [size=128]
    Expansion ROM at efe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: nouveau, nvidiafb

03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs SB0570 [SB Audigy SE]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at cca0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106

03:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
    Subsystem: Dell Device 01ab
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at ebeff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ccc0 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

A lot of kernals are mentioned. Which one should I be looking out for?
Many thanks
Zirgut

---

### Post by jmfal on 2012-07-02
It looks like there are no kernals in use.

Try installing the nvidia-current from the x-swat-x ppa using synaptic or in a terminal:

```
 sudo apt-get install nvidia-current    
```

---

### Post by zirgut on 2012-07-02
Hi,

Looks like it is installed.
This came up when i put in the command line
# Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by zirgut on 2012-07-02
This is what came up when I entered the command line.
# 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Sorry but what is ppa using synaptic

---

### Post by jmfal on 2012-07-02
OK you need to restart  to the desktop an make sure everything is good.

---

### Post by zirgut on 2012-07-02
Hi,
Well I restarted the computer and same thing.I get the lilac ubuntu screen colour for about 2 minutes and then it goes black and nothing more.
In a previous version I get the lilac screen for about 2 minutes and then black and about 15 secs the low graphics mode message comes on screen and after about 5 secs the mouse  becomes operative and I can reach the log-in screen.

---

### Post by zirgut on 2012-07-02
I am just wondering if I should try the nomodeset.  I was reading about how to do it in another thread. Is that still viable option?

---

### Post by jmfal on 2012-07-02
Reboot to the recovery kernal>>>low graphics>>log in>>open a terminal and open the blacklist file

```
   sudo gedit /etc/modprobe.d/blacklist.conf    
```

Put your cursor after the last word of the last line of the file and press enter two times.

You can leave a comment if you want, be sure to put a # in front of it.
enter this to the list
blacklist       nouveau
blacklist       nvidiafb

save and close the file close out all running app and restart.

---

### Post by zirgut on 2012-07-02
Hi again,
Tried all that and remains the same.
Will check in tomorrow
zirgut

---

### Post by zirgut on 2012-07-03
Just by the way I did give the "nomodeset" a try by editing in the boot menu, placing before the "splash quiet" string and rebooting. Again it made no difference. hum hum!

---

### Post by jmfal on 2012-07-03
I know you don't want to here it, but maybe reinstalling 12.04 and start over.

---

### Post by zirgut on 2012-07-03
Ok. If that is the best way. Just exactly what is the best way to do that and save the files and reload them. Never quite sure about that.

---

### Post by jmfal on 2012-07-03
I'm not going to tell you what to do, but that's what I would do.

It's going to be hard to get help for a graphic/video problem when the title of your thread is about sound, I saw your other thread, you can continue with that one, maybe someone  will chip in with some advice.  

I'll try to help all that I can but my knowledge of  graphics problems is minimal.

If you want to reinstall,  backup your important files--pictures,music, documents to external hdd or DVD  and redo it .

---

### Post by zirgut on 2012-07-03
Much thanks for your help and time you have put in
Regards
zirgut

---

