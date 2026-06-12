---
title: "ion Pure LP?"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by Toni_Vines on 2014-12-05
Hi, I've been given a ION Pure LP USB record turntable. It says on the box that it's compatible with Windows and MAC. I've plugged it in and connected the USB cable but Ubuntu is not seeing it. I'm running 12.04 LTS.
Does anyone have any ideas please?
Thanking you all.
Toni.

---

### Post by ajgreeny on 2014-12-05
What does command **lsusb** show you, if anything?
Also it is worth plugging it in and immediately running **dmesg | tail -n 20** to show thefinal 20 lines of dmesg, which may give some clues about the hardware.

---

### Post by mcduck on 2014-12-06
How have you tried using it? It's obviously not going to pop up as an icon on your desktop or anything like that, and the software that comes with the device is for Windows and Mac only. However I'd expect it to appear as USB sound card, in which case you should be able to open any decent sound recording software (Audacity, for example), set the recording input to the turntable's soundcard and start recording...

Of course if none of the sound recording programs are able to see it, then checkign the output from cmmands ajgreeny mentioned would be a good start.

---

### Post by Rob Sayer on 2014-12-06
In addition to trying the commands in post #2, try looking at sound in system settings after you plug it in.  See if it's there under recording devices.  I haven't used the unity DE for some time so I don't remember exactly where it'd be.

---

### Post by ajgreeny on 2014-12-06
You get to Sound Settings (ie, pulseaudio-volume-control) from clicking the volume icon in the taskbar, just like other DE versions, as far as I'm aware.

---

