---
title: "Extending nautilus"
date: 2010-09-04
forum: Programming Talk
---

### Post by Ooki on 2010-09-04
Hey

To be honest I dont really know where to begin, I am a decent software engineer that work at a small firm (where we all use Ubuntu), and as a hobby project I figured it would be fun to do some work on nautilus.

Basically what I want to do is to replace the panel where the folders are drawn with my own drawing code. Preferably without having to recompile Nautilus, I am thinking more along the lines of hooking some draw code in for some pre-configured folders.

Say if the folder is /home/myuser/dev/ 
use draw_system_A, else draw_system_Default. 

I assume hoping that the support for such a plug-in system is pretty far fetched but still I figured I would ask here before starting to roll my own
solution.

Any feedback on how to achieve this would be nice :)

cheers Ooki

---

### Post by hakermania on 2010-09-04
Why not recompiling nautilus? In this way you could make options for the user to choose his preferable panel... By your way you have to go and edit files in order to use your custom panel

---

