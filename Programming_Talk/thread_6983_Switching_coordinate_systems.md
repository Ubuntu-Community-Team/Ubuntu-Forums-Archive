---
title: "Switching coordinate systems?"
date: 2004-12-03
forum: Programming Talk
---

### Post by HungSquirrel on 2004-12-03
Sorry for the vague title, I wasn't sure how to word this in so few characters!  This pertains to Java, but if you're a non-Java person, pseudocode, etc. would really help me out.

The origin for a Java Graphics area is the top-left corner.  The data I am given to plot on the Graphics area (northwestern hemisphere latitude and longitude coordinates) have a bottom-right origin (for example, see [this map](http://www.kabb.com/weather/hurricane/Hurricane.gif)).

Is there any way somebody could nudge me in the right direction on writing a method that will take the data I am given and "switch" it to Java's coordinate system?

It doesn't have to be exact, it just has to be close.

---

### Post by Daniel G. Taylor on 2004-12-04
You should be able to take the width/height and subtract the coordinate's values from that to convert.

new_coord_width = graph_width - old_coord_width;
new_coord_height = graph_height - old_coord_height;

That's assuming your graph starts at 0. If you want to start your image in the top left (versus somewhere in the middle of the window) you might want to subtract the value of the lowest coordinate from the values you get (so it starts at 0, and the other coordinates will go out from that).

---

### Post by HungSquirrel on 2004-12-04
Heh, thanks.  After 1000+ lines of coding, all it takes is something this simple to short-circuit me.  ;)

---

