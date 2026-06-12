---
title: "Any Way to Disable Login Sound?"
date: 2011-07-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-07-19
Well, another change in Oneiric seems to have been to remove the login sound from startup apps; anyone know a nice, neat way to disable it?

---

### Post by lucazade on 2011-07-19
> **moore.bryan said:**
> Well, another change in Oneiric seems to have been to remove the login sound from startup apps; anyone know a nice, neat way to disable it?

uninstall gnome-session-canberra
or change visibility from /etc/xdg/autostart/gnome-session-canberra.desktop (iirc the filename) and you'll get back loginsound control in startup app.

---

### Post by mc4man on 2011-07-19
```
gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```
Then change the NoDisplay= to false, ect.

---

### Post by moore.bryan on 2011-07-19
Wow... you two seem to be following me around, answering all my questions! Thanks, again.

Any reason why the decision was made to "hide" this on the startup programs?

---

### Post by donniezazen on 2011-07-19
sudo rm /usr/share/sounds/ubuntu/stereo/system-ready.ogg

This is what i do every time, i do a clean install, for past 4-5 releases.

---

