---
title: "fixing audio frontal jack that doesn't work"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by antoelca on 2013-10-06
Hi, I recently installed Lubuntu 12.04 and I have the problem that audio conection in the front of my computer doesn't work.
I've read and tried the alsamixer thing but the frontal configuration doesn't apperar in the screen, so I can't make it work.

Thank you very much.

The **lspci** thing
> 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8500 GT] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]




---

### Post by walterorlin on 2013-10-08
Since you specified the front jack does any other sound work from built in speakers or another audio jack. Are you sure the speakers or headphones you plug in to the front jack work. One obvious thing to check is to make sure your sound is not muted. Can you paste the results of ```
amixer contents
``` There might be a software switch turning off your jack somewhere.

---

### Post by antoelca on 2014-06-03
[SIZE=3][COLOR=#000000]**Thanks for your time walterorlin, : )**
[/COLOR]
This is the output you asked for:[/SIZE]

> numid=37,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=36,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=9,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=38,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=255,255
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=18,iface=MIXER,name='Front Mic Boost Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=3,step=0
  : values=1,1
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=19,iface=MIXER,name='Front Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=17,iface=MIXER,name='Front Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=15,15
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=2,iface=MIXER,name='Front Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=1,iface=MIXER,name='Front Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=4,iface=MIXER,name='Surround Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=3,iface=MIXER,name='Surround Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=7,iface=MIXER,name='Center Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=5,iface=MIXER,name='Center Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=8,iface=MIXER,name='LFE Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=6,iface=MIXER,name='LFE Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=31
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=13,iface=MIXER,name='Line Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=12,iface=MIXER,name='Line Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=11,iface=MIXER,name='CD Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=10,iface=MIXER,name='CD Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=23,23
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=15,iface=MIXER,name='Mic Boost Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=3,step=0
  : values=1,1
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=16,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=14,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=31,31
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=21,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=22,iface=MIXER,name='Capture Switch',index=1
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=23,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-16.50dB,step=1.50dB,mute=0
numid=24,iface=MIXER,name='Capture Volume',index=1
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-16.50dB,step=1.50dB,mute=0
numid=31,iface=MIXER,name='IEC958 Default PCM Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=27,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=28,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=29,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=30,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=33,iface=MIXER,name='IEC958 Capture Default'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=32,iface=MIXER,name='IEC958 Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=35,iface=MIXER,name='Beep Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
numid=34,iface=MIXER,name='Beep Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=20,iface=MIXER,name='Channel Mode'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 '2ch'
  ; Item #1 '4ch'
  ; Item #2 '6ch'
  : values=0
numid=39,iface=MIXER,name='Digital Capture Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=120,step=0
  : values=120,120
  | dBscale-min=-30.00dB,step=0.50dB,mute=0
numid=25,iface=MIXER,name='Input Source'
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=0
numid=26,iface=MIXER,name='Input Source',index=1
  ; type=ENUMERATED,access=rw------,values=1,items=4
  ; Item #0 'Mic'
  ; Item #1 'Front Mic'
  ; Item #2 'Line'
  ; Item #3 'CD'
  : values=0

[SIZE=3]My headphones work normally. The point is that i managed to change some configuration and now I can hear a very low sound that I play. I use a small pair of normal headphones and I also have a bigger ones with microphone wich I use to skype with family. The sound is lower with the skype ones connected.[/SIZE]

---

