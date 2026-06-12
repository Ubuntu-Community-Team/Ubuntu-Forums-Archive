---
title: "Sound card not working"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by yesterdays jam on 2012-10-27
Hi Everyone,

I've just installed ubuntu 12.04, but now I have no sound from my speakers.

volume is on full

sound card (as far as I can tell) is; Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

I've read that other people have had problems like this, but the solutions haven't helped :(

Help much appreciated

---

### Post by gordintoronto on 2012-10-27
The command lspci should help identify the sound device. In Sound Settings/
Output, you might try a different "connector."

---

### Post by yesterdays jam on 2012-10-28
lspci output is
```

jam@angel1:~$ lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8310 and 88W8000G [Libertas] 802.11g client chipset (rev 07)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. IT8212 Dual channel ATA RAID controller (rev 13)
01:05.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
05:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI R430 [Radeon X800 (PCIE)]
05:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI R430 [Radeon X800] (PCIE) (Secondary)
```

What do you mean be a different 'connector'? Is this like a audio jack adaptor, or something with the software.

---

### Post by gordintoronto on 2012-10-28
The "connector" is a software setting. I think you can click on the speaker icon and select "Sound Settings." There are five "tabs," and the first one is called "Output". At the bottom of that window is a drop-down selector labelled "Connector". For my earphones, I use "Analog Output". Different devices have different options, so I can't predict what you will see there. If you change it, I think it takes effect immediately, so you can begin playing a song and try different options.

Oh, at the top-right is an on-off switch, you should also check it.

There's also a "Hardware" tab, which may have a whole bunch of "profiles" you can try. Mine is set to "Analog Stereo Duplex".

You were correct about the sound device in your computer.

---

### Post by yesterdays jam on 2013-01-14
Ok, so I located these settings, this did not, however, solve the problem.

But, after about a month of trying 12.04, I installed 12.10 and now it works!

Thanks for your help!

---

