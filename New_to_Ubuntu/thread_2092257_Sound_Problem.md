---
title: "Sound Problem"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by MyatKo on 2012-12-07
I have use the system settings, install updates and I downloaded all the files and installed it. Then sound suddenly stopped functioning. When I open the sound setting, it says in the output tab
"Dummy output"
and there is no hardware in playback.
My laptop is Toshiba Satellite L310. 
sound is working just fine when I first installed ubuntu 12.04
Now I can't watch movies or listen to music. I am new to ubuntu 12.04
please help me

---

### Post by Isamu715 on 2012-12-08
Open a terminal and type:
```
alsamixer
```see if any channels are muted(especially the master channel) and that Auto-Mute is disabled. If your channels are not muted and the problem persists try:
```
killall pulseaudio
```

---

