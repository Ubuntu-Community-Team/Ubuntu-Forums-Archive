---
title: "How to extract Bézier equation from truetype fonts?"
date: 2014-08-23
forum: Programming Talk
---

### Post by Dr._Valy_G._Rousse on 2014-08-23
Hello,

I wrote a ray-tracing class that can handle primitives such as spheres, boxes, planes, polygons, cones, ..., and CSG objects. Now I would like to be able to render text. I can do it by describing the shape of a given character with a Bézier curve.

Since I read that truetype fonts are described by Bézier curves, I would like to know how I can extract from a truetype file the Bézier path of a given character?

---

### Post by ofnuts on 2014-08-24
If this is for some characters in some fonts,  create text in Inkscape  and export the SVG file, then parse the SVG. You can also do it with  Gimp (create text layer, Text to path, Export path (this also creates a  SVG)).

AFAIK in all formats, fonts are mostly described with  Bézier curves (but IIRC they are usually "conical" ones  (2nd-order  polynomial), while graphics programs use cubic Bézier splines (3rd-order  ploynomial), but you can always convert up. 

If you want a  complete set, you would have to work from the font file directly, in  which case you may want to look at OpenType fonts since the format isn't  proprietary. You can also find libs that can read font formats for you  (Cairo?)

---

### Post by Dr._Valy_G._Rousse on 2014-08-25
Thank you, I succeeded to do it with Gimp!

---

