---
title: "Python mouse drawing path smoothing"
date: 2009-03-03
forum: Programming Talk
---

### Post by Acapulco on 2009-03-03
Hello. I'm working on this program which takes input coordinates (x,y) and I want to draw them on screen. The problem is with the input. The nature of the device makes it "noisy" or shaky.

A picture of what I have now is here:
[http://saganus00.googlepages.com/shaky1.jpg]("http://saganus00.googlepages.com/shaky1.jpg")

What I would like is to be able to smooth that out into a nicer-looking writing. Sort of what you get when using an stylus-type input device.Any ideas?

I've already thought of Bezier 3-point lines but I need to set control points, which I believe would be different for each segment, maybe depending on mouse speed or whatnot. 

Maybe there's something simpler?

I'm working with PyGame also, and it's only possible to draw lines with integer start and end positions, or draw individual pixels, so I'm not sure how the Bezier approach works out when most of the calculations get cut off to an integer number.

Did I make any sense?

Thanks

---

### Post by Acapulco on 2009-03-04
I found this:

[Hysteresis smoothing for X-monotonic polygonal chains]("http://cgm.cs.mcgill.ca/~godfried/teaching/pr-projects/tallman/hysterisis.html")

and it's almost exactly what I need, except that some segments will be non-monotonic so I need to solve this case as well.

Anyone know of this techniques?

---

