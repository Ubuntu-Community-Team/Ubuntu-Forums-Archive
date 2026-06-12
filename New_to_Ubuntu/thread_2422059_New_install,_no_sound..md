---
title: "New install, no sound."
date: 2019-07-01
forum: New to Ubuntu
---

### Post by zosolm2 on 2019-07-01
Hi all!

I've searched around and couldn't find an answer explained at a level I could understand (I'm pretty new!). I got this laptop my friend was throwing away because she said it doesn't have any sound. I, knowing a touch more about computers than her (though still not an awful lot) thought it probably did and so she gave it me instead. The first thing I did was install Ubuntu as I've been running away from Windows for ages and like to avoid it wherever possible.

So, the situation is:

There was no sound on Windows. There's no sound on Ubuntu (I think I'm running the Bionic version)

see the output of the following (I have made in bold the part I think is relevant)

:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 **Audio device: Intel Corporation Haswell-ULT HD Audio Controller** (rev 0b)
00:04.0 Signal processing controller: Intel Corporation Haswell-ULT Thermal Subsystem (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)




So besides this, I'm not really too sure how to proceed. The only other relevant thing I've discovered from looking into it is in settings, the audio  output device is a 'Dummy Output'.

Other random info:-

My laptop is ASUS "sonicmaster" model (yes, I know - sonicmaster with no sound). I used to use ubuntu years ago but for one reason or another went back to windows, so if you are able to give me any advice/instructions then please make them step by step and as basic as possible. 

Thank you so much!
Zoso

---

### Post by CatKiller on 2019-07-01
Since there was no sound in Windows either, it's pretty definitely a hardware issue of some kind. See if it's been turned off in the BIOS - the only configuration capability you have - and if it can't be enabled there use a USB sound card - the only replacement option you have, because it's a laptop.

---

### Post by him610 on 2019-07-03
Hello zosolm2, 
Often times people claim this or that device doesn't work, and sometimes it may be true, but quite often the device is improperly configured. Electronic chips are actually fairly rugged, and seldom fail. 
What are you using for audio output - internal speakers or headset?
I unsuccessfully tried to look up the specs to your machine. I think ASUS sonicmaster is more of a feature than a model. The model (alpha-numeric) number can normally be found on the bottom of the laptop on a sticker.

Could you please show the results of* inxi -Fxz* within code tags? It will show slightly different information than lspci.

---

### Post by Skaperen on 2019-07-04
something is broken. but there are lots of thing that could break and kill the sound.  if the speakers are in the upper panel then another possibility is the wiring going across the fold. at a place i used to work, we had 3 laptops lose or mess up video at the fold, though they worked over the VGA connect near the keyboard.  try the headphone connector.  look for sound/audio related error messages in the files in /var/log.  if any, they might give a clue if there is a chip or BIOS issue.

---

