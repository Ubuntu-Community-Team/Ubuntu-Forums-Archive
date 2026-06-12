---
title: "[SOLVED] No sound/play for flash player"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by clap.your.hands on 2008-05-27
Hello,

I just changed to Linux (well sort of I still have XP) and I am not very computer literate. These forums have been amazing and have helped me with the small problems I have had. But I have been unable to fix the flash player with no audio. I downloaded it using the terminal. I was wondering does anyone know how to get sound? Do I have to download anything else?
The audio works when I play cds.As well the video will stop playing after a few seconds. 
Any help would be great appreciated. Thanks

Sorry if I double posted

---

### Post by ZabiGG on 2008-05-27
Hi and welcome to Ubuntu.

For general information, click on the first link in my signature below.

For your flash problem, one question: did you install the open-source or the closed-source version of the player?

---

### Post by clap.your.hands on 2008-05-28
I have no idea. How would I find out?

---

### Post by clap.your.hands on 2008-05-28
I used this code to install flash:

sudo apt-get install flashplugin-nonfree

I hope that helps

---

### Post by diablo75 on 2008-05-28
Type this:

```
sudo apt-get install libflashsupport
```

Make sure firefox isn't running beforehand (or atleast restart it after installing the above package).

Let us know what happens!

---

### Post by clap.your.hands on 2008-05-28
I installed that but the problem is still there. No sound and no play. The video appears but stops after two seconds (on youtube).

---

### Post by clap.your.hands on 2008-05-28
I spoke too soon. I restarted my computer and now the video is playing along with the sound. Thanks!

---

