---
title: "Yet another sound issue"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-10-26
Despite using ubuntu now for 3 years, I still find the whole area of managing sound obscure, so I need help again...
(ubuntu Hardy)
On my old Dell desktop, music & video with sound play fine in VLC but with Amarok and Rhythmbox, I get no sound.  I do get the drum beat at startup with Ubuntu splash screen for login, but I don't get the trill as the system finally loads up.
Amarok:  gives message alert:  Audio output is unavailable; the device is busy.

Sound card: intel 82801BA
alsamixer: "function snd_ctl open failed for default:  No such device"
Volume control: device is Intel82802BA-ICH2(Alsa mixer);master, headphone, PCM, line-in and CD are un-muted.

Sorry, I'm trying to give as much useful information as possible but I may not be listing the crucial bit b/c I'm confused! (I have had sound working in the past but not now; I've tried the Comprehensive Sound troubleshooting but my sound card is detected and I think the driver is present too)
Thanks for any guidance

---

### Post by Yashiro on 2008-10-27
Do pulseaudio -v in a terminal. What does it say?

---

### Post by kansasnoob on 2008-10-27
This tutorial solved all of my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by robert shearer on 2008-10-27
> **kansasnoob said:**
> This tutorial solved all of my pulse audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Same here though the Master volume applet in the panel did not work afterwards.(only on headphone)

Workaround was to right click on the volume applet and select 'Preferences', then hold down Ctrl and select Master and Headphone.
This associated both with the applet and restored the control.

(I am also using the Intel 82801BA-ICH2 chipset)

---

