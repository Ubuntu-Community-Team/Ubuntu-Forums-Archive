---
title: "No audio Ubuntu 14.04 Intel HDA"
date: 2015-02-28
forum: New to Ubuntu
---

### Post by Tim_Stephens on 2015-02-28
Hi, I'm new to ubuntu and struggling with a sound issue!

First I discovered from a post I made in launchpad forum that ubuntu wasn't recognising the sound card, someone there suggested I add this to  the
 /etc/modprobe.d/alsa-base.conf file:

options snd-hda-intel enable_msi=0

This enables the sound card, but only the digital spdif ouput not the speakers or headphone output!

Then tried the following:
comment out (put a # in front of) or remove 
options snd-cmipci mpu_port=0x330 fm_port=0x388

and add 
options snd-hda-intel model=3stack-dig
Didn't work, so tried adding:

options snd-hda-intel model=laptop-dig
no difference, so:

options snd-hda-intel model=basic
still no difference!

Anyone any ideas?

Cheers,
Tim


```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sun Mar  1 11:24:44 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 14.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.2 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      higraded
Product Name:      Alviso & ICH6M Chipset
Product Version:   Not Applicable
Firmware Version:  H.0B-1203-8A20


!!Kernel Information
!!------------------

Kernel release:    3.13.0-46-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-46-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb0000000 irq 11


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:2668 (rev 04)
    Subsystem: 1509:3741


!!Modprobe options (Sound related)
!!--------------------------------

snd_hda_intel: enable_msi=0
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_hda_intel: model=basic
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
    align_buffer_size : -1
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : 0
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    model : basic,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N
    snoop : Y


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC260
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0260
Subsystem Id: 0x02600000
Revision Id: 0x100400
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3
  Power: setting=D0, actual=D0
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC260 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC260 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x04 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC260 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x0a 0x0a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 7
     0x12 0x13 0x14* 0x15 0x16 0x0f 0x10
Node 0x05 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC260 Alt Analog", type="Audio", device=2
  Amp-In caps: ofs=0x00, nsteps=0x23, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 8
     0x12* 0x13 0x14 0x15 0x16 0x07 0x0f 0x10
Node 0x06 [Audio Input] wcaps 0x100391: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC260 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x19
Node 0x07 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="CD Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="CD Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Aux Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Aux Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=3, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0xc1 0xc1] [0xc1 0xc1] [0x80 0x80] [0xc1 0xc1] [0xc1 0xc1] [0x80 0x80] [0x80 0x80]
  Connection: 8
     0x12 0x13 0x14 0x15 0x16 0x17 0x0f 0x10
Node 0x08 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x07
Node 0x09 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x37 0x37]
  Connection: 2
     0x02 0x07
Node 0x0a [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x80]
  Amp-Out caps: ofs=0x23, nsteps=0x41, stepsize=0x03, mute=0
  Amp-Out vals:  [0x23]
  Connection: 2
     0x02 0x07
Node 0x0b [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0c [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0d [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0e [Audio Selector] wcaps 0x300101: Stereo
  Connection: 2
     0x08* 0x09
Node 0x0f [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001003f: IN OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x2: EAPD
  Pin Default 0x01014000: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x10 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Headphone Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003f: IN OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x2: EAPD
  Pin Default 0x02214000: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=06, enabled=1
  Connection: 1
     0x09
Node 0x11 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x50171000: [N/A] Speaker at Int N/A
    Conn = Analog, Color = Black
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0a
Node 0x12 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Rear Mic Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x01a19000: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x0b
Node 0x13 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Front Mic Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x02a19000: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Connection: 1
     0x0c
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Line Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x01813000: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x0d
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Aux Phantom Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000133f: IN OUT HP Detect Trigger ImpSense
    Vref caps: HIZ 50 80
  Pin Default 0x99931000: [Fixed] Aux at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0e
Node 0x16 [Pin Complex] wcaps 0x400001: Stereo
  Control: name="CD Phantom Jack", index=0, device=0
  Pincap 0x00000020: IN
  Pin Default 0x99331000: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Black
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x17 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x90f71000: [Fixed] Other at Int N/A
    Conn = Analog, Color = Black
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
Node 0x18 [Pin Complex] wcaps 0x400380: Mono Digital
  Control: name="SPDIF Jack", index=0, device=0
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01446000: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Orange
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x03
Node 0x19 [Pin Complex] wcaps 0x400280: Mono Digital
  Control: name="SPDIF In Jack", index=0, device=0
  Pincap 0x00000024: IN Detect
  Pin Default 0x01c41000: [Jack] SPDIF In at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x1a [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=13
Node 0x1b [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=64, direct=0, val=0
  Unsolicited: tag=00, enabled=0
  Connection: 0
Codec: Generic 163c Si3054
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x163c3155
Subsystem Id: 0x163c3055
Revision Id: 0x100700
Modem Function Group: 0x1
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 11 Feb 28 18:26 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 10 Feb 28 18:26 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  9 Feb 28 18:26 /dev/snd/hwC0D1
crw-rw----+ 1 root audio 116,  8 Feb 28 18:27 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  7 Feb 28 18:27 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  6 Feb 28 18:29 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  5 Feb 28 18:27 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  4 Feb 28 18:26 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  3 Feb 28 18:26 /dev/snd/pcmC0D6c
crw-rw----+ 1 root audio 116,  2 Feb 28 18:26 /dev/snd/pcmC0D6p
crw-rw----+ 1 root audio 116,  1 Feb 28 18:26 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Feb 28 18:26 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb 28 18:26 .
drwxr-xr-x 3 root root 300 Feb 28 18:26 ..
lrwxrwxrwx 1 root root  12 Feb 28 18:26 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC260 Alt Analog [ALC260 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xb0000000 irq 11'
  Mixer name    : 'Realtek ALC260'
  Components    : 'HDA:10ec0260,02600000,00100400 HDA:163c3155,163c3055,00100700'
  Controls      : 45
  Simple ctrls  : 16
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 55 [86%] [-9.00dB] [on]
  Front Right: Playback 55 [86%] [-9.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [off]
  Front Right: Playback 65 [100%] [30.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [off]
  Front Right: Playback 65 [100%] [30.00dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [off]
  Front Right: Playback 65 [100%] [30.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 65 [100%] [30.00dB] [off]
  Front Right: Playback 65 [100%] [30.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 10 [29%] [10.00dB] [on]
  Front Right: Capture 10 [29%] [10.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Rear Mic' 'Front Mic' 'Line' 'CD' 'Aux'
  Item0: 'Line'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Rear Mic' 'Front Mic' 'Line' 'CD' 'Aux'
  Item0: 'Rear Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]


!!Alsactl output
!!--------------

--startcollapse--
state.Intel {
    control.1 {
        iface MIXER
        name 'Master Playback Volume'
        value.0 55
        value.1 55
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 64'
            dbmin -6400
            dbmax 0
            dbvalue.0 -900
            dbvalue.1 -900
        }
    }
    control.2 {
        iface MIXER
        name 'Master Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.3 {
        iface MIXER
        name 'Rear Mic Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 65'
            dbmin -3500
            dbmax 3000
            dbvalue.0 -3500
            dbvalue.1 -3500
        }
    }
    control.4 {
        iface MIXER
        name 'Rear Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.5 {
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 65
        value.1 65
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 65'
            dbmin -3500
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
    control.6 {
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.7 {
        iface MIXER
        name 'Line Playback Volume'
        value.0 65
        value.1 65
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 65'
            dbmin -3500
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
    control.8 {
        iface MIXER
        name 'Line Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.9 {
        iface MIXER
        name 'CD Playback Volume'
        value.0 65
        value.1 65
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 65'
            dbmin -3500
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
    control.10 {
        iface MIXER
        name 'CD Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.11 {
        iface MIXER
        name 'Aux Playback Volume'
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 65'
            dbmin -3500
            dbmax 3000
            dbvalue.0 -3500
            dbvalue.1 -3500
        }
    }
    control.12 {
        iface MIXER
        name 'Aux Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.13 {
        iface MIXER
        name 'Input Source'
        value Line
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Rear Mic'
            item.1 'Front Mic'
            item.2 Line
            item.3 CD
            item.4 Aux
        }
    }
    control.14 {
        iface MIXER
        name 'Input Source'
        index 1
        value 'Rear Mic'
        comment {
            access 'read write'
            type ENUMERATED
            count 1
            item.0 'Rear Mic'
            item.1 'Front Mic'
            item.2 Line
            item.3 CD
            item.4 Aux
        }
    }
    control.15 {
        iface MIXER
        name 'Capture Volume'
        value.0 10
        value.1 10
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 35'
            dbmin 0
            dbmax 3500
            dbvalue.0 1000
            dbvalue.1 1000
        }
    }
    control.16 {
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.17 {
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 0
        value.1 0
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 35'
            dbmin 0
            dbmax 3500
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.18 {
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.19 {
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.20 {
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.21 {
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.22 {
        iface MIXER
        name 'IEC958 Playback Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.23 {
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.24 {
        iface MIXER
        name 'IEC958 Capture Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.25 {
        iface MIXER
        name 'IEC958 Capture Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.26 {
        iface CARD
        name 'Rear Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.27 {
        iface CARD
        name 'Front Mic Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.28 {
        iface CARD
        name 'Line Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.29 {
        iface CARD
        name 'CD Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.30 {
        iface CARD
        name 'Aux Phantom Jack'
        value true
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.31 {
        iface CARD
        name 'Front Headphone Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.32 {
        iface CARD
        name 'SPDIF Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.33 {
        iface CARD
        name 'SPDIF In Jack'
        value false
        comment {
            access read
            type BOOLEAN
            count 1
        }
    }
    control.34 {
        iface MIXER
        name 'Beep Playback Volume'
        value.0 65
        value.1 65
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 65'
            dbmin -3500
            dbmax 3000
            dbvalue.0 3000
            dbvalue.1 3000
        }
    }
    control.35 {
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.36 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.37 {
        iface PCM
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.38 {
        iface PCM
        device 1
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.39 {
        iface PCM
        device 1
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.40 {
        iface PCM
        device 2
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.41 {
        iface MIXER
        name 'Off-hook Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.42 {
        iface MIXER
        name 'Caller ID Switch'
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.43 {
        iface PCM
        device 6
        name 'Playback Channel Map'
        value 0
        comment {
            access read
            type INTEGER
            count 1
            range '0 - 36'
        }
    }
    control.44 {
        iface PCM
        device 6
        name 'Capture Channel Map'
        value 0
        comment {
            access read
            type INTEGER
            count 1
            range '0 - 36'
        }
    }
    control.45 {
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
        comment {
            access 'read write user'
            type INTEGER
            count 2
            range '0 - 255'
            tlv '0000000100000008ffffec1400000014'
            dbmin -5100
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
michael_mic
arc4
lib80211_crypt_tkip
lib80211_crypt_ccmp
bnep
rfcomm
snd_hda_codec_si3054
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
pcmcia
pcspkr
ipw2200
joydev
snd_seq_device
snd_timer
libipw
btusb
serio_raw
i915
lib80211
lpc_ich
yenta_socket
snd
drm_kms_helper
bluetooth
pcmcia_rsrc
pcmcia_core
tifm_7xx1
cfg80211
tifm_core
soundcore
drm
shpchp
i2c_algo_bit
video
parport_pc
ppdev
lp
mac_hid
parport
pata_acpi
ahci
firewire_ohci
tg3
firewire_core
sdhci_pci
psmouse
ptp
crc_itu_t
libahci
sdhci
pps_core


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x0f 0x01014000
0x10 0x02214000
0x11 0x50171000
0x12 0x01a19000
0x13 0x02a19000
0x14 0x01813000
0x15 0x99931000
0x16 0x99331000
0x17 0x90f71000
0x18 0x01446000
0x19 0x01c41000

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC0D1/init_pin_configs:

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:

/sys/class/sound/hwC0D1/hints:


!!ALSA/HDA dmesg
!!--------------

[   21.384324] realtek: Enable default setup for auto mode as fallback
[   21.419973] input: HDA Intel SPDIF In as /devices/pci0000:00/0000:00:1b.0/sound/card0/input21
[   21.421156] input: HDA Intel SPDIF as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[   21.422903] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[   21.423179] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   21.423416] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   21.423663] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   21.878892] type=1400 audit(1425148019.382:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=652 comm="apparmor_parser"
```

---

### Post by Tim_Stephens on 2015-03-01
Now tried every model in the ALC260 list none work! Very frustrating this! Anybody? Really stuck now and don't want to go back to Windose!

Cheers,
Tim

---

### Post by JeQhdMD on 2015-03-01
Have you read thru these instructions?

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

Also, because of the later kernel, it might be interesting to try a live DVD (or better yet, Live USB 14.10) to see if sound works with the latest stable Ubuntu version. 

On a similar note, I've used Suse Linux's Yast tool to debug and fix sound issues in the past (using a gui tool that's a bit more user friendly).   Might also be worth give the latest Suse a try on USB Flash drive.

---

