---
title: "Sound problems"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Stargazer777 on 2008-08-17
The volume on my computer is having trouble. It wont go even 1/10 from max. I dont know if it is related, but I have two earphone jacks on the front of my laptop and when I plug in a secound pair, the first pair stops working.

---

### Post by Crafty Kisses on 2008-08-17
Post the following output:
```
lspci
```

---

### Post by Stargazer777 on 2008-08-17
Sorry, but When I posted that into the terminal, it didn't do anything.

---

### Post by Stargazer777 on 2008-08-17
can anyone tell me how to get into the volume mixer?

---

### Post by Unanimated on 2008-08-17
I'm not completely sure about your problem, but to get into the volume mixer, right click the speaker icon at the top deskbar of your screen.

First, I would install PulseAudio, then open Rhythmbox and start playing a song, and see if it comes up as an audio stream in PulseAudio. Also, make sure you are using the correct audio hardware.

PulseAudio Volume Manager: Click icon-->Volume Control
Audio Hardware Chooser: Right click speaker icon-->File-->Change Device

---

### Post by Stargazer777 on 2008-08-18
I tried that and all that I have for an option is "Conextant HSF (OSS)". Also... I tried to adjust the volume in the window that came up, and the left bar and the right bar in the volume panel wont stay connected together.

---

