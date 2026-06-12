---
title: "Beats audio HP Envy TS 15 not working"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by mmarti92 on 2013-11-23
I have read past threads about how to solve the problem, I have tried installing HDA jack retasking and some of the other solutions provided and none of them seem to work for me. Is there anything else I could try?
Thank you

---

### Post by Paul_Maki on 2014-01-01
mmarti92,

  I'm not going to be able to assist you as I'm experiencing the same issue and I believe we may have very similar hardware. However, in order for others to lend a helping hand with this extremely irritating and vile problem, you will have to provide some more information. Please reply with exact information about your laptop including chipset, video card, RAM, etc, and the outputs of the following commands in the terminal:

This will tell us what audio cards you have:
```
lspci | grep "Audio"
```

This will tell us your various audio devices:
```
aplay -l
```

This will tell us specific information about your audio cards:
```
pacmd list-sinks
```

Here is my information:
HP ENVY 15t-j000 Quad Edition Notebook PC
&#8226; Windows 8 64
&#8226; 4th generation Intel(R) Core(TM) i7-4700MQ Processor
&#8226; NVIDIA GeForce GT 740M Graphics with 2048MB of dedicated video memory
&#8226; 15.6-inch diagonal Full HD BrightView LED-backlit Display (1920x1080)
&#8226; 16GB DDR3 System Memory (2 Dimm)
&#8226; 1TB 5400RPM Hybrid Hard Drive
&#8226; HP TrueVision HD Webcam w/ integrated digital mic
&#8226; 802.11b/g/n WLAN and Bluetooth(R)

```
@UbuntuEnvy:~$ lspci | grep "Audio"
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)

```

```
@UbuntuEnvy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: 92HD91BXX Analog [92HD91BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
l@UbuntuEnvy:~$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 3 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_03.0.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9950
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_03.0>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "0"
        alsa.card_name = "HDA Intel MID"
        alsa.long_card_name = "HDA Intel MID at 0xd3710000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0c0c"
        device.product.name = "Haswell HD Audio Controller"
        device.form_factor = "internal"
        device.string = "hdmi:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Built-in Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "Intel Haswell HDMI"
        alsa.components = "HDA:80862807,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "92HD91BXX Analog"
        alsa.id = "92HD91BXX Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xd3714000 irq 48"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8c20"
        device.product.name = "Lynx Point High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "IDT 92HD91BXX"
        alsa.components = "HDA:111d76e0,103c1963,00100303"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-speaker>
    index: 2
    name: <combined>
    driver: <module-combine-sink.c>
    flags: DECIBEL_VOLUME LATENCY 
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1000
    volume: 0:  56% 1:  56% 2: 100% 3: 100% 4:  56% 5: 100%
            0: -15.11 dB 1: -15.11 dB 2: 0.00 dB 3: 0.00 dB 4: -15.11 dB 5: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 103 KiB
    max rewind: 0 KiB
    monitor source: 3
    sample spec: s16le 6ch 44100Hz
    channel map: front-left,front-right,rear-left,rear-right,front-center,lfe
                 Surround 5.1
    used by: 0
    linked by: 0
    fixed latency: 200.00 ms
    module: 21
    properties:
        device.class = "filter"
        device.description = "Simultaneous output to Built-in Audio Digital Stereo (HDMI), Built-in Audio Analog Stereo"
        device.icon_name = "audio-card"
```

One of the most frustrating things about this is the fact that I (and probably you too) have the same sound card (Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller) as many others and the same audio codec (IDT 92HD91BXX) also. In fact, many people with HP laptops with this very codec have found solutions using HDA Jack Retask or editing config files:
[Beats Audio on Linux]("http://www.linux.org/threads/beats-audio-on-linux.4443/")
[URL="http://www.reddit.com/r/linux/comments/17sov5/"][HowTo] Beats Audio HP Laptop speakers on Ubuntu/PulseAudio
[/URL][Beats Audio Driver For HP CV-6-7040tx]("http://askubuntu.com/questions/299769/beats-audio-driver-for-hp-dv6-7040tx")
[Beats Audio (HP Envy 15) On Ubuntu]("http://incognitech.wordpress.com/2013/10/27/beats-audio-hp-envy-15-on-ubuntu/")

For some reason, in spite of having the same audio chip, HP continuously changes something requiring different fixes with virtually every model. It is infuriating. Also, the higher end HP laptops of 2013 like the one I purchased require completely different fixes than previous models. Hopefully, this will breathe some new life into this thread and with some more information from you and what I provided, we can work together with some fully caffeinated Ubuntu Forums members to find a solid fix.

I apologize in advance for any errors or lack of information, I too am a new Ubuntu user. I've been using it for a while as a second laptop, but now I'm trying to convert full time and the Beats Audio issue is one of a few holding me back.

