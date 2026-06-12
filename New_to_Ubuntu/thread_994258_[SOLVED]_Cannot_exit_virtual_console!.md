---
title: "[SOLVED] Cannot exit virtual console!"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by kajman on 2008-11-26
As I was using wine today, some app did not respond. I wanted to kill it using top command. So I've pressed Ctrl+Alt+F1 and went to virtual console (I hope thats the right name for it). When I finished and wanted to leave i gave it the exit command.

It went back to user login (still in console). I logged again, and again wrote exit. And so on, about seven more times. It didn't go out of the console. What was I doing wrong? Or is a bug or something?

I use Ubuntu 8.04.

---

### Post by taurus on 2008-11-26
Press <Alt>F7 if you want to get back to your GUI.

---

### Post by kestrel1 on 2008-11-26
If you want to get back to the graphical desktop, press Ctrl+Alt+F7.

---

### Post by kajman on 2008-11-26
Thank you both for a quick reply! :D

---

### Post by jimreynold2nd on 2008-11-26
To make things a little more clear:
Your computer has 8 consoles, labeled from 1 to 8 and can be accessed by Ctlr-Alt-Fx
Normally, 2 consoles are active by default: 7th console is the GUI, 1st console is textmode.
You can of course make X run on any console you want but I would rather not going into it right now for the sake of simplicity :)

---

### Post by psusi on 2008-11-26
Actually you can have as many virtual consoles as you want, but Ubuntu only bothers setting up 6 then runs X on the 7th.

---

