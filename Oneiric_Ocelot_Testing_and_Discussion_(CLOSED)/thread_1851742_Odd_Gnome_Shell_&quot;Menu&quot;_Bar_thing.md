---
title: "Odd Gnome Shell &quot;Menu&quot; Bar thing"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fillmont on 2011-09-28
So I finally got around to switching my Gnome Shell theme, and noticed something odd. Take a look at this screenshot:

[IMG]http://img15.imageshack.us/img15/3513/screenshotat20110928203.png[/IMG]

The Gnome Shell "Menu" bar has an odd overlay with what looks to be a nautilus menu. The Nautilus menu isn't at all functional - it's just kinda there.

---

### Post by effenberg0x0 on 2011-09-28
**EDIT:** 
Previous code worked on Unity, not GS... Best shot = gnome-tweak-tool I guess. Or playing around with gconf-editor.

Regards,
Effenberg

---

### Post by fillmont on 2011-09-28
Thanks for the attempt, but the given code was a no go. Still has the funky nautilus background. 

Poking around gnome tweak tool now.

---

### Post by cariboo on 2011-09-28
If you don't use Unity, you can remove appmenu-gtk and appmenu-gtk3, that should remove the nautilus menu bar.

---

### Post by fillmont on 2011-09-28
> **cariboo907 said:**
> If you don't use Unity, you can remove appmenu-gtk and appmenu-gtk3, that should remove the nautilus menu bar.

I found that this didn't work either.

What did work, though, was effenberg's suggestion of using gnome tweak. Worked like a charm!

I guess the follow-up question would be: what do I lose by not having nautilus control my desktop? So far functionality seems the same.

---

### Post by xyzzyman on 2011-09-29
Sorry as it's off topic, but is that bird pouncing on pedo bear?

---

### Post by jbicha on 2011-09-29
Besides drawing desktop icons, Nautilus also provides the right-click option to change your background. Of course, the background can also be changed in System Settings>Appearance.

---

### Post by crdlb on 2011-09-29
Also note that nautilus drawing the desktop is supposed to be disabled by default for Gnome 3 anyway. If you do want desktop icons, you probably just needed to restart nautilus after you removed the appmenu-gtk3 plugin.

---

### Post by fillmont on 2011-09-29
> **xyzzyman said:**
> Sorry as it's off topic, but is that bird pouncing on pedo bear?

Heh, nope. It is Beatato and Reginald, from the webcomic [Nedroid]("http://www.nedroid.com"). It comes highly recommended by me, a stranger from the internet. 

> **jbicha said:**
> Besides drawing desktop icons, Nautilus also provides the right-click option to change your background. Of course, the background can also be changed in System Settings>Appearance.

Ah, I see! Yea, not a major feature loss, but it would be nice to get those back...

> **crdlb said:**
> Also note that nautilus drawing the desktop is supposed to be disabled by default for Gnome 3 anyway. If you do want desktop icons, you probably just needed to restart nautilus after you removed the appmenu-gtk3 plugin.

...and hey, this totally worked! I've got right clickability and no phantom menu. This forum is quite good, I say. 

Thanks everyone for your help!

---

