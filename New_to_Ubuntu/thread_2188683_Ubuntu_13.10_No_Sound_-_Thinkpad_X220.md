---
title: "Ubuntu 13.10 No Sound - Thinkpad X220"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by EuropaCar on 2013-11-18
I have recently upgraded to 13.10. Sound had worked perfectly in 13.04. Now, in 13.10, no applications can play sound, I don't have a volume indicator, the physical volume buttons don't do anything, and when I go to sound settings, there are no outputs listed. I have already tried sudo alsa reload, to no avail. Anyone have advice?

---

### Post by EuropaCar on 2013-11-19
Any ideas?

---

### Post by EuropaCar on 2013-12-26
Still experiencing this problem.. Cannot find a solution online.
Here is the output to: "sudo dpkg -l | grep -e alsa -e pulseaudio"

```
ii  alsa-base                                   1.0.25+dfsg-0ubuntu4                     all          ALSA driver configuration files
ii  alsa-utils                                  1.0.27.1-1ubuntu1                        i386         Utilities for configuring and using ALSA
ii  bluez-alsa:i386                             4.101-0ubuntu8b1                         i386         Bluetooth ALSA support
ii  gstreamer0.10-alsa:i386                     0.10.36-1.1ubuntu1                       i386         GStreamer plugin for ALSA
ii  gstreamer0.10-pulseaudio:i386               0.10.31-3+nmu1ubuntu3                    i386         GStreamer plugin for PulseAudio
ii  gstreamer1.0-alsa:i386                      1.2.0-1ubuntu1                           i386         GStreamer plugin for ALSA
ii  gstreamer1.0-pulseaudio:i386                1.2.0-1ubuntu1                           i386         GStreamer plugin for PulseAudio
rc  libsdl1.2debian-pulseaudio                  1.2.14-6.1ubuntu4                        i386         Simple DirectMedia Layer (with X11 and PulseAudio options)
ii  pulseaudio                                  1:4.0-0ubuntu6                           i386         PulseAudio sound server
rc  pulseaudio-equalizer                        2.7.0.2-2~webupd8~oneiric3               all          PulseAudio Equalizer - LADSPA plugin graphical user interface
ii  pulseaudio-module-x11                       1:4.0-0ubuntu6                           i386         X11 module for PulseAudio sound server
ii  pulseaudio-utils                            1:4.0-0ubuntu6                           i386         Command line tools for the PulseAudio sound server
```

Any ideas?
thanks

---

