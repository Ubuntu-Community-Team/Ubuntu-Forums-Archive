---
title: "Conky Always On Top"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-25
I set Conky to execute during start up. However, if I open other program (Firefox, Pidgin), Conky will permanently stay on top. The only solution is kill Conky from Sys Monitor and re start the program again. I've tried script (conky_start) that I found in "How to beautify Conky....." thread but it seem not to work because Conky still start along the start up(not 60 minutes afterward). Dont know what is the problem. Please assist me.

---

### Post by bumanie on 2008-05-25
Which bash script did you use? You can remove conky from the start up list and manually start it by pushing alt F2 and typing conky in the window.

---

### Post by wariskampar on 2008-05-25
#!/bin/bash
sleep 60 && conky;

I C&P this code on txt document and save in /usr/bin. then put it on start up list. but problem persist. do I have to put this file in /home/xxxx/

---

