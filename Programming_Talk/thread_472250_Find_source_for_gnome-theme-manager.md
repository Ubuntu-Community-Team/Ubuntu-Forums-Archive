---
title: "Find source for gnome-theme-manager"
date: 2007-06-12
forum: Programming Talk
---

### Post by martinrandau on 2007-06-12
Hi!

I have some programming ideas on the gnome-theme-manager that I'd like to try out. The problem is that I can't find the source anywhere. Can someone please direct me on where to get the source for this application?

---

### Post by odiseo77 on 2007-06-12
Hi, have you tried: [http://www.gnome.org/start/2.18/](http://www.gnome.org/start/2.18/) ? (scroll to the botton of the page, there are several sources categories there).

Regards.

---

### Post by martinrandau on 2007-06-12
Thanks for your reply!

Yeah, that was the first place I looked (should have told you). I can find gnome-themes there but I don't think the theme-manager is in there.

---

### Post by odiseo77 on 2007-06-12
I think the gnome-themes-manager program is part of the gnome-control-center package (at least it is on ubuntu), so you could try the 'control-center' sources (it's under the 'Desktop sources' category).

Greetings.

---

### Post by martinrandau on 2007-06-13
Thanks! Yes, that's definitely the correct source.

I realized I could do ```
sudo apt-get source gnome-control-center
``` to get the ubuntu version of it.

---

