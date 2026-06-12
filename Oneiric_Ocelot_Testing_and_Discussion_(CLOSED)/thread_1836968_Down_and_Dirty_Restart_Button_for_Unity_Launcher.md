---
title: "Down and Dirty Restart Button for Unity Launcher"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lidex on 2011-08-31
Tired of jumping through hoops to restart, stumbled on this trick I haven't seen anywhere. Open terminal, run this command:
```
cp /usr/share/applications/indicator-session-restart.desktop ~/.local/share/applications

```
Now browse to 
```
~/.local/share/applications
```
using nautilus and drag
```
indicator-session-restart.desktop
```
to the launcher.

---

### Post by ranch hand on 2011-08-31
Very neat.  Where did you run across this?

---

### Post by lidex on 2011-09-01
> **ranch hand said:**
> Very neat.  Where did you run across this?

Was scanning /usr/share/applications on another mission and saw "Restart" there. Immediately piqued my interest. Played around with it a little bit based on some of the things I've seen here regarding quick lists, adding launchers, etc. I'm sure mc4man lernt me a thing or two.

---

### Post by 3rdalbum on 2011-09-01
You know that you can just go to the cog menu and choose Shut Down... and then click the Restart button?

---

### Post by lidex on 2011-09-01
> **3rdalbum said:**
> You know that you can just go to the cog menu and choose Shut Down... and then click the Restart button?

Yes, but I prefer the restart button. Its a bit more elegant and I was really frustrated for weeks not having that menu at all due to a indicator-session bug.

---

### Post by shuttleworthwannabe on 2011-09-01
screenshots??

---

### Post by MacUntu on 2011-09-01
Tbh, I wouldn't want such a critical action linked to my launcher. :-o

---

### Post by cecilpierce on 2011-09-01
> **shuttleworthwannabe said:**
> screenshots??

Heres my screen shot,looks like a U-turn
:P

---

