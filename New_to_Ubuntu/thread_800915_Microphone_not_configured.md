---
title: "Microphone not configured"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by expatCM on 2008-05-20
My sound works, volume a bit quiet but it works,   the microphone however does not.  I am not sure how to set it.  I have tried to get it working with the preferences in Audacity and in Skype but neither delivers a result.  The hardware is good, it used to work with Ubuntu 7.10 but after installing 8.04 fresh I have not managed to get it going.

I am missing something ...  but I do not quite understand what .....   What is the next step I should take?

**lshw**

 ```
*-multimedia

          description: Audio device

          product: MCP55 High Definition Audio

          vendor: nVidia Corporation

          physical id: 6.1

          bus info: pci@0000:00:06.1

          version: a2

          width: 32 bits

          clock: 66MHz

          capabilities: pm msi ht bus_master cap_list

          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel


```
**aplay -l**
```

**** List of PLAYBACK Hardware Devices ****

card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]

  Subdevices: 1/1

  Subdevice #0: subdevice #0



```
**amixer**
```

Simple mixer control 'Master',0

  Capabilities: pvolume pvolume-joined pswitch pswitch-joined

  Playback channels: Mono

  Limits: Playback 0 - 31

  Mono: Playback 26 [84%] [-7.50dB] [on]

Simple mixer control 'Headphone',0

  Capabilities: pswitch

  Playback channels: Front Left - Front Right

  Mono:

  Front Left: Playback [on]

  Front Right: Playback [on]

Simple mixer control 'PCM',0

  Capabilities: pvolume

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 255

  Mono:

  Front Left: Playback 255 [100%] [0.00dB]

  Front Right: Playback 255 [100%] [0.00dB]

Simple mixer control 'Front',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 25 [81%] [-9.00dB] [on]

  Front Right: Playback 25 [81%] [-9.00dB] [on]

Simple mixer control 'Front Mic',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 25 [81%] [3.00dB] [off]

  Front Right: Playback 25 [81%] [3.00dB] [off]

Simple mixer control 'Front Mic Boost',0

  Capabilities: volume

  Playback channels: Front Left - Front Right

  Capture channels: Front Left - Front Right

  Limits: 0 - 3

  Front Left: 0 [0%]

  Front Right: 0 [0%]

Simple mixer control 'Surround',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 0 [0%] [-46.50dB] [off]

  Front Right: Playback 0 [0%] [-46.50dB] [off]

Simple mixer control 'Center',0

  Capabilities: pvolume pvolume-joined pswitch pswitch-joined

  Playback channels: Mono

  Limits: Playback 0 - 31

  Mono: Playback 0 [0%] [-46.50dB] [off]

Simple mixer control 'LFE',0

  Capabilities: pvolume pvolume-joined pswitch pswitch-joined

  Playback channels: Mono

  Limits: Playback 0 - 31

  Mono: Playback 0 [0%] [-46.50dB] [off]

Simple mixer control 'Side',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 0 [0%] [-46.50dB] [off]

  Front Right: Playback 0 [0%] [-46.50dB] [off]

Simple mixer control 'Line',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 26 [84%] [4.50dB] [off]

  Front Right: Playback 26 [84%] [4.50dB] [off]

Simple mixer control 'CD',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 25 [81%] [3.00dB] [on]

  Front Right: Playback 25 [81%] [3.00dB] [on]

Simple mixer control 'Mic',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 25 [81%] [3.00dB] [on]

  Front Right: Playback 25 [81%] [3.00dB] [on]

Simple mixer control 'Mic Boost',0

  Capabilities: volume

  Playback channels: Front Left - Front Right

  Capture channels: Front Left - Front Right

  Limits: 0 - 3

  Front Left: 2 [67%]

  Front Right: 2 [67%]

Simple mixer control 'IEC958',0

  Capabilities: pswitch pswitch-joined cswitch cswitch-joined

  Playback channels: Mono

  Capture channels: Mono

  Mono: Playback [off] Capture [off]

Simple mixer control 'PC Speaker',0

  Capabilities: pvolume pswitch

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 31

  Mono:

  Front Left: Playback 0 [0%] [-34.50dB] [off]

  Front Right: Playback 0 [0%] [-34.50dB] [off]

Simple mixer control 'Capture',0

  Capabilities: cvolume cswitch

  Capture channels: Front Left - Front Right

  Limits: Capture 0 - 31

  Front Left: Capture 10 [32%] [3.00dB] [off]

  Front Right: Capture 10 [32%] [3.00dB] [off]

Simple mixer control 'Capture',1

  Capabilities: cvolume cswitch

  Capture channels: Front Left - Front Right

  Limits: Capture 0 - 31

  Front Left: Capture 0 [0%] [-12.00dB] [off]

  Front Right: Capture 0 [0%] [-12.00dB] [off]

Simple mixer control 'Channel Mode',0

  Capabilities: enum

  Items: '6ch' '8ch'

  Item0: '6ch'

Simple mixer control 'Digital',0

  Capabilities: cvolume

  Capture channels: Front Left - Front Right

  Limits: Capture 0 - 120

  Front Left: Capture 60 [50%] [0.00dB]

  Front Right: Capture 60 [50%] [0.00dB]

Simple mixer control 'Input Source',0

  Capabilities: cenum

  Items: 'Mic' 'Front Mic' 'Line' 'CD'

  Item0: 'Mic'

Simple mixer control 'Input Source',1

  Capabilities: cenum

  Items: 'Mic' 'Front Mic' 'Line' 'CD'

  Item0: 'Mic'



```
**audacity** 

Selecting Alsa default or any of the Alsa optional ALC883 devices which list the sound card give an error
```

Error while opening sound device. Please check the input device settings and the project sample rate.
```

Sample rate is the default of 44,100


Only selecting the OSS mixer does not generate the error....  but that also does not record ...

---

### Post by kitsune ravo on 2008-05-20
This is just an idea, and I have know idea if it will work, but I had a smiler problem, and I had to uninstall JACK to fix it.

Try
```
sudo apt-get remove jackd
```
and see if it helps at all...

---

### Post by expatCM on 2008-05-20
nice idea but jackd is not installed ........

---

### Post by expatCM on 2008-05-22
anything related to sound in Ubuntu appears to be very hard.  No ideas at all?

---

