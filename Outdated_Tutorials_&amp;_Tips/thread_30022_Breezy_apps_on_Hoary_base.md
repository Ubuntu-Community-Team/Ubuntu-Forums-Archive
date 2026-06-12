---
title: "Breezy apps on Hoary base?"
date: 2005-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by closure on 2005-04-26
I read on another thread that more current versions of common apps such as firefox & gaim are in the breezy repositories. is it possible and functional to link to the breezy repos JUST for apps and retain the more stable hoary base?

---

### Post by TravisNewman on 2005-04-26
possible, but with the potential to mess things up.

I'd suggest using the backports (see 3rd party forums), which also has firefox and gaim at their current version.

---

### Post by XDevHald on 2005-04-26
To answer it in a small based layout...

Go here --> [http://backports.ubuntuforums.org]("http://backports.ubuntuforums.org") And check out the placed information guided for you. Then...

if you want FireFox 1.0.3 and the New Gaim, Gimp, etc...

 [PHP]sudo gedit /apt/sources.list[/PHP] 

And place this text in there at the bottom of that page.

 [PHP]deb  http://backports.ubuntuforums.org/backports warty-backports main universe multiverse restricted 
deb http://backports.ubuntuforums.org/backports warty-extras main universe multiverse restricted[/PHP] This is the UbuntuForums backports in which are all mainly requests from users such as yourself that have asked for applications and more to be added so they can grab them much quicker.

If you have any questions, feel free to post'em :)

---

### Post by closure on 2005-04-26
[QUOTE=panickedthumb]possible, but with the potential to mess things up.

I'd suggest using the backports (see 3rd party forums), which also has firefox and gaim at their current version.[/QUOTE]
2 people on IRC said that if i plan to upgrade to breezy i should not use backports as it will affect the upgrade? is this true? backports does not update my base at all does it?

---

### Post by TravisNewman on 2005-04-26
jdong provides backports upgrades as well-- when you decide to upgrade to breezy, change from hoary backports to breezy backports. You may have to wait longer than you'd like to do this.

You can also just uninstall any backports and then upgrade.

---

### Post by closure on 2005-04-26
[QUOTE=panickedthumb]jdong provides backports upgrades as well-- when you decide to upgrade to breezy, change from hoary backports to breezy backports. You may have to wait longer than you'd like to do this.

You can also just uninstall any backports and then upgrade.[/QUOTE]
how would i go about knowing what apps are upgraded by backports and which ones official?

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=closure]how would i go about knowing what apps are upgraded by backports and which ones official?[/QUOTE]


The packages that are backports have ubp in the name.

---

