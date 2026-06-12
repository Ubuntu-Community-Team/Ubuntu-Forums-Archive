---
title: "no sound in 14.04 hda-intel no codecs initialized sony vaio p"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by violajack on 2014-04-24
In 13.04 I was able to fix the lack of sound by following these instruction I found in a bug report via google:

> Recent Sony Vaios use snd_hda_intel for audio, which is generally good and supported by alsa >= 1.0.15, but the Ubuntu installer does not properly detect hardware and configure the driver. The well-known fix to this bug is to install the newest available alsa and add to the end of /etc/modprobe.d/alsa-base these 3 lines:

alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel model=vaio

This did not work in 13.10 and is now not working in 14.04. I'd really like to run 14.04 as 13.04 is no longer supported. I've been tinkering with Ubuntu since Warty, but I've grown accustomed to things just working, so my troubleshooting skills are not so strong anymore. 

[http://www.alsa-project.org/db/?f=b9c841b0b2c70986cb8857ea15a3404fa14a2563](http://www.alsa-project.org/db/?f=b9c841b0b2c70986cb8857ea15a3404fa14a2563)

From lspci: 00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 06)

During boot, before the graphical lubuntu loading screen comes up, I see an error along the lines of "no codecs initialized" 

I'm not having much luck via google as most fixes to the no codecs error are from 2011 or earlier and suggest compiling the latest alsa to fix things.

Any ideas?

---

