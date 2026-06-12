---
title: "no sound internal speaker"
date: 2014-08-17
forum: New to Ubuntu
---

### Post by jozefls on 2014-08-17
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.63
!!################################

!!Script ran on: Sun Aug 17 08:52:12 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 14.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.1 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VPCL12M1E
Product Version:   C6U1E6H4
Firmware Version:  R1060T5


!!Kernel Information
!!------------------

Kernel release:    3.13.0-32-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-32-generic
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
                      HDA Intel at 0xfcff8000 irq 46


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:3a3e
	Subsystem: 104d:9060


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: index=0 model=auto
snd_hda_intel: model=6stack-dig


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : 0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : 6stack-dig,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
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

Codec: Realtek ALC889
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0889
Subsystem Id: 0x104d3d00
Revision Id: 0x100005
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=2, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC889 Analog", type="Audio", device=0
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC889 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC889 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x1b 0x1b]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x90 0x90]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x570]: 32000 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=5, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Control: name="Internal Mic Phantom Jack", index=0, device=0
  Pincap 0x00000020: IN
  Pin Default 0x90a6012e: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0xe
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Phantom Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x0321101f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a15020: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Red
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03811050: [Jack] Line In at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Control: name="SPDIF Phantom Jack", index=0, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x01451130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=28
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12*
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3e 0x3e]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  6 Aug 17 08:07 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Aug 17 08:07 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  4 Aug 17 08:32 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Aug 17 09:37 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  2 Aug 17 08:32 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  1 Aug 17 08:07 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Aug 17 08:07 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Aug 17 08:07 .
drwxr-xr-x 3 root root 200 Aug 17 08:07 ..
lrwxrwxrwx 1 root root  12 Aug 17 08:07 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfcff8000 irq 46'
  Mixer name	: 'Realtek ALC889'
  Components	: 'HDA:10ec0889,104d3d00,00100005'
  Controls      : 40
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [2.00dB] [on]
  Front Right: Playback 64 [100%] [2.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-62.00dB] [off]
  Front Right: Playback 0 [0%] [-62.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-62.00dB] [off]
  Front Right: Playback 0 [0%] [-62.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-62.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [-62.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Line Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 31
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 27 [59%] [11.00dB] [on]
  Front Right: Capture 27 [59%] [11.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Internal Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]


!!Alsactl output
!!--------------

--startcollapse--
state.Intel {
	control.1 {
		iface MIXER
		name 'Channel Mode'
		value '2ch'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 '2ch'
			item.1 '4ch'
			item.2 '6ch'
		}
	}
	control.2 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6200
			dbmax 200
			dbvalue.0 200
			dbvalue.1 200
		}
	}
	control.3 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.4 {
		iface MIXER
		name 'Surround Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6200
			dbmax 200
			dbvalue.0 -6200
			dbvalue.1 -6200
		}
	}
	control.5 {
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.6 {
		iface MIXER
		name 'Center Playback Volume'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6200
			dbmax 200
			dbvalue.0 -6200
		}
	}
	control.7 {
		iface MIXER
		name 'LFE Playback Volume'
		value 0
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6200
			dbmax 200
			dbvalue.0 -6200
		}
	}
	control.8 {
		iface MIXER
		name 'Center Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'LFE Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6200
			dbmax 200
			dbvalue.0 -6200
			dbvalue.1 -6200
		}
	}
	control.11 {
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.12 {
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.13 {
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.14 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.15 {
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
	control.16 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.17 {
		iface MIXER
		name 'Capture Source'
		value 'Internal Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Mic
			item.1 'Internal Mic'
			item.2 Line
		}
	}
	control.18 {
		iface MIXER
		name 'Capture Volume'
		value.0 27
		value.1 27
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 46'
			dbmin -1600
			dbmax 3000
			dbvalue.0 1100
			dbvalue.1 1100
		}
	}
	control.19 {
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
	control.20 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.21 {
		iface MIXER
		name 'Line Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.22 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.23 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.24 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.25 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.26 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.27 {
		iface MIXER
		name 'Master Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
		}
	}
	control.28 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.29 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.30 {
		iface CARD
		name 'Internal Mic Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.31 {
		iface CARD
		name 'Line Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.32 {
		iface CARD
		name 'Headphone Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.33 {
		iface CARD
		name 'Speaker Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface CARD
		name 'SPDIF Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.35 {
		iface MIXER
		name 'Beep Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.36 {
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
	control.37 {
		iface PCM
		name 'Playback Channel Map'
		value.0 3
		value.1 4
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.38 {
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
	control.39 {
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
	control.40 {
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
bnep
rfcomm
joydev
hid_sunplus
hid_generic
hid_sony
ff_memless
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
usbhid
videodev
hid
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
coretemp
kvm_intel
arc4
kvm
snd_seq
serio_raw
ath9k
ath9k_common
snd_seq_device
lpc_ich
btusb
ath9k_hw
snd_timer
ath
bluetooth
mac80211
nouveau
snd
sony_laptop
mxm_wmi
cfg80211
wmi
video
ttm
drm_kms_helper
drm
soundcore
i2c_algo_bit
mac_hid
mei_me
mei
parport_pc
ppdev
lp
parport
firewire_ohci
firewire_core
sdhci_pci
crc_itu_t
sdhci
e1000e
ptp
pps_core


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x90a6012e
0x14 0x90170110
0x15 0x0321101f
0x16 0x411111f0
0x17 0x411111f0
0x18 0x03a15020
0x19 0x411111f0
0x1a 0x03811050
0x1b 0x411111f0
0x1c 0x411111f0
0x1d 0x411111f0
0x1e 0x01451130
0x1f 0x411111f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:


!!ALSA/HDA dmesg
!!--------------

[   20.846428] fbcon: nouveaufb (fb0) is primary device
[   20.919282] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   20.937066] hda_codec: ALC889: SKU not ready 0x411111f0
[   20.937369] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
--
[   20.937375] realtek: Enable default setup for auto mode as fallback
[   20.948604] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.952146] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.952301] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   21.079272] hidraw: raw HID events driver (C) Jiri Kosina

---

