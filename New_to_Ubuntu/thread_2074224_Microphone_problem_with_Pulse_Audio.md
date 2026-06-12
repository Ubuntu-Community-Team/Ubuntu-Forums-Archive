---
title: "Microphone problem with Pulse Audio"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by hans12345 on 2012-10-21
Some time ago I could not get the microphone working. So I did some looking around in these forums and installed Pulse Audio.

I found a master control screen (I'm nearly sure in Pulse Audio) that had about a dozen vertical bars controlling all aspects of my audio. At lot were disabled, so I enabled everything. It worked, except that the microphone was always on. 

I suffered this for some months but my wife doesn't like it, so now I want to fix it so that the microphone only works when I have a use for it, which is normally for Skype.

But I cannot find the master control screen! How do I find it?

Your help appreciated.

---

### Post by Lisiano on 2012-10-21
I am guessing this master control screen you are referring to is alsamixer.
Open a terminal (Ctrl+Alt+T) then type in this
```
alsamixer
```
Use the arrow keys to modify the volume and select which output/input you want to modify. To switch between devices, press F6. To exit, press Escape.

Also, what do you mean by the microphone always being on? You mean it's constantly looped back?

---

### Post by NikTh on 2012-10-21
Hi , 

as an addition to [Lisiano]("http://ubuntuforums.org/member.php?u=1108763")'s advice 

do not forget to Unmute any channel related to "Mic" or "Internal Mic" . You can Unmute by pressing  [M] key in your keyboard. Muted channels appeared with this symbol [MM].

Thanks

---

### Post by hans12345 on 2012-10-21
> **Lisiano said:**
> I am guessing this master control screen you are referring to is alsamixer.
Open a terminal (Ctrl+Alt+T) then type in this
```
alsamixer
```
Use the arrow keys to modify the volume and select which output/input you want to modify. To switch between devices, press F6. To exit, press Escape.

Also, what do you mean by the microphone always being on? You mean it's constantly looped back?

Thanks Lisiano.

It does look like I meant Alsamixer. But it's strange that it was not installed and I cannot remember uninstalling anything. I shall play around with the controls to see what happens, but I'm a complete noob with audio. Is there a guide you can recommend?

As for you last question, the micro is on all the time. So when I type, or even move the mouse, the micro picks up the vibration and I hear it on the speakers.

---

### Post by hans12345 on 2012-10-21
> **NikTh said:**
> Hi , 

as an addition to [Lisiano]("http://ubuntuforums.org/member.php?u=1108763")'s advice 

do not forget to Unmute any channel related to "Mic" or "Internal Mic" . You can Unmute by pressing  [M] key in your keyboard. Muted channels appeared with this symbol [MM].

Thanks

Thanks NikTh

I tried the mute command in the Pulse Audio box. I muted both front and back micro inputs, but no change, and I still get the active micro! But of course, this could be due to me installing the Alsamixer, which I did 30 mins ago! See previous post.

---

### Post by hans12345 on 2012-10-21
> **hans12345 said:**
> Thanks NikTh

I tried the mute command in the Pulse Audio box. I muted both front and back micro inputs, but no change, and I still get the active micro! But of course, this could be due to me installing the Alsamixer, which I did 30 mins ago! See previous post.

I just tried the obvious next step and uninstalled the Alsamixer, but still the muting of all the inputs (front, rear, line) does not stop the micro being active.

Any ideas?

---

### Post by Lisiano on 2012-10-21
So it is constantly looping back. Could you please do the following, open a Terminal (Ctrl+Alt+T) and type in
```
pactl list > ~/pactl.list
gedit ~/pactl.list
```
You will see gedit open up, please copy paste everything in that file (Ctrl+A then Ctrl+C) here.
Also please paste here the contents of the following files
```
gedit /etc/pulse/*
```
Please use [noparse]```
these tags
```[/noparse] while pasting the contents here.

---

### Post by hans12345 on 2012-10-22
> **Lisiano said:**
> So it is constantly looping back. Could you please do the following, open a Terminal (Ctrl+Alt+T) and type in
```
pactl list > ~/pactl.list
gedit ~/pactl.list
```
You will see gedit open up, please copy paste everything in that file (Ctrl+A then Ctrl+C) here.
Also please paste here the contents of the following files
```
gedit /etc/pulse/*
```
Please use [noparse]```
these tags
```[/noparse] while pasting the contents here.

First output!

[noparse]```

Module #0
	Name: module-device-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute state of devices"
		module.version = "1.1"

Module #1
	Name: module-stream-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the volume/mute/device state of streams"
		module.version = "1.1"

Module #2
	Name: module-card-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore profile of cards"
		module.version = "1.1"

Module #3
	Name: module-augment-properties
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Augment the property sets of streams with additional static information"
		module.version = "1.1"

Module #4
	Name: module-alsa-card
	Argument: device_id="0" name="pci-0000_00_05.0" card_name="alsa_card.pci-0000_00_05.0" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"
	Usage counter: 0
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "1.1"

Module #5
	Name: module-alsa-card
	Argument: device_id="1" name="pci-0000_02_00.1" card_name="alsa_card.pci-0000_02_00.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"
	Usage counter: 0
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ALSA Card"
		module.version = "1.1"

Module #6
	Name: module-udev-detect
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Detect available audio hardware and load matching drivers"
		module.version = "1.1"

Module #7
	Name: module-bluetooth-discover
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Joao Paulo Rechi Vita"
		module.description = "Detect available bluetooth audio devices and load bluetooth audio drivers"
		module.version = "1.1"

Module #8
	Name: module-esound-protocol-unix
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "ESOUND protocol (UNIX sockets)"
		module.version = "1.1"

Module #9
	Name: module-native-protocol-unix
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Native protocol (UNIX sockets)"
		module.version = "1.1"

Module #10
	Name: module-zeroconf-discover
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "mDNS/DNS-SD Service Discovery"
		module.version = "1.1"

Module #11
	Name: module-gconf
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "GConf Adapter"
		module.version = "1.1"

Module #12
	Name: module-default-device-restore
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically restore the default sink and source"
		module.version = "1.1"

Module #13
	Name: module-rescue-streams
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
		module.version = "1.1"

Module #14
	Name: module-always-sink
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Colin Guthrie"
		module.description = "Always keeps at least one sink loaded even if it's a null one"
		module.version = "1.1"

Module #15
	Name: module-intended-roles
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Automatically set device of streams based of intended roles of devices"
		module.version = "1.1"

Module #16
	Name: module-suspend-on-idle
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "When a sink/source is idle for too long, suspend it"
		module.version = "1.1"

Module #17
	Name: module-console-kit
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Create a client for each ConsoleKit session of this user"
		module.version = "1.1"

Module #18
	Name: module-position-event-sounds
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
		module.version = "1.1"

Module #19
	Name: module-filter-heuristics
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Colin Guthrie"
		module.description = "Detect when various filters are desirable"
		module.version = "1.1"

Module #20
	Name: module-filter-apply
	Argument: 
	Usage counter: n/a
	Properties:
		module.author = "Colin Guthrie"
		module.description = "Load filter sinks automatically when needed"
		module.version = "1.1"

Module #21
	Name: module-switch-on-port-available
	Argument: 
	Usage counter: n/a
	Properties:
		

Module #22
	Name: module-x11-publish
	Argument: display=:0
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 credential publisher"
		module.version = "1.1"

Module #23
	Name: module-x11-bell
	Argument: display=:0 sample=bell.ogg
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 bell interceptor"
		module.version = "1.1"

Module #24
	Name: module-x11-cork-request
	Argument: display=:0
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "Synthesize X11 media key events when cork/uncork is requested"
		module.version = "1.1"

Module #25
	Name: module-x11-xsmp
	Argument: display=:0 session_manager=local/OldAtlas:@/tmp/.ICE-unix/1281,unix/OldAtlas:/tmp/.ICE-unix/1281
	Usage counter: n/a
	Properties:
		module.author = "Lennart Poettering"
		module.description = "X11 session management"
		module.version = "1.1"

Sink #0
	State: SUSPENDED
	Name: alsa_output.pci-0000_00_05.0.analog-stereo
	Description: Built-in Audio Analogue Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 4
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor Source: alsa_output.pci-0000_00_05.0.analog-stereo.monitor
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "AD198x Analog"
		alsa.id = "AD198x Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xddff8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:05.0"
		sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "MCP61 High Definition Audio"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analogue Stereo"
		device.description = "Built-in Audio Analogue Stereo"
		alsa.mixer_name = "Analog Devices AD1988"
		alsa.components = "HDA:11d41988,10438241,00100400"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Ports:
		analog-output: Analogue Output (priority: 9900)
		analog-output-headphones: Headphones (priority: 9000)
	Active Port: analog-output
	Formats:
		pcm

Sink #1
	State: SUSPENDED
	Name: alsa_output.pci-0000_02_00.1.hdmi-stereo
	Description: Cedar HDMI Audio [Radeon HD 5400/6300 Series] Digital Stereo (HDMI)
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor Source: alsa_output.pci-0000_02_00.1.hdmi-stereo.monitor
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
	Properties:
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
		alsa.card = "1"
		alsa.card_name = "HD-Audio Generic"
		alsa.long_card_name = "HD-Audio Generic at 0xdffbc000 irq 44"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:02:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
		device.product.name = "Cedar HDMI Audio [Radeon HD 5400/6300 Series]"
		device.string = "hdmi:1"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "hdmi-stereo"
		device.profile.description = "Digital Stereo (HDMI)"
		device.description = "Cedar HDMI Audio [Radeon HD 5400/6300 Series] Digital Stereo (HDMI)"
		alsa.mixer_name = "ATI R6xx HDMI"
		alsa.components = "HDA:1002aa01,00aa0100,00100200"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Ports:
		hdmi-output-0: HDMI / DisplayPort (priority: 5900, not available)
	Active Port: hdmi-output-0
	Formats:
		pcm

Source #0
	State: SUSPENDED
	Name: alsa_output.pci-0000_00_05.0.analog-stereo.monitor
	Description: Monitor of Built-in Audio Analogue Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 4
	Mute: yes
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor of Sink: alsa_output.pci-0000_00_05.0.analog-stereo
	Latency: 0 usec, configured 0 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Monitor of Built-in Audio Analogue Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xddff8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:05.0"
		sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "MCP61 High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Formats:
		pcm

Source #1
	State: SUSPENDED
	Name: alsa_input.pci-0000_00_05.0.analog-stereo
	Description: Built-in Audio Analogue Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 4
	Mute: yes
	Volume: 0:   0% 1:   0%
	        0: -inf dB 1: -inf dB
	        balance 0.00
	Base Volume:  13%
	             -52.50 dB
	Monitor of Sink: n/a
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "AD198x Analog"
		alsa.id = "AD198x Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xddff8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:05.0"
		sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "MCP61 High Definition Audio"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analogue Stereo"
		device.description = "Built-in Audio Analogue Stereo"
		alsa.mixer_name = "Analog Devices AD1988"
		alsa.components = "HDA:11d41988,10438241,00100400"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Ports:
		analog-input-microphone-front: Front Microphone (priority: 8500)
		analog-input-microphone-rear: Rear Microphone (priority: 8200)
		analog-input-linein: Line In (priority: 8100)
	Active Port: analog-input-microphone-front
	Formats:
		pcm

Source #2
	State: SUSPENDED
	Name: alsa_output.pci-0000_02_00.1.hdmi-stereo.monitor
	Description: Monitor of Cedar HDMI Audio [Radeon HD 5400/6300 Series] Digital Stereo (HDMI)
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 5
	Mute: no
	Volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor of Sink: alsa_output.pci-0000_02_00.1.hdmi-stereo
	Latency: 0 usec, configured 0 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Monitor of Cedar HDMI Audio [Radeon HD 5400/6300 Series] Digital Stereo (HDMI)"
		device.class = "monitor"
		alsa.card = "1"
		alsa.card_name = "HD-Audio Generic"
		alsa.long_card_name = "HD-Audio Generic at 0xdffbc000 irq 44"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:02:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
		device.product.name = "Cedar HDMI Audio [Radeon HD 5400/6300 Series]"
		device.string = "1"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Formats:
		pcm

Client #0
	Driver: module-console-kit.c
	Owner Module: 17
	Properties:
		application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
		console-kit.session = "/org/freedesktop/ConsoleKit/Session1"

Client #1
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "GNOME Volume Control Media Keys"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.id = "org.gnome.VolumeControl"
		application.icon_name = "multimedia-volume-control"
		application.version = "3.4.2"
		application.process.id = "1353"
		application.process.user = "wayyie"
		application.process.host = "OldAtlas"
		application.process.binary = "gnome-settings-daemon"
		application.language = "en_GB.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "24822a32c3b9dc83e069558400000007"
		application.process.session_id = "24822a32c3b9dc83e069558400000007-1350714391.505133-329575736"

Client #2
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "Indicator Sound"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.id = "com.canonical.indicator.sound"
		application.icon_name = "multimedia-volume-control"
		application.version = "0.8.5.0"
		application.process.id = "1613"
		application.process.user = "wayyie"
		application.process.host = "OldAtlas"
		application.process.binary = "indicator-sound-service"
		application.language = "en_GB.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "24822a32c3b9dc83e069558400000007"
		application.process.session_id = "24822a32c3b9dc83e069558400000007-1350714391.505133-329575736"

Client #7
	Driver: module-x11-xsmp.c
	Owner Module: 25
	Properties:
		application.name = "XSMP Session on gnome-session as 1059522b3dbd12e9b7135071440140398600000012810039"
		xsmp.vendor = "gnome-session"
		xsmp.client.id = "1059522b3dbd12e9b7135071440140398600000012810039"

Client #21
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "Skype"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.process.id = "6267"
		application.process.user = "wayyie"
		application.process.host = "OldAtlas"
		application.process.binary = "skype"
		window.x11.display = ":0"
		application.language = "en_GB.UTF-8"
		application.process.machine_id = "24822a32c3b9dc83e069558400000007"
		application.process.session_id = "24822a32c3b9dc83e069558400000007-1350714391.505133-329575736"
		application.icon_name = "skype.png"

Client #22
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "Firefox"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.icon_name = "firefox"
		application.version = "16.0.1"
		application.process.id = "6341"
		application.process.user = "wayyie"
		application.process.host = "OldAtlas"
		application.process.binary = "firefox"
		window.x11.display = ":0"
		application.language = "en_GB.UTF-8"
		application.process.machine_id = "24822a32c3b9dc83e069558400000007"
		application.process.session_id = "24822a32c3b9dc83e069558400000007-1350714391.505133-329575736"

Client #23
	Driver: protocol-native.c
	Owner Module: 9
	Properties:
		application.name = "pactl"
		native-protocol.peer = "UNIX socket client"
		native-protocol.version = "26"
		application.process.id = "8079"
		application.process.user = "wayyie"
		application.process.host = "OldAtlas"
		application.process.binary = "pactl"
		application.language = "en_GB.UTF-8"
		window.x11.display = ":0"
		application.process.machine_id = "24822a32c3b9dc83e069558400000007"
		application.process.session_id = "24822a32c3b9dc83e069558400000007-1350714391.505133-329575736"

Card #0
	Name: alsa_card.pci-0000_00_05.0
	Driver: module-alsa-card.c
	Owner Module: 4
	Properties:
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xddff8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:05.0"
		sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.name = "MCP61 High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		device.description = "Built-in Audio"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profiles:
		output:analog-stereo: Analogue Stereo Output (sinks: 1, sources: 0, priority. 6000)
		output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
		output:analog-surround-40: Analogue Surround 4.0 Output (sinks: 1, sources: 0, priority. 700)
		output:analog-surround-40+input:analog-stereo: Analogue Surround 4.0 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 760)
		output:analog-surround-41: Analogue Surround 4.1 Output (sinks: 1, sources: 0, priority. 800)
		output:analog-surround-41+input:analog-stereo: Analogue Surround 4.1 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 860)
		output:analog-surround-50: Analogue Surround 5.0 Output (sinks: 1, sources: 0, priority. 700)
		output:analog-surround-50+input:analog-stereo: Analogue Surround 5.0 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 760)
		output:analog-surround-51: Analogue Surround 5.1 Output (sinks: 1, sources: 0, priority. 800)
		output:analog-surround-51+input:analog-stereo: Analogue Surround 5.1 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 860)
		output:iec958-stereo: Digital Stereo (IEC958) Output (sinks: 1, sources: 0, priority. 5500)
		output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 5560)
		input:analog-stereo: Analogue Stereo Input (sinks: 0, sources: 1, priority. 60)
		off: Off (sinks: 0, sources: 0, priority. 0)
	Active Profile: output:analog-stereo+input:analog-stereo
	Ports:
		analog-output: Analogue Output (priority 9900)
			Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-40, output:analog-surround-40+input:analog-stereo, output:analog-surround-41, output:analog-surround-41+input:analog-stereo, output:analog-surround-50, output:analog-surround-50+input:analog-stereo, output:analog-surround-51, output:analog-surround-51+input:analog-stereo
		analog-output-headphones: Headphones (priority 9000)
			Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo
		analog-input-microphone-front: Front Microphone (priority 8500)
			Part of profile(s): output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
		analog-input-microphone-rear: Rear Microphone (priority 8200)
			Part of profile(s): output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
		analog-input-linein: Line In (priority 8100)
			Part of profile(s): output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:iec958-stereo+input:analog-stereo, input:analog-stereo
		iec958-stereo-output: Digital Output (S/PDIF) (priority 0)
			Part of profile(s): output:iec958-stereo, output:iec958-stereo+input:analog-stereo

Card #1
	Name: alsa_card.pci-0000_02_00.1
	Driver: module-alsa-card.c
	Owner Module: 5
	Properties:
		alsa.card = "1"
		alsa.card_name = "HD-Audio Generic"
		alsa.long_card_name = "HD-Audio Generic at 0xdffbc000 irq 44"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:02:00.1"
		sysfs.path = "/devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
		device.product.name = "Cedar HDMI Audio [Radeon HD 5400/6300 Series]"
		device.string = "1"
		device.description = "Cedar HDMI Audio [Radeon HD 5400/6300 Series]"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Profiles:
		output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5400)
		off: Off (sinks: 0, sources: 0, priority. 0)
	Active Profile: output:hdmi-stereo
	Ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900)
			Part of profile(s): output:hdmi-stereo


```[/noparse]

I hope I got the tags right.

---

### Post by hans12345 on 2012-10-22
> **Lisiano said:**
> So it is constantly looping back. Could you please do the following, open a Terminal (Ctrl+Alt+T) and type in
```
pactl list > ~/pactl.list
gedit ~/pactl.list
```
You will see gedit open up, please copy paste everything in that file (Ctrl+A then Ctrl+C) here.
Also please paste here the contents of the following files
```
gedit /etc/pulse/*
```
Please use [noparse]```
these tags
```[/noparse] while pasting the contents here.

2nd outputs:

```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for PulseAudio clients. See pulse-client.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; default-sink =
; default-source =
; default-server =
; default-dbus-server =

; autospawn = yes
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; auto-connect-localhost = no
; auto-connect-display = no

```

```

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0
```


```

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect
.fail
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
.ifexists module-console-kit.so
load-module module-console-kit
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

### Load DBus protocol
#.ifexists module-dbus-protocol.so
#load-module module-dbus-protocol
#.endif

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

load-module module-switch-on-port-available

### Make some devices default
#set-default-sink output
#set-default-source input

```

```

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started in system
# mode.

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Automatically restore the volume of streams and devices
load-module module-stream-restore
load-module module-device-restore

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

.ifexists module-dbus-protocol.so
### If you want to allow TCP connections, set access to "remote" or "local,remote".
load-module module-dbus-protocol access=local
.endif

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Enable positioned event sounds
load-module module-position-event-sounds

```

---

### Post by Lisiano on 2012-10-24
Sadly, I'm not seeing anything which could show what is looping the sound back. There doesn't appear (To me) that there is a loopback module loaded or that any program is trying to loop sound.

EDIT: You used the tags correctly on your 2nd try. On the 1st one, it seems you quoted my post and copied the tags with the [noparse][noparse][/noparse][/noparse] tags, they disable tag parsing so I can use tags in text to "demo" their usage.

---

### Post by hans12345 on 2012-10-27
I have not forgotten your help.

It's just that I had a dead PC with a failure on the system disk, so I have been distracted!

---

