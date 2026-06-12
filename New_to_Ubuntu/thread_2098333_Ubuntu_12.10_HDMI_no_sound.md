---
title: "Ubuntu 12.10 HDMI no sound"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by ra7v on 2012-12-26
Hi,
 I recently installed ubuntu 12.10 on a dell studio xps. I cant get  sound through the HDMI output. There is sound from the headphones  output. I have tried to do a bunch of fixes that I found online, but I  dont know enough to fix it.
 Please let me know what to do, i need a step by step help.

 Ravi

---

### Post by ra7v on 2012-12-26
sudo aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC887 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC887 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC887 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC887 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC887 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC887 Digital
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions

---

### Post by bryanl on 2012-12-26
this looks to be another of those '2 steps forward, one step back' that plagues Linux and makes me rather afraid to upgrade at times. I never can tell what will break on the upgrade. (at least I've got the all-in-one printer back and the laptop dual screen setup going again in 12.10!)

[http://ubuntuforums.org/showthread.php?t=2098245](http://ubuntuforums.org/showthread.php?t=2098245) says he modified a /etc/default/grub item about his radeon audio - I might try that on my AMD machine to see if it works. I did go through the sound settings and make sure output was routed to the HDMI in both places as that was the problem in previous iterations. This time, it didn't do the job.

meanwhile, I went back to the VGA and sound line connection for my media machine.

The next one is that irritating screen blanking despite screen and power settings. That seems to cycle just about every release. I've put an 'xset s 0 0' in the startup script and it seems to have fixed it for now.

Sorry I can't be of more help. I hope some suggestions will show up here so maybe I can solve the same problem on my end and get the HDMI audio going again. If I encounter anything from elsewhere, I'll pass it along here.

---

### Post by ra7v on 2012-12-27
Solved it, this is what i did.

1. Downgraded to Ubuntu 12.04, as I read somewhere that it's more stable.
2. Went to System Settings and under Hardware clicked Additional Driver.
3. Installed the graphic card driver (propietary)
4. Restarted.
5. Checked sound settings and HDMI audio output finally appeared. Tested sound and it worked great!
6. Ran Update Manager to update everything else. Works like a charm!

---

### Post by webdesigncompanyla on 2013-03-29
i confirm that it works for 12.04 and not 12.10 for ati radeon 3600 series...  huge bummer, ubuntu needs to fix these kinds of driver problems!  driver/hardware issues are the #1 or #2 priority besides not being able to run adobe photoshop and other mainstream software natively...  come on ubuntu you can do better!

---

### Post by webdesigncompanyla on 2013-03-29
btw, this means that the sound _AND_ video doesnt work properly for ati radeon 3600 based machines

---

### Post by flows69 on 2013-03-29
> **ra7v said:**
> Solved it, this is what i did.

1. Downgraded to Ubuntu 12.04, as I read somewhere that it's more stable.
2. Went to System Settings and under Hardware clicked Additional Driver.
3. Installed the graphic card driver (propietary)
4. Restarted.
5. Checked sound settings and HDMI audio output finally appeared. Tested sound and it worked great!
6. Ran Update Manager to update everything else. Works like a charm!


Could you explain how you downgraded to 12.04 ?

---

