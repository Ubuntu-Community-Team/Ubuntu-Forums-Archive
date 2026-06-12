---
title: "new HOWTO: MythTV with Ubuntu 5.10 (Breezy), with Hauppauge PVR-150"
date: 2005-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by dhyams on 2005-12-21
[B]
UPDATE: MythTV 0.19 now included!  See section 9.8.[/B]

First, credit where credit is due: I first set up MythTV under Fedora Core 3, using the excellent HOWTO by Jarod Wilson. For reasons better left unexplained, I decided to try out MythTV on Ubuntu. For this, I leaned heavily on two HOWTOS: one written by Andrew Barbaccia and one by Joe Kallo. While each are very useful, I did run into a couple of issues that I wanted to pass along, and therefore, this HOWTO was born. In this HOWTO, I also give you links to various files along the way, so that you can see exactly how it is set up on my system.

For PVR-250, PVR-350, and PVR-500 users: there is nothing in this HOWTO that is necessarily PVR-150 specific! As such, you should be able to use this HOWTO without much problem, *unless* there is something special that needs to be done for your particular card. As the folks working on the ivtv driver have done a very good job with the driver and making it card-agnostic, I doubt that this will be the case. But, as I don't have any of these cards and can't test them, I just don't know. PVR-500 users should be able to follow this guide with good results, since a PVR-500 is just two PVR-150's on a card. The only thing to be concerned about there would be to set up both tuners in the initial MythTV setup.


This HOWTO tries to address the entire MythTV experience, from the installation to the tuning of MythTV.  Many tips are given for places where there might be difficulty, and special attention is given to upgraders from old distros of MythTV.

Anyway, here is the URL:

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Enjoy!

---

### Post by reefland on 2005-12-25
I'm trying to use your HOWTO with Kubuntu 5.1 and a PVR-500 unit.  All of your instructions have worked in my setup upto step 5.3 "Verification of IVTV drivers".  The only minor exception is in Step 2.

"gedit /etc/apt/sources.list"

I used:

"kwrite /etc/apt/sources.list"  since I'm using KDE.

I'm only able to get static on both /dev/video0 and /dev/video1 using your testing instructions provided.   The wall jack and cable is fine (my TV uses them).

I tried your instructions on setting channels as well, no difference.  Any suggestions on how to proceed troubleshooting this?

Thanks for the HOWTO, it has gotten me a lot further then I would have gotten on my own.

Two suggestions, add a revision number to the document.  I've noticed it changing over the past few days.  A revision number will make it easier to know when to print it out again.  Secondly, it might be helpful to add a comment about the zap2it.com subscription to ignore the subscription expires messages since the service is free, just means you have to fill out a survey again.

---

### Post by dhyams on 2005-12-25
> 
I'm only able to get static on both /dev/video0 and /dev/video1 using your testing instructions provided.   The wall jack and cable is fine (my TV uses them).

I tried your instructions on setting channels as well, no difference.  Any suggestions on how to proceed troubleshooting this?


Hmm.  When you say "static", I assume that you are talking about what I would call "snow". Maybe the correct input is not being selected?  Do a 
"ivtvctl -n" in order to list the possible video inputs.  Use "ivtvctl -l #" in order to set the video input to one of the numbers.  Do this while you have an mplayer running, using /dev/video0 as the input to mplayer.

You might also want to post the output between the START INIT IVTV and END INIT IVTV lines after typing "dmesg".  I've seen it and didnt' see anything wrong, but perhaps someone else will.  Also post the output of ivtvctl -a.


> 
Thanks for the HOWTO, it has gotten me a lot further then I would have gotten on my own.


:D 

> 
Two suggestions, add a revision number to the document.  I've noticed it changing over the past few days.  A revision number will make it easier to know when to print it out again.  


Yes, I know; I've been working on it, adding new sections.  I'll add a rev number; good suggestion!

> 
Secondly, it might be helpful to add a comment about the zap2it.com subscription to ignore the subscription expires messages since the service is free, just means you have to fill out a survey again.

Done.

---

### Post by dhyams on 2005-12-25
> Use "ivtvctl -l #"  

Oops!  That should be "ivtvctl -p #"!

---

### Post by reefland on 2005-12-26
[QUOTE=dhyams]Hmm.  When you say "static", I assume that you are talking about what I would call "snow". 
[/QUOTE]

Well snow to me is white (looking outside).   I'm not seeing white, I see dark random lines, with color speckles all over.  No sign of any pictures.

[QUOTE=dhyams]Maybe the correct input is not being selected?  Do a 
"ivtvctl -n" in order to list the possible video inputs.
[/QUOTE]

This is the output:

ioctl: VIDIOC_ENUMINPUT
        Input   : 0
        Name    : Tuner
        Type    : 0x00000001
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x0000000000003000 ( NTSC )
        Status  : 0

        Input   : 1
        Name    : Composite 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 2
        Name    : Composite 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 3
        Name    : S-Video 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 4
        Name    : S-Video 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0


[QUOTE=dhyams] Use "ivtvctl -l #" in order to set the video input to one of the numbers.  Do this while you have an mplayer running, using /dev/video0 as the input to mplayer.[/QUOTE]

I tried 0-4, 0 produced the most "snow".  The others stayed fairly black.  If I disconnect the cable to the tuner I see no difference in the "snow" pattern.

[QUOTE=dhyams]You might also want to post the output between the START INIT IVTV and END INIT IVTV lines after typing "dmesg".  I've seen it and didnt' see anything wrong, but perhaps someone else will.
[/QUOTE]

