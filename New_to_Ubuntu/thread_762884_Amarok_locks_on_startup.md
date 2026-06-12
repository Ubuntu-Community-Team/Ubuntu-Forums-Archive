---
title: "Amarok locks on startup"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by gulagarchipelago on 2008-04-22
I am running a brand new Kubuntu 7.10 install on a Dell laptop.  Whenever I try to open Amarok, it instantly freezes at the first screen (the Context Browser).  XMMS will play mp3s, but not Amarok.  Here's what I get when I run Amarok from command line:

ckeneston@angola:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8140938 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8140938 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?


Anyone else suffer a problem similar to this?

---

### Post by gulagarchipelago on 2008-04-22
Never mind; a reboot seems to somehow have fixed the problem.

---

