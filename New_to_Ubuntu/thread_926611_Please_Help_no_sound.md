---
title: "Please Help no sound"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by GonZo1323 on 2008-09-22
I had sound 30 minutes ago.
First flash sounds went now everything went please help

---

### Post by Orange_and_Green on 2008-09-22
Hello :)

Just a few preliminary questions:

1) Have you tried rebooting the system?
2) Have you made sure the speakers are plugged in, turned on and connected to the green plug of the sound card? If you are using headphones, try unplugging them and use the speakers (I once spent five hours cussing and messing around because I had just compiled a program and I was thinking that had killed my sound --- it later turned out that the earphones were dead...:()
3) Have you tried ```
alsamixer
``` and made sure nothing is muted and volume is up on everything?

Good luck,

---

### Post by GonZo1323 on 2008-09-22
yes ive tried all this

---

### Post by TheLions on 2008-09-22
do you have pulseaudio enabled???(check at System->Settings->Sound->Devices->Sound playback)

also try restart several(<4) times till you get sound

---

### Post by Crafty Kisses on 2008-09-22
I'd like to see the results of this command:
```
lspci
```

---

