---
title: "Relatively fresh install - no sound 18.04"
date: 2018-06-12
forum: New to Ubuntu
---

### Post by jacklebird on 2018-06-12
Hey, don't have working sound anywhere at the moment with or without headphones, playback of videos is jumpy and at 2-3x speed, not quite sure where to start to begin fixing it.

Some information that might be relevant

Alsamixer:
```

Card: Intel HDMI/DP LPE Audio

"This sound device does not have any controls."

```

Sound settings:
```

Atom/Celeron/Pentium Processor x5-E9000/j3xxx/N3xxx Series PCI Configuration Registers Stereo

Only output is Analogue Output

```

Output of pacmd list-cards
```

1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_02.0-platform-hdmi-lpe-audio>
    driver: <module-alsa-card.c>
    owner module: 7
    properties:
        alsa.card = "0"
        alsa.card_name = "Intel HDMI/DP LPE Audio"
        alsa.long_card_name = "Intel HDMI/DP LPE Audio"
        alsa.driver_name = "snd_hdmi_lpe_audio"
        device.bus_path = "pci-0000:00:02.0-platform-hdmi-lpe-audio"
        sysfs.path = "/devices/pci0000:00/0000:00:02.0/hdmi-lpe-audio/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "22b0"
        device.product.name = "Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers"
        device.string = "0"
        device.description = "Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        output:stereo-fallback: Stereo Output (priority 5100, available: unknown)
        output:multichannel-output: Multichannel Output (priority 100, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:stereo-fallback>
    sinks:
        alsa_output.pci-0000_00_02.0-platform-hdmi-lpe-audio.stereo-fallback/#10: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers Stereo
    sources:
        alsa_output.pci-0000_00_02.0-platform-hdmi-lpe-audio.stereo-fallback.monitor/#10: Monitor of Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers Stereo
    ports:
        analog-output: Analogue Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        multichannel-output: Multichannel Output (priority 0, latency offset 0 usec, available: unknown)
            properties:

```

Thanks

---

### Post by grier-devon on 2018-06-13
Okay first question...

Your thread says "Relatively fresh install", does this mean it has been not working since the install or just recently?

---

### Post by jacklebird on 2018-06-15
Thats correct sorry

---

