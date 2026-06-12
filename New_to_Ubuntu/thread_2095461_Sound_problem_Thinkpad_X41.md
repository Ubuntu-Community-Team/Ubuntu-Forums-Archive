---
title: "Sound problem Thinkpad X41"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by thomaswbdswim on 2012-12-16
i was given an old thinkpad x41 laptop to use as a note taking laptop at school and i have set it up with 12.04 and it is working great except i am unable to get any sound at all from it i have checked the mute and volume and i can see the speaker through one of the exhaust vents so it has the hardware but i am a recent convert so i do not know if i am missing drivers or the ubuntu alternative help would be appreciated as i love this laptop and i would like to be able to use it to its potential.

---

### Post by gnusci on 2012-12-16
Please post the output of the following command:

$ lspci

---

### Post by thomaswbdswim on 2012-12-17
thomas@thomas-ThinkPad-X41:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
04:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 13)
04:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
thomas@thomas-ThinkPad-X41:~$

---

### Post by thomaswbdswim on 2012-12-20
any ideas not trying to be impatient but i am traveling over the holidays and i would like to take the nice lightweight thinkpad rather than my bigger toshiba

---

### Post by tgalati4 on 2012-12-20
Output of:

```
aplay -l
```

I have a T43p which is probably similar vintage.  Mine reads:


tgalati4@tpad-Gloria7 ~/Desktop $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by thomaswbdswim on 2012-12-20
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by tgalati4 on 2012-12-20
So our machines have identical sound hardware.

If you have a speaker icon in your system tray, right-click and open "Volume-Control"

There are several mixers in Ubuntu:  ALSA mixer, pulseaudio mixer, OSS mixer.  Choose ALSA mixer and open up preferences.

Select all tracks to be visible.  Now you should see lots of sliders.  Raise them all up and play some music.

---

### Post by thomaswbdswim on 2012-12-21
i can not reach the alsa slider that you mentioned i am only able to configure the sound balance

---

### Post by tgalati4 on 2012-12-22
Open a terminal:

gnome-volume-control

gnome-sound-properties

---

### Post by thomaswbdswim on 2012-12-22
terminal shows " Command not found " when either command is entered

---

### Post by tgalati4 on 2012-12-26
Look through /usr/bin for similar commands to bring up sound-properties (which define the sound framework to use for inputs and outputs) and volume-control (to bring up the appropriate mixer).

I'm running Jaunty on this laptop which runs Gnome2.  You are running Gnome3 and Unity and I don't know what the equivalent commands are for that environment.

---

### Post by thomaswbdswim on 2013-01-18
What is /usr/bin and how do i get there

---

### Post by Cadin on 2013-03-13
I have just been through an install to 12.04, the secret apparently is to install 9.10 to gain the alda, and install updates from there until you are at 12.04. 

 I found it on a forum:  ([http://ubuntuworks.blogspot.com/](http://ubuntuworks.blogspot.com/))

He has all the workarounds to get your tablet buttons to do whatever you wish as well.  

Apparently the x41 has a bluetooth set inside as well,  getting that to work is my current task!

---

