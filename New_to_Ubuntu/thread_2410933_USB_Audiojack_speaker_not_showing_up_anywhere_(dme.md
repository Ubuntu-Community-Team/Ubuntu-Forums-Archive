---
title: "USB Audiojack speaker not showing up anywhere (dmesg, lsusb,..)"
date: 2019-01-22
forum: New to Ubuntu
---

### Post by mxox on 2019-01-22
So this is a strange one,

all my devices work and are getting detected, except my USB Audiojack speakers (charge over USB). It does not show up in ```
sudo dmesg -w
``` or ```
lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 258a:1007  
Bus 003 Device 002: ID 045e:0800 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 258a:1006  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```.
(The Microsoft entry being a different USB connection.)
I have a keyboard and a mouse as USB connected as well, but they only show up in dmesg and not in lsusb

As a result it does not show up when choosing audio output devices either.

Since this is a dual boot system, I also have Windows 10 running on the same machine, where the speakers work flawlessly. They are Amazon Basic speakers.

I appreciate your help 

Ubuntu 18.04
Newest Kernel 4.20.3


Edit: I previously had installed the GUI for pulseaudio which only showed my headphones in the output. I don't know if lsusb or what helped, but now there is another entry called "Line Out (unplugged)" which happens to be my speakers! 

Now I would like to know why is it detected as unplugged? Why is it not recognized correctly?

```
 pactl list sinks
Sink #0
    State: IDLE
    Name: alsa_output.pci-0000_26_00.1.hdmi-stereo-extra5
    Description: Ellesmere [Radeon RX 580] Digital Stereo (HDMI 6)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 7
    Mute: no
    Volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    Base Volume: 65536 / 100% / 0,00 dB
    Monitor Source: alsa_output.pci-0000_26_00.1.hdmi-stereo-extra5.monitor
    Latency: 39929 usec, configured 40000 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 5"
        alsa.id = "HDMI 5"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "11"
        alsa.card = "0"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xfe960000 irq 55"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:26:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:03.1/0000:26:00.1/sound/card0"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "aaf0"
        device.product.name = "Ellesmere [Radeon RX 580]"
        device.string = "hdmi:0,5"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo-extra5"
        device.profile.description = "Digital Stereo (HDMI 6)"
        device.description = "Ellesmere [Radeon RX 580] Digital Stereo (HDMI 6)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,00aa0100,00100700"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        hdmi-output-5: HDMI / DisplayPort 6 (priority: 5400, available)
    Active Port: hdmi-output-5
    Formats:
        pcm

Sink #1
    State: IDLE
    Name: alsa_output.pci-0000_28_00.3.analog-stereo
    Description: Family 17h (Models 00h-0fh) HD Audio Controller Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 8
    Mute: no
    Volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
            balance 0,00
    Base Volume: 65536 / 100% / 0,00 dB
    Monitor Source: alsa_output.pci-0000_28_00.3.analog-stereo.monitor
    Latency: 24953 usec, configured 25000 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC892 Analog"
        alsa.id = "ALC892 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "HD-Audio Generic"
        alsa.long_card_name = "HD-Audio Generic at 0xfe800000 irq 57"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:28:00.3"
        sysfs.path = "/devices/pci0000:00/0000:00:08.1/0000:28:00.3/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1022"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD]"
        device.product.id = "1457"
        device.product.name = "Family 17h (Models 00h-0fh) HD Audio Controller"
        device.string = "front:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Family 17h (Models 00h-0fh) HD Audio Controller Analog Stereo"
        alsa.mixer_name = "Realtek ALC892"
        alsa.components = "HDA:10ec0892,18496893,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-output-lineout: Line Out (priority: 9900, not available)
        analog-output-headphones: Headphones (priority: 9000, available)
    Active Port: analog-output-lineout
    Formats:
        pcm


```

I got a HDMI device connected, so this may be the reason for the many HDMI entries. Sorry for that.

---

