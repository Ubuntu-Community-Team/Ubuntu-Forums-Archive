---
title: "Is it me or is Gnome very developer-unfriendly?"
date: 2007-08-06
forum: Programming Talk
---

### Post by mostwanted on 2007-08-06
The Gtk+ C tutorial is pretty much the only 100% done Gnome tutorial. In all other areas of Gnome development (other programming languages, other essential APIs, etc.) I've yet to find substantial documentation. Gnome feels very alienating to a hobbyist programmer such as myself. KDE seems to be doing a better job, but I haven't really looked that much into apart from a few Google searches.

Am I just imagining this?

---

### Post by Lord Illidan on 2007-08-06
I also second this...gnome documentation is pretty sparse..

---

### Post by AlexThomson_NZ on 2007-08-06
Yep I agree 100%.  I have ranted on this too...

And don't even get me started with gtkmm and libglademm too!

---

### Post by walkerk on 2007-08-06
I agree but I don't think this will change anything :)

---

### Post by AlexThomson_NZ on 2007-08-06
> **walkerk said:**
> I agree but I don't think this will change anything :)

Good point!

Now for some positivity- maybe we should note what we would like to see, then work towards implementing it.

Personally, I would like to see:
 * More simple tutorials on EVERY widget
 * Better GtkTreeView documentation (ideally a better way of implementing this entirely!)
 * Better documentation on creating a gtk applications from scratch (which libs are required, makefile, etc.)
 * More UP-TO-DATE information- particularly regarding obsolete components
 * Better structured OFFICIAL on-line documentation.  At the moment, it is all links to links that either go to extremely out-of-date info, 404 pages, or the same Gtk tutorial (you know the one- tic-tac-toe, scribble...)

Any other thoughts?

---

### Post by vambo on 2007-08-06
> **AlexThomson_NZ said:**
> Good point!

Now for some positivity- maybe we should note what we would like to see, then work towards implementing it.

Personally, I would like to see:
 * More simple tutorials on EVERY widget
 * Better GtkTreeView documentation (ideally a better way of implementing this entirely!)
 * Better documentation on creating a gtk applications from scratch (which libs are required, makefile, etc.)
 * More UP-TO-DATE information- particularly regarding obsolete components
 * Better structured OFFICIAL on-line documentation.  At the moment, it is all links to links that either go to extremely out-of-date info, 404 pages, or the same Gtk tutorial (you know the one- tic-tac-toe, scribble...)

Any other thoughts?

A half decent set of man pages wouldn't go amiss.

---

### Post by Jessehk on 2007-08-06
KDE is amazing (from my perspective anyways) because of its Qt base (which is seems to be very well made) and because they take documentation very seriously. They also seem to have more of a vision then the GNOME people.

Honestly, the only reason I don't use KDE is its lack of usibility and polish, though I suspect that will change in KDE 4.

---

### Post by AlexThomson_NZ on 2007-08-06
Jessehk, I am in exactly the same boat.  A few days ago, I all but threw in Gnome and started with KDevelop.  Unfortunately the 'lack of polish' just drove me crazy, and I found myself back with gnome!  I will give KDE4 a serious look though...

---

### Post by kknd on 2007-08-06
Agreed!

The only good documentation that I know of is GTK and gtkmm.

---

### Post by pmasiar on 2007-08-06
Why you guys don't start a wiki with any good links you found? Each of you have some, and if you share each of you will get more. You can get free wiki at pbwiki.com (as in my sig)

---

### Post by j_g on 2007-08-06
I think that KDE is very unfriendly to a C developer. For some reason, the KDE developers made the unfortunate decision to tether development to C++, and therefore make it unusable with other languages (unless you make some sort of custom wrapper in C++).

But on the matter of Gnome documentation, yes, it is in need of major reworking (ie, better organization of material, updating of some obsolete tutorials, and much more indepth tutorials for what few articles can be found).

---

### Post by AlexThomson_NZ on 2007-08-06
> **pmasiar said:**
> Why you guys don't start a wiki with any good links you found? Each of you have some, and if you share each of you will get more. You can get free wiki at pbwiki.com (as in my sig)

Unfortunately we don't- I know of only one site- the official GTK site, that has a few (2 samples) and a few pages of widget examples.  This page is pretty outdated too, and doesn't provide any examples using libglade, which is pretty much a must now.

I would be happy to contribute to a how-to wiki though, except I have no idea if my approach, or code is at all acceptable, you know, on account of there being no docs! ;)

---

