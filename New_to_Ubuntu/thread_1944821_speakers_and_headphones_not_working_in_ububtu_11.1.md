---
title: "speakers and headphones not working in ububtu 11.10"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by amitpokhrel on 2012-03-22
I am ausing ubuntu 11.10 64 bit. Every..thing was working fine but a wwk ago my speakers and headphone stopped working. I have a dual boot(windows and ubuntu) speakers are working fine in windows...
can anyone help???
thanks

---

### Post by Rodney9 on 2012-03-22
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

---

