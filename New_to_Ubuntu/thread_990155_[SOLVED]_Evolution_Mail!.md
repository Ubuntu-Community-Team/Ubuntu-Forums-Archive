---
title: "[SOLVED] Evolution Mail!"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by aut-omatic on 2008-11-22
Hi, i was wondering if there is a way to hide evolution mail while it still being open.

I guess just like windows' "tray". 

All help is appreciated!! :)

---

### Post by Martje_001 on 2008-11-22
```
sudo apt-get install alltray -y
alltray evolution
```
I don't know the 'official' way, unfortunately.

---

### Post by aut-omatic on 2008-11-22
i tried this, and the first code worked.

but the second one just responded by saying this :

(evolution:19830): evolution-shell-CRITICAL **: e_shell_set_crash_recovery: assertion `E_IS_SHELL (shell)' failed
^C

---

### Post by amauk on 2008-11-22
just put it on a different desktop

---

### Post by Martje_001 on 2008-11-22
Which version of Ubuntu are you using? I'm using 8.04 and it works:
```
martijn@mekkie:~$ alltray evolution
evolution-shell-Message: Killing old version of evolution-data-server...

```

---

### Post by aut-omatic on 2008-11-22
will that still make the "new message" icon appear at the menu bar when i'm at another desktop?

(this was to amauk)

---

### Post by aut-omatic on 2008-11-22
to martje,

ya, i tried it again and it displayed the same error message as before.

i'm using ubuntu 8.10

---

### Post by laurielegit on 2008-11-22
> **aut-omatic said:**
> will that still make the "new message" icon appear at the menu bar when i'm at another desktop?

(this was to amauk)

yes it will. I usually have evolution on one desktop and control it mainly through the bar. You can do this with all applications with a icon in the notification bar/area.

---

### Post by aut-omatic on 2008-11-22
oh ok!,

problem solved ^^

thanks guys!:)

---

