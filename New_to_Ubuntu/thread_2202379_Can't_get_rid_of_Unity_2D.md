---
title: "Can't get rid of Unity 2D"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by desconocido on 2014-01-28
I have just installed Ubuntu 12.04 on a new machine.

I installed Gnome shell:
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell
sudo shutdown now -r
```

Restart now shows five choices.

I tried to remove unity & unity-2d:
```
sudo apt-get remove unity unity-2d
```
Restart now shows four choices - unity-2d still there.

Any way to remove it?

---

### Post by steeldriver on 2014-01-28
If you just want to stop it from being presented in the lightdm dialog, I *think* you just need to remove/rename the .desktop file e.g.

```

sudo mv /usr/share/xsessions/ubuntu-2d.desktop /usr/share/xsessions/ubuntu-2d.desktop.ignore

```

---

### Post by desconocido on 2014-01-28
> **steeldriver said:**
> If you just want to stop it from being presented in the lightdm dialog, I *think* you just need to remove/rename the .desktop file e.g.


Yes, that works nicely. I meant to say, of course, that the phrase "**Ubuntu** 2D" was still being shown in the lightdm dialogue.

---