Regards,

---

### Post by a-shmakov90 on 2014-02-22
I have the same issue on my HP Envy 15 with almost the same configuration:

[COLOR=#000000]• Windows 8 64[/COLOR]
[COLOR=#000000]• 4th generation Intel(R) Core(TM) i7-4900MQ Processor[/COLOR]
[COLOR=#000000]• Intel Haswell 4600[/COLOR]
[COLOR=#000000]• 15.6-inch diagonal Full HD BrightView LED-backlit Display (1920x1080)[/COLOR]
[COLOR=#000000]• 16GB DDR3 System Memory (2 Dimm)[/COLOR]
[COLOR=#000000]• SSD Intel Series 520 256GB[/COLOR]
[COLOR=#000000]• HP TrueVision HD Webcam w/ integrated digital mic[/COLOR]
[COLOR=#000000]• 802.11b/g/n WLAN and Bluetooth(R)
[/COLOR]
```
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)

```
```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: 92HD91BXX Analog [92HD91BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

>>> 3 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_03.0.hdmi-stereo-extra1>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9950
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_03.0>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 1"
        alsa.id = "HDMI 1"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "7"
        alsa.card = "0"
        alsa.card_name = "HDA Intel MID"
        alsa.long_card_name = "HDA Intel MID at 0xb2710000 irq 48"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0c0c"
        device.product.name = "Haswell HD Audio Controller"
        device.form_factor = "internal"
        device.string = "hdmi:0,1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra1"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Built-in Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "Intel Haswell HDMI"
        alsa.components = "HDA:80862807,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-1>
    index: 2
    name: <combined>
    driver: <module-combine-sink.c>
    flags: DECIBEL_VOLUME LATENCY 
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1000
    volume: 0: 100% 1: 100% 2: 100%
            0: 0.00 dB 1: 0.00 dB 2: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 51 KiB
    max rewind: 0 KiB
    monitor source: 3
    sample spec: s16le 3ch 44100Hz
    channel map: front-left,front-right,lfe
    used by: 0
    linked by: 0
    fixed latency: 200.00 ms
    module: 20
    properties:
        device.class = "filter"
        device.description = "Simultaneous output to Built-in Audio Digital Stereo (HDMI), Built-in Audio Analog Surround 4.1"
        device.icon_name = "audio-card"
  * index: 4
    name: <alsa_output.pci-0000_00_1b.0.analog-surround-41>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0:  75% 1:  75% 2:  75% 3:  75% 4:  75%
            0: -7.50 dB 1: -7.50 dB 2: -7.50 dB 3: -7.50 dB 4: -7.50 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 5
    sample spec: s16le 5ch 48000Hz
    channel map: front-left,front-right,rear-left,rear-right,lfe
                 Surround 4.1
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 113.75 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "92HD91BXX Analog"
        alsa.id = "92HD91BXX Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xb2714000 irq 47"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8c20"
        device.product.name = "Lynx Point High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "surround41:1"
        device.buffering.buffer_size = "54600"
        device.buffering.fragment_size = "27300"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-surround-41"
        device.profile.description = "Analog Surround 4.1"
        device.description = "Built-in Audio Analog Surround 4.1"
        alsa.mixer_name = "IDT 92HD91BXX"
        alsa.components = "HDA:111d76e0,103c1962,00100303"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
    active port: <analog-output>


```

I tried all combinations of pins overriding via hdajackretask tool but I never got to work front and rear speakers simultaneously.

---

### Post by Riley_Chapple on 2014-04-03
I dont know if you guys have figured this out, but just upgrade to 13.10 thru the software center and the hda-reJack thing works straight away. Currently getting my ear drums blown out. Screen brightness also works out of the box.

---

### Post by a-shmakov90 on 2014-04-22
Tried everything on 13.10, now it's 14.04 but sound still doesn't work properly... :'(

---

### Post by drplix on 2014-04-23
I have exactly the same laptop.  I've been using the Beta of 14.04 for about 6 weeks - I can confirm that until recently the hdajackretask pin assignment trick worked (see  [http://incognitech.wordpress.com/2013/10/27/beats-audio-hp-envy-15-on-ubuntu/](http://incognitech.wordpress.com/2013/10/27/beats-audio-hp-envy-15-on-ubuntu/)).   However, earlier this week I accepted the final set of updates to the full 14.04 and since then my laptop speakers have stopped working even with the pin assignment.

Please post here if anyone makes any progress with this.

PS If I use hdajackretask and clear the pin assignment override (to, I guess, the default) then I do get two speakers working again after a reboot - but its a long way from the full quality/capability of the beats audio sub-system.

---

### Post by anirban-ninja on 2014-04-24
Any updates on Ubuntu 14.04 LTS - if Beats audio works?

---

