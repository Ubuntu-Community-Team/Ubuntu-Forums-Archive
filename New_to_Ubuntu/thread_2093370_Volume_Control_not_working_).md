---
title: "Volume Control not working :)"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by SukuC23101993 on 2012-12-10
Hey guys, the volume control isn't working on my panel. Mute or just raising or decreasing the volume does nothing, however, It works if I open pulse up and change the volume from there. If it helps, before this stopped working I accidentally removed indicator apps from it. 

Thank you for any help :D

---

### Post by SteveDee on 2012-12-12
Open a terminal and type:-
alsamixer

Now go back to the panel and adjust the volume control. You should see the Master control in alsamixer changing as you adjust the panel volume control.

If not, use the alsamixer display to diag the problem (e.g. what IS changing when you adjust the panel volume control?, is it adjusting the wrong control, the wrong device?).

---

### Post by vasilisc on 2012-12-12
Install and use pavucontrol
```
sudo apt-get install pavucontrol
```

---

