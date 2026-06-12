---
title: "[Gtkmm] Get string width with Pango"
date: 2010-12-30
forum: Programming Talk
---

### Post by t1497f35 on 2010-12-30
Hi folks,
I'm using Pango to draw strings on a DrawingArea through Cairo.
Say I have a string "hello world", how do I calculate its width using Pango?

Solved:
Glib::RefPtr<Pango::Layout> layout = Pango::Layout::create(cr);
layout->set_text("hello world");
int stringWidth, stringHeight;
layout->get_pixel_size(stringWidth, stringHeight);

---

### Post by worksofcraft on 2010-12-30
> **t1497f35 said:**
> Hi folks,
I'm using Pango to draw strings on a DrawingArea through Cairo.
Say I have a string "hello world", how do I calculate its width using Pango?

Solved:
Glib::RefPtr<Pango::Layout> layout = Pango::Layout::create(cr);
layout->set_text("hello world");
int stringWidth, stringHeight;
layout->get_pixel_size(stringWidth, stringHeight);

Hey... thanks...
I was just looking for that :)

I'm kind of wondering how it knows what font will be used and all that malarkey because it must make a difference in the result.

---

