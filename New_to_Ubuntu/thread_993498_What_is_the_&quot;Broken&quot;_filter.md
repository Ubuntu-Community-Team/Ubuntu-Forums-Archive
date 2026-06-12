---
title: "What is the &quot;Broken&quot; filter"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2008-11-25
what is the broken filter and where can i find it cause i had a problem loading avg antivirus and then i went to do updates later and an error message came up telling me to fix something and it said to go to the BROKEN filter thing

---

### Post by amauk on 2008-11-25
you don't need any antivirus

---

### Post by handydan918 on 2008-11-25
Synaptic has the ability to show "broken"packages. IIRC, it's under Tools.

---

### Post by diablo75 on 2008-11-25
1.  AVG antivirus is intended to be run on a Windows system (although it might run with WINE; I don't know).  And you don't need antivirus protection in Linux (unless you plan to use your computer to scan other computers... I doubt you will be doing that).

2.  Ignore that message about the broken filter.  There's more to that message... I guessing it said to open a terminal and type:

```
sudo apt-get install -f
```

Am I right?

Well, to do that, click Applications>Accessories>Terminal.  And type that in and press enter.  It will ask you for your password (you will NOT see ***'s appear while typing).

That will fix whatever package is broken.

---

