---
title: "custom widgets in qt how to??"
date: 2009-07-12
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-12
if i want to create some electronics widgets like adder,logic gates and circuits, how can i create and use in Qt, 
there are lot of documentation when i searched, but i din't find what i needed, 
so please anyone could provide me link or tell how to make and use custom widgets, also can we save those widgets in standard toolbar in Qt designer??

---

### Post by abhilashm86 on 2009-07-14
well i found out that these widgets can be done using Qgraphics with Qpaint system in qt, well this seems to much of coding and stuff, do i have any other alternative??

---

### Post by monraaf on 2009-07-14
Use GTK+ with goocanvas :-)

---

### Post by abhilashm86 on 2009-07-14
> **monraaf said:**
> Use GTK+ with goocanvas :-)

is that in-built in Qt, actually how should i use this??

---

### Post by JordyD on 2009-07-14
> **abhilashm86 said:**
> is that in-built in Qt, actually how should i use this??

GTK+ is a different toolset. Qt is what KDE uses natively and GTK+ is what GNOME uses natively. I don't think you can use them together without trouble. Plus, then your program would require the user to install both Qt and GTK+.

I can't say anything about the actual widget since I've never used it.

---

