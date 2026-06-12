---
title: "Something's wrong with Gtk::DrawingArea"
date: 2008-06-23
forum: Programming Talk
---

### Post by xlinuks on 2008-06-23
Hi,
I'm working with Gtk with C++,
I have a window that has two components
1) Upper one - a little red component like a toolbar.
2) Lower one - the big DrawingArea onto which I draw the core stuff.
For some reason between them appears a gap (of gray color) equal to the height of the upper red component (let's call it "toolbar"), like on the screenshot.
The interesting thing is that if I make the class that extends DrawingArea to extend HBox (and paint on the HBox rather than on a DrawingArea) the gray area disappears without modifying anything else. So I think there's something special about the DrawingArea class.

Painting on the HBox is fine, but the HBox seems not to receive button clicks, so I have to either solve the mouse clicks issue with HBox or solve the gray area issue of the DrawinArea.
Any help would be appreciated, a attached the screenshot and the NetBeans project (the code is a bit cumbersome since I'm only learning C++).

---

