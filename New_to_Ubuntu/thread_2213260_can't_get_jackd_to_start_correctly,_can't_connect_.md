---
title: "can't get jackd to start correctly, can't connect to server socket"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by kimberly2 on 2014-03-25
hi all, I'm trying to get jackd to work. i have jackd version 1.9.10 and  qjackctl version 0.3.9 from the repositories.

when i start qjackctl (the program itself, not hitting the start button within the program), in the messages window i get:

```
01:40:23.980 Patchbay deactivated.
01:40:23.987 Statistics reset.
01:40:24.025 ALSA connection change.
01:40:24.041 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
01:40:24.057 ALSA connection graph change.


```

some info on my sound cards:

```
$ cat /proc/asound/cards 
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0244000 irq 45
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0240000 irq 16
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: Generic_1 [HD-Audio Generic], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

i'm not using any special sound cards or anything, just the regular one(s) that came with my comp. i made myself a member of the audio group (though i heard that doesn't matter anyway). 

someone also said to try jackd from the command line:

 ```
$ jackd -d alsa
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server

```

when i googled first i found that there are a million threads about this but they aren't helpful at all, they all seem to do unexplained weird workarounds.

can anyone please help me?

thank you!!

---

### Post by kimberly2 on 2014-03-26
hi again, i think i've briefly solved the problem, or at least part of it. in my first post i only had the not-very-illuminating arecord -l, but aplay tells me more:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

so my default in the qjackctl settings would've been than HDMI port. changing it from "default" to hw:1 seems to make it so hitting start doesn't give me nasty errors, and appears to work:

```
03:23:34.320 D-BUS: JACK server is starting...
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
03:23:34.363 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Wed Mar 26 03:23:34 2014: Starting jack server...
Wed Mar 26 03:23:34 2014: JACK server starting in realtime mode with priority 10
Wed Mar 26 03:23:34 2014: Acquired audio card Audio1
Wed Mar 26 03:23:34 2014: creating alsa driver ... hw:1|hw:1|64|2|44100|0|0|nomon|swmeter|-|32bit
Wed Mar 26 03:23:34 2014: configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
Wed Mar 26 03:23:34 2014: ALSA: final selected sample format for capture: 32bit integer little-endian
Wed Mar 26 03:23:34 2014: ALSA: use 2 periods for capture
Wed Mar 26 03:23:34 2014: ALSA: final selected sample format for playback: 32bit integer little-endian
Wed Mar 26 03:23:34 2014: ALSA: use 2 periods for playback
Wed Mar 26 03:23:34 2014: graph reorder: new port 'system:capture_1'
Wed Mar 26 03:23:34 2014: New client 'system' with PID 0
Wed Mar 26 03:23:34 2014: graph reorder: new port 'system:capture_2'
Wed Mar 26 03:23:34 2014: graph reorder: new port 'system:playback_1'
Wed Mar 26 03:23:34 2014: graph reorder: new port 'system:playback_2'
Wed Mar 26 03:23:35 2014: Saving settings to "/home/declan/.config/jack/conf.xml" ...
03:23:36.597 JACK connection change.
03:23:36.600 Server configuration saved to "/home/declan/.jackdrc".
03:23:36.602 Statistics reset.
03:23:36.609 Client activated.
03:23:36.618 XRUN callback (1).
03:23:36.620 JACK connection graph change.
Wed Mar 26 03:23:36 2014: New client 'qjackctl' with PID 9003
03:23:38.619 XRUN callback (425 skipped).
03:23:40.625 XRUN callback (423 skipped).
03:23:42.631 XRUN callback (422 skipped).
03:23:44.251 Client deactivated.
03:23:44.320 D-BUS: JACK server is stopping...
03:23:44.342 D-BUS: JACK server was stopped (org.jackaudio.service aka jackdbus).
Wed Mar 26 03:23:44 2014: Client 'qjackctl' with PID 9003 is out
Wed Mar 26 03:23:44 2014: Stopping jack server...
Wed Mar 26 03:23:44 2014: Client 'system' with PID 0 is out
Wed Mar 26 03:23:44 2014: Released audio card Audio1
```

however, i still get this error before hitting start or anything:

```
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

what is that? should i worry?

i've killed pulseaudio and disabled its autospawn just to be sure because i read that could be a problem, but it hasn't changed anything.

---

