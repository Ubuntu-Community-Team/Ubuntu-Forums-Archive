---
title: "Xfce Panel Problem"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-11-19
Well I was I fancied a change of theme last night so I downloaded the files, put them in the right directories etc. Everything went well apart from my Panel, for some reason the it doesn't change to match the theme. I Googled it but found little help, so has anyone here got any suggestions?

---

### Post by LeAstrale on 2008-11-19
Im not at my Linux machine right now, but give this a try.

Take a look in the "system monitor" and check for "xfce4-panel" and kill the processes you find. (alternatively do: "sudo killall -9 xfce4-panel" in terminal) after that you should be able to launch a new instance of the panels with alt+F2 and then "xfce4-panel" Alternatively check your panel settings in the settings manager.

---

### Post by Jack Bonner on 2008-11-19
> **LeAstrale said:**
> Im not at my Linux machine right now, but give this a try.

Take a look in the "system monitor" and check for "xfce4-panel" and kill the processes you find. (alternatively do: "sudo killall -9 xfce4-panel" in terminal) after that you should be able to launch a new instance of the panels with alt+F2 and then "xfce4-panel" Alternatively check your panel settings in the settings manager.

Didn't do anything i'm afraid

---

### Post by cardinals_fan on 2008-11-19
What did you expect it to do?  How does it not match the theme?

---

### Post by LeAstrale on 2008-11-24
Are you using compiz? I had the problem when I had desktop effects enabled.

---

