---
title: "Gnome-/Unity Panel wrong colour"
date: 2011-05-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Jack9099 on 2011-05-27
After minimally installing ubuntu 11.10 and then gdm and the ubuntu-desktop packages the panel is plain and grey.
Any help, as to get the normal panel would be appreciated :D

---

### Post by Framli on 2011-05-27
It's perfectly normal, Oneiric is now mostly running with GTK+3. The current version of the Ambiance theme is still GTK+2 only and will be fully ported during the cycle.
Here is a quick how-to to take a peek at what is being done for Ambiance GTK+3 [http://ubuntuforums.org/showpost.php?p=10842422&postcount=46](http://ubuntuforums.org/showpost.php?p=10842422&postcount=46)

---

### Post by Quadunit404 on 2011-05-27
Why don't they just use Adwance? Someone had already ported Ambiance to GTK3 under the name Adwance.

---

### Post by ranch hand on 2011-05-27
Looks better.

---

### Post by Jack9099 on 2011-05-27
ahh cheers, I've been sat here for an hour trying to compile the gnome-appearance-properties and it's just not working out :')

---

### Post by screaminj3sus on 2011-05-27
> **Quadunit404 said:**
> Why don't they just use Adwance? Someone had already ported Ambiance to GTK3 under the name Adwance.

Adwance is certainly not quality enough for a default theme. The nautilus breadcrumbs look atrocious for example.

---

### Post by Quadunit404 on 2011-05-27
I suppose so, as I had tried it out and the breadcrumbs in Nautilus looked terrible. The rest looked normal though.

Since GTK3 uses CSS it should be possible to make the breadcrumbs look normal by tweaking the values in the theme's gtk.css (or is it gtk-widgets.css? I haven't really bothered to check tbh.) I'll see if editing one of those two files gives me better thumbnails.

EDIT: Reading the comments on the Adwance entry on deviantART, the author of the theme IS going to try improving things like tabs and breadcrumbs. He will not try to recreate Ambiance exactly as it is because he is certain that Canonical is porting the theme to GTK3.

---

### Post by CreativeReach on 2011-05-30
that will be awsome to have a "real" Ambiance in GTK3!

---

### Post by dino99 on 2011-05-30
how to change/set/tweak themes now ? (system prefs appearance is gone)

---

### Post by MacUntu on 2011-05-30
It's my understanding that lucazade is working on the official Ambiance port.

[https://code.launchpad.net/~lucazade/+junk/ambiance-gtk3](https://code.launchpad.net/~lucazade/+junk/ambiance-gtk3)

---

### Post by lucazade on 2011-05-30
> **MacUntu said:**
> It's my understanding that lucazade is working on the official Ambiance port.

[https://code.launchpad.net/~lucazade/+junk/ambiance-gtk3](https://code.launchpad.net/~lucazade/+junk/ambiance-gtk3)

Yes, I'm porting the Ambiance gtk3 theme..
at the moment both Unico engine and theme  are under development, we'll see in the next months how things will evolve.

---

### Post by MacUntu on 2011-05-30
Looks fine so far, just needs some spit and polish. I just went back to Adwaita because certain applications failed to open with Unico/Ambiance ([https://bugs.launchpad.net/unico/+bug/789010](https://bugs.launchpad.net/unico/+bug/789010)).

Does it make sense to already report such things?

---

### Post by Framli on 2011-05-30
MacUntu, one crasher is already fixed in trunk.
[https://bugs.launchpad.net/unico/+bug/789010](https://bugs.launchpad.net/unico/+bug/789010)

---

### Post by lucazade on 2011-05-30
> **MacUntu said:**
> Looks fine so far, just needs some spit and polish. I just went back to Adwaita because certain applications failed to open with Unico/Ambiance ([https://bugs.launchpad.net/unico/+bug/789010](https://bugs.launchpad.net/unico/+bug/789010)).

Does it make sense to already report such things?

Yes, of course.
Unfortunately gtk3-engines-unico package has not been updated in OO repos after that bug was fixed, so new gnome control center still crash. At the moment only way to work around the  issue is to build engine from bzr repo.

This plugin for gedit could help css theme development, I shoud try it :)
[http://libregraphicsworld.org/news.php?readmore=792](http://libregraphicsworld.org/news.php?readmore=792)
[http://lanedo.com/~carlos/gedit-cossa-demo.webm](http://lanedo.com/~carlos/gedit-cossa-demo.webm)

---

### Post by T.Ephraim on 2011-09-01
Hey,

my unity panel looks exactly like the screenshot of the first post.
Ambiance theme stopped working since 2 days now, I think it happend when the appearance ui first appeared in the control center.

Have I screwed it up somehow, or is it a oneiric bug?

I double checked the dconf and gconf stuff via the editors. The window theme is used correctly, but the GTK+-, Icon- and Cursor-Theme are ignored.

Ciao 
Ephraim

---

### Post by T.Ephraim on 2011-09-01
Ok works again :).
I'm not sure what repaired it but here is what I did more or less.
All these commands I entered in the console (Ctrl+Alt+F1)

All these commands intend to reset any configuration I probably set wrong/deleted. Take care it removes some stuff which you migth don't want to be removed!!!!!

sudo stop lightdm
sudo apt-get remove unity-services
sudo apt-get install ubuntu-desktop
sudo gconftool-2 --recursive-unset /apps/compiz-1
sudo gconftool-2 --recursive-unset /apps/compizconfig-1
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm -r ~/.local
rm -r ~/.gtk*
rm -r ~/.gnome2*
rm -r ~/.dbus
rm -r ~/.config/dconf
rm -r ~/.config/compiz-1
rm -r ~/.config/gnome-session
rm -r ~/.cache
sudo start lightdm


Ciao
Ephraim

---

