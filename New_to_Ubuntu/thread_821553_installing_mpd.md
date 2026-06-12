---
title: "installing mpd"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Inxsible on 2008-06-07
I tried to install mpd on my Debian Xfce. It installed ok, but gave me the following errors. What am I missing?```
inxsible@debian:~$ sudo apt-get install mpd
[sudo] password for inxsible: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libao2 libid3tag0 libmikmod2 libsamplerate0
Suggested packages:
  icecast2 mpd-client pulseaudio
The following NEW packages will be installed:
  libao2 libid3tag0 libmikmod2 libsamplerate0 mpd
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1617kB/1680kB of archives.
After this operation, 2490kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ftp.us.debian.org lenny/main libmikmod2 3.1.11-a-6 [124kB]
Get:2 http://ftp.us.debian.org lenny/main libsamplerate0 0.1.3-1 [1343kB]
Get:3 http://ftp.us.debian.org lenny/main mpd 0.13.1-3 [151kB]                 
Fetched 1617kB in 7s (216kB/s)                                                 
Selecting previously deselected package libao2.
(Reading database ... 77376 files and directories currently installed.)
Unpacking libao2 (from .../libao2_0.8.8-4_i386.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-10_i386.deb) ...
Selecting previously deselected package libmikmod2.
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6_i386.deb) ...
Selecting previously deselected package libsamplerate0.
Unpacking libsamplerate0 (from .../libsamplerate0_0.1.3-1_i386.deb) ...
Selecting previously deselected package mpd.
Unpacking mpd (from .../archives/mpd_0.13.1-3_i386.deb) ...
Processing triggers for man-db ...
Setting up libao2 (0.8.8-4) ...
Setting up libid3tag0 (0.15.1b-10) ...
Setting up libmikmod2 (3.1.11-a-6) ...
Setting up libsamplerate0 (0.1.3-1) ...
Setting up mpd (0.13.1-3) ...
Starting Music Player Daemon: mpd* creating /var/lib/mpd/tag_cache... 
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

E: client-conf-x11.c: XOpenDisplay() failed
.

```

---

### Post by quelx on 2008-06-07
Its trying to launch an X11 application and unable > Xlib: connection to ":0.0" refused by server

Try installing from Synaptic (so the X server is avaliable)

or do ```
xhost +
``` in the terminal before **apt-get**

---

