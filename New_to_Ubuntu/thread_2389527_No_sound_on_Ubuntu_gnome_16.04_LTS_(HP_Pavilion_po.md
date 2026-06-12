---
title: "No sound on Ubuntu gnome 16.04 LTS (HP Pavilion power 15)"
date: 2018-04-18
forum: New to Ubuntu
---

### Post by inomnicausa on 2018-04-18
I bought a new laptop and immediately installed ubuntu as my second OS. For the first two days things were OK, but then the sound in internal speakers suddenly disappeared. Speakers work perfectly when i boot into windows, and headphones work in both systems. 

I tried reinstalling ubuntu (bless backups), but the problem just keeps coming back after some time, so that's not really a solution.

I unmuted speakers in alsamixer, but still no sound

output of [COLOR=#000000][FONT=monospace]lspci -v | grep -i -A7 audio: 
[/FONT][/COLOR]```
00:1f.3 Audio device: Intel Corporation Device a171 (rev 31)	Subsystem: Hewlett-Packard Company Device 836b
	Flags: bus master, fast devsel, latency 32, IRQ 143
	Memory at b4428000 (64-bit, non-prefetchable) [size=16K]
	Memory at b4410000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

```

aplay -l: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC295 Analog [ALC295 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

lsmod | grep snd:
```
snd_hda_codec_realtek    98304  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  8
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  25 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd

```

Please tell me if you need more details.

---

