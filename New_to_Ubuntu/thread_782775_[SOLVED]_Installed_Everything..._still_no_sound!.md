---
title: "[SOLVED] Installed Everything... still no sound!"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-05
I have installed codecs, restricted hardware, everything... but I still don't have sound!!! I also installed ALSA aswell and still nothing :( Any help with this? My sound card is a EMUK10K1 SSB0220 sound card. I have the sound card on my desktop, but I have no idea how to install it:

```
Installation
------------
1. As root type:

	make install

2. Add a new reference to the driver in /etc/modules.conf:

	alias sound emu10k1

3. Play some sound. The module should be auto-loaded.

Note for Debians' users: use /etc/modutils directory,
   create file emu10k1 here with the same content as is suggested in
   the paragraph (5.) and run update-modules afterwards - this
   will create the correct /etc/modules.conf file)
```

Any help is appreciated.

---

### Post by northern lights on 2008-05-05
Can you please post the outputs of ```
cat /proc/asound/cards
``` and ```
lshw -C multimedia
```

Thanks.

Further run "alsamixer" and check whether nothing's muted (OO is on, MM is muted...).

---

### Post by UnknownFear on 2008-05-05
```
dan@dan-desktop:~$ cat /proc/asound.cards
cat: /proc/asound.cards: No such file or directory
```

```
dan@dan-desktop:~$ lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
  *-multimedia
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
dan@dan-desktop:~$ 
```

Does this help?

---

### Post by UnknownFear on 2008-05-05
> **northern lights said:**
> 
Further run "alsamixer" and check whether nothing's muted (OO is on, MM is muted...).

There are some that are muted, but I can't unmute them. I'll go into the Alsamixer and uncheck everything and see if that makes a difference.

---

### Post by northern lights on 2008-05-05
--> It's "/proc/asound**/**cards"...

Is music playing from your SB Live?

The "m" key toggles muting - unmute literally everything and try again. If it fails, return the output and an answer to the SB. Thanks.

---

