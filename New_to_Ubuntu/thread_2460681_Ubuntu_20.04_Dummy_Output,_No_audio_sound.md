---
title: "Ubuntu 20.04: Dummy Output, No audio sound"
date: 2021-04-15
forum: New to Ubuntu
---

### Post by smakbar on 2021-04-15
```
/sbin/lsmod | grep snd
```

snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_codec_hdmi     61440  2
snd_hda_intel          53248  7
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         139264  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               114688  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  2 snd_seq,snd_pcm
snd                    94208  25 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd


```
lspci -v
```

Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company RTS522A PCI Express Card Reader
    Physical Slot: 4
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Memory at b4300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci


```
pavucontrol
```

no card detected

```
alsamixer
```
 Card: HDA Intel PCH                                                                                                                                       
&#9474; Chip: Realtek ALC295                                                                                                                                  
&#9474; View: F3:[Playback] F4: Capture  F5: All                                                                                                                
&#9474; Item: Master [dB gain: 0.00]                                                                                                                        


HDAJackRetask
3 options availabe Nvidia GPU 80 HDMI/UP,  Intel Kaylake HDMI, Realtek ALC 295


[B]Initially the speakers and earphones were working properly but the mic wasn't. However, I ruined everything in order to fix mic input.
PLEASE, PLEASE HELP!!! 
[/B]

---

### Post by coffeecat on 2021-04-16
Duplicate posted [here]("https://ubuntuforums.org/showthread.php?t=2460695"). Please do not post duplicates.

Closed.

---

