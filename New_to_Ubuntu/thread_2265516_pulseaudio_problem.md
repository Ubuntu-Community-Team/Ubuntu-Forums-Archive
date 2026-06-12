---
title: "pulseaudio problem"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by klyushin on 2015-02-15
Hi guys! Please help me with pulseaudio.

I want to stream my audio to another laptop (also Lubuntu on board).
I went to [pulseaudio first steps guide]("http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/FirstSteps/") and the first command they tell to perform ```
pulseaudio -nC

``` causes an error:
```
klyushin@klyushin-Aspire-5720Z:~$ pulseaudio -nC
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.


```

What can be done? THX!

p.s.: I should mention that at the moment everything is okay with my sound - I can listen to music etc w/o any problems.

---

### Post by klyushin on 2015-02-16
So, I managed to make through this problem. By killing the process pulseaudio by command:
```
pulseaudio -k
```

So this issue is closed.

---

### Post by sandyd on 2015-02-16
Hi,
If you have found a solution to your problem, please mark this thread as solved using Thread Tools -> Mark Thread as Solved.

Thanks!

---

### Post by klyushin on 2015-02-16
Sorry but I haven't managed to make pulseaudio work yet - I've done everything posted in [this article ]("http://www.techytalk.info/pulseaudio-network-sound-server/")and I'm stuck at entering "gnome-volume-control" I don't know if I should install it ... I've got some ALSA mixer v1.0.28 installed. Have you got any idea what should I do next? 

The guide says to do these final steps to make the thing work:
> **Using your PC as PulseAudio network client**

 Now you can open sound options on your client PC by pressing Alt+F2  and entering "gnome-volume-control" into the "Run Application" dialog.  On the "Output" tab you should be able to select any of the devices on  your server PC as well as any local sound device as output device. If  you don't find all of your server sound devices on the "Output" list  inside "gnome-volume-control" of your client PC, retrace your steps and  make sure that all settings on the server PC as well as on the client  PCs are OK. One more thing. Pulse audio is network application so  restrictive firewall could get into the way of your remote audio. Also  sometimes is required to reboot server and client PCs for everything to  work properly after enabling PulseAudio network capabilities. If  everything is OK and you have selected client sound device of your  choice as the output device inside "gnome-volume-control", you can start  your preferred music player on the client and listen your audio on the  speakers connected to the selected client PC.



---

### Post by sandyd on 2015-02-16
Does it show up in pavucontrol?

Pavucontrol stands for pulse audio volume control, and is not installed by default.
To install:
```

sudo apt-get install pavucontrol
pavucontrol

```

---

### Post by klyushin on 2015-02-16
I've installed pavucontrol now I'm getting this message whet I execute **pavucontrol** 


[IMG]http://i.imgur.com/EZphXeY.png[/IMG]

---

### Post by sandyd on 2015-02-16
Is pulseaudio running on the client?

Post output of```
ps aux | grep pulseaudio
```

---

### Post by klyushin on 2015-02-16
```
klyushin@klyushin-Aspire-5720Z:~$ ps aux | grep pulseaudio
klyushin  7667  0.0  0.0   5928  2308 pts/1    S+   04:16   0:00 grep --color=auto pulseaudio

```

---

### Post by sandyd on 2015-02-16
Pulseaudio isnt started

Run
```

pulseaudio --start --log-target=syslog
ps aux | grep pulseaudio

```

---

### Post by klyushin on 2015-02-17
```
klyushin@klyushin-Aspire-5720Z:~$ pulseaudio --start --log-target=syslog
klyushin@klyushin-Aspire-5720Z:~$ ps aux | grep pulseaudio
klyushin 10679  0.0  0.0   5928  2256 pts/4    S+   15:50   0:00 grep --color=auto pulseaudio

```

still **pavucoltrol** gives the same message

...

tried to do:  =>   delete the .config/pulse folder   =>  reboot

it didn't work ... output:
```
klyushin@klyushin-Aspire-5720Z:~$ pulseaudio 
E: [pulseaudio] ltdl-bind-now.c: Failed to open module module-esound-protocol-tcp.so: module-esound-protocol-tcp.so: cannot open shared object file: No such file or directory
E: [pulseaudio] module.c: Failed to open module "module-esound-protocol-tcp".
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.
klyushin@klyushin-Aspire-5720Z:~$ pulseaudio --start
E: [pulseaudio] main.c: Daemon startup failed.


```

**pulseaudio -v**

