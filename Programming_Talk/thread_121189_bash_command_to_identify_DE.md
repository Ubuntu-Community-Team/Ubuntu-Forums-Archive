---
title: "bash command to identify DE"
date: 2006-01-24
forum: Programming Talk
---

### Post by jackrobinson on 2006-01-24
Hi,
   Is there any bash command (or combination of commands) which can tell us what DE we are using? (Gnome/KDE/XFCE etc)?
Thanks,
Jack

---

### Post by ubuntumaneh on 2006-01-24
[QUOTE=jackrobinson]Hi,
   Is there any bash command (or combination of commands) which can tell us what DE we are using? (Gnome/KDE/XFCE etc)?
Thanks,
Jack[/QUOTE]

try this:

echo $DESKTOP_SESSION

---

### Post by ow50 on 2006-01-24
[QUOTE=ubuntumaneh]try this:

echo $DESKTOP_SESSION[/QUOTE]
```
$ echo $DESKTOP_SESSION
default
```
So, what does this tell us?

You can indentify GNOME based on the existance of "GNOME_DESKTOP_SESSION_ID" environment variable, which for bash probably means that "echo $GNOME_DESKTOP_SESSION_ID" returns something. GNOME_DESKTOP_SESSION_ID should be distro-independent. I don't know about other DEs.

---

### Post by jackrobinson on 2006-01-25
[QUOTE=ubuntumaneh]try this:

echo $DESKTOP_SESSION[/QUOTE]
Thanks a lot! thats exactly what I wanted. :)

---

