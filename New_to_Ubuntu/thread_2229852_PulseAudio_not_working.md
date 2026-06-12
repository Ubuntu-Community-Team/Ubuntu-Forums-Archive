---
title: "PulseAudio not working"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by ViliX64 on 2014-06-15
I was looking up in my volume control panel and I have unintentionally switched some device to another (I don't recall which one) and since then, the volume is not working and when I try to launch volume control, i get this message in the window:

```
Connection to PulseAudio failed. Automatic retry in 5s.

In this case this is likely because PULSE_SERVER in the Enviroment/X11 Root Window Properties or default-server in client.conf is misconfigured.
This situation can also arrise when PulseAudio crashed and left stale fetails in the X11 Root Window. If this is the case, then PulseAudio should autospawn again, or if this is not configure, you should run start-pulseaudio-x11 manually.
```

I know it was dumb of me, but it happened. I have tried purging and then installing pulseaudio, but it didn't worked. Also I've tried removing the pulse directory from /etc/ so everything would be fresh. But it didn't worked neither.

When I try to run it from Terminal, I get this error:
```
E: [pulseaudio] module-ladspa-sink.c: Master sink not foundE: [pulseaudio] module.c: Failed to load module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=5.0,4.0,3.9,3.3,0.0,-4.5,-10.0,-8.9,-8.1,-5.5,-1.5,3.0,6.0,6.1,5.8"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

```

I don't need to use pulseaudio explicitly, I just want to be able to play sound. So if there are any alternatives to pulseaudio..

---

