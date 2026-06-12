---
title: "Disaster - Most QT programs no longer work"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by TheMono on 2008-07-03
Hi - 

This has come at the worst possible time for me, during a very heavy workload, so if anyone can help it would be most appreciated.

Most QT apps no longer work properly for me after updating to the most recent Hardy kernel. For example: 

Amarok opens, will play music and work as normal, but freezes if you click in any of the text entry boxes for searching collection.
The prompt to unlock the screen is blank
Gwenview freezes when clicking on the menu for resizing options, ie, fit to screen etc.
Yakuake unrolls one line then freezes
Opening a new tab in Konqueror freezes it.

These are just a few of the issues. They all appeared yesterday on doing a swathe of updates.

The only unofficial repositories I am using are medibuntu and the gnome-do ppa.

Everything in QT4 works fine.

The only app which gives me decent terminal output is amarok, and for a clean start and shutdown, it gives me

```

kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x7c26f0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x7c26f0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )

```

On freezing it adds nothing to the terminal. It just stops responding.

Any ideas? Please! And preferably not of the "reformat/reinstall" kind...

---

### Post by cmnorton on 2008-07-03
Are you able to boot using a previous version of the kernel?

---

### Post by TheMono on 2008-07-03
The Nvidia driver dislikes it when I do that! 

I just discovered, the kdesu text entry dialog is broke too, but if I run any of those programs as root with gksudo they run fine.

---

### Post by cmnorton on 2008-07-05
> **TheMono said:**
> The Nvidia driver dislikes it when I do that! 

I just discovered, the kdesu text entry dialog is broke too, but if I run any of those programs as root with gksudo they run fine.

The only other thing I can think of is to boot into recovery mode, and enter
dpkg-reconfigure xserver-xorg

I would read up on it first. Basically, you might have to use different resolution or even fall back to the vesa driver.

---

### Post by TheMono on 2008-07-05
Tried that and it did nothing.

There's something really broke either in QT3 or in the KDElibs / KDEbase. I pulled down KDE4.1 beta 2 from the Kubuntu testing PPA and that is running fine, and I can run all my QT3 apps under KDE4 just fine too. It's all very odd. It's just KDE3 that has completely crapped out on me.

---

### Post by iceeey on 2008-07-12
Hi, I had the exact same problem.
I ran gdb on amarokapp and noticed it was hanging, trying to find something relating to SCIM. I don't know really much about SCIM, but I was able to fix this by either removing the package scim-qtimm or by running skim. Since I have no use for scim, I just removed the package.

I don't know what the proper fix is, but perhaps if someone comes around who knows more about this, we could find the real problem. At least, I can use my Qt3 apps now.

Hope this fixes it for you too.

---

### Post by maybeway36 on 2008-07-12
You could try just resetting the KDE settings by moving the settings folder away:
```
mv .kde old.kde
```
If that doesn't fix it, move it back:
```
rm -rv .kde&&mv old.kde .kde
```

---

