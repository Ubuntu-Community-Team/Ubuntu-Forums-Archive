---
title: "[SOLVED] no VCD detected"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-24
Hi! I'm Melvin from India. I'd like to know how to mount a VCD in ubuntu 7.10. when i put in a VCD, nothing happens at all. Other CD's open as normal CD's including DVD's.

---

### Post by prshah on 2008-07-24
> **melrokz said:**
> I'd like to know how to mount a VCD in ubuntu 7.10. when i put in a VCD, nothing happens at all. Other CD's open as normal CD's including DVD's.

if you're sure the VCD is "healthy", then open a terminal (Applications-Accessories-Terminal) and give the command ```
mplayer vcd://1
``` If it doesn't work, post back errors shown.

if it works fine, for the future you can do this the GUI way: in mplayer (totem), right click the playback area, then select VCD, then select "Open disc".

if you get persistent errors, the disc may not actually be a VCD; does it have an /MPEGAV directory with various *.dat files in it?

---

