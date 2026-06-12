---
title: "sound not working."
date: 2008-08-12
forum: New to Ubuntu
---

### Post by AnLGP on 2008-08-12
I'm trying to get the sound working following this guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I get to the point where it says to put in

```
aplay -l
```

and this is what I believe to be the Audio device:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 01)
        Subsystem: Gateway 2000 Unknown device 5049
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 522c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

It tells me to put this in

```
sudo modprobe snd-
```

and to hit tab before I press enter.  I do and it prints this list (this isn't the whole thing but contains what I believe to be mine):

snd-atiixp-modem    snd-ice1724         snd-sb8-dsp
snd-au8810          snd-ice17xx-ak4xxx  snd-sbawe
snd-au8820          snd-indigo          snd-sb-common
snd-au8830          snd-indigodj        snd-sc6000
snd-azt2320         snd-indigoio        snd-seq
snd-azt3328         **snd-intel8x0 **       snd-seq-device
snd-bt87x           **snd-intel8x0m**       snd-seq-dummy
snd-bt-sco          snd-interwave       snd-seq-midi
snd-ca0106          snd-interwave-stb   snd-seq-midi-emul
snd-cmi8330         snd-korg1212        snd-seq-midi-event

The two in bold are the two I believe can be mine because they say "intel"...  am I on the right path?  Playing sound is a huge deal for me..  Thanks.

---

### Post by Pro-reason on 2008-08-13
Dunno.

Here are some more guides to look at:

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by AnLGP on 2008-08-13
Thanks.  I'll give those a whirl in a bit.

---

### Post by tangibleorange on 2008-08-13
Just try modprobing those two modules. I don't see how anything bad could happen - if they don't change anything just remove them again. you could also see if snd_hda_intel is loaded:

```
lsmod | grep intel
```

---

### Post by AnLGP on 2008-08-17
The following is what ```
lsmod | grep intel
``` outputs

snd_hda_intel         344600  0 
snd_pcm                78596  3 snd_hda_intel,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11528  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  2 snd_hda_intel,snd_usb_audio
intel_agp              25620  1 
snd                    56868  13 snd_hda_intel,snd_usb_audio,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_usb_lib,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  3 drm,intel_agp

---

