---
title: "[KDE-HOWTO] Load Beryl/Compiz as part of desktop (not session)"
date: 2007-05-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Ateo on 2007-05-18
Beryl tends to break things when you have it auto-start on login (by dropping a script into ~/.kde/Autostart). So, to combat this issue, this formula ensures that your desktop is ready only after Beryl/Compiz has initialized. This makes it nice for people who have other programs to autostart in ~/.kde/Autostart. Most of you know how it lags and breaks karamba when you drop a beryl/emerald startup script in your Autostart folder...

This method DOES NOT employ beryl-manager, so you there will be no beryl systray icon. If beryl crashes, it will not revert to any default window manager (ie: kwin). If you are not comfortable with this, don't do it. It may render your desktop useless. So, with that said, no guarantees are given nor implied with this HOWTO.

So, enough of my babbling; here it is in all it's glory..

**1.** Create ~/.kde/env/berylwm.sh

**2.** Add the following code to ~/.kde/env/berylwm.sh (the name is arbitrary)```
#!bin/sh
LD_LIBRARY_PATH=/usr/lib/xorg/modules/
KDEWM=/usr/bin/beryl
beryl --replace dbus settings &
emerald --replace &
```

**3.** Make the script an executable file```
chmod a+x ~/.kde/env/berylwm.sh
```

**4.** Remove beryl and emerald scripts (or *.desktop, whichever applies) from ~/.kde/Autostart

**5.** Fin.

**[COLOR="Red"]NOTE[/COLOR]**: If you are using Compiz and want to use Emerald, you need to use Compiz available in Synaptic AND you need these Emerald debs: [http://ubuntuforums.org/showthread.php?t=423743](http://ubuntuforums.org/showthread.php?t=423743). Otherwise, comment out the line that loads Emerald.

Resources: 

Step #5: [http://forum.beryl-project.org/viewtopic.php?f=44&t=54&p=5380](http://forum.beryl-project.org/viewtopic.php?f=44&t=54&p=5380)

KDE ENV script: [http://gentoo-wiki.com/Beryl](http://gentoo-wiki.com/Beryl)

---

### Post by KubuntuKilledMe on 2007-05-20
Thanks, that was quite useful.

---

### Post by deadlydeathcone on 2007-05-21
Thank you much for figuring that out.

---

### Post by me1on on 2007-07-17
Thanks for this how-to, you have no idea how many problems this fixed for me. For those of us who still want beryl-manager to start, do:

```
kate ~/.kde/Autostart/BerylManagerSafe.desktop
```

Then add the following and save the file:

```
[Desktop Entry]
Comment=
Exec=beryl-manager --no-force-window-manager --no-force-decorator
GenericName=
Icon=beryl-manager
Name=BerylManagerSafe
Path=
StartupNotify=false
Terminal=0
TerminalOptions=
Type=Application
X-KDE-SubstituteUID=false
X-KDE-Username=

```

This starts beryl-manager without messing up the window manager or flashing the screen.

---