```
klyushin@klyushin-Aspire-5720Z:~$ pulseaudio -v
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 4.0
I: [pulseaudio] main.c: Page size is 4096 bytes
I: [pulseaudio] main.c: Machine ID is 83597cbc1597f0472684b2f254480132.
I: [pulseaudio] main.c: Session ID is c2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/klyushin/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 
I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/klyushin/.config/pulse/83597cbc1597f0472684b2f254480132-device-volumes'.
I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/klyushin/.config/pulse/83597cbc1597f0472684b2f254480132-stream-volumes'.
I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/klyushin/.config/pulse/83597cbc1597f0472684b2f254480132-card-database'.
I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #4; argument: "").
I: [pulseaudio] (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/HDA Intel/HDA Intel.conf
I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card HDA Intel
I: [pulseaudio] (alsa-lib)main.c: error: failed to import HDA Intel use case configuration -2
I: [pulseaudio] alsa-ucm.c: UCM not available for card HDA Intel
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround40:0: Invalid argument
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround41:0: Invalid argument
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround50:0: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround51:0: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround71:0: Invalid argument
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL iec958:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer iec958:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D3p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D7p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D7p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,1: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D8p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D8p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,2: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
I: [pulseaudio] module-card-restore.c: Restoring port latency offsets for card alsa_card.pci-0000_00_1b.0.
I: [pulseaudio] card.c: Created 0 "alsa_card.pci-0000_00_1b.0"
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
I: [pulseaudio] alsa-sink.c: Successfully opened device front:0.
I: [pulseaudio] alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] sink.c: Created sink 0 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
I: [pulseaudio] sink.c:     device.api = "alsa"
I: [pulseaudio] sink.c:     device.class = "sound"
I: [pulseaudio] sink.c:     alsa.class = "generic"
I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] sink.c:     alsa.name = "ALC268 Analog"
I: [pulseaudio] sink.c:     alsa.id = "ALC268 Analog"
I: [pulseaudio] sink.c:     alsa.subdevice = "0"
I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] sink.c:     alsa.device = "0"
I: [pulseaudio] sink.c:     alsa.card = "0"
I: [pulseaudio] sink.c:     alsa.card_name = "HDA Intel"
I: [pulseaudio] sink.c:     alsa.long_card_name = "HDA Intel at 0xdb300000 irq 45"
I: [pulseaudio] sink.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: [pulseaudio] sink.c:     device.bus = "pci"
I: [pulseaudio] sink.c:     device.vendor.id = "8086"
I: [pulseaudio] sink.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] sink.c:     device.product.id = "284b"
I: [pulseaudio] sink.c:     device.product.name = "82801H (ICH8 Family) HD Audio Controller"
I: [pulseaudio] sink.c:     device.form_factor = "internal"
I: [pulseaudio] sink.c:     device.string = "front:0"
I: [pulseaudio] sink.c:     device.buffering.buffer_size = "65536"
I: [pulseaudio] sink.c:     device.buffering.fragment_size = "32768"
I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer"
I: [pulseaudio] sink.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] sink.c:     device.profile.description = "Analog Stereo"
I: [pulseaudio] sink.c:     device.description = "Built-in Audio Analog Stereo"
I: [pulseaudio] sink.c:     alsa.mixer_name = "Realtek ALC268"
I: [pulseaudio] sink.c:     alsa.components = "HDA:10ec0268,1025011e,00100003 HDA:14f12c06,1025011e,00100000"
I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] source.c: Created source 0 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of Built-in Audio Analog Stereo"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     alsa.card = "0"
I: [pulseaudio] source.c:     alsa.card_name = "HDA Intel"
I: [pulseaudio] source.c:     alsa.long_card_name = "HDA Intel at 0xdb300000 irq 45"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "8086"
I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] source.c:     device.product.id = "284b"
I: [pulseaudio] source.c:     device.product.name = "82801H (ICH8 Family) HD Audio Controller"
I: [pulseaudio] source.c:     device.form_factor = "internal"
I: [pulseaudio] source.c:     device.string = "0"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-sink.c: Using 2,0 fragments of size 32768 bytes (185,76ms), buffer size is 65536 bytes (371,52ms)
I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20,00ms
I: [pulseaudio] alsa-sink.c: Successfully enabled deferred volume.
I: [pulseaudio] alsa-sink.c: Hardware volume ranges from -179,00 dB to 0,00 dB.
I: [pulseaudio] alsa-sink.c: Fixing base volume to 0,00 dB
I: [pulseaudio] alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-sink.c: Using hardware mute control.
I: [alsa-sink-ALC268 Analog] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-sink-ALC268 Analog] alsa-sink.c: Starting playback.
I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
I: [pulseaudio] alsa-source.c: Successfully opened device front:0.
I: [pulseaudio] alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: [pulseaudio] alsa-source.c: Successfully enabled mmap() mode.
I: [pulseaudio] alsa-source.c: Successfully enabled timer-based scheduling mode.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] source.c: Created source 1 "alsa_input.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     alsa.resolution_bits = "16"
I: [pulseaudio] source.c:     device.api = "alsa"
I: [pulseaudio] source.c:     device.class = "sound"
I: [pulseaudio] source.c:     alsa.class = "generic"
I: [pulseaudio] source.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] source.c:     alsa.name = "ALC268 Analog"
I: [pulseaudio] source.c:     alsa.id = "ALC268 Analog"
I: [pulseaudio] source.c:     alsa.subdevice = "0"
I: [pulseaudio] source.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] source.c:     alsa.device = "0"
I: [pulseaudio] source.c:     alsa.card = "0"
I: [pulseaudio] source.c:     alsa.card_name = "HDA Intel"
I: [pulseaudio] source.c:     alsa.long_card_name = "HDA Intel at 0xdb300000 irq 45"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "8086"
I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] source.c:     device.product.id = "284b"
I: [pulseaudio] source.c:     device.product.name = "82801H (ICH8 Family) HD Audio Controller"
I: [pulseaudio] source.c:     device.form_factor = "internal"
I: [pulseaudio] source.c:     device.string = "front:0"
I: [pulseaudio] source.c:     device.buffering.buffer_size = "65536"
I: [pulseaudio] source.c:     device.buffering.fragment_size = "32768"
I: [pulseaudio] source.c:     device.access_mode = "mmap+timer"
I: [pulseaudio] source.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] source.c:     device.profile.description = "Analog Stereo"
I: [pulseaudio] source.c:     device.description = "Built-in Audio Analog Stereo"
I: [pulseaudio] source.c:     alsa.mixer_name = "Realtek ALC268"
I: [pulseaudio] source.c:     alsa.components = "HDA:10ec0268,1025011e,00100003 HDA:14f12c06,1025011e,00100000"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-source.c: Using 2,0 fragments of size 32768 bytes (185,76ms), buffer size is 65536 bytes (371,52ms)
I: [pulseaudio] alsa-source.c: Time scheduling watermark is 20,00ms
I: [pulseaudio] alsa-source.c: Successfully enabled deferred volume.
I: [pulseaudio] alsa-source.c: Hardware volume ranges from -16,50 dB to 70,00 dB.
I: [pulseaudio] alsa-source.c: Fixing base volume to -70,00 dB
I: [pulseaudio] alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-source.c: Using hardware mute control.
I: [alsa-source-ALC268 Analog] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-source-ALC268 Analog] alsa-source.c: Starting capture.
I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"").
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card0 (alsa_card.pci-0000_00_1b.0) module loaded.
I: [pulseaudio] module-udev-detect.c: Found 1 cards.
I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #6; argument: "").
I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
E: [pulseaudio] ltdl-bind-now.c: Failed to open module module-esound-protocol-tcp.so: module-esound-protocol-tcp.so: cannot open shared object file: No such file or directory
E: [pulseaudio] module.c: Failed to open module "module-esound-protocol-tcp".
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.
I: [pulseaudio] module.c: Unloading "module-native-protocol-unix" (index: #7).
I: [pulseaudio] module.c: Unloaded "module-native-protocol-unix" (index: #7).
I: [pulseaudio] module.c: Unloading "module-udev-detect" (index: #6).
I: [pulseaudio] module.c: Unloaded "module-udev-detect" (index: #6).
I: [pulseaudio] module.c: Unloading "module-alsa-card" (index: #5).
I: [pulseaudio] sink.c: Freeing sink 0 "alsa_output.pci-0000_00_1b.0.analog-stereo"
I: [pulseaudio] source.c: Freeing source 0 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor"
I: [pulseaudio] source.c: Freeing source 1 "alsa_input.pci-0000_00_1b.0.analog-stereo"
I: [pulseaudio] card.c: Freed 0 "alsa_card.pci-0000_00_1b.0"
I: [pulseaudio] module.c: Unloaded "module-alsa-card" (index: #5).
I: [pulseaudio] module.c: Unloading "module-switch-on-port-available" (index: #4).
I: [pulseaudio] module.c: Unloaded "module-switch-on-port-available" (index: #4).
I: [pulseaudio] module.c: Unloading "module-augment-properties" (index: #3).
I: [pulseaudio] module.c: Unloaded "module-augment-properties" (index: #3).
I: [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
I: [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
I: [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
I: [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
I: [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
I: [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
I: [pulseaudio] main.c: Daemon terminated.


```

