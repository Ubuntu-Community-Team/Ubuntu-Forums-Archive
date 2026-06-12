---
title: "Java + SVG?"
date: 2008-06-01
forum: Programming Talk
---

### Post by Phristen on 2008-06-01
What would be the easiest way to display an SVG image in a desktop application (e.g. JFrame)?
I searched google but there is little on the subject :confused:

---

### Post by xlinuks on 2008-06-01
Java doesn't have built-in support for it.

I wonder how you googled, "Java SVG" the first page was:
[http://xmlgraphics.apache.org/batik/index.html](http://xmlgraphics.apache.org/batik/index.html)

---

### Post by Phristen on 2008-06-01
I know about batik, but application I'm making is meant to be very small and I don't want to import 3rd party libraries.> Java doesn't have built-in support for it.Sad :(

---

### Post by Balazs_noob on 2008-06-01
As i know only jpg,gif and png is supported without 3rd party libs.

So you either convert it to png or use third party lib.

---

### Post by Phristen on 2008-06-01
Yes, I already converted to png.

---

### Post by CptPicard on 2008-06-01
SVG is a vector-graphics format and PNG is a raster format... you're going to lose the ability to scale losslessly in that kind of conversion.

---

### Post by Phristen on 2008-06-01
That's the reason I originally wanted to use SVG.

---

