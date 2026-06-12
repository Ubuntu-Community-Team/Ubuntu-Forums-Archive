---
title: "recursive function drawing"
date: 2011-04-21
forum: Programming Talk
---

### Post by vivichrist on 2011-04-21
can anyone suggest a good library for recursive function drawing with c++. I have tried a few but my approach is all wrong and documentation is scant. I just want an object that I can call simple object.draw_line(x ,y, nx, ny); and hand said object to the next recursive call or is member of this class etc. cairo gives me segfaults, Gtk::GC and GtkDrawingArea do the same. I am at my wits end.

---

### Post by simeon87 on 2011-04-22
Do you mean that functions are recursively calling themselves or that each function returns an object upon which the next function can be called, such as:

```
draw_line(10, 10, 100, 100).draw_rect(50, 30, 40, 40).draw()
```

While convenient in writing, why specifically do you need this feature? The Gtk DrawingArea and Cairo can be used together to draw what you want although it doesn't allow you to write the code like that.

Having said that, I wouldn't know a library that could do this.

---

### Post by vivichrist on 2011-04-24
[http://ubuntuforums.org/showthread.php?p=10708762&styleid=109#post10708762]("http://ubuntuforums.org/showthread.php?p=10708762&styleid=109#post10708762")
I was having trouble with C++ math causing seg faults and infinite recursion. I'm use to Java and not accustomed to being able to compile code that can so easily break but leave me scratching my head as to why. I need to master debugging and polymorphism. I did get recursion to work on a Cairo::RefPtr<Cairo::Context> with grand results and much higher quality than with the java graphics object. now I must ponder how to animate cairo or try some other library. I have made recursive tree graphics and now I want to show them growing.

[http://ubuntuforums.org/showthread.php?t=1748955]("http://ubuntuforums.org/showthread.php?t=1748955")

---

