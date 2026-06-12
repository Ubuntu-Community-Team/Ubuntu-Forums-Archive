---
title: "No sound.  No Explanation"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by veganbikepunk on 2008-07-27
So when I first installed hardy, it came with pulseaudio, which worked well enough except when I wanted to use two programs that required sound at the same time.  So I switched to alsa, using this guide:
[http://ph.ubuntuforums.com/showthread.php?t=843012](http://ph.ubuntuforums.com/showthread.php?t=843012)

And it worked great... until a few days ago, when there was just mysteriously no sound.  I tried plugging headphones into the jack to see if it was the speakers, no dice.  I tried using module-assistant to rebuild the alsa module.  I know I need to give more information for someone to know what the problem is but I really don't know what to give, there was no error message or anything.

Thanks in advance,
pax

---

### Post by northern lights on 2008-07-28
Can you please post the outputs of ```
cat /proc/asound/cards
``` and ```
sudo lshw -C multimedia
```

---

### Post by veganbikepunk on 2008-07-28
Actually, just as randomly as it stopped working, it started again.  Thanks anyway.

---

### Post by fenT1 on 2008-07-28
> **northern lights said:**
> Can you please post the outputs of ```
cat /proc/asound/cards
``` and ```
sudo lshw -C multimedia
```

0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0353]
                      Audigy 2 ZS [SB0353] (rev.4, serial:0x10031102) at 0xccc0, irq 23

*-multimedia            
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: e
       bus info: pci@0000:05:0e.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1

---

### Post by northern lights on 2008-07-28
> **fenT1 said:**
> 0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0353]
                      Audigy 2 ZS [SB0353] (rev.4, serial:0x10031102) at 0xccc0, irq 23

*-multimedia            
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: e
       bus info: pci@0000:05:0e.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1

yes. and now what?

that info would have been important to fix the veggie lovin' punkster's audio...
(coming from _his_ comp also)

thanks though, very kind.

---

### Post by fenT1 on 2008-07-28
> **northern lights said:**
> yes. and now what?

that info would have been important to fix the veggie lovin' punkster's audio...
(coming from _his_ comp also)

thanks though, very kind.

Ok, yes sorry i kind of have the same problem but no sound whatsoever. i thought that maybe since he had resolved i might step in and get some help. I you could help me it would be appreciated.

---

### Post by northern lights on 2008-07-28
> **fenT1 said:**
> Ok, yes sorry i kind of have the same problem but no sound whatsoever. i thought that maybe since he had resolved i might step in and get some help. I you could help me it would be appreciated.
Aight. The thing is your card looks configured.

Run ```
alsamixer
```from a terminal. Are any of the relevant channels muted (MM)?

---

### Post by fenT1 on 2008-07-28
This is what i saw muted that could be relevant.

Tone, 3D contr, IEC958, AUDIGYA, Sigmatel

---

### Post by northern lights on 2008-07-28
Well, up 'em all! For the sake of checking, crank up everything.

--> 'M' toggles mute...

---

### Post by fenT1 on 2008-07-28
OK i did it but the volume on the ones that i deselected the mute will not go up. Also i have ALSA on devices should i use another one?

---

