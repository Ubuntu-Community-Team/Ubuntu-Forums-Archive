---
title: "Broken ambiance theme"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xyzzyman on 2011-09-28
Sometime within the last 24 hours of updates, I have lost part of my UI theme. Right clicking on a page in Chrome for example still has ambience look, but right click on the desktop or on a file in nautilus and it looks the same as the attached screen shot. I have switched even to high contrast and everything changes except for these things. I searched this forum and launchpad and no seeing anyone else reporting the same issue. Any ideas? Opened nautilus from a terminal but no errors.

---

### Post by Quackers on 2011-09-28
I found that yesterday but updates seem to have cured it.

---

### Post by chlorox on 2011-09-28
That happened to me a couple of days ago, I ended up rebooting my box.

I think it's an easter egg that old icky Gnome-98 is still in there somewhere. :p

---

### Post by mc4man on 2011-09-28
Happens every once & a while here - a log out/in fixes.
Some random problem with gnome-settings-daemon,

---

### Post by dino99 on 2011-09-28
have had some borked config too, so into a terminal i've ran:

gnome-panel --replace
gnome-shell --replace
unity --reset

then everything is ok now :)

---

### Post by xyzzyman on 2011-09-28
Even a cold restart didn't fix, but I woke up to 101 updates, applied them, restarted and fixed. NVM this thread.

---

### Post by homeofpoe on 2011-10-05
Happened to me yesterday I think, no solution yet.  Rebooting stuff makes no difference, unfortunately, and my system is fully updated.

Seems to be a problem with theme detection?  When I go to the Appearance dialog, it only shows a very small selection of stock themes (Adwaita, Ambiance, Radiance, HighContrast, HighContrastInvert).  Changing from one to another makes no apparent difference.

It also uses some default icon pack, not ubuntu-mono-dark like is selected.  Tried changing via gnome-tweak-tool to no avail.

---

### Post by homeofpoe on 2011-10-05
Narrowed down the issue to gnome-settings-daemon.

Fix found here:
[https://bugzilla.redhat.com/show_bug.cgi?id=739069](https://bugzilla.redhat.com/show_bug.cgi?id=739069)


$ sudo rm /usr/share/GConf/gsettings/pythonconsole.convert
$ gsettings-data-convert
$ gnome-settings-daemon

---

