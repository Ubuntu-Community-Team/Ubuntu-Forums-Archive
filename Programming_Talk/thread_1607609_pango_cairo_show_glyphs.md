---
title: "pango_cairo_show_glyphs"
date: 2010-10-28
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-28
GdkFont is deprecated and should not be used in newly-written code.

gdk_draw_text has been deprecated since version 2.4 and should not be used in newly-written code. Use gdk_draw_layout() instead.

gdk_draw_layout is deprecated and should not be used in newly-written code.

gdk_draw_glyphs has been deprecated since version 2.22 and should not be used in newly-written code. Use pango_cairo_show_glyphs() instead.

gdk: Deprecate all drawing functions

These functions will be gone in Gtk 3.0 and be replaced by Cairo
functions.

...
but where does one find documentation on pango_cairo_show_glyphs et. al... even Google doesn't know either :P

---

### Post by worksofcraft on 2010-11-09
Anyone else trying to plot glyphs on a drawing area has probably run into this same brick wall that I did. ](*,) but there are many reasons for wanting to accurately control glyph positioning. e.g. to put annotations on schematic drawing, to make a cool image with text in it, or in my case to make a simple terminal emulator that renders them on a fixed pitch grid.

A very useful bit of code for exploring the higher level abstractions of bidirectional text was contributed [in post #5 on this thread]("http://ubuntuforums.org/showthread.php?t=1616067") and it only served to convince me that I really **DO** want to have control of which direction bidirectional text gets plotted rather than submitting to the Unicode stupidity - oops I mean standard. 

I found a document on the web "[State of Text Rendering]("http://behdad.org/text/")" and as far as I can tell the level I need to interface is called [HarfBuzz]("http://www.freedesktop.org/wiki/Software/HarfBuzz"). Everything else has been "deprecated" but alas it says: "There are no releases available for download yet, but we expect to start 0.x release soon and aim for a 1.0 release with stable API around March 2011." and I can't find so much as provisional  documentation on the web.

My choice has been to cut straight back to the freetype API and you can read [more about that on my r2l thread]("http://ubuntuforums.org/showthread.php?p=10031999#post10031999") and I might even post some updates there when I make some more progress ;)

---

