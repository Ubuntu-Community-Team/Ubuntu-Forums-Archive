---
title: "no audio"
date: 2014-09-03
forum: New to Ubuntu
---

### Post by mycal2 on 2014-09-03
hiyer just installed lubuntu latest version and i cant get any sound ,,any help appreicated:mad:

---

### Post by christopher9 on 2014-09-03
Use the Software Center to install PulseAudio volume control>configure to your system

---

### Post by Dennis N on 2014-09-03
The user tool that controls your audio (besides the panel volume control) in Lubuntu is called alsamixer. You need to check that none of the important settings is muted or at a very low volume. 

To check: In your terminal, type:

**[FONT=Courier New]alsamixer[/FONT]** 

If **Master** or **PCM** is at a low level, use the left and right arrow keys to select it along the bottom, then the up arrow key to increase it. Esc to exit.

---

