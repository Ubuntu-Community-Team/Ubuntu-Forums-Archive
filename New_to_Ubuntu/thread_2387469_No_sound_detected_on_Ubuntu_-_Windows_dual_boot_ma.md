---
title: "No sound detected on Ubuntu - Windows dual boot machine after a windows update"
date: 2018-03-19
forum: New to Ubuntu
---

### Post by felmoreno1726 on 2018-03-19
Hi, after the update I noticed the sound was stuck on headphones mode and no sound was coming out. I changed the output manually to speakers, but I got no sound coming out either. I looked at alsamixer, but there was nothing muted. I tried restoring the files from the sound troubleshoot procedure doing:

 killal pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*

I also tried doing:
alsactl restore which gives me an interesting input/output error:

alsactl: state_lock:125: file /var/lib/alsa/asound.state lock error: File exists
alsactl: load_state:1683: Cannot open /var/lib/alsa/asound.state for reading: File exists
Found hardware: "HDA-Intel" "Realtek ALC3266" "HDA:10ec0298,102806e4,00100103" "0x1028" "0x06e4"
Hardware is initialized using a generic method
/usr/share/alsa/init/default:98: value write error: Input/output error

I don't know how to proceed from here. Any suggestions?

EDIT1: Solved the problem by re-installing the Realtek driver from the Windows partition.

---

### Post by T.J. on 2018-03-20
Mark as solved please.

---

