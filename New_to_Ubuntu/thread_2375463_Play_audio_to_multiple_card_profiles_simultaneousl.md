---
title: "Play audio to multiple card profiles simultaneously"
date: 2017-10-24
forum: New to Ubuntu
---

### Post by ofekih on 2017-10-24
Hello, I saw tons of ways to play audio to multiple devices which have separate sinks, but my problem is that I have multiple card profiles on the same sound card. My laptop is connected to a monitor via an HDMI cable, and I wanted to be able to play sound out of both devices at once.

I can switch between devices by running:

```

    pactl set-card-profile alsa_card.pci-0000_00_1f.3 output:hdmi-stereo
    pactl set-card-profile alsa_card.pci-0000_00_1f.3 output:analog-stereo

```

With each profile, only one sink is showing. The outputs of ```
pactl list sinks short
``` for one is:

```
alsa_output.pci-0000_00_1f.3.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    RUNNING
```

And for the other:

```
    alsa_output.pci-0000_00_1f.3.hdmi-stereo    module-alsa-card.c    s16le 2ch 44100Hz    RUNNING
```

Does anyone know if it's possible to play out of both profiles at once?

Thanks in advance!

---

### Post by yetimon_64 on 2017-10-25
That should be much easier to accomplish in the GUI rather than the terminal by running "Pulseaudio Preferences" (use "alt + f2" and type in "paprefs" without the quotes and pressing the "Enter" key will launch it.)
On the last tab for "Simultaneous output" tick the box for "Add virtual output device for simultaneous output on all local sound cards". This will give you a set of controls in the pulseaudio volume controls for simultaneous output which is much easier than trying to add such controls with the terminal.

However if you do want to try with the terminal to add such controls you could try with the pacmd commands below, I have copy/pasted in your device descriptions you posted,

```
pacmd load-module module-combine-sink sink_name=combined sink_properties=device.description="Simultaneous_output" slaves=alsa_card.pci-0000_00_1f.3,alsa_card.pci-0000_00_1f.3 channels=2
```
The above command, if it works, will add a Simultaneous_Output option to the pulse audio volume controls.

The next command if run will remove the simultaneous output device from the volume controls when it is needed to be removed ...
```
pacmd unload-module module-combine-sink
```

Regards, yeti.

---

