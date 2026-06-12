---
title: "HOWTO: Install artwiz fonts on edgy/feisty"
date: 2007-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2007-05-24
This guide will tell you how to install artwiz fonts on ubuntu edgy (6.10) and feisty (7.04).

Q - What are "artwiz fonts" ?
A - The artwiz fonts are a set of small futuristic fonts for x11, created by Artwiz, TigerT, and Daniel Erat. It seems that these fonts are most popular with openbox/fluxbox users.

Q - What do they look like ?
A - [IMG]http://home.no.net/%7Estaura/ttm.png[/IMG]
nu from the artwiz collection, probably the coolest one.

Q - Which fonts are in the collection ?
A - Anorexia (9x11 variable width),
  Aqui (12x13 variable width),
  Cure (6x10 fixed width),
  Drift (6x11 fixed width),
  Edges (5x10 fixed width),
  Fkp (8x16 fixed width),
  Gelly (9x10 variable width),
  Glisp-bold (10x11 variable width),
  Glisp (9x11 variable width),
  Kates (7x14 fixed width),
  Lime (5x10 fixed width),
  Mints-mild (9x9 variable width),
  Mints-strong (9x9 variable width),
  Nu (7x9 variable width),
  Smoothansi (6x13 fixed width) and
  Snap (9x10 variable width) by Artwiz,

  Runt (5x10 fixed width) and
  Smooth (6x13 fixed width) by Daniel Erat,

  Tixus (5x10 fixed width) by TigerT.

TO INSTALL:

1. Install this package: ```
sudo aptitude install xfonts-artwiz
```2. Enable bitmapped fonts. To do this, run: ```
sudo dpkg-reconfigure fontconfig-config
```On the first two questions, just press enter. The third question will ask whether you want to enable bitmapped fonts by default. Move the selection to "yes" and press enter. 

3. Restart your x by pressing Ctrl+Alt+Backspace. 

4. If you are using fluxbox or openbox, you can select these fonts for your apps by running ```
gnome-font-properties
``` then selecting "Application font". If you are using gnome, go to System > Preferences > Font.

Please post any questions, comments, or concerns.

---

### Post by JMO707 on 2007-05-27
Excellent. Its just what I was looking for. Now my Fluxbox is complete =D

---

### Post by dbbolton on 2007-05-27
> **JMO707 said:**
> Excellent. Its just what I was looking for. Now my Fluxbox is complete =D
i'm glad i could help

---

### Post by JMO707 on 2007-05-28
Question: Do you know if there is any package of Artwiz with special characters around?

---

### Post by dbbolton on 2007-05-28
> **JMO707 said:**
> Question: Do you know if there is any package of Artwiz with special characters around?
unfortunately, i don't think such a package exists.

---

### Post by groggyboy on 2007-05-28
the artwiz fonts aren't appearing on my GNOME system.  any idea what gives?

i don't know if it's relevant, but when I was installing the package, aptitude produced this warning:
"warning: /usr/lib/X11/fonts/misc does not exist or is not a directory"

a quick peek revealed that there is no such /usr/lib/X11/fonts directory on my computer.

also, I ran "locate smoothansi" (one of the fonts you listed).  It told me that smoothansi is in the /usr/**share**/fonts/X11/misc directory.

So the fonts are installed.  Why can't I see them in font-properties (or other apps like AbiWord)?

---

### Post by dbbolton on 2007-05-28
> **groggyboy said:**
> the artwiz fonts aren't appearing on my GNOME system.  any idea what gives?

i don't know if it's relevant, but when I was installing the package, aptitude produced this warning:
"warning: /usr/lib/X11/fonts/misc does not exist or is not a directory"

a quick peek revealed that there is no such /usr/lib/X11/fonts directory on my computer.

also, I ran "locate smoothansi" (one of the fonts you listed).  It told me that smoothansi is in the /usr/**share**/fonts/X11/misc directory.

So the fonts are installed.  Why can't I see them in font-properties (or other apps like AbiWord)?
do ```
sudo mkdir '/usr/lib/X11/fonts/misc'
``` then reinstall the package

---

### Post by groggyboy on 2007-05-28
edit: just saw dbbolton's post

---

### Post by dbbolton on 2007-05-29
> **groggyboy said:**
> UPDATE:



a quick google search gave me a solution.  it's so obvious, its embarrasing! :lol:

i purged xfonts-artwiz with aptitude, then created the directory in question.

after reinstalling the package, the fonts appeared in gnome-font-properties.
if that didn't work, i was going to tell you to run the command in your sig.

---

### Post by groggyboy on 2007-06-10
> **dbbolton said:**
> if that didn't work, i was going to tell you to run the command in your sig.

:p

i may be a little slow on the uptake at times, but i'm not suicidal!

---

### Post by dbbolton on 2007-07-26
i originally wrote this guide from edgy. after a clean install of feisty, i had to go through the process several times before i was able to use the fonts...

---

### Post by ayoli on 2007-07-31
hi,
i cant manage to install these fonts on feisty.
i tried to make the dir /usr/lib/X11/fonts/misc but it was deleted after package reinstall.
After a look to the package contents, i saw that the fonts were installed in /usr/share/fonts/X11/misc so i made a link in /usr/lib/X11/fonts/ then reconfigure fontconfig-config but still no dice :( I cant see them in gnome font selector.
how the hell did you manage to install this on feisty ?
thx in advance.

---

### Post by dbbolton on 2007-07-31
> **ayoli said:**
> hi,
i cant manage to install these fonts on feisty.
i tried to make the dir /usr/lib/X11/fonts/misc but it was deleted after package reinstall.
After a look to the package contents, i saw that the fonts were installed in /usr/share/fonts/X11/misc so i made a link in /usr/lib/X11/fonts/ then reconfigure fontconfig-config but still no dice :( I cant see them in gnome font selector.
how the hell did you manage to install this on feisty ?
thx in advance.
try installing the package with dpkg and check the output.

they are working fine for me, and they are located in '/usr/share/fonts/X11/misc'

i got this to work just by following my first post several times. i had to restart my computer a couple of times too. i have no idea why, but it finally just worked.

---

