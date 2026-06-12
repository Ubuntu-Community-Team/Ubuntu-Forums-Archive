---
title: "Python, matlab, image processing"
date: 2008-06-11
forum: Programming Talk
---

### Post by sbilstein on 2008-06-11
So, I dabbled in VB in high school but did not really learn anything. So my first real introduction to programming was last semester in a computation class. We used matlab for network modeling, image manipulation, all kinds of cool modeling.
Im changing my major to compsci and to catch up with the year i wasted doing all mechanical engineering req's I want to learn a language well and some basic compsci knowledge. To do this, I want to write a program that does fun image effects, sort of like or exactly like the filters in photoshop and gimp.

Anyways, the bulk of my question has to do with matrix manipulation and python. We did this cool thing in school in which we parametrized an image into polar coordinates, performed like a radial twist on it and then interpolated the new pixel coordinates back into xy positions. Reinserting new pixels into the image involved multiplying adjacency matrices. This is really easy in matlab. I'm not sure how to go about doing this in python. I also like being able to access multi dimesional arrays of data sequentially or through coordinates.  Is this possible with lists? Do I need to use some module I'm not aware of to multiply matrices in matlab? Would it be worthwhile for me to write my own matrix multiplication module?  What kind of things should I be looking into before I start developing my image program??

Thanks for the help!

---

### Post by pmasiar on 2008-06-12
Can you use one of many image libraries, instead of rolling out your own? Like [http://www.pythonware.com/products/pil/](http://www.pythonware.com/products/pil/) ?

One of python's mantras is: "batteries included" - for whatever generic functionality you may need, there is library to do it, and many are included in core language. In fact, this arrangement was one of designing principles of Python from very beginning. Libraries are debugged, and often written in C for speed (and have community to ask for help).

Don't roll generic libraries - use existing, just add your custom functionality.

---

