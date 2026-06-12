---
title: "weird class related gtk segfault and mouse alignment problem"
date: 2008-12-24
forum: Programming Talk
---

### Post by blake82 on 2008-12-24
Hi everyone,

I'm writing a multichannel audio program using gtk for the ui. I've created a class for the controls of each audio channel, sice a static ui wouldn't make sense for this.

However, the gui is doing 2 very bad things

1.  When I call functions that change values of GUI elements that are contained in classes, the program will eventually seg fault. Not immediately though

2. I can't select any of the hscale handles with my mouse, it seems like the mouse alignment is off.

Both these problems go away when I create hScales WITHOUT using classes. Is there a known problem from using classes to instance groups of controls?

Here's how the hScale is defined:

```
FX2bFader = gtk_hscale_new_with_range(-1, 1, .02);
            gtk_scale_set_value_pos(GTK_SCALE(FX2bFader), GTK_POS_BOTTOM);
            gtk_widget_set_size_request(FX2bFader, 70, 300);
            gtk_fixed_put(GTK_FIXED(guiFrame), FX2bFader, (localX + 5), (localY + hsclStart + (hsclSpace * 8)));
            gtk_range_set_value(GTK_RANGE(FX2bFader), 0);
```

I'm using c++ and the gtk+ 2.0 library and header files.

I feel like there's something really simple I'm missing here, but I've been trying to figure this out for several days now with no luck.

I've tested both functions on widgets that are NOT contained in a class, and there's no problem whatsoever

But why would using classes cause problems? The class instances just contain pointers (as far as I know) to the widgets, and all pointers are in the private part of the class, as far as gtk knows, I'm just making a bunch of widgets... so why are there eventually illegal memory operations when I use classes???

Sorry for the long post, but thanks for reading.:popcorn:

-Blake

---

