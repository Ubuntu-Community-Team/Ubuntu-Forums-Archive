---
title: "How to remove Gnome 3 Extensions?"
date: 2011-06-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xxhopingtearsxx on 2011-06-03
I downloaded some eyesore extensions for Gnome 3 like a Dock that goes on the right of my screen, and on my menubar there's buttons of my favorite programs. No way to get rid of it, which bothers me especially since it's pointless since I can just go to Applications.

I don't know how to get rid of this.. Can someone help? I removed some extensions on Ubuntu Software Center but I still have the dock and menubar icons. (I downloaded the dock from Ubuntu Software Center from a Test PPA btw)

Please help?

---

### Post by cecilpierce on 2011-06-03
take a look in /home/.local/share/gnome-shell/extensions or /usr/share/gnome-shell/extensions, thats where it was hiding for me.

---

### Post by cariboo on 2011-06-03
If you installed from a ppa, use ppa-purge to remove what you installed, it's in the repositories.

---

### Post by mc4man on 2011-06-04
Gnome-shell could use an extension manager extension or some means to enable, disable other than removing, moving, or renaming

---

### Post by uBeer on 2011-06-04
I believe that you can do that now already with gnome-tweak-tool. With that tool you can enable/disable extensions, tweak fonts, themes, etc.

---

### Post by ronacc on 2011-06-06
what PPA did you use ? I tried the Ricotz PPA and they installed but would not take effect , I also tried localy compiling the extensions , again they installed but didn't work .I would like to try them and see if they make things a little more palatable for me , it is really annoying me to have to hold the alt key to shut-down/reboot the machine.I'm running a fully up to date oneric (64bit) . alternately what file do I have to hack to change the top rightmost menu .

---

### Post by mc4man on 2011-06-09
It would seem at this point some extensions work, others don't, and some 3rd party ones will prevent gnome-shell from even opening 

From the so called ['official' ones]("http://live.gnome.org/GnomeShell/Extensions") - all work here except the 'app menu one'

One of the possibly useful ones - 'Places Menu Status Indicator' seems to work fine for a bit, it opens places, bookmarks and mounted drives from the dropdown in the indicator area icon.
The problem here is that if one then opens any dir. from the r. right context with anything but nautilus than the extension will start using that app instead of nautilus. (gnome-shell itself correctly stays w/ nautilus
(- a new variation of the old issue in nautilus about folder-handler

---

