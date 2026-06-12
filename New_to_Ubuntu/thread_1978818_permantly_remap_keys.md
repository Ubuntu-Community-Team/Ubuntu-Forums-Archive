---
title: "permantly remap keys"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2012-05-12
I would like to turn my super key into a spacebar since my spacebar is broken on my laptop.

---

### Post by mike555 on 2012-05-12
install " xkeycaps ", open it through terminal, set it and save.

---

### Post by LunaticHiatus on 2012-05-12
> **mike555 said:**
> install " xkeycaps ", open it through terminal, set it and save.

I tried that, but it resets everytime on startup.

---

### Post by LunaticHiatus on 2012-05-12
someone suggested this to me

1 - Installed xbindkeys and its gui configuration utility:
sudo apt-get install xbindkeys xbindkeys-config

2 - Execute this:
xbindkeys --defaults > ~/.xbindkeysrc

3 - Run xbindkeys and xbindkeys-config
xbindkeys
xbindkeys-config

---

### Post by KittyCatHerder on 2013-03-28
I am trying to do something similar. I want to map my Windows/Super key to open gnome-terminal. I have been trying to figure out how to do this for the last 3 days. I've spent probably 6 hours trying to get it working and I am amazed that something so simple and basic is so difficult. I have made a forum thread asking for help but no one has responded. 

I already tried the xbindkeys software. I experimented with it for about 30 minutes but it just will not work. I have tried all of the settings in the standard Ubuntu 12.04 keyboard utility. 

Did you eever figure out how to get this done, so that maybe I could use the same technique to get my Windows key to open gnome-terminal?

---

