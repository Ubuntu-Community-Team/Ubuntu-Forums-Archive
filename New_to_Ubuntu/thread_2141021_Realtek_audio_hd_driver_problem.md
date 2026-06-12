---
title: "Realtek audio hd driver problem"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by piervallese on 2013-05-01
Hello everybody! First of all, i wanted to tell that this forum is awesome, and it's been very helpful during my recent introduction in the world of ubuntu.
The reason i'm posting is that i've installed Ubuntu 12.04 on my computer, in dual boot with windows 7.
After the installation the audio was working, but the quality was not that of windows. so i thought to install the hd audio drivers.
Here comes the problems, because i've had a couple errore through installation, and since then i can't hear a sound through my audio card.
Installing and reinstalling alsamixer had no effect, a part completely remove the audio symbol on the top of the bar. 
if i write alsamixer on terminal, i obtain no such file or directory.
What can i do to hear again?

Ask for all the information you need, and thank for your help!
piervallese

---

### Post by zero2xiii on 2013-05-02
Hay,

Please see this thread and post all the related out puts of the commands so we can see what is going on on your system:
[http://ubuntuforums.org/showthread.php?t=2140012](http://ubuntuforums.org/showthread.php?t=2140012)

Most helpful should include:
```
history
lsmod
lspci
cat /var/log/apt/term.log 
```

But please review the above.

Cheers

---

