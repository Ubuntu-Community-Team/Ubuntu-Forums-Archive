---
title: "Multiple wall papers gnome shell."
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kmsalex on 2011-09-11
Been doing some googling and haven't found much, and what I have isn't quite what I want.

Is there a way to have a diffrant wallpaper for every new desktop gnome  shell creates (the first few i'd chose and maby random after like 5).  The way i've seen this done in unity is to, well first be using unity,  and second using compiz. Neither of which fits my description :/

So can this be done on a gnome (3.1x) oneric 64 bit desktop?

---

### Post by Harry33 on 2011-09-11
Hmm, I cannot even change a single background wallpaper with gnome-control-center:
Opening "System Settings", then "Appearance", but it won't even start.

So I have to change the file from the .cache/gnome-control-center/backgrounds/

---

### Post by VinDSL on 2011-09-11
> **Harry33 said:**
> I have to change the file from the .cache/gnome-control-center/backgrounds/
Heh!  I've resorted to using Nautilus.

[LIST]
[*]Find the wall with "Nautilus"
[*]Right-click wall -> "Open With Image Viewer"
[*]Then "Image" -> "Set as Desktop Background"
[/LIST]

It's a ghetto workaround, but it's the easiest way I've found. :)

---

### Post by VinDSL on 2011-09-11
> **kmsalex said:**
> Is there a way to have a diffrent wallpaper for every new desktop gnome shell creates[...]?
Not AFAIK.

There's probably a way of doing it using 'Feh', but you would need a pretty good understanding of the underpinnings of the UI to succeed.

---

### Post by jbicha on 2011-09-12
I suspect you'd be interested in this ancient [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=48004").

---

### Post by VinDSL on 2011-09-12
> **jbicha said:**
> I suspect you'd be interested in this ancient [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=48004").
Bwahahaha!  10 year-old bug report.

That's hilarious!

---

### Post by kmsalex on 2011-09-12
If I realy wanted this to work could I even use compiz while gnome shell is running?

---

### Post by cariboo on 2011-09-12
Compiz and mutter don't work together.

---

