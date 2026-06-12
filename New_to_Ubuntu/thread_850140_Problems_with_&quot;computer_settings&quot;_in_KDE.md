---
title: "Problems with &quot;computer settings&quot; in KDE"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Benbow on 2008-07-05
I run KDE side by side with Ubuntu, meaning that I log into one or the other. Ubuntu is fine but when I try to access anything in "computer" in KDE (home, network etc) I get totem and a simple error message with no explanation. Funnily enough on the same list, "settings" is ok.
This is a major problem as apart from anything else I am unable to access my cd/dvd or hard drives.
I have tried reinstalling KDE but the problem remains.
I am stuck!!

---

### Post by apswartz on 2008-07-05
how did you install kde? Try...
```
sudo aptitude install kubuntu-desktop
```
to make sure you get everything you need.

---

### Post by Benbow on 2008-07-05
Thanks. Will this overwrite the existing KDE install and more importantly will it still allow me to run Ubuntu as another desktop?

---

### Post by nowshining on 2008-07-05
yes, yes and yes.

---

### Post by apswartz on 2008-07-06
> **Benbow said:**
> Thanks. Will this overwrite the existing KDE install and more importantly will it still allow me to run Ubuntu as another desktop?

It won't overwrite your personal settings in KDE. If you do want them wiped out, you need to delete or rename your ~/.kde folder. (or the ~/.kde4 folder for KDE4).

---

