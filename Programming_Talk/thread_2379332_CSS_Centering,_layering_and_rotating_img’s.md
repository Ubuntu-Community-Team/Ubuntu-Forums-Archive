---
title: "CSS: Centering, layering and rotating img’s"
date: 2017-12-04
forum: Programming Talk
---

### Post by Drone4four on 2017-12-04
Have a look at [this pen]("https://codepen.io/Angeles4four/pen/mqoWOJ?editors=1100").

I have two issues with this code.

The first is that the img&#8217;s and h1 elements aren&#8217;t center aligning even though I invoke margin: auto in three different locations.  Why aren&#8217;t h1 and imgs aligning in the centre? 

The second issue is specifying the img to each transform and rotate uniquely.  &#8216;one&#8217; should transform 35 degrees, &#8216;two&#8217; 225deg and &#8216;three&#8217; 325deg.  I&#8217;ve attempted to achieve this at lines 10, 15, and 19 in the CSS by adding subclasses, .one, .two, .three next to .site-logo:hover.   When I uncomment those lines, the img&#8217;s are just frozen on the spot.  What am I doing wrong here? How do I get each of the three img&#8217;s to be layered and rotate by a few degrees in different directions with mouseover?

Thanks for your attention.

---

### Post by Dimarchi on 2017-12-05
IMG is not a block element. Besides, IMG elements are positioned absolutely to be at top left corner, never to move from there (apart from *transfrom *CSS which does work with each and every IMG element). Try ```
text-align: center;
``` with H1. Remove *position*, *top*, and *left *from *img *and replace them with ```
display: block;
``` to see the difference. Although I think 

```
img {
    position: absolute;
    left: 50%;
    top: 0px;
    z-index: -1;
    margin: auto;
}

h1 { text-align: center; }
``` 

is closer to what you are probably trying to achieve.

---

### Post by Drone4four on 2017-12-07
Thank you, **@Dimarchi **, this helps.

---

