---
title: "Slight Sound issue in Hardy..."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by aheicher on 2008-06-04
Ok, short intro.  I just totally deleted Windows from my system, and am loving Ubuntu.  I have a Emachines T3626, Amd Sempron, etc.  The machine comes equipped with two frontal audio jacks, one for headphones and one for a mic.  Now I am a frequent user of Skype and am not so fond of digging around behind my computer to get the mic and headphones plugged in so they work.  In case I didn't make it obvious, my problem is these two front Jacks arent working for me, and Id like to get them working.  On Windows I had to install the Realtek HD drivers to get sound to work at all.  Im not sure if thats the problem, but if it is I couldn't get myself through the installation of the HD audio drivers.  If you guys could help that'd be great.  Heres the output of ```
lsmod | grep snd
```

```
snd_hda_intel         344728  5 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

Thanks again, 
-sintax

---

### Post by iaculallad on 2008-06-04
You could try visiting this link if it will work in your case.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314)

---

### Post by aheicher on 2008-06-04
Alright, believe it or not that seemed to fix it, thanks.

---

### Post by msrk on 2011-12-07
Believe it or not I am having this exact problem on the same emachines t3626  now with Ubuntu 11, several years later.  The complicated fixes of 2008 probably don't apply to the current versions of Alsa etc.
I tried every sound setting possible in the Sound Settings tool.  I don't know much about how sound software configuration stuff should work.  Can someone please provide an Apple-esque solution like do some apt-get install thing and then choose something in a box?  It would be greatly appreciated for a dummy like me.  Thank you.

---

