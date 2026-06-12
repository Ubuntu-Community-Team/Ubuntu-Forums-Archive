---
title: "Lost window manager?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Keira-Chan on 2008-08-14
Ok I'm brand new to Ubuntu and I decided to explore with the themes and window managers. I tried using fluxbox inside Gnome but decided to go back. Now it seems I have no window manager at all. How do I get Metaticy back?

---

### Post by starcannon on 2008-08-14
I'm not sure but I think the command would be
```

sudo dpkg-reconfigure gdm

```

again, I stress, I'm not certain that will fix it. If I were where you are, its probably the thing I'd try though.

---

### Post by Gannon8 on 2008-08-14
I thought you had to run fluxbox while in the terminal to start an XOrg session, not through the themes manager... :confused:

---

### Post by smooth3006 on 2008-08-14
install "compiz-fusion icon" from synaptic and choose which window decorator or to reload it.

---

### Post by Keira-Chan on 2008-08-14
Heh, I figured it out. It was pretty simple

```
Metacity &
```

Thanks for the help though.

---

