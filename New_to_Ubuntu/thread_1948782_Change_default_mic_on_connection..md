---
title: "Change default mic on connection."
date: 2012-03-28
forum: New to Ubuntu
---

### Post by mn_voyageur on 2012-03-28
On my laptop, I have a camera and a mic.  However, I prefer to use my USB camera and mic.

How can I automatically change the default camera and mic from the built in devices to thee USB devices when I connect the camera?

Thanks,
MarkN

---

### Post by Rodney9 on 2012-03-28
To help you with changing the mike

sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

---

### Post by mn_voyageur on 2012-04-01
Rodney9,

How is PulseAudio Volume Control going to help?  Will it automatically select my external mic, when it is connected?

MarkN

---

