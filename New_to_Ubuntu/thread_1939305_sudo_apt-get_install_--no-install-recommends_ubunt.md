---
title: "sudo apt-get install --no-install-recommends ubuntu-desktop"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by adym333 on 2012-03-11
[COLOR=red][B][COLOR=Black]sudo apt-get install --no-install-recommends ubuntu-desktop

[/COLOR][/B][COLOR=Black]after entering above comnd got all the installation done but aftr  running whole processes ............ still not able to get GUI for  ubuntu server ....????

did tried Ctrl +Alt + (F1/F2/F3/F4 ....)........!!!!!!!!!!!!!!!!!!

help required .....!!!.....:sad::sad:[/COLOR][/COLOR]

---

### Post by adym333 on 2012-03-11
[COLOR=red][B][COLOR=Black]sudo apt-get install --no-install-recommends ubuntu-desktop

[/COLOR][/B][COLOR=Black]after entering above comnd got all the installation done but aftr  running whole processes ............ still not able to get GUI for  ubuntu server ....????

did tried Ctrl +Alt + (F1/F2/F3/F4 ....)........!!!!!!!!!!!!!!!!!!

help required .....!!!.....:sad::sad:[/COLOR][/COLOR]

---

### Post by Vishal Agarwal on 2012-03-11
Once I installed the GUI in my server with apt-get install ubuntu-desktop.
And it worked for me.

---

### Post by adym333 on 2012-03-11
[COLOR=red][B][COLOR=Black]sudo apt-get install --no-install-recommends ubuntu-desktop

[/COLOR][/B][COLOR=Black]after entering above comnd got all the installation done but aftr  running whole processes ............ still not able to get GUI for  ubuntu server ....????

did tried Ctrl +Alt + (F1/F2/F3/F4 ....)........!!!!!!!!!!!!!!!!!!

also tried rebooting system ..................... using Vbox ...............

help required .....!!!.....:sad::sad:[/COLOR][/COLOR]

---

### Post by Vishal Agarwal on 2012-03-11
sudo aptitude install _xserver-xorg _x-window-system-core gnome-core gdm

and use the startx to start GUI.

---

### Post by volkswagner on 2012-03-11
Have you tried to start X-server?  It is likely not going to automatically start, using server edition (especially using without recommends).

Try:

```
startx
```

---

### Post by oldos2er on 2012-03-11
Post moved to its own thread.

Edit: Posts from other thread merged. adym333, please do not hijack other people's threads, and do not create more than one thread per question.

---

### Post by Elfy on 2012-03-11
Thread closed. Please do not post duplicates, it dilutes community effort.

---

