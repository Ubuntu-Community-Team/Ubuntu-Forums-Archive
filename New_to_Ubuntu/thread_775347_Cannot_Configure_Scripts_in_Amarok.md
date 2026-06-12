---
title: "Cannot Configure Scripts in Amarok"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ExBuM on 2008-04-30
I just did a fresh install of Hardy and installed Amarok. I downloaded some scripts like AmarokPidgin but whenever I click the Configure button after I run the script nothing happens. Anyone know how to fix this?

---

### Post by hermes0710 on 2008-04-30
> **ExBuM said:**
> I just did a fresh install of Hardy and installed Amarok. I downloaded some scripts like AmarokPidgin but whenever I click the Configure button after I run the script nothing happens. Anyone know how to fix this?

Start amarok from a console and try again what you are now trying to see the output. Then post here in case we can help

---

### Post by ExBuM on 2008-04-30
Sorry but how do you start amarok from a console? >.>
What do you type? I tried amarok and it opened but after it loaded the terminal stopped showing everything that was going on.

---

### Post by hermes0710 on 2008-04-30
> **ExBuM said:**
> Sorry but how do you start amarok from a console? >.>
What do you type? I tried amarok and it opened but after it loaded the terminal stopped showing everything that was going on.

Open a terminal (<alt>+F2 and type gnome-terminal) and execute "amarokapp". I just tried this and i get the output in whatever i do in amarok...

---

### Post by ExBuM on 2008-05-01
I ran amarokapp this time but pretty much the same thing happened. I stop getting output of whatever I do in amarok as soon as it loads. (So basically no output)

This is what I get :x

```
$ amarokapp
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x96e0d0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x96e0d0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
STARTUP
QColor::setRgb: RGB parameter(s) out of range

```

---

