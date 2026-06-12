---
title: "Gnome 3.2 nautilus + sushi"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zacbarton on 2011-09-27
Anyone know if sushi will be available in 11.10?

[http://blogs.gnome.org/cosimoc/2011/04/29/sushi/](http://blogs.gnome.org/cosimoc/2011/04/29/sushi/)

I found a bug report asking to get it packaged - [https://bugs.launchpad.net/ubuntu/+bug/829277](https://bugs.launchpad.net/ubuntu/+bug/829277)

---

### Post by jbicha on 2011-09-27
Good question. Unfortunately, it looks quite unlikely for 11.10 but I'm sure it'll be packaged for 12.04.

I haven't even seen a Debian/Ubuntu package for it yet. Same with gnome-documents.

---

### Post by bash on 2011-09-27
Since we are already on the topic of new 3.2 features/packages: Any idea if gnome-contacts will land in 11.10?

---

### Post by zacbarton on 2011-09-27
> **bash said:**
> Since we are already on the topic of new 3.2 features/packages: Any idea if gnome-contacts will land in 11.10?

You'll find gnome-contacts is already available.

---

### Post by zacbarton on 2011-10-02
[www.webupd8.org](www.webupd8.org) has created a PPA for sushi

[http://www.webupd8.org/2011/10/install-sushi-gnome-32-nautilus-quick.html](http://www.webupd8.org/2011/10/install-sushi-gnome-32-nautilus-quick.html)

---

### Post by mc4man on 2011-10-02
> **zacbarton said:**
> [www.webupd8.org](www.webupd8.org) has created a PPA for sushi

[http://www.webupd8.org/2011/10/install-sushi-gnome-32-nautilus-quick.html](http://www.webupd8.org/2011/10/install-sushi-gnome-32-nautilus-quick.html)Works pretty well, for A/V files as long as you have gstreamer supported installed it should be good
(note it won't warn if support is missing

---

### Post by alecive on 2011-10-03
> **zacbarton said:**
> [www.webupd8.org]("http://www.webupd8.org") has created a PPA for sushi

[http://www.webupd8.org/2011/10/install-sushi-gnome-32-nautilus-quick.html](http://www.webupd8.org/2011/10/install-sushi-gnome-32-nautilus-quick.html)

The link was removed and the page is dead :(

---

### Post by mc4man on 2011-10-03
> **alecive said:**
> The link was removed and the page is dead :(
It seems the article & all the packages from the ppa have been removed without comment, interesting

---

### Post by karmila on 2011-10-03
> **mc4man said:**
> It seems the article & all the packages from the ppa have been removed without comment, interesting

This is his explanation:
        > A debian maintainer asked me 
to remove it because the package in Debian (and Ubuntu, when it will be 
uploaded, probably in 12.04 but anyway) might be renamed and then it 
would cause errors when trying to install the new package.

on a comment at this post [http://www.webupd8.org/2011/10/gnome-shell-global-menu-instructions.html](http://www.webupd8.org/2011/10/gnome-shell-global-menu-instructions.html)

---

### Post by jbicha on 2011-10-06
gnome-sushi will be in the Oneiric archives within the next few hours. Thanks to bjsnider for the help!

If you've previously installed from a PPA, you'll probably need to completely uninstall it and its libraries or you'll have conflicts.

---

### Post by dino99 on 2011-10-06
i've installaed the oneiric repo packages and got:

- viewing xsession-error (text file) works (135 kb)
- viewing a crash file: the loader seem freezed, never get loaded (398 kb)

dont find errors/warnings logged

---

### Post by thatguruguy on 2011-10-06
> **jbicha said:**
> gnome-sushi will be in the Oneiric archives within the next few hours. Thanks to bjsnider for the help!

If you've previously installed from a PPA, you'll probably need to completely uninstall it and its libraries or you'll have conflicts.

I got it, and it's working fine here.

---

### Post by philinux on 2011-10-06
> **thatguruguy said:**
> I got it, and it's working fine here.

Same here just came through.

Had to read the blurb.

Left click file and hit space to activate.

---

### Post by nrundy on 2011-10-06
I've not been able to get thumbnails of videos to show. Will Sushi have any effect on this? Or is it only a preview when pressing space-bar?

---

### Post by gexi on 2011-10-06
it's fast and working great.

only two downsides (for now) are:
- it doesn't seem to care about the window-button position of the current theme
- it seems to have some theming problems. in ambiance for example, it is drawing a white square around the window-button (adwaita works fine). also the window title is very pallid.

---

### Post by philinux on 2011-10-06
> **nrundy said:**
> I've not been able to get thumbnails of videos to show. Will Sushi have any effect on this? Or is it only a preview when pressing space-bar?

Works here. Like I said you have to left click to select the item and the space bar.

And indeed the X button is on the right lol as Gexi inferred.

---

### Post by anders_c_ on 2011-10-06
Amazing! Works great and i find it very useful.
Does anyone know if i can make it start in fullscreen?

---

