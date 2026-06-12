---
title: "[SOLVED] No sound from front speakers (surround mode)"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by xwhisper on 2008-07-09
Hi!
I set up my 5.1 surround speakers to work using this guide:
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)
It always worked for me until now. My front speakers doesn't play any sound (but center and rear work). I checked Volume Control, alsamixer and PulseAudio - everything is set to max. I only miss *Front* option in Volume Control, but it never have been a problem until today.
Maybe some of these programs is blocking/muting front speakers:
gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3 libdvdcss2 ffmpeg w32codecs x264 dvdauthor quicktime-utils libmikmod2 lame lame-extras flac alsa-base alsa-oss alsa-tools alsa-tools-gui alsa-utils libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

Any ideas?

---

