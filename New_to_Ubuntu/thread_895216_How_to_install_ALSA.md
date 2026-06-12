---
title: "How to install ALSA?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by chickendude on 2008-08-20
I have tried installing ALSA from source and from synaptic and followed a few different HOWTOs after searching google the past few weeks, but no matter what I do I can't seem to get it to show up in under the System/Preferences/Sound Device setting, it only displays Realtek ALC861 (OSS Mixer). I've been having a ton of problems ever since upgrading to Hardy and I've already done two fresh installs! In Gutsy, Feisty, and Edgy I never had any problems getting ALSA to work, so I'm not quite sure what's going on here.

I do have sound, and I'm not exactly sure how all this works but I believe I've got Pulseaudio installed as well. It isn't as loud as it was with ALSA, I can hardly hear my music if, for example, the TV is on or I am sitting near the air conditioner.

I'm not sure what information I can give you to make it clearer how exactly I can fix this!
Here are some things which may or may not help:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
and after:
$ sudo lspci -v
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Toshiba Satellite A100-796 audio (Realtek ALC861)
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at de300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

```

Thanks!

---

### Post by nicedude on 2008-08-20
Alsa is installed by default in Ubuntu so there is no reason to install it from source. To open the alsa control panel for adjusting volume here is the command.

sudo alsamixer

and here is a command to open Gnome sound properties

gnome-sound-properties

Take a look at both of those and see if you can't work out your problem.

---

### Post by chickendude on 2008-08-21
Here is what I get when I try to run "sudo alsamixer":

> *** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

And I finally got ALSA to show up in gnome-sound-properties, but now I have no sound and when I try to choose HDA Intel (ALSA mixer) under Devices, it displays the following in the terminal:
> ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL equalized
Segmentation fault

Thanks.

---

### Post by halcyonbuddha on 2009-01-29
Hey, I'm not sure if this will help you or not, but here's what I did...

0. Open a terminal and enter:
   
   *sudo apt-get install alsa*

   to be sure that you have ALSA installed.

1. *System>Preferences>Sessions*  Uncheck "PulseAudio Sound System"

2. Click the "+Add" button.

3. Name:     ALSA startup
   Command:  alsa-utils

4. Click the "Save" button.

I had no sound when I started playing with Jaunty 9.04 Alpha 3, but this is what I did to get the sound working.  I think this should work for Intrepid 8.10 as well, and it should make Skype sound ready.  Good Luck!

---

### Post by cfw34683 on 2010-10-02
what i did to fix my sound was

```
sudo apt-get remove alsa
```
then
```
sudo apt-get install alsa
```and it fixed my sound


edit: this was in Ubuntu 10.04 (Lucid Lynx)

---

### Post by lidex on 2010-10-03
A lot of cat scratching here. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by diablo75 on 2010-10-03
I think if you just simply remove/uninstall PulseAudio, ALSA takes over.

---

### Post by kitzogen on 2010-11-27
I also havent sound, but had.
Here my Alsa: [http://www.alsa-project.org/db/?f=f0a106a0001567bad1fe7b32e50197359b27e84d](http://www.alsa-project.org/db/?f=f0a106a0001567bad1fe7b32e50197359b27e84d)

Thanks


(SOLVED)

---

### Post by lidex on 2010-11-27
> **kitzogen said:**
> I also havent sound, but had.
Here my Alsa: [http://www.alsa-project.org/db/?f=f0a106a0001567bad1fe7b32e50197359b27e84d](http://www.alsa-project.org/db/?f=f0a106a0001567bad1fe7b32e50197359b27e84d)

Thanks


(SOLVED)

So you're fixed then?

---

### Post by ramanandbedia on 2011-07-15
here's my alsa 
[http://www.alsa-project.org/db/?f=56b68e2c37d51eec36e7a99dc5e221ec7b42547e](http://www.alsa-project.org/db/?f=56b68e2c37d51eec36e7a99dc5e221ec7b42547e)

please anybody help 
thanks in advance.... :popcorn:

---

