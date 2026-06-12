---
title: "[SOLVED] How do I open Kommando?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-20
I just installed Kommando from the repos; running it from the CLI gives me the bash error.  How do I start it up?

---

### Post by InfinityCircuit on 2008-09-20
```
kommando: /usr/lib/kde3/kcm_kommando.la
kommando: /usr/lib/kde3/kcm_kommando.so
kommando: /usr/lib/kde3/kded_kommandod.la
kommando: /usr/lib/kde3/kded_kommandod.so
kommando: /usr/lib/libkommando.la
kommando: /usr/lib/libkommando.so.1
kommando: /usr/lib/libkommando.so.1.0.0
kommando: /usr/share/applications/kde/kommando.desktop
kommando: /usr/share/doc/kde/HTML/en/kommando/common
kommando: /usr/share/doc/kde/HTML/en/kommando/index.cache.bz2
kommando: /usr/share/doc/kde/HTML/en/kommando/index.docbook
kommando: /usr/share/doc/kommando/NEWS.Debian.gz
kommando: /usr/share/doc/kommando/README
kommando: /usr/share/doc/kommando/changelog.Debian.gz
kommando: /usr/share/doc/kommando/changelog.gz
kommando: /usr/share/doc/kommando/copyright
kommando: /usr/share/doc/kommando/examples/kommandorc
kommando: /usr/share/icons/hicolor/16x16/apps/kommando.png
kommando: /usr/share/icons/hicolor/32x32/apps/kommando.png
kommando: /usr/share/icons/hicolor/64x64/apps/kommando.png
kommando: /usr/share/services/kded/kommandod.desktop

```

Since it has no executable but does have a kde .desktop service, you should be able to configure it in kcontrol/on kicker/wherever after restarting kde.

---

### Post by tarahmarie on 2008-09-20
Ok, so kcontrol is system settings, right?  I don't see anything in system settings about kommando.  Also, searching for it IN system settings didn't help.

---

### Post by mc4man on 2008-09-20
> so kcontrol is system settings, not really
open kcontrol from konsole  or add an applet "Settings" to panel

Kommander is available in Kmenu under Development

I'm sorry, late, mis read Kommando

Kommando is in kcontrol under desktop

---

