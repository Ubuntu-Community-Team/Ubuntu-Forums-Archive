---
title: "no sound at all!"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by eagzor on 2011-09-06
Using all kind of apps and i get no sound at all, latest updates as of today. Well everything plays, but just no sound at all, and its unmuted of course.

using
lsmod | grep snd 
as root gives output:
snd_hda_codec_analog    75090  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm

---

### Post by axatrikx on 2011-09-06
whats the output of ```
sudo aplay -l
```

or check this link
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by atno on 2011-09-06
> **eagzor said:**
> Using all kind of apps and i get no sound at all, latest updates as of today. Well everything plays, but just no sound at all, and its unmuted of course.

using
lsmod | grep snd 
as root gives output:
snd_hda_codec_analog    75090  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm

had the same problem, add your username in /etc/group under the audio group.

here's how mine it looks like.
```
audio:x:29:pulse,atno
```

---

### Post by eagzor on 2011-09-06
Oh my god how was i even supposed to figure out that one, thanks alot.

---

### Post by theanswriz42 on 2011-09-06
deleted

---

