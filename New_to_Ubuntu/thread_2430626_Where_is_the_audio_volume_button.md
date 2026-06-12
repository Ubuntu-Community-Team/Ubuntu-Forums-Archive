---
title: "Where is the audio volume button ?"
date: 2019-11-05
forum: New to Ubuntu
---

### Post by janvi2 on 2019-11-05
installed Ubuntu / Gnome using a Nvidia graphics with display port monitor. Basic audio is working but volume is very low. 
The monitors speakers go over DP cable. There is not response from the monitors on screen menue volume setup. 
There is response from all applications volume setup but 100% are hardly audible. 
Anywhere another mixer with summary output ?

---

### Post by ajgreeny on 2019-11-05
In terminal use command ```
alsamixer
``` as a start and look for the level settings of the columns in that.

With some audio playing try raising column levels one by one using the cursor keys to move up/down and from column to column.  Hit Esc to save settings and exit.

Settings needed will obviously depend on your hardware, and you can find the sound card hardware available from command ```
aplay -l
```

---

### Post by janvi2 on 2019-11-05
alsamix works fine. Beside the switch off button I found another volume slider

---

