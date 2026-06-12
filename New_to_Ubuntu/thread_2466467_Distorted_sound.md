---
title: "Distorted sound"
date: 2021-08-28
forum: New to Ubuntu
---

### Post by psychohermit on 2021-08-28
Hi folks,

Running ubuntu 20.04.2.0 LTS and loving it.  I have a 7 year old HP Envy Touchsmart Notebook (em6na)
s
Playing tunes with RythmBox.  Sometimes sound is distorted.  Closing and reopening Rythmbox corrects the issue sometimes.  I may have to close and reopen several time before sound is clear again.

```

 sudo lspci |grep Audio
[sudo] password for glenn: 
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
glenn@Psycho:~/Desktop$

sudo /sbin/lsmod | grep snd
snd_hda_codec_realtek   135168  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  1
snd_hda_intel          53248  6
snd_intel_dspcfg       28672  1 snd_hda_intel
soundwire_intel        40960  1 snd_intel_dspcfg
snd_hda_codec         147456  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_soc_core          286720  1 soundwire_intel
snd_compress           28672  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm               114688  9 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_compress,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                    94208  24 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
sounsudo /sbin/lsmod | grep snd
snd_hda_codec_realtek   135168  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  1
snd_hda_intel          53248  6
snd_intel_dspcfg       28672  1 snd_hda_intel
soundwire_intel        40960  1 snd_intel_dspcfg
snd_hda_codec         147456  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_soc_core          286720  1 soundwire_intel
snd_compress           28672  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm               114688  9 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_compress,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                73728  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                    94208  24 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
dcore              16384  1 snd

```

Thanks in advance for any assistance you can offer.

[edit] I used aumix to lower the levels to 86%.  Time wil tell if that helps. [/edit]

--glenn

---

