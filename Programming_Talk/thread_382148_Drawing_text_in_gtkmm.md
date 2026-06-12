---
title: "Drawing text in gtkmm"
date: 2007-03-11
forum: Programming Talk
---

### Post by evster on 2007-03-11
Hello,

I am writing an applications in gtkmm.  I am currently working on building a custom widget which I hope can be done with a DrawingArea.  So far everything is going good, but I need the ability to draw numbers on the DrawingArea.  The documentation I have found is pretty confusing about how to do this.  I am doing my drawing with a cairo context that I got with the call: 
```
Cairo::RefPtr<Cairo::Context> cr = window->create_cairo_context();
```

But I can't seem to figure out how I could draw some simple text with this context.

Any help is much appreciated!
Thanks
evster

---

### Post by lnostdal on 2007-03-11
have you seen [http://www.cairographics.org/manual/cairo-Text.html](http://www.cairographics.org/manual/cairo-Text.html) and [http://www.cairographics.org/manual/Fonts.html](http://www.cairographics.org/manual/Fonts.html) ..?

---

