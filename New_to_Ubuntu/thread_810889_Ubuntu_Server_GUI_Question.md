---
title: "Ubuntu Server GUI Question"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by goldenwolf703 on 2008-05-28
I just installed Ubuntu server on one of my HP machine and I know "Servers aren't supposed to have GUIs!"
Tell me this though:
My team and I were wondering if we could put a GUI on the server and just turn it off when the GUI is not needed. Even off would it be a resource killer? Or when it is off would it just take up storage space, which is not a problem for my current situation.

Thank you

---

### Post by PinkFloyd102489 on 2008-05-28
You can install something light, like Fluxbox or IceWM. Then when you dont need it, just kill off the process.

---

### Post by Dr Small on 2008-05-28
Indeed, a server is not built for a GUI, but yes. You can install one such as Gnome or KDE which is a BIG desktop environment, or you could install a simple Window Manager.

In the end, you can disable it for bootup, so it does not start except by you involking the 'startx' command. Is this system directly connected to a monitor, or accessible via SSH ?

Dr Small

---

