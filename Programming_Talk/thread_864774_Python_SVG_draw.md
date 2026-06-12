---
title: "Python: SVG draw"
date: 2008-07-20
forum: Programming Talk
---

### Post by ashvala on 2008-07-20
Is it possible to draw SVG images with python?

---

### Post by mssever on 2008-07-20
> **ashvala said:**
> Is it possible to draw SVG images with python?
Yes.

---

### Post by ashvala on 2008-07-20
How?

---

### Post by Wybiral on 2008-07-20
> **ashvala said:**
> How?

You mean to render them, or to generate them?

Generating would be easy since SVG is a fairly simple XML format.

---

### Post by ashvala on 2008-07-20
Generate!

---

### Post by WW on 2008-07-20
Take a look at [SVGFig](http://code.google.com/p/svgfig/).

For example,

svgtest.py
```

from svgfig import *
from math import pi

curve1 = Curve("50+45*sin(3*t),50+45*cos(5*t)",0,2*pi).SVG()
sq = SVG("rect",x=0,y=0,width="100%",height="100%",rx=8,fill="blue",fill_opacity="0.2")
shape1 = SVG("circle",cx="20%",cy="48%",r="12%",fill="red",fill_opacity="0.25")
shape2 = SVG("ellipse",cx="70%",cy="77%",rx="25%",ry="10%",fill="green",fill_opacity="0.8")
shape3 = SVG("circle",cx="65%",cy="35%",r="15%",fill="blue",fill_opacity="0.8")
g = SVG("g",sq,curve1,shape1,shape2,shape3)
svgwrap = canvas(g,width="150px",height="150px")
svgwrap.save("tmp.svg")

```

(I don't know if that is the "best" way to use SVGFig--that bit of code was the result of an hour or so of browsing the SVGFig site, and messing around with SVG.)

---

### Post by Quikee on 2008-07-20
You could also use Cairo for this (draw to a SVG surface).

---

