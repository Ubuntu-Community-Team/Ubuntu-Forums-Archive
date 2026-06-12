---
title: "GPU Driver Upgrade -- Sound Problems -- Ubuntu 13.04"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by Gnawnsense on 2013-06-21
Greetings all!

Relative Linux noob here. Just upgraded from 12.04 to 13.04 via clean install and have ran into a bit of a snag.

I installed my AMD drivers and enabled hardware acceleration right after doing the clean install and went straight to Steam to make sure performance was OK. I noticed that the frame rate seemed OK, but I was missing sound. I panicked around for a bit, checked my volume settings and made sure they were OK. I searched around the web for similar issues and couldn't find anyone who was in my direct scenario.

So I rebooted and noticed that when Ubuntu started, the intro drum-roll played. So I tried signing into the guest account and tada! Sound played. Logged out and into another administrator account on the computer. Sound played. Back into my original user account and no sound.

Below is the results of the *lspci -v* command, which shows my audio device. I don't know if there's a better command that shows more relevant, helpful information or not at this point.

```
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]    
    Subsystem: ASUSTeK Computer Inc. Device aa88
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at feabc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
```

I'm wondering if I should just log into the other administrator account and delete the one without the sound problems, but I don't know if that will cause issues. And I'd also like to just try and fix whatever problem is causing this, so I could know why it happened in the first place.

Any assistance would be greatly appreciated!

---

### Post by TheFu on 2013-06-21
If audio works for some users and not others, that usually means there is a group permissions difference. Use the 'id' command do find what the differences are.

---

### Post by deri on 2013-06-21
Have you looked your sound settings if you have correct audio device enabled/priority 1.

---

### Post by Gnawnsense on 2013-06-21
I'm not very experienced with the ID command, but from using *id* and *id <otheraccountname>* this is what turned up, the second being the profile with working sound:

```
ricky@ricky-uPC:~$ iduid=1000(ricky) gid=1000(ricky) groups=1000(ricky),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
```

```
ricky@ricky-uPC:~$ id gnawnsense
uid=1001(gnawnsense) gid=1001(gnawnsense) groups=1001(gnawnsense),4(adm),27(sudo),108(lpadmin),124(sambashare)
ricky@ricky-uPC:~$
```

Both are administrators, so I don't know what to make about the differences. It seems that the Gnawnsense profile has elevated permissions in the shared groups, but it missing a number of the others completely, so I don't really know what I'm looking at, to be honest. However, even my guest account has sound, if that has anything to do with anything.

> **deri said:**
> Have you looked your sound settings if you have correct audio device enabled/priority 1.

Below are the results from *sudo aplay -l*:

```
**** List of PLAYBACK Hardware Devices ****card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: ALC888 Digital [ALC888 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So there's an obvious difference there, with the middle being activated on the second profile, which has the working sound. But I can't for the life of me figure out how to actually enable the middle device and set it to 1/1.

---

### Post by Gnawnsense on 2013-06-22
Ahh, I feel pretty silly now.

I just went into system settings and into the sound options and noticed it was set to HDMI default. I clicked Analog and got sound back. I had done this switch on accident when going through issues with GPU driver installation earlier. 

Thanks for the help, tho, everyone!

---