---

### Post by sandyd on 2015-02-17
```
E: [pulseaudio] module.c: Failed to open module "module-esound-protocol-tcp".
```
Well, thats an issue.

Lets go install the module and try again
```

sudo apt-get install pulseaudio-esound-compat
```

---

### Post by klyushin on 2015-02-17
I made what was recommended in [this article]("http://startubuntu.ru/?p=104278") and it helped me to launch **pavucontrol** ....

---

### Post by klyushin on 2015-02-17
So I've found what was the reason why I got the error:
I was reading an article and I've used a wrong prompt - I removed comment symbols # from file /etc/pulse/default.pa
in lines bold:
```
### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
**#load-module module-esound-protocol-tcp**
[B]#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish[/B]
```

when I put them up again I managed to launch pulseaudio

Now after I rebooted both laptops I can choose the recepient laptop in Playback tab - and the sound starts working on the second laptop.

[IMG]http://i.imgur.com/Ak5EYP6.png[/IMG]

the strange thing is that it can be done only after I first uncheck and then check again these options on both laptops - as if it helps to load up some features - if I don't do it - it will not work.
[IMG]http://i.imgur.com/WNkwNAw.png[/IMG]
----
[IMG]http://i.imgur.com/OvoWNI5.png[/IMG]

another strange feature is that when I start doing something (surf in a browser of the server laptop) the sound on the client laptop starts lagging. The same issue I've experienced on Windows earlier - I thought that it won't be the same on linux - is it because my hardware is slow or something can be adjusted? Any ideas?

