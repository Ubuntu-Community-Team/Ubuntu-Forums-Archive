---
title: "No sound - ubuntu 13.04"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by hamilker on 2013-06-02
Hey all,

I am a complete beginner and I'm soooo annoyed! 

I recently put Ubuntu 13.04 - 32 bit on my EMachines comp.  EVerything was working fine, I went out for a day and now there is no sound.

Under the "output" tab in the sound folder it says Dummy Output in the Play Sound Through box.

Can anyone help me please?

Thanks a bunch!

---

### Post by sargetech on 2013-06-02
> **hamilker said:**
> Hey all,

I am a complete beginner and I'm soooo annoyed! 

I recently put Ubuntu 13.04 - 32 bit on my EMachines comp.  EVerything was working fine, I went out for a day and now there is no sound.

Under the "output" tab in the sound folder it says Dummy Output in the Play Sound Through box.

Can anyone help me please?

Thanks a bunch!
Can you please give more information on what model Emachines you are installing on! This will give info on the integrated sound card that is on the motherboard!

---

### Post by MiamiHF on 2013-06-02
i have this same problem but on my iBook G4 can you also post the driver for that 2, id greatly appriciate it

---

### Post by hamilker on 2013-06-02
> **sargetech said:**
> Can you please give more information on what model Emachines you are installing on! This will give info on the integrated sound card that is on the motherboard!

Sure! THanks so much for responding.  IT's Emachines (PC) T5010

---

### Post by ShadowVegan on 2013-06-02
Did you make sure that your speakers are plugged in securely?

---

### Post by hamilker on 2013-06-02
> **ShadowVegan said:**
> Did you make sure that your speakers are plugged in securely?

Yes, my speakers are plugged in properly and the light shows they are receiving power. I also plugged my earphones into the computer and there is not sound that way either.

---

### Post by ShadowVegan on 2013-06-02
I sometimes have issues with my headset working with my laptop due to the laptop being old and the ports being a little bit off/loose. There's a chance that this is the issue in which case you'd have to adjust them physically. (Don't try it if you don't know what you're doing, opening a computer can be dangerous to you and the computer.) The fact that they were working fine then randomly stopped working is what leads me to think this is potentially an issue, but it seems unlikely unless it's a fairly old computer. If it's an issue with the sound card and/or software I wouldn't really know where to go with it so I'll let someone else help you there.

---

### Post by hamilker on 2013-06-02
> **ShadowVegan said:**
> I sometimes have issues with my headset working with my laptop due to the laptop being old and the ports being a little bit off/loose. There's a chance that this is the issue in which case you'd have to adjust them physically. (Don't try it if you don't know what you're doing, opening a computer can be dangerous to you and the computer.) The fact that they were working fine then randomly stopped working is what leads me to think this is potentially an issue, but it seems unlikely unless it's a fairly old computer. If it's an issue with the sound card and/or software I wouldn't really know where to go with it so I'll let someone else help you there.

HI there,

Thanks for your input. Everything was working fine and I never had this issue with the WIndows 8 that was on the computer before. It only seems to be an issue with Ubuntu.  I've also been reading posts online as well and there are many other people with the issue but I can't really find anyone resolving it. It may just be a bug with the 13.04.  Not too sure.  Hopefully, someone will be able to help me.

THanks,

---

### Post by pqwoerituytrueiwoq on 2013-06-02
make sure all updates are installed
[http://ubuntuforums.org/showthread.php?t=2141858](http://ubuntuforums.org/showthread.php?t=2141858)
most likely the reinstalling pulse or using the ppa will get it working

---

### Post by HavingFun on 2013-06-10
I have the same problem.  Also have an Emachines (PC) T5010.  Upgraded to 13.04 and lost sound.  I completed all steps of the Ubuntu sound troubleshooting guide here:  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

One thing that stood out:  When executing this tip


sudo aplay -lThe output of that command should look something like this: 

**** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]   Subdevices: 0/1   Subdevice #0: subdevice #0

I only received this:
**** List of PLAYBACK Hardware Devices ****


Didn't list the card.  But when I execute this:  lspci -v | grep -A7 -i "audio", 

I do get -

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Gateway, Inc. Device 4040
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at b01c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])

I'm new with ubuntu and any help would be very much appreciated.

---