[4294686.666000] ivtv:  ==================== START INIT IVTV ====================
[4294686.666000] ivtv:  version 0.4.1 (tagged release) loading
[4294686.666000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4294686.666000] ivtv:  In case of problems please include the debug info between
[4294686.666000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294686.666000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294686.666000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294686.666000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294686.744000] tveeprom: Second (radio) tuner idx 101
[4294686.744000] tveeprom: ivtv version
[4294686.744000] tveeprom: Hauppauge: model = 23552, rev = D487, serial# = 8757842
[4294686.744000] tveeprom: tuner = Samsung TCPN 2121P30A (idx = 87, type = 4)
[4294686.744000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294686.744000] tveeprom: audio processor = CX25843 (type = 25)
[4294686.744000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294686.744000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294686.744000] ivtv0: This is the first unit of a PVR500
[4294686.748000] tuner (ivtv): chip found at addr 0xc0 i2c-bus ivtv i2c driver #0
[4294686.750000] TEA5767 detected.
[4294686.750000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=60]
[4294686.751000] tuner: type set to 62 (Philips TEA5767HN FM Radio) by autodetect
[4294686.751000] type set to 62 (Philips TEA5767HN FM Radio)
[4294686.751000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294686.751000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294686.804000] cx25840 0-0044: ivtv driver
[4294686.804000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294688.688000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294688.777000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294688.850000] wm8775 0-001b: ivtv driver
[4294688.850000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294688.862000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294688.871000] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[4294689.538000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294689.748000] ivtv0: Encoder revision: 0x02050032
[4294689.748000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294689.749000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294689.750000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294689.751000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294689.752000] ivtv0: Create encoder radio stream
[4294689.752000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[4294689.995000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[4294689.995000] ivtv:  ======================  NEXT CARD  ======================
[4294689.995000] ivtv1: Autodetected WinTV PVR 150 card (cx23416 based)
[4294689.995000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294690.067000] tveeprom: Second (radio) tuner idx 101
[4294690.067000] tveeprom: ivtv version
[4294690.067000] tveeprom: Hauppauge: model = 23552, rev = D487, serial# = 8757842
[4294690.067000] tveeprom: tuner = Samsung TCPN 2121P30A (idx = 87, type = 4)
[4294690.067000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294690.067000] tveeprom: audio processor = CX25843 (type = 25)
[4294690.067000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294690.067000] ivtv1: i2c attach to card #1 ok [client=tveeprom, addr=50]
[4294690.069000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #1
[4294690.069000] ivtv1: i2c attach to card #1 ok [client=(tuner unset), addr=61]
[4294690.095000] cx25840 1-0044: ivtv driver
[4294690.095000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[4294691.796000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294691.885000] ivtv1: i2c attach to card #1 ok [client=cx25840, addr=44]
[4294691.894000] wm8775 1-001b: ivtv driver
[4294691.894000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[4294691.906000] ivtv1: i2c attach to card #1 ok [client=wm8775, addr=1b]
[4294691.949000] ivtv1: This is the second unit of a PVR500
[4294691.949000] ivtv1: Correcting tveeprom data: no radio present on second unit
[4294692.641000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294692.851000] ivtv1: Encoder revision: 0x02050032
[4294692.853000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294692.905000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294692.906000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294692.906000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294692.907000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #1
[4294693.156000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[4294693.156000] ivtv:  ====================  END INIT IVTV  ====================


[QUOTE=dhyams]Also post the output of ivtvctl -a.[/QUOTE]

ioctl IVTV_IOC_G_CODEC ok
Codec parameters
aspect      : 2
audio       : 0x00e9
bframes     : 3
bitrate_mode: 0
bitrate     : 8000000
bitrate_peak: 9600000
dnr_mode    : 0
dnr_spatial : 0
dnr_temporal: 8
dnr_type    : 0
framerate   : 0
framespergop: 15
gop_closure : 1
pulldown    : 0
stream_type : 14
ioctl VIDIOC_G_FMT ok
        Type   : Video Capture
        Width  : 720
        Height : 480
ioctl VIDIOC_QUERYCAP ok
        Driver name   : ivtv
        Card type     : WinTV PVR 500 (unit #1)
        Bus info      : 0000:06:08.0
        Driver version: 1025
        Capabilities  : 0x01070011
ioctl: VIDIOC_ENUMINPUT
        Input   : 0
        Name    : Tuner
        Type    : 0x00000001
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x0000000000003000 ( NTSC )
        Status  : 0

        Input   : 1
        Name    : Composite 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 2
        Name    : Composite 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 3
        Name    : S-Video 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 4
        Name    : S-Video 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0
ioctl VIDIOC_G_INPUT ok
Video input = 0
ioctl: VIDIOC_ENUMOUTPUT
ioctl VIDIOC_G_OUTPUT failed: Invalid argument
ioctl: VIDIOC_ENUMAUDIO
        Input   : 0
        Name    : Tuner Audio In

        Input   : 1
        Name    : Audio Line 1

        Input   : 2
        Name    : Audio Line 2

        Input   : 3
        Name    : Audio Line 3

        Input   : 4
        Name    : Audio Line 4
ioctl VIDIOC_G_AUDIO ok
Audio input = 0: Tuner Audio In
ioctl VIDIOC_G_FREQUENCY ok
Frequency = 8180
ioctl: VIDIOC_ENUMSTD
        index       : 0
        ID          : 0x0000000000003000
        Name        : NTSC
        Frame period: 1001/30000
        Frame lines : 525

        index       : 1
        ID          : 0x00000000000000FF
        Name        : PAL
        Frame period: 1/25
        Frame lines : 625

        index       : 2
        ID          : 0x00000000007F0000
        Name        : SECAM
        Frame period: 1/25
        Frame lines : 625
ioctl VIDIOC_G_STD ok
Video standard = 0x00003000
ioctl: VIDIOC_QUERYCTRL
Brightness = 383
Contrast = 63
Saturation = 63
Hue = 0
Volume = 60928
Mute = 1

Thanks,

-Rich

---

### Post by dhyams on 2005-12-27
I see in your IVTV dmesg that the tuner type is set to 4: NoTuner.

Take a look at the following recent (Dec 20) thread:

[http://www.gossamer-threads.com/lists/ivtv/devel/26129](http://www.gossamer-threads.com/lists/ivtv/devel/26129)

It looks like the poster has some success with tuner type 57. I hate to be the bearer of bad news, but your PVR-500 has the same Samsung tuner, which is not fully supported by the ivtv drivers.

---

### Post by Stormbringer on 2005-12-27
**EDIT: PROBLEM SOLVED**

Problem that showed up:
Error at modprobing ivtv --- "unable to open firmware v4l-cx2341x-dec.fw"

```

Linux video capture interface: v1.00
ivtv:  ==================== START INIT IVTV ====================
ivtv:  version 0.4.1 (tagged release) loading
ivtv:  Linux version: 2.6.12-10-386 386 gcc-3.4
ivtv:  In case of problems please include the debug info between
ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
ivtv:  any module options, when mailing the ivtv-users mailinglist.
ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
tveeprom: ivtv version
tveeprom: Hauppauge: model = 48134, rev = J321, serial# = 2763850
tveeprom: tuner = Philips FM1216 (idx = 21, type = 5)
tveeprom: tuner fmt = PAL(B/G) (eeprom = 0x04, v4l2 = 0x00000007)
tveeprom: audio processor = MSP4418 (type = 19)
tveeprom: decoder processor = SAA7115 (type = 13)
ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
saa7115 1-0021: ivtv driver
saa7115 1-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
saa7127 1-0044: ivtv driver
saa7127 1-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
msp3400 1-0040: ivtv driver
msp3400 1-0040: chip=MSP4418G-A2 +nicam +simple +simpler +radio mode=simpler
ivtv0: i2c attach to card #0 ok [client=MSP4418G-A2, addr=40]
 msp3400 1-0040: msp34xxg daemon started
ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
ivtv0: unable to open firmware v4l-cx2341x-dec.fw
ivtv0: did you put the firmware in the hotplug firmware directory?
ivtv0 warning: failed loading decoder firmware
ivtv0 warning: Error loading firmware -1!
ivtv0: Error -1 initializing firmware.
ivtv0: Error -12 on initialization
ivtv: probe of 0000:00:05.0 failed with error -12
ivtv:  ====================  END INIT IVTV  ====================

```

**SOLUTION**

At the point of the HOWTO where you copy the files into the firmware directory an additional step seems to be required ...

[I]The Hauppauge cards require firmware files, as the firmware is not stored in the ROMs on the card.  We must download and install these properly now.  To do this,

cd utils
wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/
mv /lib/modules/ivtv-fw-enc.bin /usr/lib/hotplug/firmware/
cp ../v4l-cx2341x-init-mpeg.bin /usr/lib/hotplug/firmware
**ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw**[/I]

Then proceed onwards.

---

### Post by tritium on 2005-12-28
I've been working my way through the linked tutorial and hit a snagging point right out of the gate.  My sources.list file looks identical to the one provided in the tut, and I'm running as root (sudo -i).

I've isolated the problem to the following line:

> apt-get install build-essential dialog apache2 mysql-server phpmyadmin gcc-3.4 

Which, I can modify to the following to make it work:

> apt-get install build-essential apache2 mysql-server phpmyadmin gcc-3.4 

You see, it has something to do with the "dialog" part, and I'm in the dark as to why.  Here's the error that displays when I run just "apt-get install dialog" (and the original full line):

> 
root@isengard:~# apt-get install dialog
Reading package lists... Done
Building dependency tree... Done
Package dialog is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dialog has no installation candidate

Any ideas?  TIA
-tritium

Edit: Nevermind, I'm a big dummy.  I neglected to remove one pound sign comment in sources.list.  What a doofus...

---

### Post by xeta on 2005-12-28
Great writeup! Followed it to the tee and have gotten further with your writeup than I have with any other. I'm still having some problems with IVTV however. Im using a pvr350.

Here is my dmesg:

```

[4302980.836000] ivtv:  ==================== START INIT IVTV ====================
[4302980.836000] ivtv:  version 0.4.1 (tagged release) loading
[4302980.836000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4302980.836000] ivtv:  In case of problems please include the debug info between
[4302980.836000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4302980.836000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4302980.848000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4302980.849000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4302980.849000] PCI: setting IRQ 10 as level-triggered
[4302980.849000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4302980.941000] tveeprom: ivtv version
[4302980.941000] tveeprom: Hauppauge: model = 48132, rev = K168, serial# = 2947170
[4302980.941000] tveeprom: tuner = LG TAPE H001F MK3 (idx = 68, type = 47)
[4302980.941000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4302980.941000] tveeprom: audio processor = MSP4448 (type = 1b)
[4302980.941000] tveeprom: decoder processor = SAA7115 (type = 13)
[4302980.941000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4302981.048000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4302981.048000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4302981.145000] saa7115 0-0021: ivtv driver
[4302981.145000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4302981.327000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4302981.601000] saa7127 0-0044: ivtv driver
[4302981.604000] saa7127 0-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[4302981.604000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4302981.773000] msp3400 0-0040: ivtv driver
[4302981.773000] msp3400 0-0040: chip=MSP4448G-A2 +nicam +simple +simpler +radio mode=simpler
[4302981.780000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-A2, addr=40]
[4302981.780000] msp3400 0-0040: msp34xxg daemon started
[4302981.945000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4302981.945000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4302982.957000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4302982.957000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4302982.957000] ivtv0 warning: failed loading encoder firmware
[4302982.957000] ivtv0 warning: Error loading firmware -3!
[4302982.957000] ivtv0: Error -3 initializing firmware.
[4302983.073000] ivtv0: Error -12 on initialization
[4302983.073000] ivtv: probe of 0000:01:08.0 failed with error -12
[4302983.073000] ivtv:  ====================  END INIT IVTV  ====================

```

---

### Post by dhyams on 2005-12-28
[QUOTE=Stormbringer]**EDIT: PROBLEM SOLVED**


**ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw**[/I]

Then proceed onwards.[/QUOTE]

Thanks, Stormbringer, for pointing this out!  I have added it to the HOWTO, so that PVR-350 folks won't run into this snag.

Please let us all know how the Myth project goes!

---

### Post by dhyams on 2005-12-28
[QUOTE=xeta]Great writeup! Followed it to the tee and have gotten further with your writeup than I have with any other. I'm still having some problems with IVTV however. Im using a pvr350.
```

[4302982.957000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4302982.957000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4302982.957000] ivtv0 warning: failed loading encoder firmware
[4302982.957000] ivtv0 warning: Error loading firmware -3!
[4302982.957000] ivtv0: Error -3 initializing firmware.
[4302983.073000] ivtv0: Error -12 on initialization
[4302983.073000] ivtv: probe of 0000:01:08.0 failed with error -12
[4302983.073000] ivtv:  ====================  END INIT IVTV  ====================

```[/QUOTE]

Thanks for the compliment, and I hope that your MythTV works out for you!  I enjoy the heck out of mine.

If you do:

ls -ltra /usr/lib/hotplug/firmware 

Do you see a file in there named v4l-cx2341x-enc.fw, and does it have sufficient read permission?  If not, go back over the step in section 5.2 of the HOWTO, where the firmware gets downloaded and copied to the correct place.  If you do see the file and it has sufficient permissions, I am not sure why ivtv is refusing to load it.  Be sure to check the spelling of the file, as a mistyping when copying the firmware file would cause a problem like this.

As a shot in the dark, you might try doing (assuming that you followed my firmware install directions exactly)

cd /usr/lib/hotplug/firmware
mv v4l-cx2341x-enc.fw v4l-cx2341x-enc.fw.orig
cp ivtv-fw-enc.bin v4l-cx2341x-enc.fw

and see if that makes a difference.  According to [http://ivtvdriver.org/index.php/Firmware](http://ivtvdriver.org/index.php/Firmware), the two firmware files are the same but one has zero padding, which should be ignored by ivtv.  But, in a pinch, I would at least try this.  Let us know how it goes!

---

### Post by neolev on 2005-12-29
Hey i love your guide btw thanks much,

I am having a problem getting the drivers and firmware to be recognized by ivtv

when i depmod and modprobe ivtv

and dmesg it returns....

[4296003.208000] ivtv:  ==================== START INIT IVTV ====================
[4296003.208000] ivtv:  version 0.4.1 (tagged release) loading
[4296003.208000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4296003.208000] ivtv:  In case of problems please include the debug info between
[4296003.208000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4296003.208000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4296003.210000] ivtv:  ====================  END INIT IVTV  ====================

any ideas on this??


Neolev

---

### Post by xeta on 2005-12-29
No go, this is what I got.

```

[4358761.113000] ivtv:  ==================== START INIT IVTV ====================
[4358761.113000] ivtv:  version 0.4.1 (tagged release) loading
[4358761.113000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4358761.113000] ivtv:  In case of problems please include the debug info between
[4358761.113000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4358761.113000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4358761.115000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4358761.117000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4358761.117000] PCI: setting IRQ 10 as level-triggered
[4358761.117000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4358761.345000] tveeprom: ivtv version
[4358761.345000] tveeprom: Hauppauge: model = 48132, rev = K168, serial# = 2947170
[4358761.345000] tveeprom: tuner = LG TAPE H001F MK3 (idx = 68, type = 47)
[4358761.345000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4358761.345000] tveeprom: audio processor = MSP4448 (type = 1b)
[4358761.345000] tveeprom: decoder processor = SAA7115 (type = 13)
[4358761.346000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4358761.395000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4358761.395000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4358761.465000] saa7115 0-0021: ivtv driver
[4358761.465000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4358761.811000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4358761.922000] saa7127 0-0044: ivtv driver
[4358761.926000] saa7127 0-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[4358761.926000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4358762.011000] msp3400 0-0040: ivtv driver
[4358762.011000] msp3400 0-0040: chip=MSP4448G-A2 +nicam +simple +simpler +radio mode=simpler
[4358762.019000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-A2, addr=40]
[4358762.019000] msp3400 0-0040: msp34xxg daemon started
[4358762.062000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4358762.062000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4358762.991000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4358762.991000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4358762.991000] ivtv0 warning: failed loading encoder firmware
[4358762.991000] ivtv0 warning: Error loading firmware -3!
[4358762.991000] ivtv0: Error -3 initializing firmware.
[4358763.031000] ivtv0: Error -12 on initialization
[4358763.031000] ivtv: probe of 0000:01:08.0 failed with error -12
[4358763.031000] ivtv:  ====================  END INIT IVTV  ====================

```

---

### Post by tritium on 2005-12-29
Well, I ran through your walk-through last night and managed to get mythTV functioning to a degree.  Watching live television worked fine, but whenever I attempted to make a recording, the resulting NUV files were empty (0 bytes).  Well, I assumed that I did something wrong, and started over this morning on a fresh reinstall of ubuntu.  

Now, I can't get the program database to fill out... I can run mythfilldatabase until I'm absolutely purple in the face, and get absolutely nothing in the program guide in the frontend or mythweb.  I even went in and gave the mythTV mySQL user full admin priv's across the entire server (initially thinking this was related to access permissions...).  Giving mythtv total access permissions got me nowhere, so I adjusted the mysql.txt file to connect as the root.... STILL nothing.  I just don't understand it!

Last night, I was able to fill the database, and then today ... nada.  I'm not getting ANY error messages when I execute mythfilldatabase (that I can see), and the mythtv-setup program seems to understand my zip2it.com account info (it pulls down my lineup info no problem).

Why is this happening?  I'm absolutely at the end of my nerve...

Where can I look for the problem?  Is there a rate limit at which the XML TV data can be pulled?  A maximum number of times per day?

Thanks in advance.
-tritium

Edit: I should note that under *both* attempts, I am able to watch TV.

---

### Post by reefland on 2005-12-29
[QUOTE=Stormbringer]**EDIT: PROBLEM SOLVED**

***ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw***

Then proceed onwards.[/QUOTE]

I tried this as suggested, and I still get snow.  Here is an updated dmesg:

```

[4294684.408000] ivtv:  ==================== START INIT IVTV ====================
[4294684.408000] ivtv:  version 0.4.1 (tagged release) loading
[4294684.408000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4294684.408000] ivtv:  In case of problems please include the debug info between
[4294684.408000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294684.408000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294684.411000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294684.411000] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294684.502000] tveeprom: Second (radio) tuner idx 101
[4294684.502000] tveeprom: ivtv version
[4294684.502000] tveeprom: Hauppauge: model = 23552, rev = D487, serial# = 8757842
[4294684.502000] tveeprom: tuner = Samsung TCPN 2121P30A (idx = 87, type = 4)
[4294684.502000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294684.502000] tveeprom: audio processor = CX25843 (type = 25)
[4294684.502000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294684.502000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294684.503000] ivtv0: This is the first unit of a PVR500
[4294684.506000] tuner (ivtv): chip found at addr 0xc0 i2c-bus ivtv i2c driver #0
[4294684.509000] TEA5767 detected.
[4294684.509000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=60]
[4294684.509000] tuner: type set to 62 (Philips TEA5767HN FM Radio) by autodetect
[4294684.509000] type set to 62 (Philips TEA5767HN FM Radio)
[4294684.510000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294684.510000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294684.539000] cx25840 0-0044: ivtv driver
[4294684.539000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294686.392000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294686.480000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294686.506000] wm8775 0-001b: ivtv driver
[4294686.506000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294686.518000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294686.527000] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[4294687.187000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294687.397000] ivtv0: Encoder revision: 0x02050032
[4294687.397000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294687.398000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294687.399000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294687.400000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294687.401000] ivtv0: Create encoder radio stream
[4294687.401000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[4294687.644000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[4294687.644000] ivtv:  ======================  NEXT CARD  ======================
[4294687.644000] ivtv1: Autodetected WinTV PVR 150 card (cx23416 based)
[4294687.644000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294687.716000] tveeprom: Second (radio) tuner idx 101
[4294687.716000] tveeprom: ivtv version
[4294687.716000] tveeprom: Hauppauge: model = 23552, rev = D487, serial# = 8757842
[4294687.716000] tveeprom: tuner = Samsung TCPN 2121P30A (idx = 87, type = 4)
[4294687.716000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294687.716000] tveeprom: audio processor = CX25843 (type = 25)
[4294687.716000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294687.716000] ivtv1: i2c attach to card #1 ok [client=tveeprom, addr=50]
[4294687.718000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #1
[4294687.718000] ivtv1: i2c attach to card #1 ok [client=(tuner unset), addr=61]
[4294687.744000] cx25840 1-0044: ivtv driver
[4294687.744000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[4294689.445000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294689.534000] ivtv1: i2c attach to card #1 ok [client=cx25840, addr=44]
[4294689.546000] wm8775 1-001b: ivtv driver
[4294689.546000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[4294689.558000] ivtv1: i2c attach to card #1 ok [client=wm8775, addr=1b]
[4294689.608000] ivtv1: This is the second unit of a PVR500
[4294689.608000] ivtv1: Correcting tveeprom data: no radio present on second unit
[4294690.298000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294690.508000] ivtv1: Encoder revision: 0x02050032
[4294690.508000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294690.509000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294690.510000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294690.511000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294690.511000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #1
[4294690.754000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[4294690.754000] ivtv:  ====================  END INIT IVTV  ====================

```

dunno if this is helpful:

```

sh-3.00$ ls -ltra /usr/lib/hotplug/firmware
total 1076
drwxr-xr-x  3 root root   4096 2005-12-22 22:36 ..
-rw-r--r--  1 root root 262144 2005-12-23 22:46 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2005-12-23 22:46 ivtv-fw-dec.bin
-rw-r--r--  1 root root 155648 2005-12-24 22:23 v4l-cx2341x-init-mpeg.bin
-r--r--r--  1 root root  14264 2005-12-26 15:27 v4l-cx25840.fw
-r--r--r--  1 root root 376836 2005-12-26 15:28 v4l-cx2341x-enc.fw
lrwxrwxrwx  1 root root     42 2005-12-29 12:53 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin/
drwxr-xr-x  2 root root   4096 2005-12-29 12:53 .

```

---

### Post by tritium on 2005-12-29
Ok. I managed to get the channel listings in there by re-running the mythtv-setup and choosing to erase my channel listings, then re-running mythfilldatabase.  30-minutes later, I have a full program guide!  Yay!

Now, somewhere during the process, the input connectivity for Tuner unbound from PVR-150-1, and I can no longer see live TV.   I was able to rebind the Tuner, but it still will not show live TV.

Here's the result of using > 2005-12-29 20:13:20.192 MainServer::HandleAnnounce Playback
2005-12-29 20:13:20.194 adding: isengard as a client (events: 0)
2005-12-29 20:13:20.256 Using protocol version 15
2005-12-29 20:13:20.262 MainServer::HandleAnnounce Playback
2005-12-29 20:13:20.263 adding: isengard as a client (events: 1)
2005-12-29 20:13:20.271 MainServer::HandleAnnounce Playback
2005-12-29 20:13:20.272 adding: isengard as a client (events: 0)
2005-12-29 20:13:20.316 MainServer::HandleAnnounce Playback
2005-12-29 20:13:20.318 adding: isengard as a client (events: 0)
2005-12-29 20:13:20.339 adding: isengard as a remote ringbuffer
2005-12-29 20:13:20.370 Changing from None to WatchingLiveTV
2005-12-29 20:13:25.603 taking too long to be allowed to read..
2005-12-29 20:13:30.604 taking too long to be allowed to read..
2005-12-29 20:13:35.605 taking too long to be allowed to read..
2005-12-29 20:13:35.605 Took more than 10 seconds to be allowed to read, aborting.
Couldn't read file: rbuf://192.168.0.49:6543/var/cache/mythtv//ringbuf1.nuv
2005-12-29 20:13:35.609 Couldn't read data from the capture card in 15 seconds. Stopping.
2005-12-29 20:13:35.677 Changing from None to WatchingLiveTV
2005-12-29 20:13:35.678 Decoder not alive, and trying to play..
2005-12-29 20:13:35.747 Changing from WatchingLiveTV to None
2005-12-29 20:13:55.679 ReadStringList timeout (quick).
Remote encoder not responding.
2005-12-29 20:13:55.685 Changing from None to None
2005-12-29 20:14:05.816 ReadStringList timeout (quick).
2005-12-29 20:14:05.817 RemoteFile::Read(): No response from control socket.
2005-12-29 20:14:05.818 RemoteFile::Read() failed in RingBuffer::safe_read().
2005-12-29 20:14:05.820 WriteStringList: Bad socket
2005-12-29 20:14:05.822 ReadStringList: Bad socket
2005-12-29 20:14:05.823 Remote file timeout.



Reefland, it looks like IV thinks you have two cards.  Is that the case?  Perhaps the snow is coming from the "other" card that isn't plugged up on coax?

---

### Post by reefland on 2005-12-29
[QUOTE=tritium]Reefland, it looks like IV thinks you have two cards.  Is that the case?  Perhaps the snow is coming from the "other" card that isn't plugged up on coax?[/QUOTE]

The PVR-500 I'm using is basically two PVR-150's on the same card.  However, there is only one coax hookup that both tuners use.

Since I've been at this for over a week now, I made a disk image backup and tried XP media center 2005.  Had it up in running in 2 hours including wireless network and ATI Remote Wonder RF remote control.  I know all my hardware and connections are working.    I'd still rather get this working on Linux thou.

---

### Post by neolev on 2005-12-30
[QUOTE=neolev]Hey i love your guide btw thanks much,

I am having a problem getting the drivers and firmware to be recognized by ivtv

when i depmod and modprobe ivtv

and dmesg it returns....

[4296003.208000] ivtv:  ==================== START INIT IVTV ====================
[4296003.208000] ivtv:  version 0.4.1 (tagged release) loading
[4296003.208000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4296003.208000] ivtv:  In case of problems please include the debug info between
[4296003.208000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4296003.208000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4296003.210000] ivtv:  ====================  END INIT IVTV  ====================

any ideas on this??


Neolev[/QUOTE]


Alright problem solved....it was not detecting the hardware but now it works....

I am having another issue pertaining to the PVR500 with the dual tuners....basically myth is only recognizing one of the tuners....yet ivtv sees both of them correctly....as two 150s....maybe i am just a newb with trying to setup myth....but i seem to be having issues with it....also the video is not centered to the tv when i view it via svideo on a 27" tv....


Any help with any of these issues would be appreciated...


neolev

---

### Post by reefland on 2005-12-30
[QUOTE=neolev]Alright problem solved....it was not detecting the hardware but now it works....

I am having another issue pertaining to the PVR500 with the dual tuners....basically myth is only recognizing one of the tuners....yet ivtv sees both of them correctly....as two 150s....[/QUOTE]

Can you post your dmesg, I'd like to see how it differs from my PVR-500.

Thanks,

-Rich

---

### Post by Bladerunner on 2005-12-30
Thanks for this HowTo. I was up and running with my PVR-250 on my first run through. First time I've ever successfully setup Mythtv. Now to get my Airstar  HD 5000 working and I'll be all set.

---

### Post by nolodude on 2005-12-30
BTW, [Andrew Barbaccia's Ubuntu Mythtv site]("http://www.abarbaccia.com/") was also very helpful when I was setting up my own Mythtv system.

---

### Post by Stormbringer on 2005-12-30
[QUOTE=dhyams]Thanks, Stormbringer, for pointing this out!  I have added it to the HOWTO, so that PVR-350 folks won't run into this snag.

Please let us all know how the Myth project goes![/QUOTE]

Hello dhyams - sorry for the late reply, I've been a little busy lately and hadn't any time to check the thread.

Although it's just a small contribution to your, really great, HOWTO it seems as it's a crucial culprit. Glad I could help out.

As for MythTV --- by following your HOWTO I succeeded to get it installed and working. A few small problems emerged, but I've been able to solve them.

Next waypoint will be to get the IR to work ...

---

### Post by dhyams on 2005-12-30
[QUOTE=reefland]

Since I've been at this for over a week now, I made a disk image backup and tried XP media center 2005.  Had it up in running in 2 hours including wireless network and ATI Remote Wonder RF remote control.  I know all my hardware and connections are working.    I'd still rather get this working on Linux thou.[/QUOTE]

Did you see my post a few back?  According to your dmesg, you have a new Samsung tuner that the ivtv drivers just don't support yet.  It doesn't appear that implementing support will be difficult, but they do need Samsung to send them a datasheet, and they haven't yet.  

Refer to these two threads for more info.  One person reported partial success by manually setting the tuner type to 57 (i.e., 
modprobe ivtv tuner=57,57

[http://www.gossamer-threads.com/lists/ivtv/devel/26129](http://www.gossamer-threads.com/lists/ivtv/devel/26129)
[http://www.gossamer-threads.com/lists/ivtv/devel/26195](http://www.gossamer-threads.com/lists/ivtv/devel/26195)

If nothing else, you can try this and see if you can receive the first few channels.  If so, then I'm afraid you will have to wait for support to be added in the ivtv driver for your tuner.  If not, then there still must be something else wrong that we can sort out.

---

### Post by ATAQ on 2005-12-30
does anyone here know anything bout the philips SAA 7000 chipset, I know that the drivers are in 2.6 kernels but when I try to use the card it says no tuner available for card!! 
Any ideas?

---

### Post by dhyams on 2005-12-30
> 

I am having another issue pertaining to the PVR500 with the dual tuners....basically myth is only recognizing one of the tuners....yet ivtv sees both of them correctly....as two 150s....maybe i am just a newb with trying to setup myth....but i seem to be having issues with it....also the video is not centered to the tv when i view it via svideo on a 27" tv....


Any help with any of these issues would be appreciated...


neolev

As far as the single tuner is concerned, it sounds like you need to go back to the mythtv-setup stage, and make sure that you set up both "cards", and set up two video sources as well.  I'm guessing that perhaps this didn't get done?

---

### Post by nianhbg on 2005-12-31
Not an installation question but is it possible to run Mythtv with my regular user account instead of running with mythtv user?

---

### Post by neolev on 2006-01-02
[QUOTE=reefland]Can you post your dmesg, I'd like to see how it differs from my PVR-500.

Thanks,

-Rich[/QUOTE]

Hey Rich,

I'll post my dmesg for the pvr500 later this week once i get back to the pvr....

Neolev

---

### Post by neolev on 2006-01-02
[QUOTE=dhyams]As far as the single tuner is concerned, it sounds like you need to go back to the mythtv-setup stage, and make sure that you set up both "cards", and set up two video sources as well.  I'm guessing that perhaps this didn't get done?[/QUOTE]

It ended up being a mythtv conflict somewhere....i removed myth and reinstalled....both tuners were setup but it wouldnt change channels....i believe it was a backend issue that had to deal with ivtv....both are working fine now and myth is functioning.

i am still having issues with the live tv being offset....or not centered through the TV....i am still alittle puzzled as to what is causing this.....

neolev

---

### Post by t0bb3 on 2006-01-03
I'm following your guide right now and have just spent very many hours trying to install ivtv.

What I had to do was to edit the file ivtv-firmware.c in /usr/src/ivtv-0.4.1/driver/
I had to change memcpy to memcpy_toio on lines 112 and 115 (it's in the load_fw_direct function)

After that I could continue with your howto.

I had to do this since I have the 64-bit version of ubuntu. When using memcpy the compiler tried to use 64-bit memory copies, but the PCI bus that the PVR-150 is connected to can not handle this. memcpy_toio on the other hand is made for this kind of copying, and works well in this case.

This is where I found all this information: [http://www.ivtvdriver.org/pipermail/ivtv-users/2006-January/000834.html](http://www.ivtvdriver.org/pipermail/ivtv-users/2006-January/000834.html) and all the replys

Thanks for a great HowTo!

---

### Post by t0bb3 on 2006-01-03
So I got to the actual MythTV part where the HowTo said to install mythtv and a bunch of plugins. apt-get refused, so I tried to only install mythtv and no plugins by running "sudo apt-get install mythtv" but not even that worked. I got these error messages:
> The following packages have unmet dependencies:
  mythtv: Depends: mythtv-frontend (= 0.18.1-5) but it is not going to be installed
          Depends: mythtv-backend (= 0.18.1-5) but it is not going to be installed

What should I do?

EDIT: 
Apperently this also has to do with my 64-bit version of Ubuntu.
According to this page: [http://packages.ubuntu.com/breezy/graphics/mythtv-frontend](http://packages.ubuntu.com/breezy/graphics/mythtv-frontend) only version 0.17-3 is available to amd64 users :(

---

### Post by schucki.be on 2006-01-03
I am sad :( 
Tried to instal MythTv according the HowTo but did not succeed..
It went all fine until the install of mythtv.
(Note that i did not instal mplayer).

If i do the install:
apt-get install mythtv mythbrowser mythdvd mythgallery mythmusic mythnews mythvideo mythweather 

==>> PROBLEM SOLVED : Something with te repos. Will find out and write sollution here later <<==


I'll get :
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythbrowser: Depends: mythtv-frontend (>= 0.18.1-1) but it is not going to be installed
               Depends: kdelibs4c2a (>= 4:3.4.3-1) but it is not installable
               Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
               Depends: libmyth-0.18.1 but it is not going to be installed
               Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
               Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  mythdvd: Depends: mythtv-frontend (>= 0.18.1-1) but it is not going to be installed
           Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
           Depends: libmyth-0.18.1 but it is not going to be installed
           Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
           Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  mythgallery: Depends: mythtv-frontend (>= 0.18.1-1) but it is not going to be installed
               Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
               Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
               Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  mythmusic: Depends: mythtv-frontend (>= 0.18.1-1) but it is not going to be installed
             Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
             Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
             Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  mythnews: Depends: mythtv-frontend (>= 0.18.1-1) but it is not going to be installed
            Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
            Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
            Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  mythtv: Depends: mythtv-frontend (= 0.18.1-7) but it is not going to be installed
          Depends: mythtv-backend (= 0.18.1-7) but it is not going to be installed
  mythvideo: Depends: mythtv-frontend (>= 0.18.1-1) but it is not going to be installed
             Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
             Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
             Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
  mythweather: Depends: mythtv-frontend (>= 0.18.1-1) but it is not going to be installed
               Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
               Depends: libqt3-mt (>= 3:3.3.5) but 3:3.3.4-8ubuntu5 is to be installed
               Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
E: Broken packages

My source.list looks like the one in the howto, except is is in the Netherlands.
Tried the US version, and it did not matter...

I search all the net for sollutions and other docs, but can not find what i need..

Can anybody give me a hand?

I have Breezy 5.10 and a PVR-150.
Thnx,

Schucki

---

### Post by t0bb3 on 2006-01-03
schucki.be, are you using the 64-bit version of Ubuntu?

---

### Post by t0bb3 on 2006-01-03
Since there are no new version of MythTV in the repos for Ubuntu 64-bit, I had to compile it from source. This is what I had to do:

I downloaded mythtv_0.18.1-5.dsc, mythtv_0.18.1.orig.tar.gz and mythtv_0.18.1-5.diff.gz from here: [http://packages.ubuntu.com/breezy/graphics/mythtv](http://packages.ubuntu.com/breezy/graphics/mythtv)
I placed all three files in /opt/ and untared mythtv_0.18.1.orig.tar.gz so I ended up with a mythtv-0.18.1 directory. I then unpacked the diff file with ```
gunzip -d mythtv_0.18.1-5.diff.gz
``` After that I applied the patch by running ```
sudo patch -i mythtv_0.18.1-5.diff -p0
```
I went in to /opt/mythtv-0.18.1/debian and edited the "rules" file. All I changed was line 28 so it looked like this: > --cpu=x86_64 --tune=generic --enable-mmx \I then gave this command (from inside the debian folder)```
sudo chmod +x rules
```After that I installed fakeroot (sudo apt-get install fakeroot).

Now it's time to make the .deb packages. Run ```
cd /opt/mythtv-0.18.1/
sudo dpkg-buildpackage -rfakeroot -b
``` I got a lot of unmet build depencencies when I did that, but after resolving those and running the same command again I got a whole lot of .deb files in /opt/

Before I could install those .debs I had to install libqt3-mt-mysql and pwgen:```
sudo apt-get install libqt3-mt-mysql pwgen
``` It's now finaly time to install MythTV: ```
sudo dpkg -i *.deb
```

Maybe a note about 64-bit systems should be added to the HowTo?

---

### Post by schucki.be on 2006-01-03
[QUOTE=t0bb3]schucki.be, are you using the 64-bit version of Ubuntu?[/QUOTE]

Don't think so. The 2.6.12-10-386 version of the kernel.

Is that correct?:rolleyes: 

Thnx,
Schucki.be

==>> PROBLEM SOLVED <<==

---

### Post by Chuffinora on 2006-01-03
First off a big thank you,  using mostly your how-to I got my system up and running in 3 days (Newbie to Linux.)  Hardest part was getting the PVR-150 ir blaster to control the SA STB.  I found how to do it here  

[www.blushingpenguin.com/mark/blog/?p=19](www.blushingpenguin.com/mark/blog/?p=19)

(But ended up having to undo some of the stuff already done wiht Lirc and Lexmit?!)  Lots of futsing around, and had to read all the comments to figure out command #'s for cable and satelite are diff (Mine on rogers SA Ex 2000 are 0_41) thus instructions are not quite right,  but got there!

The only issue I still have, sounds the same as NeoLev.  Displaying tv my picture is offset down and to right a few pixels, and I have a blue line at left and top of screen????  It is only in TV and playback, not visible in the Gnome GUI,  thus I suspect something in Myth.

In setup, playback, tv settings, the 2nd to last screen gives overscan and picture displacement.  Nothing here corrects it and I am not sure setting anything in picture displacement is actually doing anything.

---

### Post by ichimunki on 2006-01-03
Thank you!!!

This HOWTO worked liked a charm for getting ivtv modules up and running with my PVR-150 card.

---

### Post by morphodone on 2006-01-03
I followed the how to and everything went well except for sound.

I can play entries from my previous mythtv setup in fedora core 3
and listen to those without problems

I cannot watch live tv or record new shows with sound.

I have disabled the sound server from startup and 
muted and unmuted every possible channel...

Any suggestions?

My sound is an onboard nvidia nforce2

---

### Post by t0bb3 on 2006-01-04
[QUOTE=schucki.be]Don't think so. The 2.6.12-10-386 version of the kernel.

Is that correct?:rolleyes: 

Thnx,
Schucki.be[/QUOTE]

It is correct if that's the cpu you are using...

What happens if you only try to install mythtv and not all the plugins?

---

### Post by schucki.be on 2006-01-04
[QUOTE=t0bb3]It is correct if that's the cpu you are using...

What happens if you only try to install mythtv and not all the plugins?[/QUOTE]

Hi t0bb3,
I am using a PIII 1 Ghz. Am I using the correct version then?

The issue with mythtv is solved. I copied a source.list last night, and the miraculeus solved the depends. I quit and went to sleep, and now I do not know where the solution came from. Thought it was one of your posts...
Got some database issues left, but i will look at it tonight. The frustrating thing is that i had the PVR running in 4 minutes on my widow partition, so my wife asked me the benefit of installing on Linux:p .

I am not giving up!

Thnx,
Schucki.be

---

### Post by t0bb3 on 2006-01-04
[QUOTE=schucki.be]Hi t0bb3,
I am using a PIII 1 Ghz. Am I using the correct version then?

...

The frustrating thing is that i had the PVR running in 4 minutes on my widow partition, so my wife asked me the benefit of installing on Linux:p .
...
[/QUOTE]

Yes, I think you have the correct version of the kernel.

Hehe, they're allways there with their questions, aren't they?

---

### Post by ichimunki on 2006-01-04
**this issue is resolved, sort of**

After seeing how easy it was to get ivtv going from this HOWTO, I decided to go for full-blown mythtv. Also going very smoothly for the most part. TV never looked better; DVD playback under xine is going great. Thanks again for the HOWTO.

I do have one question: Just can't get VCD playback to do anything. Anything. I put a VCD in the drive. Click Play VCD. Nothing. I get no feedback in the terminal window (I started mythbackend and mythfrontend from the terminal to get the output--which normally it gives out something, especially when running an external application like xine).

I don't see anywhere within MythTV to change any drive or player settings... I tried changing my DVD device to /media/cdrom, but that didn't help.

VCDs play fine from the terminal with ```
xine vcd://
```

Any ideas? I'm out of them after an hour or so of searching the web and documentation.

**Edit:** looks like maybe mythplugins has a default compile option of not enabling vcd, so it's possible vcd support wasn't compiled into the standard Ubuntu package... I am going to try compiling mythplugins from source and enable that option.

**Update:** it appears that VCD playback works just fine (after fiddling with appropriate MythTV configuration options available) doing it this way... only hard part was having to manually set PREFIX in settings.pro file in mythplugin source files to /usr rather than /usr/local (since Ubuntu's mythtv didn't detect plugin installation to /usr/local).

---

### Post by meastp on 2006-01-04
Although I did not follow your guide, my problem is related and I thought I could post here instead of making another thread.

I followed the "official" IVTV-guide: [http://ivtvdriver.org/index.php/Howto:Ubuntu]("http://ivtvdriver.org/index.php/Howto:Ubuntu")

This is the output of $ sudo dmesg

```

[4294703.132000] ivtv:  ==================== START INIT IVTV ====================
[4294703.132000] ivtv:  version 0.4.1 (tagged release) loading
[4294703.132000] ivtv:  Linux version: 2.6.12-10-686 686 gcc-3.4
[4294703.132000] ivtv:  In case of problems please include the debug info between
[4294703.132000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294703.132000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294703.141000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294703.142000] ACPI: PCI Interrupt Link [PIN3] enabled at IRQ 9
[4294703.142000] PCI: setting IRQ 9 as level-triggered
[4294703.142000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [PIN3] -> GSI 9 (level, low) -> IRQ 9
[4294703.257000] tveeprom: ivtv version
[4294703.257000] tveeprom: Hauppauge: model = 26034, rev = C197, serial# = 8766728
[4294703.257000] tveeprom: tuner = TCL 2002MB_3H (idx = 97, type = 55)
[4294703.257000] tveeprom: tuner fmt = PAL(B/G) PAL(D/K) (eeprom = 0x44, v4l2 = 0x00000e07)
[4294703.257000] tveeprom: audio processor = CX25842 (type = 24)
[4294703.257000] tveeprom: decoder processor = CX25842 (type = 1d)
[4294703.257000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294703.304000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294703.304000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294703.370000] cx25840 1-0044: ivtv driver
[4294703.370000] cx25840 1-0044: cx25842-23 found @ 0x88 (ivtv i2c driver #0)
[4294705.278000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294705.361000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294705.425000] wm8775 1-001b: ivtv driver
[4294705.425000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294705.437000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294706.207000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294716.560000] ivtv0 warning: 1000 ms time out waiting for firmware
[4294716.560000] ivtv0 warning: Failed api call 0x000000c4 with result 0xfffffff0
[4294716.560000] ivtv0: error getting Encoder firmware version
[4294716.560000] ivtv0: Error -16 getting firmware version!
[4294716.571000] ivtv0: Error -16 on initialization
[4294716.571000] ivtv: probe of 0000:00:0f.0 failed with error -16
[4294716.571000] ivtv:  ====================  END INIT IVTV  ====================



```

I'm kind of stuck and don't know what to do next... Any suggestions?

Best Regards,
meastp

---

### Post by dhyams on 2006-01-04
[QUOTE=meastp]Although I did not follow your guide, my problem is related and I thought I could post here instead of making another thread.

I followed the "official" IVTV-guide: [http://ivtvdriver.org/index.php/Howto:Ubuntu]("http://ivtvdriver.org/index.php/Howto:Ubuntu")

This is the output of $ sudo dmesg

[/quote]

Can you also post the output of 

ls -ltra /usr/lib/hotplug/firmware

---

### Post by meastp on 2006-01-05
[QUOTE=dhyams]Can you also post the output of 

ls -ltra /usr/lib/hotplug/firmware[/QUOTE]

```

tvuser@tvboks:~$ ls -ltra /usr/lib/hotplug/firmware
totalt 1336
drwxr-xr-x  3 root root   4096 2006-01-01 23:25 ..
-rw-r--r--  1 root root 262144 2006-01-04 18:09 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-01-04 18:09 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 2006-01-04 18:09 v4l-cx25840.fw
-r--r--r--  1 root root 376836 2006-01-04 18:10 v4l-cx2341x-enc.fw.orig
-rw-r--r--  1 root root 155648 2006-01-04 18:11 v4l-cx2341x-init-mpeg.bin
lrwxrwxrwx  1 root root     41 2006-01-04 18:11 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-rw-r--r--  1 root root 262144 2006-01-04 20:19 v4l-cx2341x-enc.fw
drwxr-xr-x  2 root root   4096 2006-01-04 20:19 .
tvuser@tvboks:~$


```

Note the v4l-cx2341x-enc.fw.orig It is a backup of the original v4l-cx2341x-enc.fw . The (current) file v4l-cx2341x-enc.fw is a copy of ivtv-fw-enc.bin

SOLVED! 

the module firmware_class was not loaded.

---

### Post by schucki.be on 2006-01-08
Got it working. It's SUPER cool.
I am working on a small doc with my findings. C that later this week.

Now i want to install a frontend only on my laptop.
Can not find clear info over such installs.
Seems that i can not connect to the backend database.
> 2006-01-08 21:12:02.171 Unable to connect to database!
2006-01-08 21:12:02.171 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.103' (111)

And this message repeates....

In setup on backend ip= correct
In Frontend ip=correct.

Anybody got ideas ?

Thnx,
schucki.be

---

### Post by dhyams on 2006-01-08
I just wanted to post a quick note to everyone on this thread, especially those who have contributed new information:  THANKS!

I will be working over the next week to incorporate new items into the HOWTO, some based on the findings in this thread.

I have been in and out of town for the last two weeks, which is why I haven't updated the HOWTO with the excellent info in here as of yet.

---

### Post by dhyams on 2006-01-08
[QUOTE=schucki.be]Got it working. It's SUPER cool.
I am working on a small doc with my findings. C that later this week.

Now i want to install a frontend only on my laptop.
Can not find clear info over such installs.
Seems that i can not connect to the backend database.


And this message repeates....

In setup on backend ip= correct
In Frontend ip=correct.

Anybody got ideas ?
[/QUOTE]

I just added a new mythfrontend myself.  I also had a little trouble at the mysql stage.  Until I get my writeup in my own HOWTO, try following Jarod's:

[http://wilsonet.com/mythtv/tips.php](http://wilsonet.com/mythtv/tips.php)

(scroll down to "remote front-ends")

And make sure you have done the recommended things there.  I also had to edit /etc/mysql/my.cnf on the *backend* and change the "bind-address" setting from "127.0.0.1" to whatever local IP the backend really is (in my case, 192.168.1.13). Restart mysql after that.

Now, try a test:

mysql -h <mythbackendhostname> -u mythtv -p mythconverg

on the frontend, and see if you can connect.  If you can't connect with this, you won't be able to with mythtv.  

One shouldn't have to do this, but I ended up, for simplicity, just adding a new mysql user on the backend with phpmyadmin, and using that user when connecting from the frontend.  That works as well.  It's decently easy to know how mythtv is going to behave with the little test that I give above.

---

### Post by dhyams on 2006-01-08
[QUOTE=meastp]```

tvuser@tvboks:~$ ls -ltra /usr/lib/hotplug/firmware
totalt 1336
drwxr-xr-x  3 root root   4096 2006-01-01 23:25 ..
-rw-r--r--  1 root root 262144 2006-01-04 18:09 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-01-04 18:09 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 2006-01-04 18:09 v4l-cx25840.fw
-r--r--r--  1 root root 376836 2006-01-04 18:10 v4l-cx2341x-enc.fw.orig
-rw-r--r--  1 root root 155648 2006-01-04 18:11 v4l-cx2341x-init-mpeg.bin
lrwxrwxrwx  1 root root     41 2006-01-04 18:11 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-rw-r--r--  1 root root 262144 2006-01-04 20:19 v4l-cx2341x-enc.fw
drwxr-xr-x  2 root root   4096 2006-01-04 20:19 .
tvuser@tvboks:~$


```

Note the v4l-cx2341x-enc.fw.orig It is a backup of the original v4l-cx2341x-enc.fw . The (current) file v4l-cx2341x-enc.fw is a copy of ivtv-fw-enc.bin

SOLVED! 

the module firmware_class was not loaded.[/QUOTE]


Thanks meastp!  This will solve several folks' problems.  So, what is the correct thing to do to make sure that the module firmware_class is loaded appropriately upon machine boot?  I suppose we could always stick a "modprobe firmware_class" somewhere in the bootup, but I thought there might be a better way.

---

### Post by schucki.be on 2006-01-09
Thnx,
I will try ot setup a frontend later today, and keep you posted.

Grtz,
Schucki.be

---

### Post by majkmil on 2006-01-09
This is my ivtv demeg.
root@ubuntu:/usr/src/ivtv-0.4.1#  dmesg
ey pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297136.148000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297136.246000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297136.246000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297136.441000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297136.441000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297136.545000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297136.545000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297136.644000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297136.644000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297136.759000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297136.759000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297136.863000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297136.863000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297136.976000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297136.976000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.093000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297137.093000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.214000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297137.214000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.310000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297137.310000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.432000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297137.432000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.533000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297137.533000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.652000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297137.652000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.754000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297137.754000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.879000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297137.879000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297137.988000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297137.988000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297138.103000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297138.103000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297138.207000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297138.207000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297138.319000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297138.319000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297138.440000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297138.440000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297138.562000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297138.562000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297138.683000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297138.683000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297138.804000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297138.804000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297151.751000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297151.751000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297151.872000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297151.872000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.090000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297153.090000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.182000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297153.182000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.275000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297153.275000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.379000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297153.379000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.463000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297153.463000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.558000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297153.558000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.639000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297153.639000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.743000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297153.743000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.821000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297153.821000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.920000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297153.920000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297153.998000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297153.998000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.104000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297154.104000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.186000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297154.186000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.301000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297154.301000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.379000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297154.379000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.490000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297154.490000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.568000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297154.568000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.674000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297154.674000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.753000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297154.753000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.865000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297154.865000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297154.948000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297154.948000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.058000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297155.058000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.137000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297155.137000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.244000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297155.244000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.326000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297155.326000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.444000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297155.444000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.519000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297155.519000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.637000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297155.637000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297155.894000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297155.894000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297156.044000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297156.044000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298614.653000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298614.653000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298614.777000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298614.777000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298614.896000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298614.896000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298615.042000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298615.042000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298615.140000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298615.140000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298616.209000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298616.209000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298617.983000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298617.983000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.104000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298618.104000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.187000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298618.187000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.344000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298618.344000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.438000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298618.438000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.564000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298618.564000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.642000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298618.642000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.775000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298618.775000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298618.874000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298618.874000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.042000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298619.042000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.112000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298619.112000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.278000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298619.278000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.368000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298619.368000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.527000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298619.527000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.603000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298619.603000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.777000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298619.777000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298619.878000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298619.878000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298620.051000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298620.051000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298620.154000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298620.154000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298620.316000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298620.316000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298648.432000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298648.432000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298648.553000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298648.553000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298649.202000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298649.202000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298650.581000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298650.581000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298650.899000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298650.899000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298651.032000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298651.032000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298651.278000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298651.278000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298651.396000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298651.396000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298652.045000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4298652.045000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298652.145000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4298652.145000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
root@ubuntu:/usr/src/ivtv-0.4.1#

Any ideas, Thanks
BTW I am using my monitor for tv out. When I try to verify the ivtv drivers I get a cant connect to video out ( X11)

---

### Post by schucki.be on 2006-01-09
Thnx !
My Frontend is working to.
Got to do some (a lott ;-0) fine tuning to do.
Keep you posted !

Grtz,
Schucki.be

---

### Post by majkmil on 2006-01-09
I think I fixed it with a restart. herehis my ivtv dmesg.

tv:  ==================== START INIT IVTV ====================
[4294833.129000] ivtv:  version 0.4.1 (tagged release) loading
[4294833.129000] ivtv:  Linux version: 2.6.12-10-386 386 gcc-3.4
[4294833.129000] ivtv:  In case of problems please include the debug info between
[4294833.129000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294833.129000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294833.134000] ivtv0: Autodetected WinTV PVR 250 card (cx23416 based)
[4294833.134000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 18
[4294833.134000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294833.223000] tveeprom: ivtv version
[4294833.223000] tveeprom: Hauppauge: model = 32552, rev = B133, serial# = 6716685
[4294833.223000] tveeprom: tuner = Temic 4039FR5 (idx = 33, type = 21)
[4294833.223000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294833.223000] tveeprom: audio processor = MSP4448 (type = 1b)
[4294833.223000] tveeprom: decoder processor = SAA7115 (type = 13)
[4294833.223000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294833.231000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294833.231000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61][4294833.259000] saa7115 0-0021: ivtv driver
[4294833.259000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4294833.431000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4294833.456000] msp3400 0-0040: ivtv driver
[4294833.456000] msp3400 0-0040: chip=MSP4448G-A2 +nicam +simple +simpler +radio mode=simpler
[4294833.463000] ivtv0: i2c attach to card #0 ok [client=MSP4448G-A2, addr=40]
[4294833.463000] msp3400 0-0040: msp34xxg daemon started
[4294834.227000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294834.437000] ivtv0: Encoder revision: 0x02050032
[4294834.438000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294834.440000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294834.442000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294834.444000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294834.447000] ivtv0: Create encoder radio stream
[4294834.447000] tuner: type set to 21 (Temic NTSC (4039 FR5)) by ivtv i2c driver #0
[4294834.765000] ivtv0: Initialized WinTV PVR 250, card #0
[4294834.765000] ivtv:  ====================  END INIT IVTV  ===================

Does this look OK?

---

### Post by dhyams on 2006-01-09
[QUOTE=majkmil]I think I fixed it with a restart. herehis my ivtv dmesg.


Does this look OK?[/QUOTE]

Looks good to me!

dhyams

---

### Post by majkmil on 2006-01-09
This is what I get when I test the mpg.

root@ubuntu:/usr/src/ivtv-0.4.1# mplayer -vo xv /tmp/test.mpg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for Debian.


86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /tmp/test.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9600.0 kbps (1200.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: couldn't open the X11 display ()!
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)
root@ubuntu:/usr/src/ivtv-0.4.1#

Ant Help Please!
As I said earlier I am using a flat panel moniter with DVI.

---

### Post by dhyams on 2006-01-09
[QUOTE=majkmil]This is what I get when I test the mpg.

root@ubuntu:/usr/src/ivtv-0.4.1# mplayer -vo xv /tmp/test.mpg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for Debian.


86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /tmp/test.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9600.0 kbps (1200.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: couldn't open the X11 display ()!
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)
root@ubuntu:/usr/src/ivtv-0.4.1#

Ant Help Please!
As I said earlier I am using a flat panel moniter with DVI.[/QUOTE]

It looks like you might have logged in as another user, and did sudo -i to get to root.  The original user that you logged in as is the only one with permission to access the X display.

So, try again by opening a fresh terminal, and then typing the mplayer command.

---

### Post by majkmil on 2006-01-09
Thank you but I tried using a fresh terminal (non root) and I get this.

mark@ubuntu:/usr/src/ivtv-0.4.1$  mplayer -vo xv /tmp/test.mpg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /tmp/test.mpg.
File not found: '/tmp/test.mpg'
Failed to open /tmp/test.mpg


Exiting... (End of file)
mark@ubuntu:/usr/src/ivtv-0.4.1$ cd
mark@ubuntu:~$  mplayer -vo xv /tmp/test.mpg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /tmp/test.mpg.
File not found: '/tmp/test.mpg'
Failed to open /tmp/test.mpg


Exiting... (End of file)
mark@ubun

---

### Post by dhyams on 2006-01-10
[QUOTE=majkmil]Thank you but I tried using a fresh terminal (non root) and I get this.

mark@ubuntu:/usr/src/ivtv-0.4.1$  mplayer -vo xv /tmp/test.mpg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /tmp/test.mpg.
File not found: '/tmp/test.mpg'
Failed to open /tmp/test.mpg


Exiting... (End of file)
mark@ubuntu:/usr/src/ivtv-0.4.1$ cd
mark@ubuntu:~$  mplayer -vo xv /tmp/test.mpg
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /tmp/test.mpg.
File not found: '/tmp/test.mpg'
Failed to open /tmp/test.mpg


Exiting... (End of file)
mark@ubun[/QUOTE]


Hmmm...first make sure that the file is actually there:

ls -l /tmp/test.mpg

If it is not, you need to recreate it.  If it is there, you might need to change permissions for it to make it readable by all:

sudo chmod a+r /tmp/test.mpg

---

### Post by greyhound4334 on 2006-01-12
Thanks very much for this awesome guide.

Apologies in advance for what turned out to be a longish post.  And for any "hijacking", but this seems like a great gathering place for Ubuntu MythTVers.  If there's any signficant interest in this topic, I'll start a new thread and continue discussion there.

Thanks largely to this HOWTO, and a few other good ones, I've got things functioning at 90+% -- certainly enough to "deploy to the living room" and turn it over to the users :)  (who will have to be convinced that this is better than the Tivo they've been asking for!)

I'm in the process of trying to fine tune things, especially the quality of the picture.  I'm fairly new to TV, video, etc. (but not so much to Linux/Ubuntu), but very interested, and willing to spend some time learning and documenting the nuances of tuning a MythTV box.  Seems like the general HowTo space is pretty well covered at this point, but there's very little gathered wisdom on tuning.

As a tiny bit of background: I'm mostly motivated to try to get the best possible picture on a Standard Definition old-fashioned CRT type television.   And I'm mostly motivated to try to make watching sports on LiveTV under MythTV as close to "broadcast quality" as possible.   And I'm using a fairly powerful processor (AMD64 3200+), so I'm not too worried about trading computing power for picture quality.

So I'm starting with a bunch of questions.  Anybody that's got insight into these (or wants to add more, or disagrees with the question), I'd sure appreciate hearing about it, including pointers to other reference material.  As I said, if I gather anything more useful than "tweak it until it breaks or looks better" ;) I'll gladly gather it up and post it here.

Here are some of my starting questions:

1. What's up with XvMC?  As far as I can tell, it's a feature supported by modern nVidia cards that, to be used by MythTV, needs to be compiled into the MythTV software.  As far as I can tell, the current breezy badger 32-bit repository versions of Myth do NOT include XvMC support.  I don't know this for sure, and would appreciate an expert opinion.

At this point, my opinion is based on running ldd on several myth binaries and not seeing any reference to the nVidia XvMC libraries (e.g., 
```
ldd /usr/lib/libmythtv-0.18.1.so.0
ldd /usr/lib/libmythavcodec-0.18.1.so.0
ldd /usr/bin/mythfrontend
```
1.a. How beneficial is XvMC to picture quality?  Opinions seem to be mixed.  What kinds of benefits is it supposed to provide?
1.b. If you DO use XvMC, are you not able to also use the "De-interlace Playback" feature?
1.c. If you DO use XvMC, are you not able to also use the "Custom Filters" feature?
1.d. If you DO use XvMC, are you not able to also use the "Use libmpeg2 for decoding" feature?

2. How do the various xorg.conf settings affect picture quality?  What are appropriate values for Display "modes" and how do they affect quality?  Do specific "modelines" provide enhanced quality?  Are there other settings (besides the ones covered in the HOWTOs, like 
```
	Option "TVStandard" "NTSC-M"
	Option "TVOutFormat" "SVIDEO"
	Option "TVOverScan" "0.6" 
	Option "ConnectedMonitor" "TV"

```
that one should be tweaking?

3. Does mythfrontend's Setup->TV Settings->Recording Profiles->MPEG-2 Encoders->LiveTV->Video Compression affect quality? For LiveTV, why not set these values as high as possible?  What is the maximum effective bit rate?  On this page, what is the "Stream Type" parameter?

4. What are the tradeoffs between using libmpeg2, ffmpeg, and XvMC (are these, in fact, 3 mutually exclusive options for mpeg-2 decoding?) 

5. How do the various features that deal with picture size/scale/overscan interact?  For example, 
- you can set DisplaySize in your xorg.conf file
- you can use nvidia-settings to change the picture scale
- you can set TvOverScan in your xorg.conf file
- you can set values in mythfrontend's Setup->TV Settings->Playback->Overscan,
- you can set values in mythfrontend's Setup->TV Settings->Recording Profiles->MPEG-2 Encoders->LiveTV->Image Size (Height/Width)

Do they have any interaction?  Any precedence?  Is there a methodology for tuning them?

6. What does the General Playback->"Use Xv Picture Controls" feature do?  Is Xv the same as XvMC?

7. How do you use the various nvidia-settings features to optimize playback?  How do these features interact with other similar settings?

Sorry for the long post.  Hopefully a few other people are interested in this topic.

Cheers,
john

---

### Post by majkmil on 2006-01-12
got myth working but video is not good on my tft monitor. I have three errors that maybe someone can help me with. Please.


* Couldn't find Xv support, falling back to non-Xv mode.
* MythTV performance will be much slower since color
* conversion and scaling will be done in software.
* Consider upgrading your video card or X server if
* you would like better performance.
X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  15
  Resource id:  0xffffffff
X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0xffffffff
2006-01-12 22:20:36.376 Couldn't get the color key color, and we need it.
You likely won't get any video.


X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  15
  Resource id:  0xffffffff
X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0xffffffff
2006-01-12 22:23:28.090 Couldn't get the color key color, and we need it.
You likely won't get any video.
QObject::disconnect: Unexpected null parameter
2006-01-12 22:23:28.132 Changing from WatchingLiveTV to None
2006-01-12 22:23:28.140 Changing from None to None
2006-01-12 22:23:28.385 Enable DPMS

These first two are when running mythTV, The next one is when I try to run mythtv setup. I cannot get into mythtv setup byt mythtv does work. What does it mean about color key color? What is Xv and how can I get this? What about the bad ports. Does myth take advantge of hardware encoding by my pvr 250? Sorry about all the questions but I am just happy to have iy running but I would really like to solve these errors.

PS. Does myth always run in full screen?

---

### Post by schucki.be on 2006-01-13
Hello John,

[QUOTE=greyhound4334]Thanks very much for this awesome guide.

If there's any signficant interest in this topic, I'll start a new thread and continue discussion there.

Thanks largely to this HOWTO, and a few other good ones, I've got things functioning at 90+% -- certainly enough to "deploy to the living room" and turn it over to the users :)  (who will have to be convinced that this is better 

Cheers,
john[/QUOTE]

I also have a large bit running now:razz: . Working on things like mythweb, remote frontend, dvd etc..
I am interested in fine tuning and getting the last parts running.
So if you start a new thread I will be following that one to, just as this one.:smile: 

Thnx,

Schucki.be

---

### Post by greyhound4334 on 2006-01-13
Well I think I'll probably start a new thread if I get any more interest in the topic.  I don't have much to share yet, except that I did get confirmation from Matt Zimmerman - former Ubuntu MythTV maintainer - that indeed the Ubuntu MythTV packages were built *without* XvMC support.  Just an interesting tidbit.

I've got a few things to experiment with tomorrow in the area of screen resolution, so will report back anything interesting.

Hoping to get things tuned enough to minimize some of the fast-motion blurring I currently see in time for the big football weekend coming up!  With apologies to any Denver friends -- Go Patriots!

Cheers,
john

---

### Post by deontaljard on 2006-01-16
Hey greyhound4334

I'd be very keen on a  "Myth Tweak" kind of thread.
Did you come right with your motion blur?  I've solved this before by editing the recording profiles to be the same frame size as your capture card.  i.e if you are capturing (in my case PAL) 720x576 then change the recording profiles from the default 480x480 to 720x576.  I can't remember what the thinking was here - maybe some kind of resize for each frame drawn?  I worked on this problem about 8 months ago so I can't remember the specifics.

Cheers
Deon

---

### Post by greyhound4334 on 2006-01-16
Hi Deon,

I decided to start a new thread on "tweaking and tuning" here: [http://www.ubuntuforums.org/showthread.php?p=662474#post662474](http://www.ubuntuforums.org/showthread.php?p=662474#post662474)

Let's continue our discussion there.  I'll copy your question and post a reply there.

Thanks,
john

---

### Post by deontaljard on 2006-01-17
Hey Dhyams

Nice how-to - just a small correction - there's a problem with your lirc section - small typo.  The line "ln -s /etc/lircrc-haupgrey.txt .lircrc" should read "ln -s /etc/lircrc-haupgrey-g3.txt .lircrc"  Hope I'm not being too pedantic - some people copy and paste their way thru how-to's :) 

Cheers
Deon

---

### Post by neolev on 2006-01-17
Here is the PVR 500 IVTV Dmesg

[4294712.416000] ivtv:  ==================== START INIT IVTV ====================
[4294712.416000] ivtv:  version 0.4.1 (tagged release) loading
[4294712.416000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4294712.416000] ivtv:  In case of problems please include the debug info between
[4294712.416000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294712.416000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294712.428000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294712.429000] logips2pp: Detected unknown logitech mouse model 62
[4294712.434000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294712.434000] PCI: setting IRQ 10 as level-triggered
[4294712.434000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294712.513000] tveeprom: Second (radio) tuner idx 101
[4294712.513000] tveeprom: ivtv version
[4294712.513000] tveeprom: Hauppauge: model = 23552, rev = D492, serial# = 8728360
[4294712.513000] tveeprom: tuner = Philips FQ1236A MK4 (idx = 92, type = 57)
[4294712.513000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294712.513000] tveeprom: audio processor = CX25843 (type = 25)
[4294712.513000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294712.513000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294712.558000] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[4294712.583000] ivtv0: This is the first unit of a PVR500
[4294712.596000] tuner (ivtv): chip found at addr 0xc0 i2c-bus ivtv i2c driver #0
[4294712.598000] TEA5767 detected.
[4294712.598000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=60]
[4294712.600000] tuner: type set to 62 (Philips TEA5767HN FM Radio) by autodetect
[4294712.600000] type set to 62 (Philips TEA5767HN FM Radio)
[4294712.600000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294712.600000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294712.677000] cx25840 0-0044: ivtv driver
[4294712.677000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294714.550000] ts: Compaq touchscreen protocol output
[4294714.885000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294714.969000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294715.040000] wm8775 0-001b: ivtv driver
[4294715.040000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294715.052000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294715.065000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4294715.065000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294715.068000] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[4294715.869000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294716.079000] ivtv0: Encoder revision: 0x02050032
[4294716.081000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294716.083000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294716.085000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294716.087000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294716.090000] ivtv0: Create encoder radio stream
[4294716.090000] tuner: type set to 57 (Philips FQ1236A MK4) by ivtv i2c driver #0
[4294716.328000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[4294716.328000] ivtv:  ======================  NEXT CARD  ======================
[4294716.328000] ivtv1: Autodetected WinTV PVR 150 card (cx23416 based)
[4294716.329000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3
[4294716.329000] PCI: setting IRQ 3 as level-triggered
[4294716.329000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[4294716.398000] tveeprom: Second (radio) tuner idx 101
[4294716.398000] tveeprom: ivtv version
[4294716.398000] tveeprom: Hauppauge: model = 23552, rev = D492, serial# = 8728360
[4294716.398000] tveeprom: tuner = Philips FQ1236A MK4 (idx = 92, type = 57)
[4294716.398000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294716.398000] tveeprom: audio processor = CX25843 (type = 25)
[4294716.398000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294716.398000] ivtv1: i2c attach to card #1 ok [client=tveeprom, addr=50]
[4294716.401000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #1
[4294716.401000] ivtv1: i2c attach to card #1 ok [client=(tuner unset), addr=61]
[4294716.427000] cx25840 1-0044: ivtv driver
[4294716.427000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[4294717.959000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294718.043000] ivtv1: i2c attach to card #1 ok [client=cx25840, addr=44]
[4294718.050000] wm8775 1-001b: ivtv driver
[4294718.050000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[4294718.063000] ivtv1: i2c attach to card #1 ok [client=wm8775, addr=1b]
[4294718.083000] tda9887 1-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #1)
[4294718.083000] ivtv1: i2c attach to card #1 ok [client=tda9887, addr=43]
[4294718.095000] ivtv1: This is the second unit of a PVR500
[4294718.095000] ivtv1: Correcting tveeprom data: no radio present on second unit
[4294718.895000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294719.105000] ivtv1: Encoder revision: 0x02050032
[4294719.107000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294719.109000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294719.111000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294719.113000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294719.114000] tuner: type set to 57 (Philips FQ1236A MK4) by ivtv i2c driver #1
[4294719.352000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[4294719.352000] ivtv:  ====================  END INIT IVTV  ====================

---

### Post by neolev on 2006-01-17
Anyone know of a good IR Blaster to use with Myth and Linux (Ubuntu) to use with a dish box???


Neolev

---

### Post by dhyams on 2006-01-17
[QUOTE=deontaljard]Hey Dhyams

Nice how-to - just a small correction - there's a problem with your lirc section - small typo.  The line "ln -s /etc/lircrc-haupgrey.txt .lircrc" should read "ln -s /etc/lircrc-haupgrey-g3.txt .lircrc"  Hope I'm not being too pedantic - some people copy and paste their way thru how-to's :) 

Cheers
Deon[/QUOTE]

Thanks for the tip!  I'll correct it asap, and yes, I want to know about any typos!

---

### Post by greyhound4334 on 2006-01-20
Hi,

Ran into a strange situation, and thought that getting more eyeballs on it might help.  Apologies for "cross posting" if you're a subscriber to the ivtv-users list, since I just posted it there, but from what I can tell, that's a fairly low-traffic area (and as we all know, when Mythtv's down, the family IS NOT HAPPY! :mad: )

Anyway, here's the problem.  Maybe it's obvious from my 
dmesg output, so I'll put that first.  See more details below.

```

[17179587.348000] ivtv:  ==================== START INIT IVTV 
====================
[17179587.348000] ivtv:  version 0.4.1 (tagged release) loading
[17179587.348000] ivtv:  Linux version: 2.6.15-ubuntu1-john K7 gcc-4.0
[17179587.348000] ivtv:  In case of problems please include the debug 
info between
[17179587.348000] ivtv:  the START INIT IVTV and END INIT IVTV lines, 
along with
[17179587.348000] ivtv:  any module options, when mailing the ivtv-users 
mailinglist.
[17179587.352000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17179587.352000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179587.352000] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC3] -> 
GSI 18 (level, low) -> IRQ 20
[17179587.352000] ivtv0: Unreasonably low latency timer, setting to 64 
(was 32)
[17179587.372000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179587.448000] tveeprom 2-0050: Hauppauge model 26552, rev C268, 
serial# 8754297
[17179587.448000] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 
68, type 47)
[17179587.448000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[17179587.448000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[17179587.448000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[17179587.448000] tveeprom 2-0050: has radio, has no IR remote
[17179587.460000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179587.460000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), 
addr=61]
[17179587.496000] cx25840: Unknown symbol i2c_adapter_id
[17179587.496000] ivtv0: Failed to load module cx25840
[17179587.496000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0xc008561c!
[17179587.508000] wm8775: Unknown symbol i2c_adapter_id
[17179587.508000] ivtv0: Failed to load module wm8775
[17179587.512000] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179587.512000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17179588.288000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179588.496000] ivtv0: Encoder revision: 0x02050032
[17179588.496000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 
buffers (4096KB total)
[17179588.496000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 
buffers (2048KB total)
[17179588.496000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 
buffers (2048KB total)
[17179588.496000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 
4608 buffers (2048KB total)
[17179588.496000] ivtv0: Create encoder radio stream
[17179588.496000] tuner 2-0061: type set to 47 (LG NTSC (TAPE series))
[17179588.496000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0x40085618!
[17179588.496000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0xc0045627!
[17179588.496000] ivtv0 warning: i2c client addr: 0x1b not found for 
command 0x40046d11!
[17179588.496000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0x40046d11!
[17179588.500000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0x40085618!
[17179588.500000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0xc008561c!
[17179588.508000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0x40045613!
[17179588.508000] ivtv0 warning: i2c client addr: 0x1b not found for 
command 0x402c5639!
[17179588.508000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0x402c5639!
[17179588.508000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0x40045612!
[17179588.624000] ivtv0 warning: i2c client addr: 0x44 not found for 
command 0xc008561c!
[17179588.624000] ivtv0: Initialized WinTV PVR 150, card #0
[17179588.624000] ivtv:  ====================  END INIT IVTV 
====================

```

This is on an AMD64-based system running Ubuntu 5.10 with a Hauppauge 
PVR-150 card.

Everything was great (ivtv and mythtv worked fine) until I decided to 
try to upgrade to a 2.6.15 series kernel (was at 2.6.12).

After doing that, in the process of rebuilding ivtv-0.4.1 from source, I 
think I messed up a step.  Sorry, I lost track a little bit at that 
point, so I'm not really sure what I did wrong, but ivtv wasn't loading 
(no output from it in dmesg, no /dev/video devices).

At that point, things were also a little funky with my nvidia drivers, 
so I basically tried to deinstall the kernel and nvidia stuff and start 
over.

The last go-round, these notable things happened:

- running make install for ivtv did NOT produce any duplicate module 
messages.  I was a bit stumped by that.
- after make install, I only had two modules in my 
/lib/modules/2.6.15-ubuntu1/ivtv directory: ivtv-fb.ko and ivtv.ko
- I re-ran make clean, make, and make install, and these were still the 
only files there.  So I copied the whole ivtv directory from my previous 
installation's /lib/modules directory (same kernel; I'd saved off the 
/lib/modules directory before re-installing) into my 
modules/2.6.15-ubuntu1-john directory
- note: uname -r returns "2.6.15-ubuntu1-john"; there's always been this strange mismatch where the ivtv modules are placed in 2.6.15-ubuntu1, not 2.6.15-ubuntu1-john; dyham's guide describes the same phenomenon and how to resolve it (by manual copying).  This workaround has worked for me in the past.

The only other possibly related thing is that when building this kernel, 
I thought I'd try to resolve some strangeness with lm-sensors by 
selecting a few more i2c_ related modules to be built.  I note that many 
of these messages in the ivtv section are related to i2c problems, so 
I'm not sure whether this is related.

Here's my /etc/modules file:

lp
mousedev
psmouse
# I2C adapter drivers
i2c-nforce2
i2c-isa
# I2C chip drivers
#eeprom
it87
ivtv

I'd appreciate any ideas and help figuring this out.  I can provide any 
additional information that's needed.

Cheers,
john

---

### Post by t0bb3 on 2006-01-24
Just thought I would share some information I found...

The mplayer build currently in the repos can't play movies with ac3 sound in them. (At least the 64bit version) That includes most DVDs and some divx/xvid movies as well. If you want to get it to work you have to compile mplayer yourself. Just search for "ac3 mplayer" here on the forums and you'll get lots of threads about this.

You can pass the sound straight through mplayer, and it'll work, but to do that you'll need an ac3 decoder connected to your computer through spdif, like for example a surround reciever.

To do this you give mplayer these command line parameters plus whatever you've already got:```
-ao alsa1x -ac hwac3 -af-adv force=3
```The problem with this is that now movies without ac3 sound will not work.

Using xine instead of mplayer seems to do the trick for most people, but it didn't for me, atleast stright out of the box.
I had to pass the sound through xine as well to get it to work. I did this by changing the xine config file in ~/.xine/config. It needs this:```
audio.output.speaker_arrangement:Pass Through
```The beauty of that is that it still works with movies without ac3 sound :) And of course switching to xine also gives you dvd menus, as already stated in the HowTo :)

So my suggestion is to make the switching to xine a more central part of the howto and not just a tip at the end.


One thing though that I don't like about using xine in MythTV is that I can see my desktop for a split second when launching a movie. Is there anything to do about that?

//t0bb3

---

### Post by schucki.be on 2006-01-25
Hello all,
I have got my backend with PVR 150 running, two frontend laptops, both wireless.
Live tv works great.:p 
Watching recording is not possible:( . 
After one or two minutes I return to the menus again. The complete shows are recorded, that is not the problem.
I have to admit that I did not try it on my server, or with my laptop wired...
Maybe somebody had this before?

One other thing is that I cannot play the mp3's from my server on my frontend. Some MAD-error. I will provide more info if needed. I had it written down, but it's on my desk at home:mad: .
Permissions are set for all users, so access should not be the problem.

Last thing is that I want to watch my photo gallerie on my frontend, but i cannot find info about settings.

Anybody ?

Thnx,
schucki.be

---

### Post by arjay1 on 2006-01-25
dhyams - did pm you re your guide but no response so thought I might post here in case others can help:

I am trying to install mythtv on ubuntu with a pvr150 card.  I have
faithfully followed your excellent howto but have now hit a snag (probably
my fault).  I also have a couple of points for you that might help make the
howto better for newbies like myself.
 
*General issue*
You recommend using "sudo -i" to create a root shell rather than the
laborious use of sudo every time.  I agree and that is a great tip.
However, in Point 2 of your howto you give the example "gedit /etc/apt/
sources.list".  Just to let you know that when i tried this command in a
root shell it says "Cannot open display".  It works fine, though, if you
use a one-off sudo command at the normal user prompt.  Worth checking?
 
*Possible install erro*r
When installing appache2 and msql-server, I noticed what seems a possible
error in my install.  I saw the message "Could not determine the server's
fully qualified domain name. Using 192.1268.1.3 for server name."  Is this
OK?  The ip address it talks about is the correct one for the machine,
entered during boot install.  Also, I used the default name of "ubuntu" for
the hostname but this is obviously not what the error above is referring to
 ....
 
*Obvious major error*
Now for the biggie.  Everything when just smoothly right up until the
section on your page 7 re firmware install.  First, let me say your timings
are optimistic in the extreme!!  I tried to download the two files
pvr_**.zip and pvr_**.inf.zip as instructed, on two different machines on
two different days with a broadband connection.  The BEST connection speed
I ever got was a miserable 3 K/s - with several timeouts and pauses with no
activity at all.  It took 45 minutes to get these two tiddly files!!
 
Anyway
 
Problem 1
When I unzipped pvr_2.0.24.2305.zip it reported that "Inflating hcwcCnv2.ax
- bad crd**d: it should be b***" something or other.  Not sure how serious
this is/was.
 
Problem 2.
This was the killer. The command "./ivtvfwextract.pl
pvr_1.18.21.22254_inf.zip" did not run fully.  It reported "cannot open /
tmp/ivtvex.****/hcwpvrp2.sys - no such file or directory".  I searched on
the internet and found several references to this in suse 9.1 and gentoo
installs.  

I tried copying the file from the CD that came with the pvr150 -
to /tmp and also other folders of the hard drive where the other related
files were.  The command still would not run (claimed it still could not
find the file).  I eventually found out that this was because of the
content of the perl script.  I found a howto that claimed I could modify
the script to force it to look at the /tmp directory where i had copied the
file hcwpvrp2.sys from the CDRom.
 
I thought this worked as there appeared to be no errors.  BUT:
 
The next set of instructions in your guide worked ok and the right four files
ended up in the hotplug/firmware folder.  I got a correct listing as per
the last box on your page7.  I entered ivtv in the /etc/modules file and
the alias command in aliases OK.
 
However, when i got to depmode and modprobe ivtv it reported "FATAL ERROR -
no modules".  This was confirmed by dmesg and lsmod.  I tried a reboot but
no good.  I also tried just re-doing your section on compiling the ivtv dirvers etc.  I got the warned of duplicate files but moved those as instructed and then make install again.  Still no modules??
 
Now I am stuck.  Don't know enough to test out anything else.
 
Can you help?
 
Thanks a bunch for an excellent guide.
 
Richard

---

### Post by Micro Rotors on 2006-01-25
Ok I have tried to install this myth tv stuff now for almost 2 months, This thing is killing me! I am using the guide [http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")
and I dont have NVidia but I have my ATI x330 installed and running but then I enter the commands in step 5.1 this is what I get. it's all cannot open blah, blah,blah stuff. I am almost ready to through the towl in!!!!


[PHP]linux-source-2.6.12/sound/pci/hda/hda_proc.c
tar: linux-source-2.6.12/sound/pci/hda/hda_proc.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/hda/patch_analog.c
tar: linux-source-2.6.12/sound/pci/hda/patch_analog.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/hda/patch_cmedia.c
tar: linux-source-2.6.12/sound/pci/hda/patch_cmedia.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/hda/patch_realtek.c
tar: linux-source-2.6.12/sound/pci/hda/patch_realtek.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/hda/patch_sigmatel.c
tar: linux-source-2.6.12/sound/pci/hda/patch_sigmatel.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/
tar: linux-source-2.6.12/sound/pci/ice1712: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/Makefile
tar: linux-source-2.6.12/sound/pci/ice1712/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/ak4xxx.c
tar: linux-source-2.6.12/sound/pci/ice1712/ak4xxx.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/amp.c
tar: linux-source-2.6.12/sound/pci/ice1712/amp.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/amp.h
tar: linux-source-2.6.12/sound/pci/ice1712/amp.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/aureon.c
tar: linux-source-2.6.12/sound/pci/ice1712/aureon.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/aureon.h
tar: linux-source-2.6.12/sound/pci/ice1712/aureon.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/delta.c
tar: linux-source-2.6.12/sound/pci/ice1712/delta.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/delta.h
tar: linux-source-2.6.12/sound/pci/ice1712/delta.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/envy24ht.h
tar: linux-source-2.6.12/sound/pci/ice1712/envy24ht.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/ews.c
tar: linux-source-2.6.12/sound/pci/ice1712/ews.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/ews.h
tar: linux-source-2.6.12/sound/pci/ice1712/ews.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/hoontech.c
tar: linux-source-2.6.12/sound/pci/ice1712/hoontech.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/hoontech.h
tar: linux-source-2.6.12/sound/pci/ice1712/hoontech.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/ice1712.c
tar: linux-source-2.6.12/sound/pci/ice1712/ice1712.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/ice1712.h
tar: linux-source-2.6.12/sound/pci/ice1712/ice1712.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/ice1724.c
tar: linux-source-2.6.12/sound/pci/ice1712/ice1724.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/juli.c
tar: linux-source-2.6.12/sound/pci/ice1712/juli.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/juli.h
tar: linux-source-2.6.12/sound/pci/ice1712/juli.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/phase.c
tar: linux-source-2.6.12/sound/pci/ice1712/phase.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/phase.h
tar: linux-source-2.6.12/sound/pci/ice1712/phase.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/pontis.c
tar: linux-source-2.6.12/sound/pci/ice1712/pontis.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/pontis.h
tar: linux-source-2.6.12/sound/pci/ice1712/pontis.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/prodigy192.c
tar: linux-source-2.6.12/sound/pci/ice1712/prodigy192.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/prodigy192.h
tar: linux-source-2.6.12/sound/pci/ice1712/prodigy192.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/revo.c
tar: linux-source-2.6.12/sound/pci/ice1712/revo.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/revo.h
tar: linux-source-2.6.12/sound/pci/ice1712/revo.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/stac946x.h
tar: linux-source-2.6.12/sound/pci/ice1712/stac946x.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/vt1720_mobo.c
tar: linux-source-2.6.12/sound/pci/ice1712/vt1720_mobo.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ice1712/vt1720_mobo.h
tar: linux-source-2.6.12/sound/pci/ice1712/vt1720_mobo.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/intel8x0.c
tar: linux-source-2.6.12/sound/pci/intel8x0.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/intel8x0m.c
tar: linux-source-2.6.12/sound/pci/intel8x0m.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/korg1212/
tar: linux-source-2.6.12/sound/pci/korg1212: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/korg1212/Makefile
tar: linux-source-2.6.12/sound/pci/korg1212/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/korg1212/korg1212-firmware.h
tar: linux-source-2.6.12/sound/pci/korg1212/korg1212-firmware.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/korg1212/korg1212.c
tar: linux-source-2.6.12/sound/pci/korg1212/korg1212.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/maestro3.c
tar: linux-source-2.6.12/sound/pci/maestro3.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/
tar: linux-source-2.6.12/sound/pci/mixart: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/mixart/Makefile
tar: linux-source-2.6.12/sound/pci/mixart/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart.c
tar: linux-source-2.6.12/sound/pci/mixart/mixart.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart.h
tar: linux-source-2.6.12/sound/pci/mixart/mixart.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart_core.c
tar: linux-source-2.6.12/sound/pci/mixart/mixart_core.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart_core.h
tar: linux-source-2.6.12/sound/pci/mixart/mixart_core.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart_hwdep.c
tar: linux-source-2.6.12/sound/pci/mixart/mixart_hwdep.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart_hwdep.h
tar: linux-source-2.6.12/sound/pci/mixart/mixart_hwdep.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart_mixer.c
tar: linux-source-2.6.12/sound/pci/mixart/mixart_mixer.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/mixart/mixart_mixer.h
tar: linux-source-2.6.12/sound/pci/mixart/mixart_mixer.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/nm256/
tar: linux-source-2.6.12/sound/pci/nm256: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/nm256/Makefile
tar: linux-source-2.6.12/sound/pci/nm256/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/nm256/nm256.c
tar: linux-source-2.6.12/sound/pci/nm256/nm256.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/nm256/nm256_coef.c
tar: linux-source-2.6.12/sound/pci/nm256/nm256_coef.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/rme32.c
tar: linux-source-2.6.12/sound/pci/rme32.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/rme96.c
tar: linux-source-2.6.12/sound/pci/rme96.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/rme9652/
tar: linux-source-2.6.12/sound/pci/rme9652: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/rme9652/Makefile
tar: linux-source-2.6.12/sound/pci/rme9652/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/rme9652/hdsp.c
tar: linux-source-2.6.12/sound/pci/rme9652/hdsp.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/rme9652/rme9652.c
tar: linux-source-2.6.12/sound/pci/rme9652/rme9652.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/rme9652/hdspm.c
tar: linux-source-2.6.12/sound/pci/rme9652/hdspm.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/sonicvibes.c
tar: linux-source-2.6.12/sound/pci/sonicvibes.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/trident/
tar: linux-source-2.6.12/sound/pci/trident: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/trident/Makefile
tar: linux-source-2.6.12/sound/pci/trident/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/trident/trident.c
tar: linux-source-2.6.12/sound/pci/trident/trident.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/trident/trident_main.c
tar: linux-source-2.6.12/sound/pci/trident/trident_main.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/trident/trident_memory.c
tar: linux-source-2.6.12/sound/pci/trident/trident_memory.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/trident/trident_synth.c
tar: linux-source-2.6.12/sound/pci/trident/trident_synth.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/via82xx.c
tar: linux-source-2.6.12/sound/pci/via82xx.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/via82xx_modem.c
tar: linux-source-2.6.12/sound/pci/via82xx_modem.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/vx222/
tar: linux-source-2.6.12/sound/pci/vx222: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/vx222/Makefile
tar: linux-source-2.6.12/sound/pci/vx222/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/vx222/vx222.c
tar: linux-source-2.6.12/sound/pci/vx222/vx222.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/vx222/vx222.h
tar: linux-source-2.6.12/sound/pci/vx222/vx222.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/vx222/vx222_ops.c
tar: linux-source-2.6.12/sound/pci/vx222/vx222_ops.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ymfpci/
tar: linux-source-2.6.12/sound/pci/ymfpci: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pci/ymfpci/Makefile
tar: linux-source-2.6.12/sound/pci/ymfpci/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ymfpci/ymfpci.c
tar: linux-source-2.6.12/sound/pci/ymfpci/ymfpci.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ymfpci/ymfpci_image.h
tar: linux-source-2.6.12/sound/pci/ymfpci/ymfpci_image.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pci/ymfpci/ymfpci_main.c
tar: linux-source-2.6.12/sound/pci/ymfpci/ymfpci_main.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/
tar: linux-source-2.6.12/sound/pcmcia: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pcmcia/Kconfig
tar: linux-source-2.6.12/sound/pcmcia/Kconfig: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/Makefile
tar: linux-source-2.6.12/sound/pcmcia/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/pdaudiocf/
tar: linux-source-2.6.12/sound/pcmcia/pdaudiocf: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pcmcia/pdaudiocf/Makefile
tar: linux-source-2.6.12/sound/pcmcia/pdaudiocf/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf.c
tar: linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf.h
tar: linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf_core.c
tar: linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf_core.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf_irq.c
tar: linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf_irq.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf_pcm.c
tar: linux-source-2.6.12/sound/pcmcia/pdaudiocf/pdaudiocf_pcm.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/
tar: linux-source-2.6.12/sound/pcmcia/vx: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/Makefile
tar: linux-source-2.6.12/sound/pcmcia/vx/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/vx_entry.c
tar: linux-source-2.6.12/sound/pcmcia/vx/vx_entry.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/vxp440.c
tar: linux-source-2.6.12/sound/pcmcia/vx/vxp440.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/vxp_mixer.c
tar: linux-source-2.6.12/sound/pcmcia/vx/vxp_mixer.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/vxp_ops.c
tar: linux-source-2.6.12/sound/pcmcia/vx/vxp_ops.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/vxpocket.c
tar: linux-source-2.6.12/sound/pcmcia/vx/vxpocket.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/pcmcia/vx/vxpocket.h
tar: linux-source-2.6.12/sound/pcmcia/vx/vxpocket.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/
tar: linux-source-2.6.12/sound/ppc: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/ppc/Kconfig
tar: linux-source-2.6.12/sound/ppc/Kconfig: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/Makefile
tar: linux-source-2.6.12/sound/ppc/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/awacs.c
tar: linux-source-2.6.12/sound/ppc/awacs.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/awacs.h
tar: linux-source-2.6.12/sound/ppc/awacs.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/beep.c
tar: linux-source-2.6.12/sound/ppc/beep.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/burgundy.c
tar: linux-source-2.6.12/sound/ppc/burgundy.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/burgundy.h
tar: linux-source-2.6.12/sound/ppc/burgundy.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/daca.c
tar: linux-source-2.6.12/sound/ppc/daca.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/keywest.c
tar: linux-source-2.6.12/sound/ppc/keywest.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/pmac.c
tar: linux-source-2.6.12/sound/ppc/pmac.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/pmac.h
tar: linux-source-2.6.12/sound/ppc/pmac.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/powermac.c
tar: linux-source-2.6.12/sound/ppc/powermac.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/toonie.c
tar: linux-source-2.6.12/sound/ppc/toonie.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/tumbler.c
tar: linux-source-2.6.12/sound/ppc/tumbler.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/ppc/tumbler_volume.h
tar: linux-source-2.6.12/sound/ppc/tumbler_volume.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/sound_core.c
tar: linux-source-2.6.12/sound/sound_core.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/sound_firmware.c
tar: linux-source-2.6.12/sound/sound_firmware.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/sparc/
tar: linux-source-2.6.12/sound/sparc: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/sparc/Kconfig
tar: linux-source-2.6.12/sound/sparc/Kconfig: Cannot open: No such file or directory
linux-source-2.6.12/sound/sparc/Makefile
tar: linux-source-2.6.12/sound/sparc/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/sparc/amd7930.c
tar: linux-source-2.6.12/sound/sparc/amd7930.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/sparc/cs4231.c
tar: linux-source-2.6.12/sound/sparc/cs4231.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/
tar: linux-source-2.6.12/sound/synth: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/synth/Makefile
tar: linux-source-2.6.12/sound/synth/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/
tar: linux-source-2.6.12/sound/synth/emux: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/synth/emux/Makefile
tar: linux-source-2.6.12/sound/synth/emux/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux.c
tar: linux-source-2.6.12/sound/synth/emux/emux.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_effect.c
tar: linux-source-2.6.12/sound/synth/emux/emux_effect.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_hwdep.c
tar: linux-source-2.6.12/sound/synth/emux/emux_hwdep.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_nrpn.c
tar: linux-source-2.6.12/sound/synth/emux/emux_nrpn.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_oss.c
tar: linux-source-2.6.12/sound/synth/emux/emux_oss.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_proc.c
tar: linux-source-2.6.12/sound/synth/emux/emux_proc.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_seq.c
tar: linux-source-2.6.12/sound/synth/emux/emux_seq.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_synth.c
tar: linux-source-2.6.12/sound/synth/emux/emux_synth.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/emux_voice.h
tar: linux-source-2.6.12/sound/synth/emux/emux_voice.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/emux/soundfont.c
tar: linux-source-2.6.12/sound/synth/emux/soundfont.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/synth/util_mem.c
tar: linux-source-2.6.12/sound/synth/util_mem.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/
tar: linux-source-2.6.12/sound/usb: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/usb/Kconfig
tar: linux-source-2.6.12/sound/usb/Kconfig: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/Makefile
tar: linux-source-2.6.12/sound/usb/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usbaudio.c
tar: linux-source-2.6.12/sound/usb/usbaudio.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usbaudio.h
tar: linux-source-2.6.12/sound/usb/usbaudio.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usbmidi.c
tar: linux-source-2.6.12/sound/usb/usbmidi.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usbmixer.c
tar: linux-source-2.6.12/sound/usb/usbmixer.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usbmixer_maps.c
tar: linux-source-2.6.12/sound/usb/usbmixer_maps.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usbquirks.h
tar: linux-source-2.6.12/sound/usb/usbquirks.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/
tar: linux-source-2.6.12/sound/usb/usx2y: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/Makefile
tar: linux-source-2.6.12/sound/usb/usx2y/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usX2Yhwdep.c
tar: linux-source-2.6.12/sound/usb/usx2y/usX2Yhwdep.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usX2Yhwdep.h
tar: linux-source-2.6.12/sound/usb/usx2y/usX2Yhwdep.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usbus428ctldefs.h
tar: linux-source-2.6.12/sound/usb/usx2y/usbus428ctldefs.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usbusx2y.c
tar: linux-source-2.6.12/sound/usb/usx2y/usbusx2y.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usbusx2y.h
tar: linux-source-2.6.12/sound/usb/usx2y/usbusx2y.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usbusx2yaudio.c
tar: linux-source-2.6.12/sound/usb/usx2y/usbusx2yaudio.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usx2y.h
tar: linux-source-2.6.12/sound/usb/usx2y/usx2y.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usx2yhwdeppcm.c
tar: linux-source-2.6.12/sound/usb/usx2y/usx2yhwdeppcm.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/usb/usx2y/usx2yhwdeppcm.h
tar: linux-source-2.6.12/sound/usb/usx2y/usx2yhwdeppcm.h: Cannot open: No such file or directory
linux-source-2.6.12/sound/bluetooth/
tar: linux-source-2.6.12/sound/bluetooth: Cannot mkdir: No such file or directory
linux-source-2.6.12/sound/bluetooth/btsco.c
tar: linux-source-2.6.12/sound/bluetooth/btsco.c: Cannot open: No such file or directory
linux-source-2.6.12/sound/bluetooth/Kconfig
tar: linux-source-2.6.12/sound/bluetooth/Kconfig: Cannot open: No such file or directory
linux-source-2.6.12/sound/bluetooth/Makefile
tar: linux-source-2.6.12/sound/bluetooth/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/usr/
tar: linux-source-2.6.12/usr: Cannot mkdir: No such file or directory
linux-source-2.6.12/usr/Makefile
tar: linux-source-2.6.12/usr/Makefile: Cannot open: No such file or directory
linux-source-2.6.12/usr/gen_init_cpio.c
tar: linux-source-2.6.12/usr/gen_init_cpio.c: Cannot open: No such file or directory
linux-source-2.6.12/usr/initramfs_data.S
tar: linux-source-2.6.12/usr/initramfs_data.S: Cannot open: No such file or directory
linux-source-2.6.12/Debian.src.changelog
tar: linux-source-2.6.12/Debian.src.changelog: Cannot open: No such file or directory
linux-source-2.6.12/README.Debian
tar: linux-source-2.6.12/README.Debian: Cannot open: No such file or directory
tar: Error exit delayed from previous errors[/PHP]

---

### Post by t0bb3 on 2006-01-26
[QUOTE=arjay1]dhyams - did pm you re your guide but no response so thought I might post here in case others can help:

I tried to download the two files
pvr_**.zip and pvr_**.inf.zip as instructed, on two different machines on
two different days with a broadband connection.  The BEST connection speed
I ever got was a miserable 3 K/s - with several timeouts and pauses with no
activity at all.  It took 45 minutes to get these two tiddly files!!
 
Anyway
 
Problem 1
When I unzipped pvr_2.0.24.2305.zip it reported that "Inflating hcwcCnv2.ax
- bad crd**d: it should be b***" something or other.  Not sure how serious
this is/was.
 
Problem 2.
This was the killer. The command "./ivtvfwextract.pl
pvr_1.18.21.22254_inf.zip" did not run fully.  It reported "cannot open /
tmp/ivtvex.****/hcwpvrp2.sys - no such file or directory".  I searched on
the internet and found several references to this in suse 9.1 and gentoo
installs.[/QUOTE]

First of all, you shouldn't use PMs for stuff like this. It's better to post here, as you already noted, because someone else might be able to help. It's also good to have it here if someone else in the future experiences the same problems he/she can just read the answers to your question...

Anyway, the problems you are having sounds a lot like a corruped file. I just downloaded the two firmware files myself to see how fast it was. And I got great speeds (60k, which is as fast as it will go on my connection). I would suggest you try downloading the files again. If that doesn't work for you I'll attach the files to a message here on the forums so you can download them from there.

//t0bb3

---

### Post by schucki.be on 2006-01-26
Hi Bill,
Been there. I was ready to trow in the towel.

[PHP]Ok I have tried to install this myth tv stuff now for almost 2 months, This thing is killing me! I am using the guide [http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")
and I dont have NVidia but I have my ATI x330 installed and running but then I enter the commands in step 5.1 this is what I get. it's all cannot open blah, blah,blah stuff. I am almost ready to through the towl in!!!![/PHP]
cut 8<

I found that the install works best on a fresh and clean install of Ubuntu.
Second is that I found out that RTFM was reality for me. :rolleyes: 
Following the instructions very precise is very important !;) 
The guide is the only one I found complete and accurate.
Looking at the error you posted, it seems an access issue to me.
Did you sudo all the commands ? 
When exactly did you get this error?
Did you download the correct source version?

I am not an expert at all, just trying to help out..:p 
If you quit, you miss something wonderfull, so don't give up!

Just give some more info, maybe we just can give you that little push you need !

schucki.be

---

### Post by t0bb3 on 2006-01-27
Quick question here... Does any one know what the default command line arguments for mplayer are in MythTV? I forgot to write them down when I switched to xine...

---

### Post by arjay1 on 2006-01-27
[QUOTE=t0bb3]Anyway, the problems you are having sounds a lot like a corruped file. I just downloaded the two firmware files myself to see how fast it was. And I got great speeds (60k, which is as fast as it will go on my connection). I would suggest you try downloading the files again. If that doesn't work for you I'll attach the files to a message here on the forums so you can download them from there.

//t0bb3[/QUOTE]

Thanks for the prompt - the files turned out to be corrupted.  Very strange about the download speeds - I tried several times over two days on different networks and computers.

Anyway - now got them ok.  Didn't help any as I am just stuck a bit further down the track.:(   Never mind, I'll have a go at sorting things out and will come back if i need help.

Thanks again.

---

### Post by dhyams on 2006-01-27
> **arjay1]dhyams - did pm you re your guide but no response so thought I might post here in case others can help:
[/QUOTE]

Sorry about that!  It was not until I saw this post that I even realized you pm'ed me.  I don't check this forum's PM regularly, and was not notified at my regular email that it had come in.  But, like a previous poster stated, better to post here and get the collective wisdom.

> 
*General issue*
You recommend using "sudo -i" to create a root shell rather than the
laborious use of sudo every time.  I agree and that is a great tip.
However, in Point 2 of your howto you give the example "gedit /etc/apt/
sources.list".  Just to let you know that when i tried this command in a
root shell it says "Cannot open display".  It works fine, though, if you
use a one-off sudo command at the normal user prompt.  Worth checking?
 

Yes, and you're right.  I tend to use vi, which doesn't try to pop a graphical interface.  I will take a look at this and fix.

> 
*Possible install erro*r
When installing appache2 and msql-server, I noticed what seems a possible
error in my install.  I saw the message "Could not determine the server's
fully qualified domain name. Using 192.1268.1.3 for server name."  Is this
OK?  The ip address it talks about is the correct one for the machine,
entered during boot install.  Also, I used the default name of "ubuntu" for
the hostname but this is obviously not what the error above is referring to
 
This should be OK, but I would have to investigate to try to reproduce.  Using the machine ip will identify you just fine.
 
> 
*Obvious major error*
Now for the biggie.  Everything when just smoothly right up until the
section on your page 7 re firmware install.  First, let me say your timings
are optimistic in the extreme!!  I tried to download the two files
pvr_**.zip and pvr_**.inf.zip as instructed, on two different machines on
two different days with a broadband connection.  The BEST connection speed
I ever got was a miserable 3 K/s - with several timeouts and pauses with no
activity at all.  It took 45 minutes to get these two tiddly files!!
 

I didn't have this experience said:**
> 
 
Problem 1
When I unzipped pvr_2.0.24.2305.zip it reported that "Inflating hcwcCnv2.ax
- bad crd**d: it should be b***" something or other.  Not sure how serious
this is/was.

Corrupted file?  Or wrong file?  Check the howto again; it is no longer necessary to download this particular file, as the firmware is fully contained in a file you can now just use wget to grab.
 
> 
Problem 2.
This was the killer. The command "./ivtvfwextract.pl
pvr_1.18.21.22254_inf.zip" did not run fully.  It reported "cannot open /
tmp/ivtvex.****/hcwpvrp2.sys - no such file or directory".  I searched on
the internet and found several references to this in suse 9.1 and gentoo
installs.  

I tried copying the file from the CD that came with the pvr150 -
to /tmp and also other folders of the hard drive where the other related
files were.  The command still would not run (claimed it still could not
find the file).  I eventually found out that this was because of the
content of the perl script.  I found a howto that claimed I could modify
the script to force it to look at the /tmp directory where i had copied the
file hcwpvrp2.sys from the CDRom.

 
I don't know what to say here...this file is not needed by ivtv, so I think we're off the reservation due to earlier problems.

> 
I thought this worked as there appeared to be no errors.  BUT:
 
The next set of instructions in your guide worked ok and the right four files
ended up in the hotplug/firmware folder.  I got a correct listing as per
the last box on your page7.  I entered ivtv in the /etc/modules file and
the alias command in aliases OK.
 
However, when i got to depmode and modprobe ivtv it reported "FATAL ERROR -
no modules".  This was confirmed by dmesg and lsmod.  I tried a reboot but
no good.  I also tried just re-doing your section on compiling the ivtv dirvers etc.  I got the warned of duplicate files but moved those as instructed and then make install again.  Still no modules??



It founds like the drivers installed to the wrong directory (/lib/modules/<kver> instead of /lib/modules/`uname -r`).  Just copy them to the right place if this is the case, using the tip that I give in the HOWTO in that area.

---

### Post by dhyams on 2006-01-27
[QUOTE=t0bb3]Quick question here... Does any one know what the default command line arguments for mplayer are in MythTV? I forgot to write them down when I switched to xine...[/QUOTE]

Hmmm I could have sworn that I wrote these down somewhere, but I can't find it...:( 

dhyams

---

### Post by dhyams on 2006-01-27
Also, I have added a lot of goodies in the last couple of weeks; if you haven't checked back to the HOWTO lately, you might want to.  Here is the revision history:

1.00  Inital revision.  12/24/2005 
1.01 added section 8.13 on making DVD iso's from MythTV recordings and burning them. 12/25/2005 
1.02 Added a couple of soft links in the firmware installation to support PVR-250/350 users. 12/28/2005 
1.03 Added section 8.14 on how to add a new PVR-150 card to an existing setup 1/2/2006 
1.04 Added a small bit to section 6.3, in order to make sure we can eject DVD's when we want to. 1/2/2006 
1.05 Revised text about ivtv drivers being installed in wrong place. This should not happen. 1/4/2006 
1.06 Added links with additional instructions for 64-bit users  1/8/2006 
1.07 Update for ivtv driver release 0.4.2, and added a bit of text that makes sure that ivtv gets installed in the correct place. 1/15/2006 
1.08 Updated comment related to ivtv 0.4.2 with remote resetting in crontab; it looks like this is no longer necessary 1/17/2006 
1.09 Added section 9.5.3, Replacing a drive in an LVM setup with a new (larger) drive 1/22/2006 
1.10 Slight adjustments to the configuration of sources.list, to reflect changes in where MythTV is in the Ubuntu repo. 1/24/2006 
1.11 Updated lircrc-haupgrey file to set the Prev. Ch. button correctly, also remapped # to change input on card, and the yellow button to change tuners while watching TV.  Added section on how to display an on-screen message with the blue button on remote. 1/24/2006 
1.12 Updated nuvexport section; the nuvexport installation is not yet finished, but quite capable. 1/24/2006 
1.13 Enable xine (and by extension, MythTV) to play DivX, AVI, WMV, etc. 1/27/2006

---

### Post by arjay1 on 2006-01-28
dhyams
Thanks for the response to my problems.  You are right - it was all caused by corrupted downloads of the pvr...zip file/s.

Your timings turned out to be OK for that section as i got good download speeds this time - very strange as i tried several times over two days on two different networks, but there you are.  

I agree you should keep the timings - they do just give some indication of how long one can expect.  As you say in your intro - there are YOUR results!!  The only problem is when you hit a snag.

Keep up the good work.

Actually, I am stuck further down the track in your howto but will come back here if I can't figure it out for myself.  

I have only been trying 6 hours a day for over a week to get mythtv working - so am nowhere near the pain barrier for linux:mrgreen:

RJ

---

### Post by t0bb3 on 2006-01-30
[QUOTE=t0bb3]Quick question here... Does any one know what the default command line arguments for mplayer are in MythTV? I forgot to write them down when I switched to xine...[/QUOTE]
I've found this out now :)
```
mplayer -fs -zoom -quiet -vo xv %s
```

---

### Post by arjay1 on 2006-02-01
dhyams

Thanks, again, for the howto - I admit that after failing with your guide,  I did slope off and try the quietglow version and also knoppmyth but I have got further with yours than anyone else's so Power to you:p 

Now: - I have got to the stage where I have a fully operational myth installation (in the sense that backend and frontend load OK and I can do everything except see a tv picture).  I have the classic situation  that a lot of posters have - a black screen with tiny red and green dots and a few thin multi-coloured lines flashing by.  Doesn't look at all like the old fashion snowy screen which was just back and white where there is obviously no signal.  This looks like a screwed up signal (I think).

OK - I am running a twin PIII CPU PC with 2.6.12-10-686-smp and have a European pvr-150 installed.  I have a scart from the sky box to svideo and audio on the pvr150 - hope that is correct?  The graphics card is a matrox g400 dualhead with installed matrox drivers.  

I am trying to get it set up to accept a signal from a sky digital box.  I know that this is not your area ( I have set up for PAL etc).  However, I have followed the mythtv guide for sky without success.  This is probably because the problem is earlier in the set up:

What I wanted to ask you is that early in your guide you suggest trying *cat /dev/video0 > tmp/test.mpg* and playing the file back with mplayer.  Well I get just the same "signal" as described above.  I presume that this means the ivtv drivers or the setup thereabouts is not correct and, it seems to me, therefore there is not much point in hoping that I will get a clear picture further on in the installation?

I have tried your line using the ivtv-tune facility but this doesn't help - presumably because it is expecting us-type channels?  For example, one of the channels I tried reported "not a recognised us-cable channel". The ivtv bit of dmesg looks fine but I notice that this setup's result shows the tveeprom (?) as tuner = 55, as opposed to the the value of 3 or 4 that other examples come up with.  I believe it is possible to change this value in one of the ivtv files but can't remember which one.  Is this worth trying?

dmesg segment:

[4294694.094000] ivtv:  ==================== START INIT IVTV =================== =
[4294694.095000] ivtv:  version 0.4.2 (tagged release) loading
[4294694.095000] ivtv:  Linux version: 2.6.12-10-686-smp SMP 686 gcc-3.4
[4294694.095000] ivtv:  In case of problems please include the debug info betwee n
[4294694.095000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294694.095000] ivtv:  any module options, when mailing the ivtv-users mailingl ist.
[4294694.099000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294694.189000] tveeprom: ivtv version
[4294694.189000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294694.270000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 0
[4294694.270000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294694.491000] cx25840 0-0044: ivtv driver
[4294694.491000] cx25840 0-0044: cx25842-23 found @ 0x88 (ivtv i2c driver #0)
[4294697.416000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294697.455000] wm8775 0-001b: ivtv driver
[4294697.455000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294697.462000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294698.343000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294698.553000] ivtv0: Encoder revision: 0x02050032
[4294698.554000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4294698.557000] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (20 48KB total)
[4294698.559000] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (204 8KB total)
[4294698.561000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4294698.563000] tuner: type set to 55 (TCL 2002MB) by ivtv i2c driver #0
[4294698.752000] ivtv0: Initialized WinTV PVR 150, card #0
[4294698.752000] ivtv:  ====================  END INIT IVTV  =================== 

Would you, or any of the wizz-folks who participate in this post know how to play around with the incoming signal in a UK setup to get a picture using cat /dev/video0?  Or anything else for that matter that might help.

I am so close now - only taken me two weeks of 6 hours a day:oops:

TIA RJ

BTW - is it ever going to be possible for the card/software to automatically scan and report available signals?  This would seem to me to be an obvious first priority.  Actually, I seem to remember a box with that choice in one of the setup screens but IIRC I could not access it?

---

### Post by t0bb3 on 2006-02-01
You can scan for digital channels (DVB). I've heard some rumors about scanning for analog channels in the next myth release, but they are just rumors, so I wouldn't hold my breath...

---

### Post by mikedtemple on 2006-02-01
I was successful using the following lines to define my tuner type in /etc/modprobe.d/ivtv (that's where I keep all of my ivtv related configs)

This is what the file looks like.

```
alias char-major-81 videodev
alias char-major-81-0 ivtv

options ivtv ivtv_debug=0 ivtv_std=1 tda9887=0

# Insert a suitable tuner type here!
options tuner type=47 #MY PVR-350 Tuner Type
options msp3400 once=1

```

You can put your tuner type as an option in the /etc/modprobe.d/aliases file too (I think).

Hope this helps!

---

### Post by arjay1 on 2006-02-01
Thanks for the tips guys - I'll give the ivtv settings a try.  As to the scanning function - does that work here in Europe?  I thought that the function was the equivalent of "greyed out" - I could not get the setup routine to allow me to select  it - I would be scanning for digital signals.

RJ

---

### Post by Micro Rotors on 2006-02-01
I keep getting an error in the front end saying that the IP address is not right and the back end is not connecting. I have set everything to 127.0.0.1 and I still get that error. 

Any clues?

Despite my wanting to give up on this mythtv stuff some of you have been telling me to keep trying, but this mythtv is really a myth at my end. :-k

---

### Post by Lem on 2006-02-02
Has anyone had any success with MythTV and DVB-T cards? Was thinking of dual-booting my Ubuntu box with Windows MCE, but an all-linux box would be preferable.

---

### Post by schucki.be on 2006-02-02
Bill,
More details please !
Can't help without them.

---

### Post by t0bb3 on 2006-02-02
[QUOTE=arjay1]Thanks for the tips guys - I'll give the ivtv settings a try.  As to the scanning function - does that work here in Europe?  I thought that the function was the equivalent of "greyed out" - I could not get the setup routine to allow me to select  it - I would be scanning for digital signals.

RJ[/QUOTE][quote=lem]Has anyone had any success with MythTV and DVB-T cards? Was thinking of dual-booting my Ubuntu box with Windows MCE, but an all-linux box would be preferable.[/quote]

Both of you guys, take a look here: [http://www.mythtv.org/wiki/index.php/Configuring_DVB-T_in_the_UK](http://www.mythtv.org/wiki/index.php/Configuring_DVB-T_in_the_UK)

---

### Post by DDM on 2006-02-02
Great Howto: I've tried a few and this is the only one that works. Now that it's setup, I can now decide if I'm willing to go out and buy a tv-in card.

However, I'm not able to see any thumbnails when I browse my videos. I did manage to get one working using a movie's IMDB number, but that's it. Any ideas? 

Also, how do I allow my regular everyday user to load up mythtv so I don't have to switch users in order to start it up?

---

### Post by arjay1 on 2006-02-02
t0bb3

Thanks for the link.  Not sure that I understand it at all, but first, I AM using Myth .18 and the 2.6.12 kernel.  It sounds if I this link is right for me then?  But what is a dvb-t card?  I presume dvb stands for digital video broadcasting, but what is the "-t"?  I have a hauppage pvr150 - is this equivalent and, if so, does this mean the info in the link applies to me?  I stand by my previous post - that the autoscan feature in myth setup is "greyed out" when i try to use it.  Also, I am trying to get signals from sky digital - this link doesn't seem to refer to that at all?  I am not interested in Freeview channels ...

We still need a really good step-by-step guide to getting sky digital up and running.  The ones I have seen so far seem poor and/or incomplete (not that i could do any better you understand):oops:.

---

### Post by arjay1 on 2006-02-02
dhyams - congrats to you and those who have supported the development of your howto.  Following it, I finally managed to get a running version of mythtv.  

After 2 weeks of blood sweat and tears it turns out my problem in not getting a picture (see mine and other posts above) was the cable connection.  I have found that if I stick a plain coax cable between the sky digital settop box and the pvr150 card - I immediately get a viewable picture.  Previously i was using a very expensive scart to svideo cable - which produced absolutely zilch. Can't believe it took me so long to try this. :( However, surely the picture from a proper gold scart cable should be superior to the rather fuzzy picture i get with a plain coax?  

Can anyone help me with how to setup using the scart cable?  Does the coax just "bypass" the mythtv setup  instructions?  The reason i ask is I have tried every combination I can think of of tuner and svideo, and every default channel/starting channel setting I have seen elsewhere.  As soon as  stick the coax in, up comes a picture??

Thanks to all of you who have helped me get this far....:cool:

---

### Post by arjay1 on 2006-02-03
mikedtemple

Thanks for the tip re additions to your modprobe.d/ivtv file.  However, I don't have any such file.  Should I have one or did you create this yourself?  If so is there any other content?

I have tried entering your settings in the aliases file but it didn't make any difference:???: 


I have now got a picture with a straight coax cable (see above post).  It is not too bad but not watchable as a long term solution.  IIf you see the picture next to the same display on the TV it is embarassing.  I need to have the card working with the scart-to-svideo lead.

Hopefully someone can give me a lead on this hee hee

---

### Post by mikedtemple on 2006-02-03
[QUOTE=arjay1]mikedtemple

Thanks for the tip re additions to your modprobe.d/ivtv file.  However, I don't have any such file.  Should I have one or did you create this yourself?  If so is there any other content?

I have tried entering your settings in the aliases file but it didn't make any difference:???: 


I have now got a picture with a straight coax cable (see above post).  It is not too bad but not watchable as a long term solution.  IIf you see the picture next to the same display on the TV it is embarassing.  I need to have the card working with the scart-to-svideo lead.

Hopefully someone can give me a lead on this hee hee[/QUOTE]


I made the file myself.  I did an ssh into my box, because I was having the hardest time getting the TV out on the PVR 350 working.  While I was sshed in, I created that file, so that way my /etc/mdoprobe.d/ailases file was a lot less cluttered.  You can do that with any item you modprobe.  For example instead of setting my setting for my 80.211g in the /etc/modprobe.d/aliases file, I use /etc/modprobe.d/ndiswrapper.  Therefore my aliases file only contains what drivers I'm actually installing and the other file contains the settings.  It's just a cleaner setup, I think, but I'm sure there's other ways to go.  Just make sure you define your tuner type somewhere.


Strange on the SCART cable vs. the coax.  My myth setup is for the bedroom secondary to my Comcast DVR downstairs, so I never worried about the picture too much.  I actually have a gold plated SVIDEO to composite connection from Radio Shack connecting my TV to the myth box.  The only thing I could think of with your situtation is that when I originally set it up, I had to set my NVIDIA settings to COMPOSITE and not S-VIDEO, due to a Black and white problem, as well as put a rubber spacer on the SVIDEO side of my cabling, becuase gold conducts electricity and the pic was ugly becuase the cable was grounding to the aluminum on the case.

If you stick the coax in, and you get a pic, then it sounds like IVTV is configured correctly.

I feel your pain man, I built the myth box for my wife for Christmas and I worked on it almose every day from November to Christmas Eve.  Hang in there...

---

### Post by t0bb3 on 2006-02-03
[QUOTE=Chuffinora]The only issue I still have, sounds the same as NeoLev.  Displaying tv my picture is offset down and to right a few pixels, and I have a blue line at left and top of screen????  It is only in TV and playback, not visible in the Gnome GUI,  thus I suspect something in Myth.

In setup, playback, tv settings, the 2nd to last screen gives overscan and picture displacement.  Nothing here corrects it and I am not sure setting anything in picture displacement is actually doing anything.[/QUOTE]

I finaly took the time to try to get live tv working and also noticed this problem. Searching the MythTV mailing lists archive makes it pretty obvious that this is a common problem, and the solution seems to be to run```
xvattr -a XV_COLORKEY -v 0
```I haven't had the time to try it myself yet though...

---

### Post by arjay1 on 2006-02-03
mikedtemple

Thanks for clearing the issue up about aliases v ivtv.

As to the cable issue, unfortunately, my tv does not offer any out sockets/plugs other than audio out. Same goes for the sky box - it only has scart sockets and two coax outs available. 

What I have at the moment is a scart lead from the sky digital settop box to the TV and a scart-svideo from the sky box to the computer.  

EDIT: Deleted issue re /dev/video0 - problem with aliases file rectified.

RJ

---

### Post by bradfordrb on 2006-02-04
[I]From the earlier post:


[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)[/I]

I've been doing a lot of reading/digging as this is my first linux experience (tried other distros and live cds.. but this is the first time I've gone all the way through to dedicating a box).  I'm intending to build this into an htpc but am having trouble getting the IVTV drivers to compile.

I've followed several guides - the one listed above, abarbaccia's, .....
I get to the same point and get the same error:

[COLOR="Blue"]bradfordrb@htpclinux:/usr/src/ivtv-0.4.2$ ls
ChangeLog      COPYING  driver    misc    test   v4l-cx2341x-init.mpg
ChangeLog.old  doc      Makefile  README  utils
bradfordrb@htpclinux:/usr/src/ivtv-0.4.2$ sudo make
make -C driver all
make[1]: Entering directory `/usr/src/ivtv-0.4.2/driver'
make -C /lib/modules/2.6.12-10-386/build M=/usr/src/ivtv-0.4.2/driver modules
make[2]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/ivtv-0.4.2/driver'
make: *** [all] Error 2
[/COLOR]

- I have the /usr/src/linux link established
- The linux headers and source for 2.6.12-10-386 are in the /usr/src directory
- The Makefile in the linux source dir was edited to show the -10-386
- gcc 3.4 is installed
- build essentials is installed

I have compiled and gotten the GNOME sensors applet installed and working with the lm_sensors but can't seem to figure this one out.  Any help will be appreciated greatly!

Thanks,

---

### Post by frkstein on 2006-02-04
dhyams,

I am having trouble getting the firmware to load. After I depmod and modprobe ivtv I get this in dmesg:

[   53.850695] ivtv:  ==================== START INIT IVTV ====================
[   53.850701] ivtv:  version 0.4.2 (tagged release) loading
[   53.850704] ivtv:  Linux version: 2.6.12-10-386 386 gcc-3.4
[   53.850707] ivtv:  In case of problems please include the debug info between
[   53.850709] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   53.850712] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   53.852076] ivtv0: Autodetected WinTV PVR 250 card (cx23416 based)
[   53.852145] PCI: Found IRQ 11 for device 0000:00:0d.0
[   53.852156] PCI: Sharing IRQ 11 with 0000:00:0a.0
[   53.852171] PCI: Sharing IRQ 11 with 0000:01:00.0
[   53.852182] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   53.861586] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[   53.894019] tveeprom: Hauppauge: model = 32062, rev = C182, serial# = 7913781
[   53.894025] tveeprom: tuner = LG TAPC H791F (idx = 82, type = 39)
[   53.894029] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[   53.894032] tveeprom: audio_processor = MSP3445 (type = 12)
[   53.919596] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[   53.920926] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   54.070974] saa7115 0-0021: ivtv driver
[   54.070980] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[   54.174592] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[   54.194815] msp34xx: init: chip=MSP3445G-B8 +nicam +simple +simpler +radio mode=simpler
[   54.198902] ivtv0: i2c attach to card #0 ok [client=MSP3445G-B8, addr=40]
[   54.198933] msp34xxg: daemon started
[   54.329360] logips2pp: Detected unknown logitech mouse model 56
[   54.379830] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[   54.610287] ts: Compaq touchscreen protocol output
[   54.910513] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[   54.910520] ivtv0: did you put the firmware in the hotplug firmware directory?
[   54.910524] ivtv0 warning: failed loading encoder firmware
[   54.910528] ivtv0 warning: Error loading firmware -3!
[   54.910532] ivtv0: Error -3 initializing firmware.
[   54.952602] ivtv0: Error -12 on initialization
[   54.952613] ivtv: probe of 0000:00:0d.0 failed with error -12
[   54.952624] ivtv:  ====================  END INIT IVTV  ====================

this is what I get when I execute ls -ltra /usr/lib/hotplug/firmware:

total 1052
drwxr-xr-x  3 root root     72 2005-05-12 13:56 ..
-rw-r--r--  1 root root 262144 2006-02-04 14:13 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-02-04 14:13 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 2006-02-04 14:17 v4l-cx25840.fw
-r--r--r--  1 root root 376836 2006-02-04 14:17 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2006-02-04 14:19 v4l-cx2341x-init.mpg
lrwxrwxrwx  1 root root     41 2006-02-04 14:20 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
drwxr-xr-x  2 root root    264 2006-02-04 14:45 .

Can you offer any suggestions to what I could be doing wrong?

**Solved - partially (shrugs)**
I am not sure what I did, but I was able to get the firmware to load. My only problem now is that I am not getting any audio. Does anyone have any ideas? I noticed the for PVR150 cards that cx25840 is mentioned in the dmesg. I have a PVR250. should I also be seeing cx25840 being loaded. I believe that is audio firmware.

**Solved - Totally**
I found that the PVR250 uses msp3400 for the sound firmware. Not sure why the version included was not enabling sound, but I had an older version of msp3400.ko from when I had mythtv running under Hoary. I just copied that version into /lib/modules/2.6.12-10/... and I had sound back.

---

### Post by schucki.be on 2006-02-06
Hi guys,
Have MythTV working on backend and second frontend.
Just replaced my videocard (on backend) for a Nvidia FX5200.
Installed the drivers following the how-to.
It's working on my monitor.
I see the Nvidia logo on both screens and can move my mouse to my tv.

Have to solve the B&W issue, but that's not the point.
Do I have to make changes in my existing Mythtv setup anywhere to get mythtv working on my TV-out instead of my monitor?

Thnx,

schucki.be

---

### Post by schucki.be on 2006-02-07
Update on my last post:

[QUOTE=schucki.be]Hi guys,
Have to solve the B&W issue, but that's not the point.

Do I have to make changes in my existing Mythtv setup anywhere to get mythtv working on my TV-out instead of my monitor?

[/QUOTE]
Black and White only on TV :SOLVED SEE : [http://camp0s.altervista.org/sVideo/sVideo.htm](http://camp0s.altervista.org/sVideo/sVideo.htm).
Just a small tweek on the cable and voila, color!

Run Mythtv on TV-screen: SOLVED: Was still in Windows mode [-( ... 
Just open Mythtv on the second desktop, the TV. Great!

Thnx,
Schucki.be

---

### Post by mattisf on 2006-02-07
Just wanted to say a big THANKS to dhyams for his brilliant howto! I bought a hauppauge 150 largely because of this howto, and I got it working like a charm. My setup is slightly different (I'll be using it on my regular computer, not on a machine that's only a media center) but whatever little issues this creates I could work around easily. 

AGAIN, awesome work, big thanks! \\:D/ 

Cheers,

Mattis

---

### Post by schucki.be on 2006-02-07
Hello there,
I would like to view my photo's and listen to my music on my frontend.
Does anyone know how to set this up ?

And is it possible to listen to the music via mythweb?
I only get a sort of search screen when I select a song in the list...

And what about viewing the recordings via mythweb?

Last issue for now :-D : I seem to lose connection or something when I watch recordings on my laptop frontend (HP Compaq nx6xx) using wifi.
The moment of loss is random. Sometimes I can watch for a half an hour, sometimes just a few minutes.

Anybody?

Thnx

schucki.be

---

### Post by t0bb3 on 2006-02-07
[QUOTE=arjay1]t0bb3

Thanks for the link.  Not sure that I understand it at all, but first, I AM using Myth .18 and the 2.6.12 kernel.  It sounds if I this link is right for me then?  But what is a dvb-t card?  I presume dvb stands for digital video broadcasting, but what is the "-t"?  I have a hauppage pvr150 - is this equivalent and, if so, does this mean the info in the link applies to me?[/QUOTE]
Sorry I didn't reply earlier, I must have missed this post :(

DVB stands for Digital Video Broadcasting (just like you said). The -t means Terrestrial (i.e. not cable or satelite). The pvr150 is not a DVB-t card, it's just a regular analogue card. You need the Hauppague Nova-t card if you want DVB-t capabilities with a Hauppauge card.

---

### Post by triplep on 2006-02-07
Thanks for the great HOWTO! I cheated a bit and ran some if it in a bash shell script cause I can be a bit lazy, but it's clear and well written, making it easy to confidentily script it all.

Just a quick note for amd64 users :

If you use: --cpu=x86_64 --tune=generic  the compiler will throw them out, and not optimize, it will still work, but just not optimize the binary. I ran 'script' before starting the compile to capture events to discover this

Those flags weren't shown in the gcc manpage, however, there were other options that would replace them nicely : -march-x86_64 -mtune=x86_64

---

### Post by minirx7 on 2006-02-07
Does anybody know how to get the TV out on the PVR350 to work?

I cant figure it out.  It worked well with Knoppmyth but doesnt work.

Thanks.

---

### Post by mattisf on 2006-02-08
Woops. Seems I was cheering a bit too early. I didn't have an antenna yesterday, just a long cable plugged into the card, and it was picking things up ... I assumed that once I had an antenna things would be hunky-dory. 

However, it's not. I get an incredibly static image ... I can make people out among the noise, but that's it. I can't tell what they're doing, much less what show I'm watching.

Poking around with ivtvctl, I found that my card was set to use PAL. I changed it to NTSC, and then I got sound. The picture might have gotten marginally better; not sure.

Does anyone have any clues - any suggestions for how to improve the picture? I mean drastic improvements ... it looks almost like I don't have an antenna at all. :-/ 

Thanks,

Mattis

PS. I saw someone having problems with -vo xv on mplayer. My current machine, with ATI drivers, doesn't seem to support xv for video out. I use -vo gl2 instead - openGL.  'mplayer -vo help' will give you a list of supported video outs. Try different ones and see what happens, you'll see which one works best for you.

EDIT: 

This is resolved now. For some reason, my card per default uses the wrong number of scanlines compared to NTSC. And it's set to PAL per default ... there was quite a bit of tweaking with ivtcctl before I got it straight. In the end, these were the magic commands:

# First, make sure we have NTSC.

sudo ivtvctl --set-standard=0x003000

# framerate 0 means setting zero, that is, 30fps = NTSC

sudo ivtvctl -c framerate=0

# Then, set the aspect ratio.

sudo ivtvctl -c aspect=2

# Third, the number of lines on the screen.

sudo ivtvctl --set-format=width=720,height=460

Cheers, and good luck,

Mattis

---

### Post by arjay1 on 2006-02-08
t0bb3

Thanks for the explantion about DVB.

Just for interest - after battling for two weeks to get mythtv working it turned out that the problem was with my brand new $40 gold scart/svideo cable.  Only found out by chance when I plugged an ordinary antenna in!!  Let that be a lesson to me and anyone else.  Try the most simple solution first.

RJ

---

### Post by Micro Rotors on 2006-02-09
OK I am almost there, I reinstalled and I got to see some TV, But I can not get the > mythfillmydatabase command to work. Also I get this print out in the terminal when I start up. I only have the internet when I am at work so I need to get the guide from labs.zap2it.com when I am at work so I can record when I am at home.

[PHP]sh-3.00$ mythbackend & mythfrontend
[1] 18594
2006-02-09 13:00:27.160 New DB connection, total: 1
Starting up as the master server.
2006-02-09 13:00:27.247 New DB connection, total: 2
2006-02-09 13:00:27.309 New DB scheduler connection
2006-02-09 13:00:27.381 mythbackend version: 0.18.1.20050510-1 www.mythtv.org
2006-02-09 13:00:27.381 Enabled verbose msgs : important general
QServerSocket: failed to bind or listen to the socket
Failed to bind port: 6543
Mutex destroy failure: Device or resource busy
2006-02-09 13:00:27.660 New DB connection, total: 1
Total desktop width=1280, height=1024, numscreens=1
2006-02-09 13:00:27.684 Using screen 0, 1280x1024 at 0,0
2006-02-09 13:00:27.699 mythfrontend version: 0.18.1.20050510-1 www.mythtv.org
2006-02-09 13:00:27.699 Enabled verbose msgs : important general
2006-02-09 13:00:27.877 Switching to square mode (blue)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-02-09 13:00:28.380 Joystick disabled.
2006-02-09 13:00:28.384 Registering Internal as a media playback plugin.
2006-02-09 13:00:28.391 Registering MythDVD DVD Media Handler as a media handler2006-02-09 13:00:28.462 Registering MythMusic Media Handler as a media handler
2006-02-09 13:00:33.510 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-02-09 13:00:33.516 Using protocol version 15
[1]+  Done(6)                 mythbackend
sh-3.00$
[/PHP]

---

### Post by greyhound4334 on 2006-02-09
```
 mythfillmydatabase
```

Oops.  That's mythfilldatabase (no "my") :) 

For the second problem... hmmm... why are you starting things with

```
mythbackend & mythfrontend 
```?

I think this parses to 

mythbackend & (start mythbackend in background)
and
mythfrontend (start mythfrontend in foreground).

Which is OK, but I'm just slightly suspicious, from the error message, that you have an old mythbackend hanging around.  Try ```
ps aux | grep mythbackend
``` and see if there's one hanging around.  If so, you can either use it (it's a backend "daemon" and can just stay running), or kill it and restart a new one if you've made changes that you want to take effect.

HTH,
john

---

### Post by Micro Rotors on 2006-02-10
Hello greyhound4334;

Thanks for your help. I guess adding my to the mythfilldatabase will screw that one up! :cry: 

Any how I ran it correctly and started the backend as you said and here is the output.```
sh-3.00$ mythfilldatabase
2006-02-10 07:54:17.306 New DB connection, total: 1
2006-02-10 07:54:17.322 New DB connection, total: 2
Refreshing Tomorrow's data
2006-02-10 07:54:17.341 New DB DataDirect connection
Retrieving datadirect data...
Grabbing data for Fri Feb 10 2006 offset 1
From : Sat Feb 11 08:00:00 2006 To : Sun Feb 12 08:00:00 2006 (UTC)
--07:54:17--  http://datadirect.webservices.zap2it.com/tvlistings/xtvdService
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]

    [       <=>                           ] 167,086       57.03K/s

07:54:21 (56.94 KB/s) - `-' saved [167086]

Your subscription expires on 05/06/2006 08:54:54 PM
Grab complete.  Actual data from Sat Feb 11 08:00:00 2006 to Sun Feb 12 08:00:00 2006 (UTC)
Clearing data for source...
Clearing from Sat Feb 11 00:00:00 2006 to Sun Feb 12 00:00:00 2006 (localtime)
2006-02-10 07:54:29.818 New DB connection, total: 3
Data for source cleared...
Main temp tables populated.  Updating myth channels...
Updating icons for sourceid: 1
Channels updated..  Updating programs...
Data is already present for Fri Feb 10 2006, skipping
Data is already present for Sun Feb 12 2006, skipping
Data is already present for Mon Feb 13 2006, skipping
Data is already present for Tue Feb 14 2006, skipping
Data is already present for Wed Feb 15 2006, skipping
Data is already present for Thu Feb 16 2006, skipping
Data is already present for Fri Feb 17 2006, skipping
Data is already present for Sat Feb 18 2006, skipping
Data is already present for Sun Feb 19 2006, skipping
Data is already present for Mon Feb 20 2006, skipping
Data is already present for Tue Feb 21 2006, skipping
Data is already present for Wed Feb 22 2006, skipping
Data is already present for Thu Feb 23 2006, skipping
Adjusting program database end times...
0 replacements made.
Marking repeats...found 0
Unmarking repeats from grabber that fall within our new episode window...found 02006-02-10 07:54:30.054 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-02-10 07:54:30.079 Using protocol version 15
sh-3.00$ mythbackend &
[1] 9165
sh-3.00$ 2006-02-10 07:55:19.045 New DB connection, total: 1
Starting up as the master server.
2006-02-10 07:55:19.100 New DB connection, total: 2
2006-02-10 07:55:19.135 New DB scheduler connection
2006-02-10 07:55:19.161 mythbackend version: 0.18.1.20050510-1 www.mythtv.org
2006-02-10 07:55:19.161 Enabled verbose msgs : important general
QServerSocket: failed to bind or listen to the socket
Failed to bind port: 6543

```

It is still failing to connect at the 6543 port. :-k 

As far as having an old back end hanging around, I am not sure. I ran the ps aux | grep mythbackendcommand and this is what I got;```
sh-3.00$ ps aux | grep mythbackend
mythtv    8396  0.0  0.7 131988 16160 ?        Ssl  22:40   0:00 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
sh-3.00$
```

What that means ,,,, I have no idea:confused: :confused: 
Thanks for you help, I have been trying this for 2 months now and I am almost there, I can feel it! :mrgreen:

---

### Post by arjay1 on 2006-02-10
micro rotors

Hi - only been trying for two months?  You don't deserve to be there yet - some of have been trying on and off for longer than that:-D 

Anyway - I'm a complete novice at this stuff so take this with a pinch of salt but I saw in a post somewhere that the "failed to bind to 6543" message just means that you already have mythbackend running. It doesn't like you trying to start a second instance of mythback end - that's all. As I say, this might not be correct but - have you then tried to run mythfrontend or mythtv-setup at this point?  If they run OK you should be good to go? 

RJ

---

### Post by greyhound4334 on 2006-02-10
Yes, you're probably getting close!

OK, so it looks like you've got a backend already running.  The ps command shows running processes.  The "| grep mythbackend" part says send the output of ps aux to grep, which then proceeds to search out and display only lines that ocntain the word mythbackend.  (Try it both ways --- just run ps aux by itself, and you'll see a whole bunch more processes).

The output from this shows that you have a mythbackend already running.  From the looks of it, you're starting it up automatically at boot.  You probably have a file like /etc/init.d/mythbackend which does this.  

Couple of possibilities.  You can just connect to this already running backend, or, if you have a reason to need to restart it (which is usually rare; usually only needed if you're making changes to your capture cards or something like that through mythtv-setup) then you can do so by running (as root, or with the sudo command) 
```

/etc/init.d/mythbackend restart
```

In general, before you start a "daemon" (a process that continues running by itself in the "background"), you should check to see if one is already running (with something like the ps command above).

OK, once you've got a single mythbackend running, you should be almost there.  Just run mythfrontend and you should be good to go.

I'm not sure about the messages you got from mythfilldatabase (Data is already present).  They probably mean you've successfully run mythfilldatabase before, but they *could* indicate a problem with your setup.  When you get the frontend running, you'll quickly see whether you've got the right channel line up and program data in place.

Good luck.  Stick with it, it's worth it.

---

### Post by Micro Rotors on 2006-02-10
Ok I just ran mythfrontend and this is what I get. ```
sh-3.00$ mythfrontend
2006-02-10 13:20:30.236 New DB connection, total: 1
Total desktop width=1280, height=1024, numscreens=1
2006-02-10 13:20:30.261 Using screen 0, 1280x1024 at 0,0
2006-02-10 13:20:30.276 mythfrontend version: 0.18.1.20050510-1 www.mythtv.org
2006-02-10 13:20:30.276 Enabled verbose msgs : important general
2006-02-10 13:20:30.447 Switching to square mode (blue)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-02-10 13:20:31.407 Joystick disabled.
2006-02-10 13:20:31.442 Registering Internal as a media playback plugin.
2006-02-10 13:20:31.453 Registering MythDVD DVD Media Handler as a media handler2006-02-10 13:20:31.555 Registering MythMusic Media Handler as a media handler
2006-02-10 13:20:36.754 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-02-10 13:20:36.761 Using protocol version 15
sh-3.00$

```

Also when the front end starts up I went to the system info screen and it says that:
> 
mythfilldatabase ran dut did n....... 
Theres no guide data available
Have you run mythfilldatabase ?
WARNING... is mythfilldatabase running? 


Go figure Agrrrrrrrrr!!!!

---

### Post by greyhound4334 on 2006-02-10
OK, I think you're close.  Mythtv is a bit finicky...

So I thought your last mythfilldatabase looked a little strange.

Did you sign up for zap2it?

Try this.  Shut down mythfrontend and mythbackend (exit from the frontend; the backend can be stopped with sudo /etc/init.d/mythtv-backend stop).

Run mythtv-setup again.  In the sources page (I think that's the one), make sure your zap2it account info is correct.  Then click on retrieve lineup.  Then exit from mythtv-setup and try mythfilldatabase again.  Hopefully you won't get all those messages about Data already exists.

If this works, start up the backend and then the frontend again, and see if you can watch tv.

cheers,
john

---

### Post by Micro Rotors on 2006-02-10
Ok I will try it. I can already watch tv, I just dont have any listings, or change the channels. I am signed up at labs.zap2it.com and the info is correct. 

> Run mythtv-setup again. In the sources page (I think that's the one), make sure your zap2it account info is correct. Then click on retrieve lineup. Then exit from mythtv-setup and try mythfilldatabase again. Hopefully you won't get all those messages about Data already exists.


Are you talking about the install setup, or the setup in the front end?

Thanks John, your a lifesaver!!!!!!!!!!!!!  ;)

---

### Post by greyhound4334 on 2006-02-10
mythtv-setup is the setup program for the backend (where the capture card and related info is kept, and which connects to the database).

run the program (type mythtv-setup at the command line), then run through the pages of the setup until you get to the part about your xmltv listings (zap2it), then tell it to get the listings (I forget what the choice is labeled, but it should be obvious).

then don't forget to run mythfilldatabase again.

If that doesn't do it, you might try signing up for a new zap2it account, then you can change the settings in mythtv-setup to the new account.  Successfully doing this *should* reset your channel & program tables in the databae, and allow mythfilldatabase to run correctly.

good luck!

---

### Post by munralamun on 2006-02-12
Hi all!

That's to all who have put in the hard work explaining the processes... I think I am close (but I'm stuck!).

I installed myth and proceeded to be able to start the front end.

But I'm concerned the backend is not initializing well.

The front end constantly pushed a message to check the backend setup for the master backend.

If I try to start myth from the terminal window of sh when logged in as mythtv, I get command not found messages (I can start as the primary administrator in my other account).

If I try to start myth in my main account using sudo /etc/init.d/mythtv-backend start

I get this message:

> Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

Any ideas what might be going on?

in MySQL, I granted mythtv user all priviledges, and the password is set up right in both front end and back end. I also tried switching to the actual IP in the setups for the box vs. localhost.

If I execute sh-3.00$ /etc/init.d/mythtv-backend start as the mythtv user, this is what I get when logged in from that account:

> Starting MythTV server: mythbackendstart-stop-daemon: Unable to set initgroups() with gid 118 (Operation not permitted)

Thanks for any tips I'm feeling close (the fact that it started at all!), but frustrated...:???:

---

### Post by [Yatta] on 2006-02-12
I'm following Hyams HowTo....

i'm trying to compile MythTV/Ubuntu 64-bit Specific BUT i've come across some nags.... 
I modified the rules file to :
```
--cpu=x86_64 --tune=generic --enable-mmx \ 
```
btw i'm using  a Sempron 2800+ AMD64

when i do:
```
sudo dpkg-buildpackage -rfakeroot -b
```
I get these error messages:
```
enigma@blacktower:/opt/src/mythtv/mythtv-0.18.1$ sudo dpkg-buildpackage -rfakeroot -b
dpkg-buildpackage: source package is mythtv
dpkg-buildpackage: source version is 0.18.1-5
dpkg-buildpackage: source changed by Matt Zimmerman <mdz@ubuntu.com>
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
debian/rules:178: warning: overriding commands for target `config.mak'
debian/rules:20: warning: ignoring old commands for target `config.mak'
debian/rules:203: warning: overriding commands for target `build-arch-stamp'
------- snip -------
debian/rules:128: warning: ignoring old commands for target `binary-arch'
dh_testdir
dh_testdir: debian/control has a duplicate entry for mythtv
make: *** [clean] Error 1
enigma@blacktower:/opt/src/mythtv/mythtv-0.18.1$ 
```
dh_testdir
dh_testdir: debian/control has a duplicate entry for mythtv 

How can i find this duplicate entry???

Any clue on how i can rectify this??


What if i 'make' and 'make install' instead of sudo dpkg-buildpackage -rfakeroot -b  woudl that work????

---

### Post by triplep on 2006-02-13
New packages for MythTV 0.19 are living at [http://deb.thehunter.ws/](http://deb.thehunter.ws/) only i386, 64bit userland still needs to roll their own.



[Yatta] - I posted the necessary flags for 64 bit on the previous page, --cputype is replaced by -march and --tune is -mtune.  As for the duplicates, I'd open a graphical package manager and see if there are any myth-ish thing s listed, sounds like an uncleaned dependcy sorta thing.

---

### Post by [Yatta] on 2006-02-13
[QUOTE=triplep]......
[Yatta] - I posted the necessary flags for 64 bit on the previous page, --cputype is replaced by -march and --tune is -mtune.  As for the duplicates, I'd open a graphical package manager and see if there are any myth-ish thing s listed, sounds like an uncleaned dependcy sorta thing.[/QUOTE]

Nope never worked... still getting ```
dh_testdir: debian/control has a duplicate entry for mythtv
```
oohh and just out of curiosity i did:
```

enigma@blacktower:/opt/src/mythtv/mythtv-0.18.1$ sudo make
---------------snip -------------
mpeg/tspacket.cpp: In member function ‘QString TSPacket::toString() const’:
mpeg/tspacket.cpp:17: error: cast from ‘const unsigned char*’ to ‘int’ loses precision
make[2]: *** [tspacket.o] Error 1
make[2]: Leaving directory `/opt/src/mythtv/mythtv-0.18.1/libs/libmythtv'
make[1]: *** [sub-libmythtv] Error 2
make[1]: Leaving directory `/opt/src/mythtv/mythtv-0.18.1/libs'
make: *** [sub-libs] Error 2

```

---

### Post by zeltak on 2006-02-13
Help!!

im very new to linux (and very six of windows). ive used this excellent guide (i have the same computer specs as in the guide) and deleted my previous windows HTPC. All went well until i got to the line:

Then, do the following:

    depmod
    modprobe ivtv
    dmesg

in modprobe ivtv i get the following error:

"Fatal: module ivtv not founf"

What am i doing wrong? im kinda stuck here without an HTPC computer (and no tv for wife ;-))... Can anyone help me out??

really appriciated

Zeltak

---

### Post by mikedtemple on 2006-02-13
[QUOTE=t0bb3]I finaly took the time to try to get live tv working and also noticed this problem. Searching the MythTV mailing lists archive makes it pretty obvious that this is a common problem, and the solution seems to be to run```
xvattr -a XV_COLORKEY -v 0
```I haven't had the time to try it myself yet though...[/QUOTE]

I had the same problem, but I traced it a little differently.  If you're using an Nvidia Card with the current drivers you can use nvidia-settings to increase the overscan (I think it's the second slider), thereby eliminating the blue line.

Just make sure your Autostart (I use Kubuntu, not sure of the Gnome equivalent) has: 

```
nvidia-settings --load-config-only &
```

to load your settings config in when you start X.

---

### Post by barbex on 2006-02-13
First of all a big thankyou for the great how-to!

Just a note: 

The new mythtv of version 0.19 is out but not included in all repositories yet. You can find them at [http://deb.thehunter.ws/]("http://deb.thehunter.ws/") and even mythgame can be installed from there.

bye!

---

### Post by zeltak on 2006-02-14
Hi!!

i devoted my whole day yesterday (about 18 hours!!!) to install MythTV and i finally have it setup!! Thx you for the really amazing instructions!!! its realy great. One thing thought that i have a problem with is the time it takes mythTv to load after the mods for the startup (chapter 6.2 in your guide:
System->Preferences->Sessions, and select the "Startup Programs" tab)

it taked a good 5 minutes for myth to load, is that normal? i followed the guide step by step so i dont think i did anything wrong

anyway thx again for all the help!!

Zeltak

---

### Post by zeltak on 2006-02-14
Helppp

another MAJOR ISSUE, man i seem to have no luck with mythtv. i tried to install the and configure nuvexport and i think that after editing my mysql.txt file mythtv stoped working...i really dont know what to do....can anyone help...i tried editing the password to my sql password (there was something written there which i erased and cant remember)...now nothing works...can anyone help?

thx 

Zeltak

---

### Post by schucki.be on 2006-02-14
He Zeltak,
I am not at my Ubuntu station, so I cannnot look with you.
What message are you getting when starting mythfrontend?

Try to fill in just the password you made up during the MYSQL- instructions in the HOWTO.

schucki.be

---

### Post by arjay1 on 2006-02-14
zeltak - just to let you know you are not alone.  I, too, have the problem that mythtv takes 5-6 minutes to fire up even though I followed the howto to have it boot up automatically.  I have no idea either why the delay happens.

It is very irritating because if I open a copy manually, then the program tries to open a second copy 5 minutes later!!

Hope that someone here can help.

RJ

---

### Post by zeltak on 2006-02-14
....from one problem to another....:p 


i cant connect to backend server on mythtv anmore for some reason...i get this message. i think (but i may be really wrong) that this has to do with me changing the default place to store videos...can this be the problem? if so whats the default place to store recorded video in mythtv?

thx again..maybe one day ill have a HTPC...who knows :mrgreen: 

Zeltak

---

### Post by barbex on 2006-02-15
zeltak, why don't you open a new thread with your error message, so the right people see it.

---

### Post by Micro Rotors on 2006-02-15
Hello all, 
There are a few bugs in it but I am sure I can work it out myself. :eek: Anyhow when I installed Ubuntu on a 300 gig HD, I wasn't planning on mythtv being in there. I partitioned the drive as followed.

/ 10 GB.
home 10 GB.
swap 6 GB

I have the rest of the drive unpartitioned for anything. Can I add another partition lets say 150 GB, and direct mythtv to place recorded shows on that new partition?

Thanks to all that have helped me. I could not have done this without you.

---

### Post by dhyams on 2006-02-16
...for now, as an upgrade to the existing MythTV 0.18 procedure in the howto.  

See section 9.8.  This will lead you through how to compile MythTV 0.19 from source (which is not hard at all), and install.  It also takes you through a couple of issues that are new for MythWeb, as it has had a overhaul since last version.

Thanks for all of the interest in the HOWTO.

---

### Post by frkstein on 2006-02-16
Micro Rotors,

When I installed Mythtv I wanted it to store on a second drive that had 150GB of unpartitioned space. All I did was format the drive with a file system. Then, when running mythtv-setup, it gives you the option of changing where you want your programs stored. Just point it to where you mount your new partition. In my case, my fstab mounts the mythtv partition as /mythtv. Under mythtv-setup, I inserted /mythtv. I have not had a problem with this setup.

---

### Post by zeltak on 2006-02-16
Hi dhymasn!

i continue to use your excellent guide! i got stuck now in the 0.19 install.

i had problems with the setenv QTDIR /usr/lib/qt3 , but managed to fix that with help. now i got stuck with the myth plugins make command. it gives me an error message about mythweb and stops after 5 sec. is anyone else having problems with this?

zeltak

---

### Post by Micro Rotors on 2006-02-16
[QUOTE=dhyams]...for now, as an upgrade to the existing MythTV 0.18 procedure in the howto.  

See section 9.8.  This will lead you through how to compile MythTV 0.19 from source (which is not hard at all), and install.  It also takes you through a couple of issues that are new for MythWeb, as it has had a overhaul since last version.

Thanks for all of the interest in the HOWTO.[/QUOTE]


Well I get problems at the get-go; I can't even get past the first block of codes.

```
bill@Linux:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://us.archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://us.archive.ubuntu.com breezy/multiverse Sources
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Fetched 3B in 4s (1B/s)
Reading package lists... Done
bill@Linux:~$ sudo apt-get build-dep mythtv
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for mythtv could not be satisfied.
bill@Linux:~$ sudo apt-get build-dep mythplugins
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for mythplugins could not be satisfied.
bill@Linux:~$

```

---

### Post by zeltak on 2006-02-16
hi 

this is the problem im getting

root@ztpc:/opt/src/mythplugins-0.19# make
cd mythbrowser && make -f Makefile
make[1]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser'
cd mythbrowser && make -f Makefile
make[2]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
g++ -c -pipe -Wall -W -fomit-frame-pointer -D_REENTRANT  -D_GNU_SOURCE
-DPREFIX=\"\" -D_FILE_OFFSET_BITS=64 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT
-DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I.
-I/include -I/usr/kde/3.3/include -I/include -I/usr/include/kde
-I/opt/kde3/include -I/usr/include/qt3 -o main.o main.cpp
main.cpp:20:30: error: mythtv/exitcodes.h: No such file or directory
main.cpp: In function 'int main(int, char**)':
main.cpp:90: error: 'FRONTEND_EXIT_NO_MYTHCONTEXT' was not declared in
this scope
main.cpp:96: error: 'FRONTEND_EXIT_DB_ERROR' was not declared in this scope
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
make[1]: *** [sub-mythbrowser] Error 2
make[1]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser'
make: *** [sub-mythbrowser] Error 2

hope this can be solved :) 

Zeltak

---

### Post by dhyams on 2006-02-16
> **Micro Rotors]Well I get problems at the get-go said:**
> 

Hmm, I'm not sure what is going on here; take a look at my current /etc/apt/sources.list and see if you have all of the same entries that I do:
[QUOTE]

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse


deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted



Even so, you might be able to proceed ahead with the howto.  When you try to configure and build MythTV, it will report back to you dependencies that have failed, most of the time.  For each one, use packages.ubuntu.com to hunt down the right package to install, and apt-get it.

---

### Post by dhyams on 2006-02-16
[QUOTE=zeltak]Hi dhymasn!

i continue to use your excellent guide! i got stuck now in the 0.19 install.

i had problems with the setenv QTDIR /usr/lib/qt3 , but managed to fix that with help. now i got stuck with the myth plugins make command. it gives me an error message about mythweb and stops after 5 sec. is anyone else having problems with this?

zeltak[/QUOTE]

Right, that QTDIR thing was definitely my fault; I forgot that I switched to tcsh before setting this variable and going through the compilation.  I'm just guessing, but if you don't want to use tcsh, I think the correct way to set QTDIR in a bash way is

export QTDIR=/usr/lib/qt3

As for the compile error, it looks like you didn't add the proper prefix when you configured the mythplugins directory for compile.  You definitely don't want to install into "/" like your current prefix is set.  From the howto, here is the command to use:

./configure --prefix=/usr/local/mythtv-0.19 --enable-transcode --enable-vcd

The compiler is correctly reporting to you that it cannot find the mythtv header files.  Here is what my compile line looks like that is the equivalent to yours:

make[1]: Entering directory `/opt/src/mythtv19/mythplugins-0.19/mythbrowser/mythbrowser'
g++ -c -pipe -march=pentiumpro -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -W -O3 -Wall -Wno-switch -fomit-frame-pointer -D_REENTRANT  -D_GNU_SOURCE -DPREFIX=\"/usr/local/mythtv-0.19\" -DMMX -Di386 -DUSING_DBOX2 -D_FILE_OFFSET_BITS=64 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/local/mythtv-0.19/include -I/usr/kde/3.3/include -I/usr/local/mythtv-0.19/include -I/usr/X11R6/include -I/usr/include/kde -I/opt/kde3/include -I/usr/include/qt3 -o main.o main.cpp

Note the differences there.

---

### Post by Micro Rotors on 2006-02-16
dhyams,

I am using a copy of your source.list that I got from you'r HOW-TO. It is exactly the same.

Thanks for your help. ;) 
Bill

---

### Post by zeltak on 2006-02-17
Hi

thx for updating the guide. the export works well. i do still get stuck here:

./configure --with-prefix=/usr/local/mythtv-0.19
Unknown option "--with-prefix=/usr/local/mythtv-0.19".
See ./configure --help for available options.

 so i used  ./configure --prefix=/usr/local/mythtv-0.19
 and it seemed to work for the mythtv install

then i again got stuck at


root@ztpc:/opt/src/mythplugins-0.19# make
cd mythbrowser && make -f Makefile
make[1]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser'
cd mythbrowser && make -f Makefile
make[2]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
g++ -c -pipe -Wall -W -fomit-frame-pointer -D_REENTRANT  -D_GNU_SOURCE -DPREFIX=\"\" -D_FILE_OFFSET_BITS=64 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/include -I/usr/kde/3.3/include -I/include -I/usr/include/kde -I/opt/kde3/include -I/usr/include/qt3 -o main.o main.cpp
main.cpp:20:30: error: mythtv/exitcodes.h: No such file or directory
main.cpp: In function 'int main(int, char**)':
main.cpp:90: error: 'FRONTEND_EXIT_NO_MYTHCONTEXT' was not declared in this scope
main.cpp:96: error: 'FRONTEND_EXIT_DB_ERROR' was not declared in this scope
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
make[1]: *** [sub-mythbrowser] Error 2
make[1]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser'
make: *** [sub-mythbrowser] Error 2

what am i doing wrong i used all the steps in guide exactly...any ideas?


thx alot

Zeltak

---

### Post by zeltak on 2006-02-17
hi

somone told me this in another forum to just disable mythweb form the ./configure. and it worked!! i guess for the time being ill forget the web module. but....after doing all the othe steps when i open mythtv it still says 0.18 in the info, how do i launch the correct mythTV, i normaly use mythfrontend command.

thx 

Zeltak

---

### Post by althepcman on 2006-02-17
I having problems with myth tv.
before I installed mythtv I used mplayer to play what was on tv and I would use ivtv-tune to set the channel. By doin the following commands:
ivtv-tune -taustralia -c40 -d/dev/video0
mplayer -vo xv /dev/video0

But when I install mythtv I can only see static no mater what channel I am on.
I have run a mythfilldatabase and mythbackend is running.
I am not sure what to do.
I have a Hauppage PVR 250 MCE

---

### Post by dhyams on 2006-02-17
[QUOTE=zeltak]hi

somone told me this in another forum to just disable mythweb form the ./configure. and it worked!! i guess for the time being ill forget the web module. but....after doing all the othe steps when i open mythtv it still says 0.18 in the info, how do i launch the correct mythTV, i normaly use mythfrontend command.

thx 

Zeltak[/QUOTE]

Take another look at the HOWTO, where I put the proper path in the /etc/profile file.  After doing this, you will have to log out and back in for this to take effect.

I'm not sure why you had to disable MythBrowser (it was mythbrowser, right?); I didn't have to do this.

---

### Post by Micro Rotors on 2006-02-17
dhyams,

I redid the source list with the one you have again just in case there was something funky with the previous one. I also saw the new entry on the HOW-TO about downloading the three files to the /opt/src directory that I had to build, but I am still getting this error about the Build-dependencies.

[PHP]bill@Linux:~$ cd /opt/src
bill@Linux:/opt/src$ sudo -i
root@Linux:~# apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://us.archive.ubuntu.com breezy Release
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://us.archive.ubuntu.com breezy/multiverse Sources
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
root@Linux:~# apt-get build-dep mythtv
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for mythtv could not be satisfied.
root@Linux:~# apt-get build-dep mythplugins
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for mythplugins could not be satisfied.
root@Linux:~#
[/PHP]

Also I added the ATI driver for my ATI Radeon X300 graphics card and now since then I get this which never was there in the past. I finally had it running now I can watch TV but the little screen on the right when the schedule comes up is now on the left and the picture is messed up. but if I hit the escape key it will take me to the full screen TV mode and the picture is fine then. Go figure.

> sh-3.00$ mythbackend &
[1] 11052
sh-3.00$ 2006-02-17 08:31:09.000 New DB connection, total: 1
Starting up as the master server.
2006-02-17 08:31:09.055 New DB connection, total: 2
2006-02-17 08:31:09.104 New DB connection, total: 3
2006-02-17 08:31:09.251 New DB scheduler connection
 is defined, but isn't attached to a cardinput.
2006-02-17 08:31:09.260 mythbackend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-02-17 08:31:09.260 Enabled verbose msgs : important general
2006-02-17 08:31:11.260 Reschedule requested for id -1.
2006-02-17 08:31:11.750 Scheduled 8 items in 0.5 = 0.47 match + 0.02 place
2006-02-17 08:31:11.754 Seem to be woken up by USER
mythfrontend
2006-02-17 08:31:20.304 New DB connection, total: 1
Total desktop width=1600, height=1200, numscreens=1
2006-02-17 08:31:20.312 Using screen 0, 1600x1200 at 0,0
2006-02-17 08:31:20.318 mythfrontend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-02-17 08:31:20.318 Enabled verbose msgs : important general
2006-02-17 08:31:20.720 Switching to square mode (blue)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-02-17 08:31:21.668 Joystick disabled.
2006-02-17 08:31:21.733 Registering Internal as a media playback plugin.
2006-02-17 08:31:21.764 Registering MythDVD DVD Media Handler as a media handler2006-02-17 08:31:22.007 Registering MythMusic Media Handler as a media handler
removing stale cache dir: /home/mythtv/.mythtv/themecache/blue.1280.1024
2006-02-17 08:32:00.541 New DB connection, total: 2
2006-02-17 08:32:00.558 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-02-17 08:32:00.564 Using protocol version 15
2006-02-17 08:32:00.569 MainServer::HandleAnnounce Playback
2006-02-17 08:32:00.569 adding: Linux as a client (events: 0)
2006-02-17 08:32:00.590 MainServer::HandleAnnounce Playback
2006-02-17 08:32:00.590 adding: Linux as a client (events: 1)
2006-02-17 08:32:00.595 Using protocol version 15
2006-02-17 08:32:00.600 MainServer::HandleAnnounce Playback
2006-02-17 08:32:00.600 adding: Linux as a client (events: 0)
2006-02-17 08:32:00.619 MainServer::HandleAnnounce Playback
2006-02-17 08:32:00.619 adding: Linux as a client (events: 0)
2006-02-17 08:32:00.627 adding: Linux as a remote ringbuffer
2006-02-17 08:32:00.636 Changing from None to WatchingLiveTV
2006-02-17 08:32:02.943 Opening audio device '/dev/dsp'.
2006-02-17 08:32:02.944 Opening OSS audio device '/dev/dsp'.
***
* Couldn't find Xv support, falling back to non-Xv mode.
* MythTV performance will be much slower since color
* conversion and scaling will be done in software.
* Consider upgrading your video card or X server if
* you would like better performance.
X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  15
  Resource id:  0xffffffff
X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0xffffffff
2006-02-17 08:32:02.967 Couldn't get the color key color, and we need it.
You likely won't get any video.
2006-02-17 08:32:03.249 Realtime priority would require SUID as root.
2006-02-17 08:32:03.254 Video timing method: USleep with busy wait
2006-02-17 08:32:03.271 Changing from None to WatchingLiveTV
2006-02-17 08:32:04.531 prebuffering pause
[mpeg2video @ 0xb7837834]skiped MB in I frame at 17 19
[mpeg2video @ 0xb7837834]Warning MVs not available
***
* Your system is not capable of displaying the
* full framerate at 480x360 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.
X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  15
  Resource id:  0xffffffff
X Error: XvBadPort 152
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0xffffffff
2006-02-17 08:32:09.545 Couldn't get the color key color, and we need it.
You likely won't get any video.
2006-02-17 08:32:09.549 Changing from WatchingLiveTV to None
2006-02-17 08:32:09.872 Changing from WatchingLiveTV to None
2006-02-17 08:32:09.881 Changing from None to None
sh-3.00$


---

### Post by Rev. Nathan on 2006-02-19
My question is if I could keep my current setup; a 1600x1200 environment for desktop computing, and still have MythTV just run in the background? Like, do all the daemon deeds it does, and when I want to watch my recordings, I can log into mythtv and output to my television? This is the kind of idea I'm lookin' for...

---

### Post by anotherMichael on 2006-02-19
**Update: edited after I found the solution **

Thanks ! 
Very useful and clear guide. 

**The problem was **
... it seems that I am missing lots of headers. Just headers are missing, compiled libraries are there so simply trying something like apt-get install lame is not helping. 

Here is attempt to compile mythtv plugins. 

[FONT="Courier New"]root@myth:/opt/src/mythtv-0.19# root@myth:/opt/src/mythplugins-0.19# ./configure --prefix=/usr/local/mythtv-0.19 --cpu=x86-64 --tune=generic --enable-mmx --enable-transcode --enable-vcd
MythMusic requires libmad and libid3tag.
MythMusic requires FLAC.
MythMusic requires libcdaudio.
MythMusic requires CDDA Paranoia.
Disabling MythMusic due to missing dependencies.
Disabling MythGallery due to missing libtiff.
Disabling MythBrowser due to missing KDE development packages.

Configuration settings:

        MythBrowser   plugin will not be built
        MythControls  plugin will be built
        MythFlix      plugin will be built
        MythDVD       plugin will be built
        MythGallery   plugin will not be built
        MythGame      plugin will be built
        MythMusic     plugin will not be built
        MythNews      plugin will be built
        MythPhone     plugin will be built
        MythVideo     plugin will be built
        MythWeather   plugin will be built
        VCD           support will be included in MythDVD
        Transcode     support will not be included in MythDVD
        FESTIVAL      support will not be included in MythPhone
[/FONT]

configure is correct as I truely do not have mad.h (I find the name ever more appropriate ;) 
find / -name mad.h 
yields nothing. 

Possible lead would be that I could not set up dependencies is here with my attempt to fix it:
[FONT="Courier New"]
root@myth:/opt/src/mythplugins-0.19# apt-get build-dep mythplugins
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for mythplugins cannot be satisfied because the package libmyth-0.18.1-dev cannot be found
root@myth:/opt/src/mythplugins-0.19# apt-get install libmyth-0.18.1-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmyth-0.18.1-dev
root@myth:/opt/src/mythplugins-0.19#
[/FONT]

**The solution was **
..  to follow Hyams guide _very_ precisely and when he means _search_ [http://packages.ubuntu.com](http://packages.ubuntu.com) actual use search feature of this site.  Search feature is at bottom and may not be visible on the page load. So use search power do not just browse around the Ubuntu breeze section ;-).

The search works great much better then search in Ubuntu gui tool. You can search for specific file e.g. mad.h.

Here is the list of modules that I've needed to solve plugin compile problems. Choice of kde-devel may have been problematic due to size.

apt-get install liblame-dev
apt-get install libmad0-dev
apt-get install libid3tag0-dev
apt-get install libflac-dev
apt-get install libcdaudio0-dev
apt-get install libcdparanoia0-dev
apt-get install libtiff0-dev
apt-get install libtiff4-dev
apt-get install kde-devel

BTW For those who wonder what are headers (something.h) - headers are not needed to run a program, but they are needed to compile anything that depends on this program. 

Thanks
Michael

---

### Post by mattisf on 2006-02-21
Hi all,

I found one odd problem with the remote ... Dhyams, you mention in the _excellent_ howto that "Obviously, the infrared receiver dongle should be plugged into your PVR-150 by this point" - but my dongle has a USB connector at the end, and doesn't plug into the PVR-150. It plugs into a regular USB port. Is this something that has changed from when you bought your card, or did you just phrase it that way?

Cheers,

Mattis

PS. The problem I'm seeing is that when I run 'irw', the lirc daemon dies. The log tells me that it 'could not open /dev/lirc' so I'm thinking that maybe something is not installed properly here... Oh, and I'm using LIRC 0.8, since it was the newest ... maybe this was a mistake.

---

### Post by dhyams on 2006-02-22
[QUOTE=mattisf]Hi all,

I found one odd problem with the remote ... Dhyams, you mention in the _excellent_ howto that "Obviously, the infrared receiver dongle should be plugged into your PVR-150 by this point" - but my dongle has a USB connector at the end, and doesn't plug into the PVR-150. It plugs into a regular USB port. Is this something that has changed from when you bought your card, or did you just phrase it that way?

Cheers,

Mattis

PS. The problem I'm seeing is that when I run 'irw', the lirc daemon dies. The log tells me that it 'could not open /dev/lirc' so I'm thinking that maybe something is not installed properly here... Oh, and I'm using LIRC 0.8, since it was the newest ... maybe this was a mistake.[/QUOTE]
Whoa...that's strange.  My PVR-150 came a combined dongle/ir blaster thingy that connects directly to the PVR-150.  The jack for this looks a lot like a 1/8" headphone jack, but a bit smaller.

I can only guess that the remote that you are talking about was bought separately from the PVR-150...is this correct?  The remote that I am talking about is the one that ships with the PVR-150, retail version.  If you bought a PVR-150MCE or PVR-150lp, they do not come with a remote.

EDIT:
Did you buy this: [http://www.hauppauge.com/pages/products/data_pvr150mcekit.html](http://www.hauppauge.com/pages/products/data_pvr150mcekit.html)
and not this: [http://www.hauppauge.com/pages/products/data_pvr150.html](http://www.hauppauge.com/pages/products/data_pvr150.html)

My HOWTO covers how to take care of the second one, not the first one, which looks like a PVR-150MCE bundled with some third part remote.  Notice the difference in the remotes...

And on the second URL I listed, if you scroll toward the bottom and enlarge the picture of the card (view of the jacks on the back), you can see at the bottom the tiny IR jack.

---

### Post by Micro Rotors on 2006-02-22
This is killing me here since I added my ATI driver. I cant figure out what the HE** is going on here. I just need to reinstall all this stuff, maybe just a fresh Ubuntu install (AGHRrrrr) . Do I go into synaptics to delate all this?

---

### Post by mattisf on 2006-02-22
Dhyams - thanks, you're absolutely right, I have the one without the IR jack. Bummer. I didn't know there were several editions ... and I thought I did good research. :-P

Thanks anyway ... at least I understand the problem better now. Maybe there's some other way I can get LIRC to support my remote... Plus now you know that your howto works for this card too, except for the remote part. :-)

Cheers,

Mattis

---

### Post by dhyams on 2006-02-26
Those of you with slow mythfrontend startup times upon login, may want to revisit the HOWTO section 6.3.  I have just reordered the items in the Sessions dialog, and that seems to solve the problem.

---

### Post by acorrigan on 2006-02-27
I just solved my problem, so I'm telling everyone what happened in case it's useful for someone else.

I went through the tutorial and everything went fine except I only kinda got channel 5 and 6, all the other channels were static.  However, when I plugged in my PS2 to the composite-in it worked perfectly.

It turned out the frequency table was the wrong one for me.  I believe it defaulted to us-cable,  but for me I had to use  us-cable-hrc  by doing the following

ivtv-tune -t us-cable-hrc -c 58   

you can find other options by listing out ivtv-tune -L

---

### Post by metrognome on 2006-02-27
[QUOTE=dhyams]Take another look at the HOWTO, where I put the proper path in the /etc/profile file.  After doing this, you will have to log out and back in for this to take effect.

I'm not sure why you had to disable MythBrowser (it was mythbrowser, right?); I didn't have to do this.[/QUOTE]

Hello,

First: Thank you for the most excellent guide!

Now, I'm having the same problem you responded to here but the mythtv id just isn't running the /etc/profile on login.

I did a fresh install of Ubuntu - then installed 0.18 then followed your upgrade instructions for 0.19.  Everything went well but I'm still running 0.18.

[after a little more experimenting]
If I log in from my other box via ssh I get the right profile.  If I log in at the console and open a terminal I don't.  Sessions is running the wrong mythbackend.

I'll keep experimenting but any ideas would be appreciated.  Thank you much!

MetroGnome.

---

### Post by meastp on 2006-02-28
Hi!

I have a computer with pvr-150, 300GB hdd (PIII800, 256MB RAM), and I want to make a box/server for recording tv-shows and make isos for dvd (I will transfer them to my computer for burning to dvd).

Then I won't need mythfrontend(?) What should i skip (in the howto?).

I will need ssh, mythweb, makedvd.sh and mythshows.sh, but those are all covered in your guide.

---

### Post by dhyams on 2006-02-28
[QUOTE=metrognome]Hello,

First: Thank you for the most excellent guide!

Now, I'm having the same problem you responded to here but the mythtv id just isn't running the /etc/profile on login.

I did a fresh install of Ubuntu - then installed 0.18 then followed your upgrade instructions for 0.19.  Everything went well but I'm still running 0.18.

[after a little more experimenting]
If I log in from my other box via ssh I get the right profile.  If I log in at the console and open a terminal I don't.  Sessions is running the wrong mythbackend.

I'll keep experimenting but any ideas would be appreciated.  Thank you much!

MetroGnome.[/QUOTE]

You're exactly right; by coincidence, I have updated the Mythtv 0.19 section in the howto to help get the paths set up correctly.

The problem is that when running "sh" it completely ignores /etc/profiles, unless it is a true login shell.  With "bash" it always runs it.  Since "sh" behaves like this, you also have to adjust your Sessions dialog appropriately as now shown in the howto.

---

### Post by dhyams on 2006-02-28
[QUOTE=meastp]Hi!

I have a computer with pvr-150, 300GB hdd (PIII800, 256MB RAM), and I want to make a box/server for recording tv-shows and make isos for dvd (I will transfer them to my computer for burning to dvd).

Then I won't need mythfrontend(?) What should i skip (in the howto?).

I will need ssh, mythweb, makedvd.sh and mythshows.sh, but those are all covered in your guide.[/QUOTE]

I would just go ahead and install mythfrontend as well, but not run it at login (see your sessions dialog).  The amount of space you would save by not installing it would be minimal.

---

### Post by acorrigan on 2006-02-28
Thank you for this guide dhyams.  MythTV is overall working very well for me.

I have one minor issue, when I watch live tv or recordings there's noise at the top of the video, maybe in the first 1 - 3 lines.  I have the PVR-150 MCE.

Anybody have any ideas why that is and how to get rid of it?

---

### Post by hallikpapa on 2006-03-04
Great howto. Unfortuneately, the upgrade didn't go well for me.

Here is my issue, and probably why I can't get WinMyth working for live tv.

Protocol version mismatch (frontend=26,backend=15)

I did a straight copy and paste from your guide.

---

### Post by hallikpapa on 2006-03-04
AHHHHHHHHHHHHHHHHHH!!!!! :) 
 
Report from the backend when I reinstalled the newest WinMyth and redid the upgrade on the backend: 
 
2006-03-04 16:02:28.303 MainServer::HandleVersion - Client speaks protocol version 15 but we speak 26! 
 
Even though I uninstall winmyth,deleted the directory, rebooted, and reinstalled it. Lots o fun! :) 

Again this is from the backend when I try and connect using WinMyth. Before the stuff was reversed...

---

### Post by Seanz0rz on 2006-03-04
edit, my stupidity and 5 restarts solved the problem. 

however i have another thats been asked a few times before but never answered. how do i get myth tv to work for my user, not mythtv's user? i dont really want to log in and out each time.

---

### Post by hallikpapa on 2006-03-05
Seems as though after the upgrade the startup script didn't get update to run the new files. This is what happens when I run 0.19 manually:
```

root@home:/etc/rc2.d#  /usr/local/mythtv/bin/mythbackend 
2006-03-05 10:45:47.984 Using runtime prefix = /usr/local/mythtv-0.19
2006-03-05 10:45:47.987 Unable to read configuration file mysql.txt
2006-03-05 10:45:47.988 Trying to create a basic mysql.txt file
2006-03-05 10:45:48.008 Writing settings file /root/.mythtv/mysql.txt
2006-03-05 10:45:48.034 New DB connection, total: 1
2006-03-05 10:45:48.037 Unable to connect to database!
2006-03-05 10:45:48.037 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-03-05 10:45:48.093 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-03-05 10:45:48.145 Failed to init MythContext, exiting.
```

Works when I run as mythtv though. Shouldn't it be able to execute as root since that's how it needs to run on boot?

---

### Post by dhyams on 2006-03-07
Actually, mythbackend runs as the mythtv user at boot.  That's what the "su -c mythtv" parts of the /etc/init.d/mythtv-backend script does.

---

### Post by wackman on 2006-03-08
Hey all,

I've gone through hyam's ivtv/mythtv HOWTO at [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html), I've gone through several other ivtv documents. I've tried various other suggestions such as copying different files, linking other files, etc. I can't, for the life of me, get all the firmware files to load. Here is my dmesg output:

```

[  850.951457] ivtv:  ==================== START INIT IVTV ====================
[  850.951553] ivtv:  version 0.4.3 (tagged release) loading
[  850.951556] ivtv:  Linux version: 2.6.15-17-amd64-k8 SMP preempt gcc-4.0
[  850.951559] ivtv:  In case of problems please include the debug info between
[  850.951561] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[  850.951563] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[  850.951899] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[  850.951934] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 193
[  850.952991] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[  850.981788] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[  850.981868] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[  851.061109] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[  851.077293] cx25840 1-0044: unable to open firmware v4l-cx25840.fw
[  851.105596] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[  851.106139] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[  851.110277] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[  851.158577] tveeprom 1-0050: Hauppauge model 26582, rev C699, serial# 8786602
[  851.158676] tveeprom 1-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[  851.158761] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[  851.158835] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[  851.158909] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[  851.158986] tveeprom 1-0050: has no radio, has no IR remote
[  851.528728] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[  851.528810] ivtv0: did you put the firmware in the hotplug firmware directory?
[  851.528898] ivtv0 warning: failed loading encoder firmware
[  851.528967] ivtv0 warning: Error loading firmware -3!
[  851.529038] ivtv0: Error -3 initializing firmware.
[  851.531173] ivtv0: Error -12 on initialization
[  851.531251] ivtv: probe of 0000:00:0b.0 failed with error -12
[  851.531334] ivtv:  ====================  END INIT IVTV  ====================
[  912.379582] No module found in object
root@homegrown:/usr/lib/hotplug/firmware#   

```

The part about no IR device kinda bugs me, but I'll worry about that once I get everything else working. 

and the output of ls -ltra /usr/lib/hotplug/firmware:

```

-rw-r--r-- 1 root root 262144 2006-03-08 01:51 v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 262144 2006-03-08 01:51 ivtv-fw-enc.bin
-rw-r--r-- 1 root root 262144 2006-03-08 01:51 ivtv-fw-dec.bin
drwxr-xr-x 3 root root      8 2006-03-08 01:52 ..
-r--r--r-- 1 root root 376836 2006-03-08 01:53 v4l-cx2341x-enc.fw.orig
-rw-r--r-- 1 root root 155648 2006-03-08 01:53 v4l-cx2341x-init.mpg
lrwxrwxrwx 1 root root     41 2006-03-08 01:59 v4l-cx2341-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-rw-r--r-- 1 root root  14264 2006-03-08 02:06 v4l-cx25840.fw
lrwxrwxrwx 1 root root     41 2006-03-08 02:23 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
drwxr-xr-x 2 root root     96 2006-03-08 04:07 .

```

+


OK, so I think I got a couple typoed filenames there, but I think all the correct ones are there. And I hate my keyboard tray, but that's unrelated.

Thanks for any and all help.

Wackman

---

### Post by mossholderm on 2006-03-08
Has anyone gotten XvMC working with an nVIDIA card? For some reason, my system always crashes with it enabled... and that's with multiple cards, motherboards, and installations :neutral: 

     --Matt

---

### Post by ravalox on 2006-03-09
I am trying to get mythbackend to startup on startup.  I have followed these instructions: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) and it works well except that now the mythbackend that gets started is the mythbackend .18 version, and yet when I run mythbackend as the mythtv user it's using the mythbackend .19 binaries.  How can I get the right mythbackend binaries running?

---

### Post by dhyams on 2006-03-10
[QUOTE=wackman]Hey all,

I've gone through hyam's ivtv/mythtv HOWTO at [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html), I've gone through several other ivtv documents. I've tried various other suggestions such as copying different files, linking other files, etc. I can't, for the life of me, get all the firmware files to load. Here is my dmesg output:

```

[  850.951457] ivtv:  ==================== START INIT IVTV ====================
[  850.951553] ivtv:  version 0.4.3 (tagged release) loading
[  850.951556] ivtv:  Linux version: 2.6.15-17-amd64-k8 SMP preempt gcc-4.0
[  850.951559] ivtv:  In case of problems please include the debug info between
[  850.951561] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[  850.951563] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[  850.951899] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[  850.951934] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 193
[  850.952991] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[  850.981788] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[  850.981868] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[  851.061109] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[  851.077293] cx25840 1-0044: unable to open firmware v4l-cx25840.fw
[  851.105596] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[  851.106139] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[  851.110277] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[  851.158577] tveeprom 1-0050: Hauppauge model 26582, rev C699, serial# 8786602
[  851.158676] tveeprom 1-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[  851.158761] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[  851.158835] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[  851.158909] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[  851.158986] tveeprom 1-0050: has no radio, has no IR remote
[  851.528728] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[  851.528810] ivtv0: did you put the firmware in the hotplug firmware directory?
[  851.528898] ivtv0 warning: failed loading encoder firmware
[  851.528967] ivtv0 warning: Error loading firmware -3!
[  851.529038] ivtv0: Error -3 initializing firmware.
[  851.531173] ivtv0: Error -12 on initialization
[  851.531251] ivtv: probe of 0000:00:0b.0 failed with error -12
[  851.531334] ivtv:  ====================  END INIT IVTV  ====================
[  912.379582] No module found in object
root@homegrown:/usr/lib/hotplug/firmware#   

```

The part about no IR device kinda bugs me, but I'll worry about that once I get everything else working. 

and the output of ls -ltra /usr/lib/hotplug/firmware:

```

-rw-r--r-- 1 root root 262144 2006-03-08 01:51 v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 262144 2006-03-08 01:51 ivtv-fw-enc.bin
-rw-r--r-- 1 root root 262144 2006-03-08 01:51 ivtv-fw-dec.bin
drwxr-xr-x 3 root root      8 2006-03-08 01:52 ..
-r--r--r-- 1 root root 376836 2006-03-08 01:53 v4l-cx2341x-enc.fw.orig
-rw-r--r-- 1 root root 155648 2006-03-08 01:53 v4l-cx2341x-init.mpg
lrwxrwxrwx 1 root root     41 2006-03-08 01:59 v4l-cx2341-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-rw-r--r-- 1 root root  14264 2006-03-08 02:06 v4l-cx25840.fw
lrwxrwxrwx 1 root root     41 2006-03-08 02:23 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
drwxr-xr-x 2 root root     96 2006-03-08 04:07 .

```

+


OK, so I think I got a couple typoed filenames there, but I think all the correct ones are there. And I hate my keyboard tray, but that's unrelated.

Thanks for any and all help.

Wackman[/QUOTE]


Hmmm I'm not sure about this one.  Try reading over the "firmware" section of [http://ivtvdriver.org](http://ivtvdriver.org).  Here, it shows you how to name your firmware appropriately and where to place it, although it looks to me you have it in the right place.  Perhaps your hotplug dir got changed somehow?

---

### Post by dhyams on 2006-03-10
[QUOTE=ravalox]I am trying to get mythbackend to startup on startup.  I have followed these instructions: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) and it works well except that now the mythbackend that gets started is the mythbackend .18 version, and yet when I run mythbackend as the mythtv user it's using the mythbackend .19 binaries.  How can I get the right mythbackend binaries running?[/QUOTE]

You might have to put the full path in your /etc/init.d/mythtv-backend script.  As in "/usr/local/mythtv/bin/mythbackend".

Look down in section 9.8 though; this tells you how to set up your paths so that you shouldn't have to do this.

---

### Post by Sn1pe on 2006-03-10
My Myth box was running perfectly (aside from when I shutdown it freezes at a blank screen, thinking it's related to the s-video out).  I decided it would be smart to use Adept to upgrade my packages (kubuntu user).  Everything still works, except for the remote.  I have reinstalled lircd per the instructions on the site, but irw still has no output.  Any suggestions?

---

### Post by Sn1pe on 2006-03-10
My problem solved itself.  While messing w/ the database I changed user from mythtv to root and now it works.

---

### Post by godrox on 2006-03-17
I decided to install the .19 from source by following the directions given in this guide, but I can't figure out what I need to add so support for Transcode, AAC, and FESTIVAL is included. What do I need to install to enable these features before I continue?

```
        MythBrowser   plugin will be built
        MythControls  plugin will be built
        MythFlix      plugin will be built
        MythDVD       plugin will be built
        MythGallery   plugin will be built
        MythGame      plugin will be built
        MythMusic     plugin will be built
        MythNews      plugin will be built
        MythPhone     plugin will be built
        MythVideo     plugin will be built
        MythWeather   plugin will be built
        VCD           support will be included in MythDVD
        Transcode     support will not be included in MythDVD
        OpenGL        support will be included in MythGallery
        EXIF          support will be included in MythGallery
        OpenGL        support will be included in MythMusic
        FFTW v.2      support will be included in MythMusic
        SDL           support will be included in MythMusic
        AAC           support will not be included in MythMusic
        FESTIVAL      support will not be included in MythPhone
```

---

### Post by meastp on 2006-03-18
I'm having problems with the makedvd.sh script:

```

*root@tvboks:/usr/local/bin#* mythshows.sh | grep nytt
 /myth/tv/1_20060317205500_20060317212500.nuv : Nytt på nytt []

*root@tvboks:/usr/local/bin#* mythshows.sh | grep Queen
 /myth/tv/1_20060318001000_20060318011000.nuv : Queen - A Night at the Opera []

*root@tvboks:/usr/local/bin#* mythshows.sh | grep sist
 /myth/tv/1_20060317212500_20060317221500.nuv : Først & sist []

*root@tvboks:/usr/local/bin#* makedvd.sh /myth/tv/1_20060317205500_20060317212500. nuv /myth/tv/1_20060318001000_20060318011000.nuv /myth/tv/1_20060317212500_20060 317221500.nuv nrk_test

rm: cannot remove `TITLES.LOG': No such file or directory
******************************************************************
DVD project is: nrk_test
Titles to be recorded:
 Nytt på nytt []
 Queen - A Night at the Opera []
 Først & sist []
******************************************************************
Running mpeg2desc for 1
Running mpeg2desc for 2
Running mpeg2desc for 3
Running mplexer for 1
Running mplexer for 2
Running mplexer for 3
/usr/local/bin/makedvd.sh: line 62: mplex: command not found
/usr/local/bin/makedvd.sh: line 62: mplex: command not found
/usr/local/bin/makedvd.sh: line 62: mplex: command not found
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing dvdmpg1...


```

...and it just stays there forever. I also checked load in mythweb: 0.

---

### Post by deadgobby on 2006-03-30
I am getting serval error and I cannot fig out how to go about this
Preparing to replace mythtv-backend 0.18.1-5 (using .../mythtv-backend_0.19-5_i386.deb) ...
Stopping MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
Unpacking replacement mythtv-backend ...
Preparing to replace mythtv-database 0.18.1-5 (using .../mythtv-database_0.19-5_all.deb) ...
Unpacking replacement mythtv-database ...
Preparing to replace mythtv-common 0.18.1-5 (using .../mythtv-common_0.19-5_all.deb) ...
Unpacking replacement mythtv-common ...
Selecting previously deselected package lcdproc.
Unpacking lcdproc (from .../lcdproc_0.4.5-1_i386.deb) ...
Selecting previously deselected package mythtv-lcdserver.
Unpacking mythtv-lcdserver (from .../mythtv-lcdserver_0.19-5_i386.deb) ...
Selecting previously deselected package libcdaudio0.
Unpacking libcdaudio0 (from .../libcdaudio0_0.99.9-2.1_i386.deb) ...
Preparing to replace mythbrowser 0.18.1-3 (using .../mythbrowser_0.19-5_i386.deb) ...
Unpacking replacement mythbrowser ...
Preparing to replace mythdvd 0.18.1-3 (using .../mythdvd_0.19-5_i386.deb) ...
Unpacking replacement mythdvd ...
Selecting previously deselected package mythgallery.
Unpacking mythgallery (from .../mythgallery_0.19-5_all.deb) ...
Selecting previously deselected package mythmusic.
Unpacking mythmusic (from .../mythmusic_0.19-5_i386.deb) ...
Selecting previously deselected package mythnews.
Unpacking mythnews (from .../mythnews_0.19-5_i386.deb) ...
Selecting previously deselected package mythweather.
Unpacking mythweather (from .../mythweather_0.19-5_i386.deb) ...
Setting up libxvmc1 (1.1.0-2) ...
Setting up mythtv-common (0.19-5) ...

Setting up mythtv-database (0.19-5) ...
Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Setting up lcdproc (0.4.5-1) ...
Starting LCDd CVS-stable-0-4-3-20020127: LCDd.

dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.19-5); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Setting up libcdaudio0 (0.99.9-2.1) ...
Setting up libmyth (0.19-5) ...

Setting up mythtv-frontend (0.19-5) ...

Setting up mythtv-backend (0.19-5) ...
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

Setting up mythtv-lcdserver (0.19-5) ...
Setting up mythbrowser (0.19-5) ...
Setting up mythdvd (0.19-5) ...

Setting up mythgallery (0.19-5) ...
Setting up mythmusic (0.19-5) ...
Setting up mythnews (0.19-5) ...
Setting up mythweather (0.19-5) ...
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

All so how do I change the pass word for myth?

THANKS
Doug

---

### Post by jmh on 2006-04-01
I'm clearly overlooking something vital - I've read this thread and found a couple where there are no lines in the ivtv dmseg o/p but no solution. The setup is a PVR250 and IVTV 0.4.4. Anyway, mine looks like this:

Linux video capture interface: v1.00
ivtv: no version for "struct_module" found: kernel tainted.
ivtv:  ==================== START INIT IVTV ==
ivtv:  version 0.4.4 (tagged release) loading
ivtv:  Linux version: 2.6.12-10-686 686 gcc-3.4
ivtv:  In case of problems please include the debug info between
ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
ivtv:  any module options, when mailing the ivtv-users mailinglist.
ivtv:  ====================  END INIT IVTV  ====================

I've read and followed two variants of the howto's and all the various software, headers and firmware is in the right place and looks like others lists in this thread. ivtvctl says /dev/video0 is not an ivtv device.

Further down the dmesg o/p are lines where it finds the h/w, but not between the INIT IVTV lines above:

bttv0: Bt878 (rev 17) at 0000:00:10.0, irq: 5, latency: 32, mmio: 0xcf000000
bttv0: detected: Hauppauge WinTV/PVR [card=80], PCI subsystem ID is 0070:4500
bttv0: using: Hauppauge WinTV PVR [card=80,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
bttv0: no altera firmware [via hotplug]
tveeprom: Hauppauge: model = 45234, rev = D742, serial# = 6046516
tveeprom: tuner = Temic 4009FR5 (idx = 42, type = 20)
tveeprom: tuner fmt = PAL(B/G) (eeprom = 0x04, v4l2 = 0x00000007)
tveeprom: audio_processor = MSP3415 (type = 6)
bttv0: using tuner=20
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
tvaudio: TV audio decoder + audio/video mux driver
tvaudio: known chips: tda9840,tda9873h,tda9874h/a,tda9850,tda9855,tea6300,tea6
320,tea6420,tda8425,pic16c54 (PV951),ta8874z
bttv0: i2c: checking for TDA9887 @ 0x86... not found
tuner (ivtv): chip found at addr 0xc2 i2c-bus bt878 #0 [sw]
tuner: type set to 20 (Temic PAL_BG (4009 FR5) or PAL_I (4069 FR5)) by bt878 #
0 [sw]
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: registered device radio0
bttv0: PLL: 28636363 => 35468950 .. ok
bt878: AUDIO driver version 0.0.0 loaded
bt878: Bt878 AUDIO function found (0).
ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [LNKD] -> GSI 5 (level, low) -> IR
Q 5
bt878(0): Bt878 (rev 17) at 00:10.1, irq: 5, latency: 32, memory: 0xce800000


Any info as to what is messed up appreciated!

---

### Post by UbuntuJohan on 2006-04-03
First off I would like to thank you for this excellent HOWTO of yours.

With it my mythtv installation was very smooth and simple.
I have followed almost all parts of and I'm now up and running on Mythtv 0.19

I have a couple of minor issues that I would like som help with.
All the HW is brand new here is a list of the most important stuff
ATHLON 64 3200, 1GB RAM, ATI X550 256MB, PVR-350, SAMSUNG 250 GB SATA2
At the moment I have connected the TV to TV_out on the ATI card. I will try to fix the TV-out on PVR-350 when I get some time.


1) The sound and video isn't completly synchronized, I think the video is some 10th of a second ahead of the sound. I saw that there is a setting in myth to use  the video as time reference so I'll try that out. Other than that are there anything else I can tweak to get this right?

2) I followed your advice and installed Xine but I can't play any DVD's with it.
It splashes an error and then returns to myth. I've tried to use it outside myth and then it complained about that it couldn't handle DVD's or somthing similar.
I have installed the codecs etc.. So I don't know what's the problem with this?

3) Is there any way to tweak so that the TV-out displays correctly throughout the whole boot-sequence? Now it's fine for BIOS and grub but then it flickers until GDM and myth is started. It's the same when I shut the machine down.

Cheers
//Johan

---

### Post by jefferbean on 2006-04-05
Thanks so much for the great HOWTO.  I followed your instructions exactly and everything works perfectly.  

When I switched to Ubuntu I thought my PVR-250 was toast.  Now it's one hundred times better than it was in Windows with the crappy WinTV software from Hauppauge.

---

### Post by t0bb3 on 2006-04-08
I decided it was time for me to upgrade to .19, but first I wanted to export some of my recorded shows to XviD so I could burn them to a CD and save them. So I read in your guide how to install nuvexport but ran in to a little problem.

The instructions you have installs nuvexport 0.3, but that doesn't work with myth .18, instead you need to download and install this version of nuvexport: [http://forevermore.net/files/nuvexport/archive/nuvexport-0.2-cvs20050311.tar.bz2](http://forevermore.net/files/nuvexport/archive/nuvexport-0.2-cvs20050311.tar.bz2) When I tried to run the .3 version I got these errors, just for reference:```
No valid recordings found!
DBD::mysql::st execute failed: Unknown column 'basename' in 'field list' at /usr/local/share/nuvexport/mythtv/recordings.pm line 67
```

So if you're running mythtv 0.18, you need version 0.2 of nuvexport

I also decided to install transcode because I was told that gave better picture quality when exporting to XviD, and that was really easy to install, just had to run apt-get install transcode

EDIT: While I was able to get it to install, I can't actually export any video... I'll post back when I know more about the problem at hand.

---

### Post by nzruss on 2006-04-09
[I][I]>  Hardest part was getting the PVR-150 ir blaster to control the SA STB. I found how to do it here

[www.blushingpenguin.com/mark/blog/?p=19](www.blushingpenguin.com/mark/blog/?p=19)

(But ended up having to undo some of the stuff already done wiht Lirc and Lexmit?!) Lots of futsing around, and had to read all the comments to figure out command #'s for cable and satelite are diff  thus instructions are not quite right, but got there!

Displaying tv my picture is offset down and to right a few pixels, and I have a blue line at left and top of screen???? It is only in TV and playback, not visible in the Gnome GUI, thus I suspect something in Myth.

In setup, playback, tv settings, the 2nd to last screen gives overscan and picture displacement. Nothing here corrects it and I am not sure setting anything in picture displacement is actually doing anything.[/I][/I]

I'm having the same two problems - 
- PVR-150 built in IR Blaster not working,  Ive followed the instructions at  [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) 
but with no luck. 

- Thin Blue line under same conditions. 

Ive tried the xvatrr solution, I dont seem to have xvattr installed, and aslo cant get the tarball untared after download. 

Im in /usr/src and using ```
sudo tar xvfz xvattr-1.3.tar.gz
``` but i get ```
tar: xvattr-1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```


anyone help me with the solution? probably something simple... but im tearing my hair out... whats left of it... 

(GEForce 4 MX440, breezy, myth 0.18, DirecTV D10)

---

### Post by nzruss on 2006-04-09
My last issue, is decoupling the tuning from makine the selections in the mythtv guide. 

At the moment when I change channel on the Mythtv it tunes the TV card (of course!). I'm using composite input from my direcTV reciever, so would like the ability to select a channel in the guide that is outside the range of the tuner (i.e channel 249.) 

This will allow me to set the mythtv to channel 249 on the myth box, then I can manually set 249 on the direcTV reciever. (i'll 'book' the show on direcTV, and Set to record the show on Mythtv) that way, the show will be recorded with all the correct meta-data. 

I dont mind doing this until i can get the IR Blaster to control the set-top box. Ive looked everywhere but cant find the answer. Can anyone help?

---

### Post by doc_holiday on 2006-04-13
Maybe a stupid question but I'm stuck:

Now switch to the /usr/src/linux directory:
cd /usr/src/linux

The ll output of the /usr/scr is:
steve@tombstone:/usr/src$ ll
total 39464
lrwxrwxrwx   1 root src        28 2006-04-12 21:02 linux -> /usr/src/linux-source-2.6.10
drwxr-xr-x  18 root root     4096 2006-04-12 20:45 linux-headers-2.6.12-10
drwxr-xr-x   4 root root     4096 2006-04-12 21:02 linux-headers-2.6.12-10-686
drwxr-xr-x  19 root root     4096 2006-03-11 18:35 linux-source-2.6.12
-rw-r--r--   1 root root 40351275 2006-03-11 18:37 linux-source-2.6.12.tar.bz2

Can somebody help me?

---

### Post by LESLIEx317537 on 2006-04-13
Are you talking about Section 5, Installing IVTV?

I assuming you type in this first to get your kernel version:
```
uname -r
```

What's in red was maybe what you missed?
If you get: [COLOR="Red"]2.6.12[/COLOR]-10-686

You then type in:
```
apt-get install linux-source-[COLOR="Red"]2.6.12[/COLOR] linux-headers-`uname -r`
```

Then:
```
tar xvjf /usr/src/linux-source-*.tar.bz2 -C /usr/src/
ln -s /usr/src/linux-source-[COLOR="Red"]2.6.12[/COLOR] /usr/src/linux
ln -s /usr/src/linux /lib/modules/`uname -r`/build
```

You should then be able to cd into the directory /usr/src/linux if you didn't get any errors above:
```
cd /usr/src/linux
```

---

### Post by LESLIEx317537 on 2006-04-14
Great How-To.

I tried to install 0.19 at first, but it didn't work.
So I installed 0.18 and now I'm trying to get 0.19 to go, compiling right now.

Both remotes I have work great with it so far, and I recorded one show allready successfully when I wasn't home.

Thanks...

---

### Post by doc_holiday on 2006-04-14
This is what I get:

root@tombstone:/usr/src# ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
ln: `/usr/src/linux': File exists
root@tombstone:/usr/src# ln -s /usr/src/linux /lib/modules/`uname -r`/build
ln: `/lib/modules/2.6.12-10-686/build/linux': File exists
root@tombstone:/usr/src# cd /usr/src/linux
bash: cd: /usr/src/linux: No such file or directory
root@tombstone:/usr/src# cd /usr/src/
root@tombstone:/usr/src# ll
total 39464
lrwxrwxrwx   1 root src        28 2006-04-12 21:02 linux -> /usr/src/linux-source-2.6.10
drwxr-xr-x  18 root root     4096 2006-04-12 20:45 linux-headers-2.6.12-10
drwxr-xr-x   4 root root     4096 2006-04-12 21:02 linux-headers-2.6.12-10-686
drwxr-xr-x  19 root root     4096 2006-03-11 18:35 linux-source-2.6.12
-rw-r--r--   1 root root 40351275 2006-03-11 18:37 linux-source-2.6.12.tar.bz2

---

### Post by blawson327 on 2006-04-15
Thanks for the tutorial. I am moving along nicely in getting a working Ubuntu setup. One question I have is how do I compile and install the ivtvdev driver for the pvr350's TV-Out? Once I have that installed I can take it from there to get X.org setup. Do I just do a:
make
make install

? I grabbed the source from ivtvdriver.org but didnt see any specific instructions for Ubuntu.  Or is there a precompiled version I can get somewhere? thanks in advance

---

### Post by Smika on 2006-04-16
Now I have this problem.

/usr/bin/ld: cannot find -lqt-mt
collect2: ld returned 1 exit status
make[2]: *** [libmythavcodec-0.19.so.0.19.0] Error 1
make[2]: Leaving directory `/opt/scr/mythtv-0.19/libs/libavcodec'
make[1]: *** [sub-libavcodec] Error 2
make[1]: Leaving directory `/opt/scr/mythtv-0.19/libs'
make: *** [sub-libs] Error 2

---

### Post by water on 2006-04-19
first thanks for a really great howto!

It's been a easy walk to the point where I'm ready to run 

```
cat /dev/video0 > /tmp/test.mpg
``` 
the computer just freezes up instantly,  I'd already posted another thread before I found this one so I'll just link to that one from here : [http://ubuntuforums.org/showthread.php?t=162657]("http://ubuntuforums.org/showthread.php?t=162657") any help is hihly apreciated!

:water

---

### Post by greg963 on 2006-04-28
Has anyone been able to get a homebrew ir-blaster working for mythtv, I have been using one successfully with knoppmyth for a couple years, but I cannot seem to make it work under ubuntu.  I have used the following to create a separate instance of lirc called ledxmit.

[http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html]("http://losdos.dyndns.org:8080/public/mythtv-info/MythTV_DISH_IR_LED_TX_via_Modified_LIRC.html")

[http://www.abarbaccia.com/content/view/21/35/]("http://www.abarbaccia.com/content/view/21/35/")

The first guide I used to create the alternate lirc (ledxmit) and the second I used to start things at boot.  I currently have the ledxmit working but the led ir is always on (I have checked and rechecked polarity no trouble there), I think maybe it is related to the serial port but I am at a loss as to what to do.  

](*,)

P.S Other than being unable to change channels mythtv works beutifully on amd64-k8.  Thanks for the How-To.

---

### Post by Smika on 2006-05-06
I am trying o download pvr_2.0.24.23035.zip but the ftp site is down. Can somebody attach this file here and also the pvr_1.18.21.22254_inf.zip?

Thanks!

Smika

Edit (Site is back)

---

### Post by Eduardo! on 2006-05-06
was actually just about to post asking for the same thing, haven't been able to get into ivtv's download site for the firmwares for two days of trying. need the firmware for a pvr-250 on ivtv 0.4.0, 2.6.12-10-686 kernel not that it probably matters.

---

### Post by Smika on 2006-05-07
Hello,

Now the site is back I was happy for 5 minutes, because now i have some new errors in dmesg. I have a PVR 150MCe (same as the PVR150). I have some errors in the dmesg:

[4294693.735000] ivtv:  ==================== START INIT IVTV ====================
[4294693.735000] ivtv:  version 0.4.4 (tagged release) loading
[4294693.735000] ivtv:  Linux version: 2.6.12-10-686 686 gcc-3.4
[4294693.735000] ivtv:  In case of problems please include the debug info between
[4294693.735000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294693.735000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294693.740000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294693.740000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[4294693.740000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294693.800000] tveeprom: The eeprom says no radio is present, but the tuner type 60
[4294693.800000] tveeprom: indicates otherwise. I will assume that radio is present.
[4294693.800000] tveeprom: ivtv version
[4294693.800000] tveeprom: Hauppauge: model = 26559, rev = C260, serial# = 8225385
[4294693.800000] tveeprom: tuner = LG S001D MK3 (idx = 60, type = 38)
[4294693.800000] tveeprom: tuner fmt = PAL(B/G) PAL(I) SECAM(L/L') PAL(D/K) (eeprom = 0x74, v4l2 = 0x00400e17)
[4294693.800000] tveeprom: audio processor = CX25843 (type = 25)
[4294693.800000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294693.800000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294693.833000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294693.833000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294693.991000] cx25840 0-0044: ivtv driver
[4294693.991000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294694.519000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[4294694.576000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294694.625000] wm8775 0-001b: ivtv driver
[4294694.625000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294694.632000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294694.648000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[4294694.648000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294695.302000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4294695.302000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4294695.302000] ivtv0 warning: failed loading encoder firmware
[4294695.302000] ivtv0 warning: Error loading firmware -3!
[4294695.302000] ivtv0: Error -3 initializing firmware.
[4294695.323000] ivtv0: Error -12 on initialization
[4294695.323000] ivtv: probe of 0000:00:09.0 failed with error -12
[4294695.323000] ivtv:  ====================  END INIT IVTV  ===================


This is my formware:

drwxr-xr-x  3 root root   4096 May  6 07:33 ..
-rw-r--r--  1 root root 262144 May  7 10:28 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 May  7 10:28 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 May  7 10:29 v4l-cx25840.fw
-r--r--r--  1 root root 376836 May  7 10:29 v4l-cx2341x-enc.fw.orig
-rw-r--r--  1 root root 155648 May  7 10:29 v4l-cx2341x-init.mpg
lrwxrwxrwx  1 root root     41 May  7 10:30 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-rw-r--r--  1 root root 262144 May  7 10:42 v4l-cx2341x-enc.fw
drwxr-xr-x  2 root root   4096 May  7 10:42 .


Can somebody help me?

Thanks a lot,

Smika

---

### Post by urvaius on 2006-05-08
Thanks for the great guide. everything was going ok until i compile. i'm a newbie so forgive me. i'm on amd 64. it seemed to compile fine. (first time doing this) mythtv did not setup a user. I am stuck when i try to  change the passwd for mythtv it says unknowd user mythtv. how do I do this manually or did I do something wrong 
Thanks for any help

---

### Post by DDM on 2006-05-08
I use a PVR-150 as well; do any of you transcode your video to xvid after recording? I'm basically looking for a way to downsample some of my recordings in order to make better use of my HD space. I used the mpeg4 transcode option a little, and the quality was pretty bad despite the (still) large file size. 

In other words, are there any scripts out there that will allow me to transcode with mencoder while retaining the newly transcoded files in the Previously Recorded menu to have them work exactly like they did before transcoding?

---

### Post by barbex on 2006-05-11
[QUOTE=Smika]I have a PVR 150MCe (same as the PVR150). I have some errors in the dmesg:

[...]
[4294694.519000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[...]
[4294694.648000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294695.302000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[4294695.302000] ivtv0: did you put the firmware in the hotplug firmware directory?[/QUOTE]

Did you really, really put the firmware in the correct directory? That directoy may be different from other systems for your distribution.

If it still does not work then you have proven that your card is not the same as a PVR150. As far as I know, MCE Products are specifically made for Windows MCE and will not work with Linux.

---

### Post by Smika on 2006-05-11
Sorry that I not edit my question. Because My Tv card 150MCE works fine now. The only thing that I must do was rebooting my computer. So the PVR150MCE works fine with linux. Now I have some other problems with mythtv, but i will search for a solution first before i ask it here.

Thanka  lot,

Smika

---

### Post by [Yatta] on 2006-05-11
[QUOTE=barbex]As far as I know, MCE Products are specifically made for Windows MCE and will not work with Linux.[/QUOTE]

I have PVR-150MCE ... it works GREAT in Linux. Only problem i have is my cable listings :-( I'm in Jamaica and i get my cable from ALL over the US so i would ave to create a custimzed XMLTV fiile ](*,)

---

### Post by Smika on 2006-05-11
The only problem that I have now, is that when i give the command:

mythbackend &mythfrontend, he will not start, becuase he can not write to a file. But when i first login with sudo in the konsole and then I do mythbackend &mythfrontend, then the mythbacken will run, but the m,ythfrontend will not? Mythfrontend will only run when i am not logn with sudo. How can i solve this problem? because now i can only run mythtv and can ony see and record tv, but i have not the menu. Please help.

Smika

---

### Post by Titus A Duxass on 2006-05-11
You will have to clarify your request a bit, it's a little confusing.

"mythbackend &mythfrontend" - I hope this is a typo, it should be mythfrontend & mythbackend.

"Mythfrontend will only run when i am not logn with sudo." - That is what is supposed to happen, you should be logged in as the user Mythtv.

"because now i can only run mythtv and can ony see and record tv, but i have not the menu." - Are you talking about the mythtv menu? What do you see when you start myth?

---

### Post by Smika on 2006-05-11
Sorry for my bad request. I am on my work now, so I have not very much time, sorry for it.

Thanks for tip 1, I will try it.

Tip 2: I don;t know how i can login asmythtv user. But i will find out tonight. If i can't find it, I will let you know.

Tip 3: I don;t see the mythtv menu. When I start mythtv, I see only a tv channel and i can record when i press R. SO i don;t see a menu.

I hope you understand this.

Smika

---

### Post by Titus A Duxass on 2006-05-11
Logging in as mythtv is normal, during Hyams HowTo user mythtv is created.

When you reboot who do you log in as?

I don't understand the lack of menus, I recommend uninstalling mythtv and then reinstalling it.

Don't give up hope, I went through the HowTo at least 3 times before I finally got it to work.

Each installation varies from the HowTo because of the hardware you use.

Maybe HowTo should be called HowIdidits.

I've just checked the howto and in step 6.1 during the mythtv install:
"The mythtv install that you just ran automatically created a "mythtv" user. "
So when you reboot login as mythtv after you have set a password for mythtv.

---

### Post by rgarlin on 2006-05-15
I was following this HOWTO, [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html), with Ubuntu 5.10, Breezy and PVR-150 Card. Everything was working OK until the line: cat /dev/video0 > /tmp/test.mpg, because I do not have a video0 file in my /dev directory, I don't know why that is. Did a driver not load properly, everything seem to work OK.

---

### Post by Smika on 2006-05-15
I reply your message 15 minutes ago, but I think there was something wrong. But I had the same problem. You must reboot your computer and wait 30 second. Then yu must turn your computer on and everything must work fine.

Smika

---

### Post by chiefy on 2006-05-17
First off: thanks for the guide, it has helped me immensly!

The box: AMD64 3000+ / Foxconn Winfast nForce 430 w/ 6150 / PATA IDE HDD / 1GB Ram 

The software: Breezy w/ 2.6.12-10-amd64-generic / mythTV 0.18 (64 bit compiled debs from guide)

The questions:

[COLOR="Gray"]1) I have myth working great with live TV, but I tried recording some stuff last night and it seems to stutter a single from every 30 seconds or so, also scenes with fast movement get "blocky" I didn't get a chance to check top when it was recording, as it was late-late night. Any ideas on what could be causing this?
[/COLOR]
(answering my own questions here)
Seemed to fix itself after a reboot.


[COLOR="Gray"]2) I want to install mythDVD mythVideo mythGame etc. but I can't do apt-get install ... because it doesn't recognize my 64bit mythTV install. I tried downloading from the myth site and compliling but I get a bunch of errors. I am a newbie, anyone have any ideas on compiling plugins for 0.18/64bit?[/COLOR]

I took a deep breath and "rolled my own" last night, following the gude for 0.19 and all went well. I'm not sure if this is truly "tuned" for 64 bit, but ehhh, at this point, I don't really care.

---

### Post by MRKiscaden on 2006-05-20
Using the guide, everything has gone perfectly. However when I get to the command: cat /dev/video0 > /tmp/test.mpg The file created does not contain data (Zero bytes in file). When I try to tune to a different channel, this is what I get:
[INDENT]
ivtv-tune -c 5 -d /dev/video0
/dev/video0: 77.250 MHz  (Signal Detected)[/INDENT]

I assume this means that Ivtv detected some sort of signal on my line. Additionally, if I use this command here is what I get:

```
sudo mplayer -vo xv /dev/video0
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 2)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /dev/video0.
Cache fill:  0.00% (0 bytes)
```

Note that a video window does not open. I can only assume there is something wrong with the capture device, but I don't know where to go from here.

```
[4294698.004000] ivtv:  ==================== START INIT IVTV ====================
[4294698.004000] ivtv:  version 0.4.4 (tagged release) loading
[4294698.004000] ivtv:  Linux version: 2.6.12-10-686 686 gcc-3.4
[4294698.004000] ivtv:  In case of problems please include the debug info between
[4294698.004000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294698.004000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294698.012000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294698.017000] PCI: Enabling device 0000:00:09.0 (0014 -> 0016)
[4294698.017000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[4294698.017000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294698.060000] tveeprom: ivtv version
[4294698.060000] tveeprom: Hauppauge: model = 26032, rev = C199, serial# = 8358359
[4294698.060000] tveeprom: tuner = TCL 2002N 5H (idx = 99, type = 50)
[4294698.060000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4294698.060000] tveeprom: audio processor = CX25841 (type = 23)
[4294698.060000] tveeprom: decoder processor = CX25841 (type = 1c)
[4294698.060000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294698.129000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294698.129000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61][4294698.262000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294698.395000] cx25840 0-0044: ivtv driver
[4294698.395000] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[4294698.622000] ts: Compaq touchscreen protocol output
[4294700.954000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294701.003000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294701.064000] wm8775 0-001b: ivtv driver
[4294701.064000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294701.070000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294701.851000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294702.061000] ivtv0: Encoder revision: 0x02050032
[4294702.062000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[4294702.065000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[4294702.067000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[4294702.069000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[4294702.070000] tuner: type set to 50 (TCL 2002N) by ivtv i2c driver #0
[4294702.258000] ivtv0: Initialized WinTV PVR 150, card #0
[4294702.258000] ivtv:  ====================  END INIT IVTV  ====================
```
```

 ls -ltra /usr/lib/hotplug/firmware/
total 1076
drwxr-xr-x  3 root root   4096 2006-05-05 14:04 ..
-rw-r--r--  1 root root 262144 2006-05-07 10:04 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-05-07 10:04 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 2006-05-07 10:04 v4l-cx25840.fw
-r--r--r--  1 root root 376836 2006-05-07 10:05 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2006-05-07 10:05 v4l-cx2341x-init.mpg
lrwxrwxrwx  1 root root     41 2006-05-07 10:06 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
```



I have not installed MythTV at this point.
the ivtvctl reports that I am using The Tuner for both Audio and Video
I am in the US, I am not using a cable box. Any and All help would be great.

---

### Post by Titus A Duxass on 2006-05-21
I have never had any success getting the test.mpg to work.
I just ignored it in the end.

The TV works okay in myth.

---

### Post by chiefy on 2006-05-22
[QUOTE=MRKiscaden]I have not installed MythTV at this point.
the ivtvctl reports that I am using The Tuner for both Audio and Video
I am in the US, I am not using a cable box. Any and All help would be great.[/QUOTE]

You might want to try upgrading the firmware. I was having a lot of problems with my brand new pvr-150, and I upgraded to the latest version and voila!

Also, [Gossamer Threads]("http://www.gossamer-threads.com/lists/ivtv/users/") was a huge resource for me, you might find someone else with the same problem.

---

### Post by EmmEff on 2006-05-25
I've been trying in vain to get XvMC working on my Breezy system but to no avail...  if I enable it (as per the docs on the MythTV Wiki and the mailing list clues), as soon as MythTV 0.19 (incl. patches from SVN) goes to disable live TV, it crashes X.

This occurs with several versions of the nVidia drivers.  I am fairly confident my system is configured properly as I've used the examples from the various docs and mailing list posts to compare with other users' settings.

Can anybody shed any light?

---

### Post by exir on 2006-06-02
thnx for the howto...its an good one :)

im now only with one problem and hope that somebody can help me out with it.

im at the point off installing / configuring mythtv
at the point that you have to login as mythtv user and run mythtv-setup went all fine.

after finishing step 3 im getting the message that i have to use 'mythfilldatabase --manual instead of mythfilldatabase

at first when i wanted to run this he couldnt find the config file with the channels. i looked in the /home/root/.../ where the config file was located. i copyd it to the right folder /home/mythtv/...../ so that problem has been solved now. 

the problem that im currently still have is when i run mythfulldatabase --manual im getting this

<code>
sh-3.00$ mythfilldatabase --manual
###
### Running in manual channel configuration mode.
### This will ask you questions about every channel.
###
2006-06-02 19:22:49.701 New DB connection, total: 1
2006-06-02 19:22:49.773 New DB connection, total: 2
----------------- Start of XMLTV output -----------------
2006-06-02 19:22:49.838 New DB connection, total: 3
using config filename /home/mythtv/.xmltv/tv_grab_nl.conf
downloading summary
[http://www.tvgids.nl/zoeken/?station=1&genre=&interval=3&timeslot=0:](http://www.tvgids.nl/zoeken/?station=1&genre=&interval=3&timeslot=0:) date in page 2006060400:00:00 (Zondag 04 juni 2006) doesn't match expected 2006-06-05 at /usr/bin/tv_grab_nl line 1171.
------------------ End of XMLTV output ------------------
Error in 4:170: unexpected end of file
Updating icons for sourceid: 1
2006-06-02 19:22:58.721 New DB connection, total: 4
Updated programs: 0  Unchanged programs: 0
Failed to fetch some program info
</code>

as you see he is going to look at an url to get some data. It hangs on the part that the page it is requesting is giving an dat of 4th of june. today it is the 2nd of june and the date settings of my ubuntu dapper are correct. When i change them to the 4th of june and running the command again, he gives the same error but than that he cannot find the date 2nd of june.

Has anybody been familar with this problem or know how to set up the mythtv database?

thnx in advance

---

### Post by schnarkle on 2006-06-23
Pure hell for me.

WinTV-PVR350

[17179592.420000] ivtv:  ==================== START INIT IVTV ====================
[17179592.420000] ivtv:  version 0.4.5 (tagged release) loading
[17179592.420000] ivtv:  Linux version: 2.6.15-25-686 SMP preempt 686 gcc-4.0
[17179592.420000] ivtv:  In case of problems please include the debug info between
[17179592.420000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179592.420000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179592.600000] intel8x0_measure_ac97_clock: measured 54081 usecs
[17179592.600000] intel8x0: clocking to 48000
[17179592.600000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179592.600000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179592.600000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179592.644000] tg3.c:v3.47 (Dec 28, 2005)
[17179592.644000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[17179592.644000] ACPI: PCI Interrupt 0000:40:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179592.644000] PCI: Setting latency timer of device 0000:40:00.0 to 64
[17179592.660000] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179592.660000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179592.664000] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:14:38:c6:b7:64
[17179592.664000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17179592.664000] eth0: dma_rwctrl[76180000]
[17179592.672000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179592.712000] tveeprom 0-0050: The eeprom says no radio is present, but the tuner type
[17179592.712000] tveeprom 0-0050: indicates otherwise. I will assume that radio is present.
[17179592.712000] tveeprom 0-0050: Hauppauge model 48132, rev K168, serial# 8809149
[17179592.712000] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[17179592.712000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179592.712000] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
[17179592.712000] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[17179592.712000] tveeprom 0-0050: has radio, has IR remote
[17179592.780000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179592.780000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17179592.976000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179593.120000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[17179593.180000] saa7127 0-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[17179593.180000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[17179593.204000] ivtv0: Failed to load module msp3400
[17179593.220000] tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179593.220000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17179593.884000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179593.908000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[17179594.132000] ivtv0: Encoder revision: 0x02050032
[17179594.140000] ivtv0: Decoder revision: 0x02020023
[17179594.140000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179594.140000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179594.140000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179594.140000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179594.140000] ivtv0: Create encoder radio stream
[17179594.140000] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1024KB total)
[17179594.140000] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (1024KB total)
[17179594.140000] ivtv0: Create decoder VOUT stream
[17179594.140000] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (1024KB total)
[17179594.216000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[17179594.324000] tuner 0-0061: type set to 47 (LG NTSC (TAPE series))
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40086d11!
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40085618!
[17179594.412000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179594.412000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179594.412000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x402c5639!
[17179594.512000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179594.512000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179594.512000] ivtv0: Initialized WinTV PVR 350, card #0
[17179594.512000] ivtv:  ====================  END INIT IVTV  ====================
[17179594.988000] Intel ISA PCIC probe: not found.
[17179595.068000] lp0: using parport0 (interrupt-driven).
[17179595.200000] Adding 2779172k swap on /dev/sdb5.  Priority:-1 extents:1 across:2779172k
[17179595.908000] NET: Registered protocol family 17
[17179596.496000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179596.496000] tg3: eth0: Flow control is off for TX and off for RX.
[17179597.284000] NET: Registered protocol family 10
[17179597.288000] lo: Disabled Privacy Extensions
[17179597.288000] IPv6 over IPv4 tunneling driver
[17179597.584000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.584000] md: bitmap version 4.39
[17179598.804000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179599.256000] cdrom: open failed.
[17179599.504000] cdrom: open failed.
[17179599.504000] cdrom: open failed.
[17179600.304000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179600.332000] NTFS volume version 3.1.
[17179600.404000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179602.676000] pcc_acpi: loading...
[17179602.688000] ACPI: Power Button (FF) [PWRF]
[17179602.692000] ACPI: Power Button (CM) [PBTN]
[17179602.732000] ibm_acpi: ec object not found
[17179602.808000] wmi_add device=dfe18c00
[17179602.808000] calling WQBA
[17179608.084000] eth0: no IPv6 routers present
[17179608.560000] ppdev: user-space parallel port driver
[17179609.560000] apm: BIOS not found.
[17179615.040000] Bluetooth: Core ver 2.8
[17179615.040000] NET: Registered protocol family 31
[17179615.040000] Bluetooth: HCI device and connection manager initialized
[17179615.040000] Bluetooth: HCI socket layer initialized
[17179615.076000] Bluetooth: L2CAP ver 2.8
[17179615.076000] Bluetooth: L2CAP socket layer initialized
[17179615.080000] Bluetooth: RFCOMM socket layer initialized
[17179615.080000] Bluetooth: RFCOMM TTY layer initialized
[17179615.080000] Bluetooth: RFCOMM ver 1.7
[17179617.724000] /dev/vmmon[5267]: Module vmmon: registered with major=10 minor=165
[17179617.724000] /dev/vmmon[5267]: Module vmmon: initialized
[17179618.272000] /dev/vmnet: open called by PID 5302 (vmnet-bridge)
[17179618.272000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179618.272000] /dev/vmnet: port on hub 0 successfully opened
[17179618.272000] bridge-eth0: enabling the bridge
[17179618.272000] bridge-eth0: up
[17179618.272000] bridge-eth0: already up
[17179618.272000] bridge-eth0: attached
[17179618.316000] /dev/vmnet: open called by PID 5316 (vmnet-natd)
[17179618.316000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179618.316000] /dev/vmnet: port on hub 8 successfully opened
[17179628.296000] /dev/vmnet: open called by PID 5441 (vmnet-netifup)
[17179628.296000] /dev/vmnet: port on hub 8 successfully opened
[17179628.296000] /dev/vmnet: open called by PID 5440 (vmnet-netifup)
[17179628.296000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179628.296000] /dev/vmnet: port on hub 1 successfully opened
[17179628.396000] /dev/vmnet: open called by PID 5467 (vmnet-dhcpd)
[17179628.396000] /dev/vmnet: port on hub 8 successfully opened
[17179628.396000] /dev/vmnet: open called by PID 5466 (vmnet-dhcpd)
[17179628.396000] /dev/vmnet: port on hub 1 successfully opened
[17179638.412000] vmnet8: no IPv6 routers present
[17179639.296000] vmnet1: no IPv6 routers present
[17179654.888000] NET: Registered protocol family 4
[17179654.940000] NET: Registered protocol family 3
[17179654.988000] NET: Registered protocol family 5
[17179714.868000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179714.868000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179714.872000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40086d11!
[17179714.872000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179714.872000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179714.972000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179714.972000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179714.972000] ivtv0 warning: i2c client addr: 0x40 not found for command 0xc054561d!

and when trying tvtime for example to test I get:
ivtv: Invalid argument
Cannot open capture device /dev/video0

ANY ideas?  Please?    :)

---

### Post by fxer on 2006-06-24
Is [http://labs.zap2it.com](http://labs.zap2it.com) down or something? I can't seem to connect to it to get the channel lineup, and am getting the error:

Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

2006-06-24 16:50:31.175 Fetching lineups from DataDirect service...
--16:50:31--  [http://datadirect.webservices.zap2it.com/tvlistings/xtvdService](http://datadirect.webservices.zap2it.com/tvlistings/xtvdService)
           => `-'
Resolving datadirect.webservices.zap2it.com... 206.18.98.160
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Connecting to datadirect.webservices.zap2it.com|206.18.98.160|:80... connected.
HTTP request sent, awaiting response... 500 Internal Server Error
16:50:33 ERROR 500: Internal Server Error.


ivtv works great, it gives me audio and video, but can't get past this part in the mythtv setup now, any ideas? (Ubuntu Dapper, Myth packages 0.18.1, ivtv 0.4.6 on a brand new PVR-150)

---

### Post by gyro on 2006-06-26
I noticed a post very similar to mine earlier on in this thread but I could not seem to find a follow up or one the helped me to solve my problem or maybe its problems...

I am trying to upgrade to version 0.19 after completeing the basic install (no remote or boot directly to myth yet etc.) of 0.18    successfully, other than the mythfilldatabase not working part due to mysql 5 being incompatible.  Rather than downgrade to mysql 4 I decided to upgrade.

Upgrading has gone well up until this step:

> ./configure --prefix=/usr/local/mythtv-0.19

where I get these results:

> # Basic Settings
Compile type     release
Compiler cache   no
DistCC           no
Install prefix   /usr/local/mythtv-0.19
CPU              x86 (model name        : AMD Athlon(tm) XP 1900+)
Big Endian       no
MMX enabled      yes
Vector Builtins  yes

# Input Support
Joystick menu    yes
lirc support     yes
Video4Linux sup. yes
ivtv support     yes
FireWire support no
DVB support      no [/usr/include]
DBox2 support    yes

# Sound Output Support
OSS support      yes
ALSA support     yes
aRts support     yes
JACK support     yes
DTS passthrough  no

# Video Output Support
x11 support      yes
xrandr support   yes
xv support       yes
XvMC support     no
XvMC VLD support no
XvMC pro support no
XvMC libs
OpenGL vsync     no
DirectFB         no

# Misc Features
[COLOR="DarkOrchid"]DVD playback     no[/COLOR]
Frontend         yes
Backend          yes

Creating libs/libmyth/mythconfig.h and libs/libmyth/mythconfig.mak

libs/libmyth/mythconfig.h is unchanged


as you can see it says 'dvd playback no' in version 0.18 I *was* able to watch dvds.

okay so that is the first problem next is when I reach this step:

> ./configure --prefix=/usr/local/mythtv-0.19 --enable-transcode --enable-vcd

and again here are the results:

> Configuration settings:

        MythBrowser   plugin will be built
        MythControls  plugin will be built
        MythFlix      plugin will be built
        MythDVD       plugin will be built
        MythGallery   plugin will be built
        MythGame      plugin will be built
        MythMusic     plugin will be built
        MythNews      plugin will be built
        MythPhone     plugin will be built
        MythVideo     plugin will be built
        MythWeather   plugin will be built
        VCD           support will be included in MythDVD
        Transcode     support will be included in MythDVD
        OpenGL        support will be included in MythGallery
        EXIF          support will be included in MythGallery
        OpenGL        support will be included in MythMusic
        FFTW v.2      support will be included in MythMusic
        SDL           support will be included in MythMusic
       [COLOR="DarkOrchid"] AAC           support will not be included in MythMusic
        FESTIVAL      support will not be included in MythPhone[/COLOR]


You can see here that I need to install AAC, and festival.  I have used the search feature pointed to in the dhyams excellent walkthrough ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)) and with that is was able to get support for most of the plugins however the last two have somehow eluded me.

I have also run 'apt-get build-dep' for both mythtv and mythplugins.  Each did   have some dependencies that were downloaded and installed.

now my third and final problem (I hope ;))

when I run this command:

> root@brian-desktop:/opt/src/mythplugins-0.19# qmake mythplugins.pro
root@brian-desktop:/opt/src/mythplugins-0.19# make


this is how the compile turns out:

> cd mythbrowser && make -f Makefile
make[1]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser'
cd mythbrowser && make -f Makefile
make[2]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
g++ -c -pipe -Wall -W -fomit-frame-pointer -D_REENTRANT  -D_GNU_SOURCE -DPREFIX=\"\" -D_FILE_OFFSET_BITS=64 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/include -I/usr/kde/3.3/include -I/include -I/usr/include/kde -I/opt/kde3/include -I/usr/include/qt3 -o main.o main.cpp
main.cpp:20:30: error: mythtv/exitcodes.h: No such file or directory
main.cpp: In function 'int main(int, char**)':
main.cpp:90: error: 'FRONTEND_EXIT_NO_MYTHCONTEXT' was not declared in this scope
main.cpp:96: error: 'FRONTEND_EXIT_DB_ERROR' was not declared in this scope
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
make[1]: *** [sub-mythbrowser] Error 2
make[1]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser'
make: *** [sub-mythbrowser] Error 2
root@brian-desktop:/opt/src/mythplugins-0.19#


Now I am pretty much a novice linux user, but it seems to me that even with the other to errors mythplugins compile should have gotten a little further.

If anyone has any pointers, could explain to me where to get the proper AAC/festval packages, tell me what caused the error when compiling or just illuminate things a little bit it would be greatly appreciated.

thanks for any help in advance,
-brain

---

### Post by leonardoxiao on 2006-08-17
> **urvaius said:**
> Thanks for the great guide. everything was going ok until i compile. i'm a newbie so forgive me. i'm on amd 64. it seemed to compile fine. (first time doing this) mythtv did not setup a user. I am stuck when i try to  change the passwd for mythtv it says unknowd user mythtv. how do I do this manually or did I do something wrong 
Thanks for any help

I have exactly the same problem. "mythtv" account is not created during "make install". Where is the log I can search for error?

Thanks!

---

### Post by nzruss on 2006-08-18
Hi guys, 

I built my Mythtv box ages ago and just got around to [posting my build.]("http://www.nzrussmyth.blogspot.com/")

I used Daniels how-to, then went away to knoppmyth for a while then went back to Daniels How-to on Ubuntu which I'm super happy with. 

Knoppmyth is great for the auto-detect and auto set-up stuff, but I prefer Ubuntu underneath. The extra scripts Daniel added are awesome (remote button to enter and exit mythtv, and jump-points etc). 

It would be really nice if someone could re-use the knoppmyth install scripts in Ubuntu as an auto mythtv installer.. I'm too new to scripting to try to figure out how to do this though. 

Anyway, if your interested you can check out [my hardware build here]("http://www.nzrussmyth.blogspot.com/"). Feel free to leave comments on my blog too. 

Cheers

NZRuss. 

(I'm looking forward to Eft!)

---

### Post by trubblemaker on 2006-11-15
> **schnarkle said:**
> Pure hell for me.

WinTV-PVR350

[17179592.420000] ivtv:  ==================== START INIT IVTV ====================
[17179592.420000] ivtv:  version 0.4.5 (tagged release) loading
[17179592.420000] ivtv:  Linux version: 2.6.15-25-686 SMP preempt 686 gcc-4.0
[17179592.420000] ivtv:  In case of problems please include the debug info between
[17179592.420000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179592.420000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179592.600000] intel8x0_measure_ac97_clock: measured 54081 usecs
[17179592.600000] intel8x0: clocking to 48000
[17179592.600000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179592.600000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[17179592.600000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179592.644000] tg3.c:v3.47 (Dec 28, 2005)
[17179592.644000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[17179592.644000] ACPI: PCI Interrupt 0000:40:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179592.644000] PCI: Setting latency timer of device 0000:40:00.0 to 64
[17179592.660000] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179592.660000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179592.664000] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:14:38:c6:b7:64
[17179592.664000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17179592.664000] eth0: dma_rwctrl[76180000]
[17179592.672000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179592.712000] tveeprom 0-0050: The eeprom says no radio is present, but the tuner type
[17179592.712000] tveeprom 0-0050: indicates otherwise. I will assume that radio is present.
[17179592.712000] tveeprom 0-0050: Hauppauge model 48132, rev K168, serial# 8809149
[17179592.712000] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[17179592.712000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179592.712000] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
[17179592.712000] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[17179592.712000] tveeprom 0-0050: has radio, has IR remote
[17179592.780000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179592.780000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17179592.976000] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179593.120000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[17179593.180000] saa7127 0-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[17179593.180000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[17179593.204000] ivtv0: Failed to load module msp3400
[17179593.220000] tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179593.220000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17179593.884000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179593.908000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[17179594.132000] ivtv0: Encoder revision: 0x02050032
[17179594.140000] ivtv0: Decoder revision: 0x02020023
[17179594.140000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179594.140000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179594.140000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179594.140000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179594.140000] ivtv0: Create encoder radio stream
[17179594.140000] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1024KB total)
[17179594.140000] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (1024KB total)
[17179594.140000] ivtv0: Create decoder VOUT stream
[17179594.140000] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (1024KB total)
[17179594.216000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[17179594.324000] tuner 0-0061: type set to 47 (LG NTSC (TAPE series))
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40086d11!
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179594.364000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40085618!
[17179594.412000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179594.412000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179594.412000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x402c5639!
[17179594.512000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179594.512000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179594.512000] ivtv0: Initialized WinTV PVR 350, card #0
[17179594.512000] ivtv:  ====================  END INIT IVTV  ====================

and when trying tvtime for example to test I get:
ivtv: Invalid argument
Cannot open capture device /dev/video0

ANY ideas?  Please?    :)

I had this error and I can't remember what fixed it.  I think it was removing the softlinks, from the /etc/firmware directory, by just coping the files to those locations.

The other thing I had to play with was the /etc/modprobe.d/aliases file.  If you followed some how to that had you adding things into that remove them.  Here is the best [mythtv howto on the planet, written for us Ubuntu folks]("https://help.ubuntu.com/community/MythTV")

hope this helps

---

### Post by nesher13 on 2006-11-16
Hexion and all,

Sorry for the kind-a-newbie question, I am trying to set up a Avermedia TV
Capture98 and everything goes normal until set 5 (make ). The result  is

root@tvmyth:/usr/src/lirc-0.8.1pre2# make
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=config.h \
             /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/usr/src/lirc-0.8.1pre2'
Making all in drivers
make[2]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.17-10-generic/build/ SUBDIRS=/usr/src/lirc-0.8.1pre2/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
mkdir -p /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_versions
rm -f /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.1pre2/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/../.. -I/lib/modules/2.6.17-10-generic/build//include/ -I/lib/modules/2.6.17-10-generic/build//drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.c
  Building modules, stage 2.
make -rR -f /usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.17-10-generic/Module.symvers -I /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/Modules.symvers -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/Modules.symvers /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.o
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.lirc_dev.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -DMODULE -c -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.mod.o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.ko /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.mod.o
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
mv Makefile.automake Makefile
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
Making all in lirc_gpio
make[3]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.17-10-generic/build/ SUBDIRS=/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
mkdir -p /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.tmp_versions
rm -f /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.lirc_gpio.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../.. -I/lib/modules/2.6.17-10-generic/build//include/ -I/lib/modules/2.6.17-10-generic/build//drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_gpio)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_gpio)" -c -o /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/.tmp_lirc_gpio.o /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:51:23: error: btcx-risc.h: No such file or directory
In file included from /usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:56:
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:128: error: field ‘top’ has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:129: error: field ‘bottom’ has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:365: error: field ‘main’ has incomplete type
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/../drivers/media/video/bt8xx/bttvp.h:232:1: warning: this is the location of the previous definition
make[5]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2
root@tvmyth:/usr/src/lirc-0.8.1pre2# make install
Making install in drivers
make[1]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers'
Making install in lirc_dev
make[2]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[3]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
test -c /dev/lirc || (/bin/bash ../../mkinstalldirs /dev && /bin/mknod /dev/lirc c 61 0)
/bin/bash ../../mkinstalldirs /lib/modules/2.6.17-10-generic/misc
mkdir /lib/modules/2.6.17-10-generic/misc
 /usr/bin/install -c -m 644 lirc_dev.ko /lib/modules/2.6.17-10-generic/misc/lirc_dev.ko
/sbin/depmod -a
make[3]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
Making install in lirc_gpio
make[2]: Entering directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[2]: *** No rule to make target `install'.  Stop.
make[2]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers/lirc_gpio'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.1pre2/drivers'
make: *** [install-recursive] Error 1


What am I doing worng?
Reply With Quote

---

### Post by trubblemaker on 2006-11-16
> **nesher13 said:**
> Hexion and all,

Sorry for the kind-a-newbie question, I am trying to set up a Avermedia TV
Capture98 and everything goes normal until set 5 (make ). The result  is

What am I doing worng? 


not trying to put you down and I'm not experienced with the actual card but this is a forum about Hauppage pvr-X50, you would probably be more likely to get a response if you posted a new thread, as it's more likely that  "Avermedia TV Capture98" users won't read a  Hauppage pvr-X50 thread. But they'll probable read a "Avermedia TV Capture98 issues with lirc" thread.

another helpful thread for you might be [this post]("http://ubuntuforums.org/showthread.php?t=288229").  I got it by typing "capture 98 issues lirc" into google and hitting I'm feeling lucky.

and I want to thank you for making me look into it as I"m not going to use that thread to setup lirc on my myth box, so thanks.

---

