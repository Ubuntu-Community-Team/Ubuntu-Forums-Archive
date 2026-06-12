---
title: "I'm having trouble recording sound from an outside source"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by stefanm on 2008-05-11
I am a small business with only 3 PCs and a computer semi-literate. I convert audio files for people from old vinyl and cassette to digital (CD or mp3). A programmer friend recommended ubuntu which I installed on one PC over a month ago.

Basically its ok but it so far doesn't do the crucial thing I need - record a stereo file from an outside source (turntable or cassette deck). 

In Windows I used NCH Wavepad which is fantastic. But as far as I know they don't make a linux version of it. I can't get Audacity to work at all. It tells me there is an error opening the sound devide and to check the device settings and project sample rate. I can use a PC and know where the main obvious bits are but frankly I don't know anything about how they work. I haven't a clue what that message means or what to do about it. 

There are lots of other problems; youtube won't show videos, can't get the monitor resolution to make my new 20in monitor to work properly to name just a few. 

When I look at the forums I am terrified and have no idea what the answers mean let alone the questions. I can't go into terminal and do anything there, I don't know what any of the technical terms I have come across mean like deb, wine, jack, edgy, gdm, grub, ext14, compiz, snap-to-pop, gui-tool and so on. This all means nothing to me. 

I have struggled on but have come to the conclusion that ubuntu is for the computer "cognicenti" and not for computer semi-literates like me. I really like the philosophy behind this kind of shareware but amd not up to it and don't have the time to learn. Sadly its back to Microsoft for me.

---

### Post by R_T_H on 2008-05-13
I'm pretty sure **krec** may help...

---

### Post by aysiu on 2008-05-13
Since you already posted another, similar rant that I've moved to Testimonials, I'm going to give you the benefit of the doubt and retitle your thread so you can get some help. If you really are going back to Windows, though, let us know, and I can close this support thread.

---

### Post by asaz989 on 2008-05-13
......and now for some actual answers to the questions asked. Or at least asking questions back.

First thing (based on your description of the error message) is how are you hooking up the analog devices to your computer? It could be a hardware connection problem (which I doubt, since it sounds like you've already been doing this with the same computers on Windows for a while) or just that one component or another on the trail to Audacity isn't recognizing the device.

To see what device Audacity is looking at, go in the menus to Edit->Preferences, and look under the "Audio I/O" tab at what the recording device is.

To test if your input device is working at all (under Ubuntu 8.04), install the application "PulseAudio Device Chooser." Run it (from the Applications menu), and it'll give you a tray icon; click it, choose "Volume Meter (Recording)", send some loud input from your analog device, and see if it registers on the volume meter.

Hope one of those things reveals something.

---

