---
title: "Cannot shutdown/restart from menu if multiple users logged in"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by prana on 2011-10-10
Hello All,

This is Oneric 32 bit fully updated on a Dell Vostro 3400 laptop.

I cannot shutdown/restart from the gear icon on the top right corner if there are multiple users logged in. It simply logs me out and takes me to the lightdm login screen.

Anyone else encountered this?

I remember that it used to warn that other users are logged in through a dialog box but would allow me shutdown/restart anyway if I entered my password.

Thanks.

---

### Post by dino99 on 2011-10-10
file a bug, it might warn about the other users logged.

---

### Post by prana on 2011-10-10
> **dino99 said:**
> file a bug, it might warn about the other users logged.

Ok. How do I identify the package name to file the bug against?

Thanks,

---

### Post by prana on 2011-10-10
Ok, logged it as a bug. If anyone else can reproduce this, please add to the bug report.

[https://bugs.launchpad.net/ubuntu/+bug/872054](https://bugs.launchpad.net/ubuntu/+bug/872054)

---

### Post by mc4man on 2011-10-10
maybe it's a bug, maybe intentional, lean towards the latter but actually don't know..

If you want to enable in a 'protected' file then try this, whether you should or not is up to you (I use .pkla's for other things, this doesn't particularly  affect me.

```
gksudo gedit /var/lib/polkit-1/localauthority/50-local.d/consolekit.pkla
```
You can close out that annoying 'Untitled Document' that also opens in gedit

paste this in & save, that's it
```
[Restart the system when multiple users are logged in]
Identity=unix-group:admin
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultActive=yes

[Stop the system when multiple users are logged in]
Identity=unix-group:admin
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultActive=yes

```

---

