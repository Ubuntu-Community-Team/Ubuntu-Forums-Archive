---
title: "Sound problem"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by LaxFreek on 2008-11-12
Well I installed Ubuntu 8.10 on my comp and I got xp also installed on it. I just realized I have no sound on my ubuntu, is there a way I can check to see if my sound driver is installed correctly? Im a Linux-noob so bear with me here.

---

### Post by nhasian on 2008-11-12
first lets find out which audio adaptor is in your computer.  type

```
lshw
```

mine says:

> *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by Captonkirk on 2008-11-12
i'm having same problem. here is output:

 description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0


is it bad etiquette to jump onto another user's thread?

---

### Post by Captonkirk on 2008-11-12
i'm having same problem. here is output:

 description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0


is it bad etiquette to jump onto another user's thread?

---

### Post by LaxFreek on 2008-11-16
*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by nhasian on 2008-11-18
wow you have the same sound card as me.  what are the odds?  also we both using the same driver snd_hda_intel.  i didnt have to do anything special, the sound worked right away for me.

---

### Post by Trafferth on 2008-11-18
Hey LaxFreek,

Have you tried the usual routine of the following:

1. Double-click the volume control, select preferences, check all the boxes, go back to the volume control mixer, unmute everything, and turn all the volume controls up.

2. Look along the top of the mixer for a tab labelled 'Switches' or similar; make sure something weird like attempting to send digital sound to analogue speakers (or vice versa) isn't going on...

3. Right-click on the volume control, select preferences, and try a different playback device (there will probably be several to try).

4. Go to System > Preferences > Sound and try switching the devices shown in the drop-down boxes.

Good luck!

Trafferth :)

---

### Post by LaxFreek on 2008-11-18
Thanks so much Traff. What you said fixed it :)

---

### Post by Trafferth on 2008-11-18
You're welcome.  Glad it's fixed.  Sound can be a pain with Linux. Guess you can mark the thread as solved, etc.

Ah, another problem out of the way! :lolflag:  Have fun with Ubuntu!

Trafferth :)

---

### Post by Captonkirk on 2008-11-18
nhasian,

I think I didn't include all info of output. When I purchased my system I upgraded to a Creative_Labs SoundCard. 

Here is part of the output for lspci -v | less:

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
Subsystem: Dell Device 010e
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at c800 [size=256]
I/O ports at cc40 [size=64]
Kernel driver in use: Intel ICH
Kernel modules: snd-intel8x0

02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
Subsystem: Creative Labs Device 8022
Flags: bus master, medium devsel, latency 64, IRQ 18
I/O ports at dce0 [size=32]
Capabilities: <access denied>
Kernel driver in use: EMU10K1_Audigy
Kernel modules: snd-emu10k1

02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
Subsystem: Creative Labs Device 0020
Flags: bus master, medium devsel, latency 64
I/O ports at dcd8 [size=8]
Capabilities: <access denied>
Kernel driver in use: Emu10k1_gameport
Kernel modules: emu10k1-gp

---

### Post by Trafferth on 2008-11-18
@CaptonKirk: Have you gone through the same procedure as LaxFreek? It seems to have solved his problem.

-T :)

---

### Post by nhasian on 2008-11-18
Captonkirk,

If you've added a creative labs sound card, you might want to disable the onboard audio adaptor so there is no confusion.  If you have an onboard audio adaptor you can disable it from the BIOS.  

also didnt creative labs recently open source their drivers?  there's probably some new drivers available now.

---

### Post by Trafferth on 2008-11-19
Hmm, since my Audigy works fine without extra drivers, I would have thought that most Creative Labs cards would be supported (except maybe the very latest models).  Disabling the on-board sound if you have a discrete sound card is always a good idea if you're experiencing problems, however.

---

### Post by Captonkirk on 2008-11-20
Using System > Preferences > Sound I was able to configure to my Creative Labs SB Live! sound card. I now get sound upon pressing "Test" button and inserting a CD into CD-ROM drive. However, no sound while online, audio or video.

Any ideas? Thanks for the help.

---

