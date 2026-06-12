---
title: "Ruby GTK+ pictionary drawing problems"
date: 2007-11-20
forum: Programming Talk
---

### Post by Completenutter2 on 2007-11-20
Hi,

I am attempting to write a cross-platform Pictionary style game in Ruby using GTK+.

Using a drawing area and a pixmap, I've managed to get drawing working on the screen. My problems comes when I want to make the size of the line bigger.

I've managed to do it, but, either I'm missing something, or the way I'm drawing is seriously flawed.

My idea was to store the 'old' mouse position, and then draw a line from the old position to the current position when the mouse moves. This works fine when the size is left at the default, but when I increase it, things start going horribly wrong.

First of all, if I move the mouse slowly, the line is drawn exactly like it was before I changed the size, and I can only make it bigger by moving the mouse quicker, and even then, you can see the separate lines that I'm drawing.

[IMG]http://aycu34.webshots.com/image/33713/2002786654404130434_rs.jpg[/IMG]

The guilty lines of code:
```

@pixmap.draw_line(@graphics_context, @last_x.to_i, @last_y.to_i, x, y)

def setupGC()
    @graphics_context = Gdk::GC.new(self.window)
    @graphics_context.set_rgb_fg_color(Gdk::Color.new(65535,0,0))
    @graphics_context.set_line_attributes(10, Gdk::GC::LINE_SOLID, Gdk::GC::CAP_NOT_LAST, Gdk::GC::JOIN_ROUND)
  end

```


This is not a Ruby issue at all, I just think I'm missing something to do with GTK+ and would appreciate a gentle nudge in the general direction. Hours of searching google to no avail has lead me to posting here.

Thanks to anyone who can help.

---

### Post by finer recliner on 2007-11-20
i dont know much about GTK. but doing a quick google for that function gives me this page
[https://libre.adacore.com/GtkAda/docs/2.8/gtkada_rm/gdk-gc.html](https://libre.adacore.com/GtkAda/docs/2.8/gtkada_rm/gdk-gc.html)

there is says that the the function "Set_Line_Attributes" takes in 4 parameters. the third one specifies how the line should end, either flat or rounded.
the forth one specifies how two consecutive lines are connected.

so i suggest playing around with those two parameters and see if that gives more accpetable results.

---

### Post by Completenutter2 on 2007-11-20
I have seen those, and I've played around with them, and I couldn't see a difference.

I'll have another go at it when I get back home.

---

### Post by Completenutter2 on 2007-11-21
Tried all possible combinations of those, didn't make a difference :(

---

### Post by Completenutter2 on 2007-12-04
Had nobody got any ideas how to help me with this? :(

---

### Post by Majorix on 2007-12-04
Have you also tried fxRuby? That's another GUI toolkit and as you might guess there is not much to learn from toolkit to toolkit.

---

