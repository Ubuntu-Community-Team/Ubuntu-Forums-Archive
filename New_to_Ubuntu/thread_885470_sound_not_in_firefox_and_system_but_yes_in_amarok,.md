---
title: "sound? not in firefox and system but yes in amarok, movie players"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by !ndy on 2008-08-10
i was playing with drivers for nvidia, can this be the cause?
i do not have any sounds in mozilla, pidgin, skype and system (only at login)
but right now i am listening to music through amarok?

monty@Perfect:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

output from lspci:
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by Ryadt on 2008-08-10
Try disabling pulseaudio```
killall pulseaudio
```

---

### Post by !ndy on 2008-08-10
> **Ryadt said:**
> Try disabling pulseaudio```
killall pulseaudio
```

did not work...

i've done some research and done this: lsmod | grep snd

BUT I DONT HAVE INTEL!!! OMG, nothing from intel :-(

monty@Perfect:~$ lsmod | grep snd
snd_hda_intel         344728  4 
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
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

---

### Post by !ndy on 2008-08-11
okay, i think that the problem was in removing mods.

i have read somwhere, that i should remove som "ohsd" or what was its name, so i used remmod and now i remember that there was someone complaining in the comments - about sound issues...

so - dont remove mods until you know what youre doing :-)

---

