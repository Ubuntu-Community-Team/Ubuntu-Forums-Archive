---
title: "Amarok won't start"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Hobo Joe on 2008-08-28
Whenever I try to start Amarok, I get this error:

```

There was an error setting up inter-process communications for DKE. The message returned by the system was:

Could not open network socket

Please check that the "dcopserver" program is running!

```

When I run it in the terminal, this is what I get:

```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/joseph/.DCOPserver_joseph-desktop__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Could not open network socket
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
DCOPClient::attachInternal. Attach failed Could not open network socket
WARNING: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
I couldn't enable notifications at the dcopserver!
DCOPRef::send(): no DCOP client or client not attached error
kdecore (KWin): WARNING: Loading of kdetrayproxy failed.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x9a9010 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x9a9010 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```

When I try the solution in [this thread]("http://www.ubuntuforums.org/showthread.php?t=107269") I get this error:

```

chown: cannot access `/home/joseph/./.gvfs': Permission denied
chown: cannot access `/home/joseph/.gvfs': Permission denied

```


Anyone know how to fix it?

---

### Post by bangmalley on 2008-08-31
go to System Monitor. kill the amarokapp or amarok. make sure dcopserver is listed there. if it is not listed there, remove /home/joseph/.DCOPserver_joseph-desktop__0
, then press Alt F2, and run the dcopserver.

---

### Post by motoperpetuo on 2008-12-06
> **bangmalley said:**
> go to System Monitor. kill the amarokapp or amarok. make sure dcopserver is listed there. if it is not listed there, remove /home/joseph/.DCOPserver_joseph-desktop__0
, then press Alt F2, and run the dcopserver.

i didn't seem to have an app called "dcopserver" when i pressed alt+f2, just "dcop." anyway, deleteing the two hidden .DCOP files in my home directory and running "dcop" fixed the problem with amarok. thansk!

---

### Post by motoperpetuo on 2008-12-17
> **motoperpetuo said:**
> i didn't seem to have an app called "dcopserver" when i pressed alt+f2, just "dcop." anyway, deleteing the two hidden .DCOP files in my home directory and running "dcop" fixed the problem with amarok. thansk!

on more question, does anyone know what to do if this happens every third time or so i boot my computer? the fix is quick, but nevertheless, i'd like to see my KDE apps start without having to do it so often.

---

