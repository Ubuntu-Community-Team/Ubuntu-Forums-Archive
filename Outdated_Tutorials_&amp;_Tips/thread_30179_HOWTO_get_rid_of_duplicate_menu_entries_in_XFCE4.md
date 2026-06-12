---
title: "HOWTO get rid of duplicate menu entries in XFCE4"
date: 2005-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by mrbass on 2005-04-27
ok XFCE4 is an awesome desktop environment. However, I have Ubuntu installed with kubuntu-desktop and I see a few duplicate entries namely for Inkscape, Evolution, Firefox, GnomeMeeting, Pan, XChat, gFTP, Audacity, MPlayer, XMMS, RealPlayer, Adobe Reader, Scribus, and tons of Games are duplicated too. Basically this took me about 2 hours to reasearch.  I couldn't find it on xfce4 mailinglists...maybe I just didn't look hard enough.

ok so the easiest solution is a simple (be careful with rm -rf)
**sudo rm -rf /usr/share/apps/kappfinder/apps/**

Wait a couple of minutes and all your dupes will be gone.  Downside to this method is you lose the KDE Settings Menu (but you don't need them in XFCE4)...other than that the KDE apps remain..Kate, KolourPaint, Kooka, Konqueror, Kopete, Kaffeine, K3b, etc.

Basically xfce4 menu (not sure if it's Utilities | XFCE4 Appfinder) or what scans all directories in /usr/share looking for any files with .desktop extensions
anyway cache is in
**~/.cache/xfce4/menu-cache/**
removing files didn't have any immediate effect as far as I could tell.

Anyway the most common locations for storing .desktop entries are:
[b]/usr/share/applications/
/usr/share/applications/kde/
/usr/share/applnk/
/usr/share/gnome-app-install/
/usr/share/gnome/apps/
/usr/share/apps/kappfinder/apps/[/b]

Now as soon as I launch a KDE session I'm sure the kappfinder directory will be repopulated so the ideal thing is to create a batch file to do this automatically each time I launch xfce4.  Anyone know how to autostart in xfce4?  Like kde it's /usr/share/autostart or ~/.kde/autostart

---

### Post by stevetone on 2005-04-27
In xfce, you can put autostart scripts and programs in the ~/Desktop/Autostart/ directory.

---

### Post by A-star on 2005-05-10
Is this really safe to use?
What happens if I start gnome afterwards, will there be missing items in the menu there?

---

### Post by mrbass on 2005-05-10
yes it is.  I thought I'd have to have it start up each time.  I logged back into KDE (everything is fine) and then back to XFCE4 and thought the duplicates would be regenerated but they weren't.  So just doing it one time does the trick.

---

