---
title: "Problem configuring audio through HDMI port"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by larmet on 2008-09-09
Problem:
Cannot configure audio through HDMI port (video is fine)

Motherboard:
Gigabyte GA-MA78GM-S2H Socket AM2+ AMD 780G + SB700 Chipset ATI Radeon HD3200 Graphics Dual Channel DDR2 1066 HD Audio GigaLAN IEEE1394 Mirco ATX

---

### Post by aeiah on 2008-09-09
what does it do with the audio? do you know if the audio chip is supported in linux? does it simply take a normal audio output from your soundcard and route it through the hdmi pins or output the audio its self?

---

### Post by larmet on 2008-09-09
When I go home tonight I'll copy/paste the results of:

aplay -l 

and

aplay -L

and 

cat /proc/asound/devices

---

### Post by larmet on 2008-09-09
Here are my results from further testing: (still not working)

aplay -l

larmet@larmet-theatre:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


aplay -L

larmet@larmet-theatre:~$ aplay -L
default:CARD=SB
    HDA ATI SB, ALC882 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=HDMI
    HDA ATI HDMI
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers

cat /proc/asound/devices
larmet@larmet-theatre:~$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 26: [ 0- 2]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 36: [ 1- 0]: hardware dependent
 51: [ 1- 3]: digital audio playback

---

### Post by larmet on 2008-09-09
One more problem:

The little sound applet near the clock has disappeared. How do I get it back?

---

### Post by nhasian on 2008-09-09
allow the HDMI spec allows for the use of both video and audio signals, you need to see if your device is capable of sending audio through HDMI.  for example my laptop which has an nvidia 8600 graphics adaptor has an HDMI connector, but its not connected to any audio devices :(

---

### Post by larmet on 2008-09-10
I've been able (but don't know how) to get SOME sound (mainly WAV files) to play... but with no regularity.

---

### Post by bghols85 on 2008-11-23
Any update on this?  I'm in the exact same boat and can't get any audio out of my hdmi.  The board does output audio through hdmi, it works fine in windows.  No such luck in ubuntu though.  Ideas?

---

### Post by Tom--d on 2008-11-23
This is a driver problem so really, there is nothing you can do (I don't think - correct me if I'm wrong).

Just wait for it to be supported.

The open source ATI driver has audio support but is being tested atm.
Can't comment on the closed source one.

---