---

### Post by sandyd on 2015-02-17
> **klyushin said:**
> So I've found what was the reason why I got the error:
I was reading an article and I've used a wrong prompt - I removed comment symbols # from file /etc/pulse/default.pa
in lines bold:
```
### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
**#load-module module-esound-protocol-tcp**
[B]#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish[/B]
```

when I put them up again I managed to launch pulseaudio

Now after I rebooted both laptops I can choose the recepient laptop in Playback tab - and the sound starts working on the second laptop.

[IMG]http://i.imgur.com/Ak5EYP6.png[/IMG]

the strange thing is that it can be done only after I first uncheck and then check again these options on both laptops - as if it helps to load up some features - if I don't do it - it will not work.
[IMG]http://i.imgur.com/WNkwNAw.png[/IMG]
----
[IMG]http://i.imgur.com/OvoWNI5.png[/IMG]

another strange feature is that when I start doing something (surf in a browser of the server laptop) the sound on the client laptop starts lagging. The same issue I've experienced on Windows earlier - I thought that it won't be the same on linux - is it because my hardware is slow or something can be adjusted? Any ideas?

What is the speed of your network/wifi?
Side note:
Even if you use something like AirPlay, it lags due to the fact that it takes time to transmit over the network.

It goes something like
Server Sound system -> Encode into format to send over network -> Send over Network -> Decode into format that is playable -> Client Sound system

As you can see, each step will add lag. 

Wifi adds extra lag depending on strength of wifi signal, however even if you use a full-ethernet network, you will notice lag. Open a Youtube video on the server and you will notice that a/v is desynced.

The amount of lag, however is subjective. Some people might think that a certain amount of lag is a lot, while some can't tolerate it.

I sure cant ;) (and ended up running speaker cables under baseboard to reach sound receiver)

---

### Post by klyushin on 2015-02-18
Maybe I've chosen the wrong definition - not a lag but it's like when the sound disappears for half a second repeatedly then  again it works fine, then again some activity on the server and again the client sound fails. It's like listening to online audio with a slow internet. But I don't understand why ... I suppose wi-fi connection should be able to cope with that amount of traffic ... Maybe if it happens because of a slow server laptop or a slow client hardware?
I've attached a hardware report of both laptops - could you identify if it's the hardware issue that causes the sound problems?

my max wi-fi speed is 54 mb/s - but if i start doing smth. (scrolling/surfing in a browser) the speed indicator may go down to 6 mb/s or so .... I'm not sure what this indicator shows, a free mb/s or the current speed ?

 [IMG]http://i.imgur.com/Oelez0P.png[/IMG]
----
[IMG]http://i.imgur.com/uylPNOz.png[/IMG]


```
klyushin@klyushin-Aspire-5720Z:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"DLink"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: F8:D1:11:25:B7:4A   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:1921   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


```

---

