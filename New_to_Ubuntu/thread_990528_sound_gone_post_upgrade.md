---
title: "sound gone post upgrade"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by malagigi on 2008-11-22
I've used Ubuntu 8.04 for some time, and I found the experience great.  After reading some good things I upgraded to 8.10, but a few problems have cropped up that I simply can't resolve.  The biggest one is that I can't get any sound at all in Ubuntu.  I've tried a variety of fixes, but nothing seems to work.  The best clue I can track down for what is wrong comes when I type alsamixer in the terminal:```

~$ alsamixer
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


alsamixer: function snd_ctl_open failed for default: Connection refused

```

Any thoughts what I can do about this?  It worked in Heron, I was a bit surprised when a couple of things stopped working in Ibex.

---

### Post by beno1990 on 2008-11-22
type "pulseaudio" in the terminal and report any error messages it gives you on trying to load.

I think this might be the same error I had earlier, but was easily fixable when I diagnosed it. :)

---

### Post by chazn85 on 2008-11-22
i got the exact same thing when i upgraded from 7.10 to 8.04, i instllaed all restricted sound modules (i forget the exact ones) and changed my sound to pulse audio may help you out

---

### Post by malagigi on 2008-11-22
Pulseaudio was not installed, as I recall, I read a forum post that said to remove it.  After apt-get'ing pulseaudio, I typed pulse audio and got:
```
~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

```

---

### Post by chazn85 on 2008-11-22
have you changed all the selections in prefs>sounds to pulse?  cant say i have any experience with ibex,

---

### Post by malagigi on 2008-11-22
They were on autodetect, but I have now changed them over to PulseAudio Sound Server.  No change in status.

---

### Post by beno1990 on 2008-11-22
Try

```
sudo gedit /etc/pulse/default.pa
```

And search for the following line:

```
load-module module-alsa-sink
```

If you find it, comment it out by adding a # to the start of the line, and then try starting pulseaudio again with this command:

```
sudo pulseaudio
```

Let me know if this works. :)

---

### Post by malagigi on 2008-11-22
The line already appeared to be commented out.  I added another # for good measure.  I then got:
```
~$ sudo pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: This program is not intended to be run as root (unless --system is specified).
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

```

---

