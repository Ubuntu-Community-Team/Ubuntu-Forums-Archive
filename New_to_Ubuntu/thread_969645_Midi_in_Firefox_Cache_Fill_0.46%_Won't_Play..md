---
title: "Midi in Firefox Cache Fill 0.46% Won't Play."
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-03
Hi Gang

Hardy 8.04, Firefox3.0.3, Plug-in for Midi Audio is Gecko-MediaPlayer0.6.0

A web site I draw midi files from, none over 10k, most are 9.0 to 9.5kb

Firefox Preferences Advanced, Cache is set to 50mb

I get Error Cache Fill: 0.46% at this setting.
If I increase the Cache to 250mb the Cache Fill: drops to 0.10%
Just the opposite of what it seems it should do.

Any Ideas?

Thanks
Gary

---

### Post by Kellemora on 2008-11-08
Bump

---

### Post by Kellemora on 2008-11-14
Bump

---

### Post by Kellemora on 2008-12-01
Bump

---

### Post by Kellemora on 2009-01-09
Bump

---

### Post by Kellemora on 2009-02-14
Hi Gang

FWIW:  I FINALLY SOLVED the problem on all 6 of our computers, including the newest 64 bit machine..........

The problem had absolutely NOTHING to do with Firefox!

And once we removed the offending program, midi's will now play direct from Firefox (when it hit's midi's that is) via any one of several players you can select.  I chose Totem (which would NOT WORK when the offending program was installed, and neither would Timidity by the way.)

The BAD BOY causing all of these problems since late August of 2008 when I first began installing Ubuntu on our computers is none other than GNOME Media Player, which is the Gecko Media Player!

Two IT guru's spent 4 and 6 hours here respectively and never figured out the problem either, so it's not surprising the folks at Mozillazine, Gnome or Launchpad could figure it out either.

Doing a Complete Removal of the Gnome Media Player allows Firefox to (with Mozplugger) find and use Totem or many other players too!

TTUL
Gary

---

