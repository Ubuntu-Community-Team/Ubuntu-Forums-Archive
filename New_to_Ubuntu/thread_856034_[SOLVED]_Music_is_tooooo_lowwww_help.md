---
title: "[SOLVED] Music is tooooo lowwww help"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by JMGM123456 on 2008-07-11
I use a vista-ubuntu dual boot, and when i put the volume on normal the music is barely audible , even when i put it on high it is still lower than normal. On vista it works fine.

Any ideas please??

---

### Post by AmericanYellow on 2008-07-11
Double click the Sound Icon on your taskbar. This will open up the Volume Control Panel. Then turn up "Master" and "PCM". If you don't see "Master" or "PCM", go to File --> Change Devices and select your main sound output device and just turn up the volume. Same as you would in Windows XP.

---

### Post by JMGM123456 on 2008-07-11
how do i know which one is my output device??

---

### Post by aktiwers on 2008-07-11
Try it out.

Go to terminal (applications = Accessories=Terminal)

And type:
```
alsamixer
```

Use the arrow keys on your keyboard to control it.

Put on some music, and play with alsamixer

---

### Post by JMGM123456 on 2008-07-11
perfect thanks

---

