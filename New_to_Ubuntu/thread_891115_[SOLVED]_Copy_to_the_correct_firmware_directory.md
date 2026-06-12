---
title: "[SOLVED] Copy to the correct firmware directory?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by yojimba on 2008-08-15
I've downloaded a firmware file that needs to be copied to the correct /lib/firmware directory . . . this is supposed to vary from distribution to distribution. 

How do I find the correct directory for my firmware?

---

### Post by yojimba on 2008-08-15
I have simply installed it to lib/firmware and that seems to be the right place.

---

### Post by nicedude on 2008-08-15
Firmware for what? I don't understand your question. Please list what this is for and what you need to do. Firmware is usually BIOS code or other code for chips that must be programmed.

---

### Post by yojimba on 2008-08-15
> **nicedude said:**
> Firmware for what? I don't understand your question. Please list what this is for and what you need to do. Firmware is usually BIOS code or other code for chips that must be programmed.

The correct location to place the following firmware for a tuner card:

This card requires a firmware file (dvb-fe-nxt2004.fw1) for the demodulator, which can be obtained using the get_dvb_firmware perl script included in the kernel sources:

# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware nxt2004

Once the download is complete, place a copy of the firmware file in your /lib/firmware directory. (This directory may differ with some distros; consult your distro's documentation for the appropriate location).

---

### Post by nicedude on 2008-08-15
OK sounds like you already solved this yourself and should mark it as solved.

---

### Post by yojimba on 2008-08-15
No . . . I'm not sure I have because it is not loading correctly . . .

I either do not have the modprobe hacked correctly or the firmware is not in the right location . . .

However, if you add

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=90

to modprobe.conf, and have the necessary nxt2004 firmware properly in place, then you will be able to force the card to be recognized and configured as if it were the KWorld ATSC 110.

---

### Post by unutbu on 2008-08-15
Have you tried placing dvb-fe-nxt2004.fw1 in /lib/firmware/$(uname -r) ?

---

### Post by yojimba on 2008-08-16
there are only two folders in usr/lib/

2.6.24-16-generic and 2.6.24-19-generic

i placed a copy of the firmware in both but to no effect . . .

---

### Post by yojimba on 2008-08-16
from what I have researched the correct directory should be in the current version of the kernel in the lib/firmware directory:

/lib/firmware/[kernal version]

that is where i have placed it so i will assume for now my problem with the firmware loading is something else for now.

---

