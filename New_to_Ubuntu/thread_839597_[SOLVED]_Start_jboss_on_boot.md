---
title: "[SOLVED] Start jboss on boot"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by anderskitson on 2008-06-24
I would like jboss to start each time I boot up, run now i run it with an sh command, not sure how to do that automatically. I tried with startup programs with no success yet, but I might be doing it wrong, any suggestions? It also wont run unless you are root.

---

### Post by Darkade on 2008-06-24
try it once more, just add gksudo at the beggining of the command.

---

### Post by Darkade on 2008-06-24
if that doesn't work try [this]("https://help.ubuntu.com/community/UbuntuBootupHowto") (not sure if it will help :()

---

### Post by anderskitson on 2008-06-24
Great so simple, it worked perfectly, so what I ended up putting as my command was,  > gksudo sh /usr/local/jboss-4.0.2/bin/run.shjust if you were curious

---

### Post by Darkade on 2008-06-24
Great :D

---

