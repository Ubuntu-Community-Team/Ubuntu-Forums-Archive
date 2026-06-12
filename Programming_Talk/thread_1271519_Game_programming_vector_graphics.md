---
title: "Game programming: vector graphics"
date: 2009-09-21
forum: Programming Talk
---

### Post by billdotson on 2009-09-21
So I was thinking, if the graphical images/models in a PC game were almost exclusively vector images/models instead of raster wouldn't said game be a lot more scalable (in terms of resolution and video hardware) and a lot easier on the CPU and GPU? It probably won't matter much for the games I am doing but I was thinking of making (or finding a free as in free beer images or models) raster images/models for my game and converting them into vector images. Does that sound viable or even possible? If so, is it a waste of time? What about on a huge game like say Wolfenstein? Could they have used almost exclusively vector models for that or would there be some reason why vector models wouldn't work?

Also, on a side note, would it be technically possible to make a game using a very large amount of photographs from different angles (i.e. drawing models from photographs)? The thought behind the question would be a game with *actual* photorealism, not just computer models drawn by a team of graphic artists.

---

### Post by scragar on 2009-09-21
Photo's won't work, the memory required to store the number of images required for any modern game would be so huge that it would be completely unfeasable(just a small 100px square image for each frame from 8 different view points with a good colour resolution would require 1GB+ of space for each image, not to mention the CPU intensity of loading different images 20 times a second to be dropped again right afterwards(because storing them in ram is unfeasable)).

---

### Post by billdotson on 2009-09-21
Yeah, that is similar to what I was thinking. Perhaps in the future when VR is commonplace (doesn't seem like it will be long) and regular computers have 32GB of RAM :) . Well, that or the majority of games are run off of giant gaming server farms and forwarded to your display. 

Anyway, what do you think about my raster to vector idea? You know, just taking raster images or models and converting them into vector images or models for use in my game (or a game in general). Vector graphics being mathematical formulas wouldn't they be a lot easier on a graphics processor (of course I don't think any of MY games are going to be pushing any hardware to its limits :P )

I wanted just to convert a photo of mine (from my digital camera) to a vector image to see the quality and how big it would be to see if it were viable but haven't figured out how to do so thus far.

---

### Post by slavik on 2009-09-21
computer graphics started out as vector based 20+ years ago ... And here we are.

Raster to vector is doable ... But lancsoz3/bicubic is faster

---

### Post by hessiess on 2009-09-21
If you make your graphics using SVG then it would be completely scalable, though reasonably large anti-aliased RGBA bitmaps+OpenGL hardware bilinear scaling works well too, see Quad-Ren in signature.

---

### Post by billdotson on 2009-09-24
lancsoz3/bicubic?

I don't really know much of 3d modeling. I have heard of NURBS curves and other things like that and I can only assume that the industry is doing things the best way they can be done at the current time (or they are attempting to.. hopefully).

---

### Post by grayrainbow on 2009-09-24
If you are really interested in the subject...
[http://en.wikipedia.org/wiki/Polygon_mesh](http://en.wikipedia.org/wiki/Polygon_mesh)
[http://en.wikipedia.org/wiki/Texture_mapping](http://en.wikipedia.org/wiki/Texture_mapping)
And btw all files are usually compressed, sometimes doubly compressed(that mean textures for example come in different compressed formats and you apply some standard compressing on a file)

---

