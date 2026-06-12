---
title: "Amarok has stopped working!!?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Beatbreaker on 2008-06-15
Why has Amarok stopped being able to play my mp3s?

```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ce20 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ce20 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
michael@michael-laptop:~$ QString::arg(): Argument missing: _: track by artist on album, I Want Your Soul
QString::arg(): Argument missing: _: SampleRate, 44100

```

---

### Post by Ub1476 on 2008-06-15
Sometimes a solution is to delete the configuration folder. It's located somewhere in /home.

Probably one of those:

~/.amarok
~/.kde/apps/amarok

If you delete it, the next time you launch Amarok it will go through the configuration setup. 

Make sure you take a **backup** (playlists, scores etc) of the folder before you delete it though!

---

