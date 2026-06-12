---
title: "[SOLVED] Amarok - No Sound?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-07
I used Amarok last night and it worked perfectly. I restarted my computer.. and now it won't play sound. I have my sound settings all set up. I can play sund in Rhythmbox, but not Amarok. Help?

---

### Post by NightwishFan on 2008-05-07
Check to see if you are using the Xine engine and if the device is set to default. Also does it play but no sound or just not play?

Also try running amarok from the terminal and see if there are any error messages relating to sound, (not display since there will likely be some if you are on gnome)
```
amarok
```

In the worse case purge amarok and reinstall it.

```
sudo apt-get update && sudo apt-get purge amarok && sudo apt-get install amarok
```

---

### Post by UnknownFear on 2008-05-07
This is what Amarok in the Terminal displays:

```
dan@dan-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099488 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099488 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
dan@dan-desktop:~$ 
```

---

### Post by NightwishFan on 2008-05-07
Perhaps reinstall I make little sense of that. I was hoping to get a xine not found of some kind. :lolflag:

---

