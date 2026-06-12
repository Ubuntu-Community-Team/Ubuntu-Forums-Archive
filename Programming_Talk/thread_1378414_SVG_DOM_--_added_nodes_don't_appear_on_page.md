---
title: "SVG DOM -- added nodes don't appear on page"
date: 2010-01-11
forum: Programming Talk
---

### Post by Potters Son on 2010-01-11
I'm experimenting with embedding an SVG file into an HTML page using XML namespaces ([http://tavmjong.free.fr/INKSCAPE/MANUAL/html/Web-Use.html]("http://tavmjong.free.fr/INKSCAPE/MANUAL/html/Web-Use.html")) and using JavaScript to make an interactive page, but I've hit a snag. Whenever I try to add an element using the XML DOM's appendNode() statement, the new object doesn't show up on the page. At first, I thought this was a Firefox glitch in SVG rendering, but I tested it in Chrome as well and got the same result.

---

### Post by Potters Son on 2010-01-12
bump.

I isolated the SVG file itself, but it still refuses to show the new nodes I add.

Anyone know why?

---

### Post by Colonel Kilkenny on 2010-01-12
If I'm not mistaken you need to specify that you're creating SVG elements (thus you need namespace in JS).
Atm. you're creating html elements which are unknown type.

So .js should look like this (notice that I list only the changed parts):

```

...
var svgns = "http://www.w3.org/2000/svg";
...
function drawboard() {
  ...
  var polygon = document.createElementNS(svgns, 'svg:polygon')
  polygon.setAttributeNS(null, 'class','woodhex')
  polygon.setAttributeNS(null, 'points',"0,60 60,30 60,-30 0,-60 -60,-30 -60,30")
  polygon.setAttributeNS(null, 'transform', "translate(200,150)")
...

```

I'm not sure if it setAttributeNS() works with "null" as a parameter but I think it should.

edit. Actually I think it should be createElementNS(svgns, 'polygon')

---

### Post by Potters Son on 2010-01-15
Thanks! I worked around it in the meantime by cloning nodes from a separate, hidden template layer, and it's working out really well...

---

