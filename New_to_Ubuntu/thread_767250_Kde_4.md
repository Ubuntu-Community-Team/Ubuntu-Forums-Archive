---
title: "Kde 4"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by lewisskinner on 2008-04-25
I have just downloaded Ubuntu hardy, but I want to added Kubuntu Hardy but with KDE4 rather than KDE 3.5.9

How can I do this/what sudo apt-get command go I need?

---

### Post by FrostiEE on 2008-04-25
sudo apt-get install kubuntu-kde4-desktop

^That's the command.

---

### Post by meborc on 2008-04-25
> **lewisskinner said:**
> I have just downloaded Ubuntu hardy, but I want to added Kubuntu Hardy but with KDE4 rather than KDE 3.5.9

How can I do this/what sudo apt-get command go I need?

you would need **sudo apt-get install kde4-core** (this is pure kde4, not kubuntu version as posted in previous post... this means it is lighter in applications and modifications)

this will install all you need... just log out and change your session to kde4

---

### Post by lewisskinner on 2008-04-25
> **meborc said:**
> you would need **sudo apt-get install kde4-core** (this is pure kde4, not kubuntu version as posted in previous post... this means it is lighter in applications and modifications)

this will install all you need... just log out and change your session to kde4

Hang on, I basically want it to look as though I've downloaded the Kubuntu CD.  So is that:
```
sudo apt-get install kubuntu-kde4-desktop
```

What does *core *vs *desktop* do differently?

---

