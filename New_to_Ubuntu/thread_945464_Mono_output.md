---
title: "Mono output"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Dungdae on 2008-10-12
I have a EMU 1212 soundcard, and got the drivers installed properly, it worked fine for months with a stereo output. 
However one day i tried to enter the *alsamixer* in the terminal, and made the mistake of writing *amixer* And since that the output have been mono:( 

I'm running dual boot and in windows, the sound works perfectly...

(System ubuntu 8.04 64 bit hardy)

Here is what it looks like

```
amixer | less:
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Tone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Bass',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 11 [28%]
  Front Right: 11 [28%]
Simple mixer control 'Treble',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 80 [80%] [-8.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 80 [80%] [-8.00dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 92 [92%] [-3.20dB]
  Front Right: Playback 92 [92%] [-3.20dB]
Simple mixer control 'Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
Simple mixer control 'DSP 0',0
  Capabilities: cenum
  Items: 'Silence' 'Dock Mic A' 'Dock Mic B' 'Dock ADC1 Left' 'Dock ADC1 Right' 'Dock ADC2 Left' 'Dock ADC2 Right' 'Dock ADC3 Left' 'Dock ADC3 Right' '0202 ADC Left' '0202 ADC Right' '0202 SPDIF Left' '0202 SPDIF Right' 'ADAT 0' 'ADAT 1' 'ADAT 2' 'ADAT 3' 'ADAT 4' 'ADAT 5' 'ADAT 6' 'ADAT 7' 'DSP 0' 'DSP 1' 'DSP 2' 'DSP 3' 'DSP 4' 'DSP 5' 'DSP 6' 'DSP 7' 'DSP 8' 'DSP 9' 'DSP 10' 'DSP 11' 'DSP 12' 'DSP 13' 'DSP 14' 'DSP 15' 'DSP 16' 'DSP 17' 'DSP 18' 'DSP 19' 'DSP 20' 'DSP 21' 'DSP 22' 'DSP 23' 'DSP 24' 'DSP 25' 'DSP 26' 'DSP 27' 'DSP 28' 'DSP 29' 'DSP 30' 'DSP 31'
  Item0: 'Silence'
Simple mixer control 'DSP 1',0
  Capabilities: cenum
  Items: 'Silence' 'Dock Mic A' 'Dock Mic B' 'Dock ADC1 Left' 'Dock ADC1 Right' 'Dock ADC2 Left' 'Dock ADC2 Right' 'Dock ADC3 Left' 'Dock ADC3 Right' '0202 ADC Left' '0202 ADC Right' '0202 SPDIF Left' '0202 SPDIF Right' 'ADAT 0' 'ADAT 1' 'ADAT 2' 'ADAT 3' 'ADAT 4' 'ADAT 5' 'ADAT 6' 'ADAT 7' 'DSP 0' 'DSP 1' 'DSP 2' 'DSP 3' 'DSP 4' 'DSP 5' 'DSP 6' 'DSP 7' 'DSP 8' 'DSP 9' 'DSP 10' 'DSP 11' 'DSP 12' 'DSP 13' 'DSP 14' 'DSP 15' 'DSP 16' 'DSP 17' 'DSP 18' 'DSP 19' 'DSP 20' 'DSP 21' 'DSP 22' 'DSP 23' 'DSP 24' 'DSP 25' 'DSP 26' 'DSP 27' 'DSP 28' 'DSP 29' 'DSP 30' 'DSP 31'
  Item0: 'Silence'
Simple mixer control 'DSP 10',0
  Capabilities: cenum
  Items: 'Silence' 'Dock Mic A' 'Dock Mic B' 'Dock ADC1 Left' 'Dock ADC1 Right' 'Dock ADC2 Left' 'Dock ADC2 Right' 'Dock ADC3 Left' 'Dock ADC3 Right' '0202 ADC Left' '0202 ADC Right' '0202 SPDIF Left' '0202 SPDIF Right' 'ADAT 0' 'ADAT 1' 'ADAT 2' 'ADAT 3' 'ADAT 4' 'ADAT 5' 'ADAT 6' 'ADAT 7' 'DSP 0' 'DSP 1' 'DSP 2' 'DSP 3' 'DSP 4' 'DSP 5' 'DSP 6' 'DSP 7' 'DSP 8' 'DSP 9' 'DSP 10' 'DSP 11' 'DSP 12' 'DSP 13' 'DSP 14' 'DSP 15' 'DSP 16' 'DSP 17' 'DSP 18' 'DSP 19' 'DSP 20' 'DSP 21' 'DSP 22' 'DSP 23' 'DSP 24' 'DSP 25' 'DSP 26' 'DSP 27' 'DSP 28' 'DSP 29' 'DSP 30' 'DSP 31'
  Item0: 'Silence'
...
And alot more like that... 

```

i think that its the topline thats important, but don't know what to do, to change it!!

Plz someone help:(

---

