---
title: "[pygtk] How to use the gtk color constants?"
date: 2008-10-14
forum: Programming Talk
---

### Post by days_of_ruin on 2008-10-14
like fg[Normal] etc...The colors that all the widgets use.Defined in
the gtkrc.I know some programs have text that use gtk color constants and
I want to know how.:guitar:

---

### Post by loell on 2008-10-14
probably

```

map = e.get_colormap()
 colour = map.alloc_color("green")
```

---

