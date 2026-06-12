---
title: "Autologin to Unity 2D / Lightdm problem"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-09-04
I have switched to Unity 2D now but it still auto logs in to the 3D desktop. Anyone know where I fix this?

Also, on both my desktop systems I seemed to be presented with a really crude login screen, whereas the laptop has the fancy lightdm screen. How do I fix that?

---

### Post by lucazade on 2011-09-04
You can tweak lightdm config file by hand to load unity-2d as default session.
gksu gedit /etc/lightdm/lightdm.conf
and change
user-session=ubuntu
to
user-session=ubuntu-2d

---

### Post by sonicb00m on 2011-09-04
Thanks! You're really helping me with my little niggly problems :D

---

### Post by lucazade on 2011-09-04
> **sonicb00m said:**
> Thanks! You're really helping me with my little niggly problems :D

ahah.. happy testing ;)

---

