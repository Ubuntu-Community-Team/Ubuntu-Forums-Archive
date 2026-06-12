---
title: "Gdm, Xdm, Icewm and memory"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by bill-linux on 2008-05-12
I am going to install Ubuntu Hardy 8.04LTS on a laptop. I'm going to use IceWM to keep the memory usage small. Ubuntu uses gdm to load Icewm ... gdm is known to be something of a memory hog. My question is this: WHEN does gdm use memory. For example, gdm starts the xsession showing the Ubuntu splashscreen, I log in as a user and that pops up icewm. Is gdm "running" when icewm and thus using up resources, or is it using resources only when starting up x? If it is the latter I can tolerate that in my system; otherwise, I'll need to use xdm or configure it to use startx.

---

### Post by rjmoerland on 2008-05-13
I think it'll be running alongside IceWM as well, but you can check yourself by typing this in a terminal:

```

pstree

```

That'll show you a list of processes running. If gdm is running, it'll be listed as well. You can directly search for the term 'gdm' by typing this in a terminal:
```

pstree|grep gdm

```
which will print all lines from pstree's output that contain the word 'gdm'.
Or, use the graphical system monitor and have a look at all processes running. Not sure here, but perhaps logging in from a terminal (before gdm starts) erases the need for gdm as no graphical login is needed? (BIG question mark here!)

HTH

---

