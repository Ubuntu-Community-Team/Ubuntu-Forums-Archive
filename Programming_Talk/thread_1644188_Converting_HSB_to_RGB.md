---
title: "Converting HSB to RGB"
date: 2010-12-12
forum: Programming Talk
---

### Post by Pyro.699 on 2010-12-12
Hello,

Ive been having some trouble converting a list of **[Hue, Saturation, Brightness]** to **[Red, Green, Blue]**. I have done a lot of reading and there seems to be more focus on HSV (Hue, Saturation, Value). I noticed that there is a library called colorsys and it has many functions used to convert different color types.

There is one for HSV and when i enter the values: 120, 100, 100 (Which should be #00FF00) the the values returned by **hsv_to_rgb** are [100, -9900.0, -9900.0] which is off by over 9000.

Thanks for any help
~Cody

---

### Post by worksofcraft on 2010-12-12
> **Pyro.699 said:**
> ...
which is off by over 9000.

Thanks for any help
~Cody

Check what parameter types are expected. In some libraries they expect a floating point value for each component and 1.0 is the max... so like you might need:

[php]
rgb = hsv_to_rgb(pi*2.0/3.0, 1.0, 1.0);
[/php]

and then being over 9000 is only to be expected with the parameter values you provided ;)

---

### Post by Pyro.699 on 2010-12-12
As is the usual with me, i found my answer after making a post -.- Here is my result:

[php]
def HSBtoRGB(h,s,v):
    import math
    if h == 360: h = 0
    s/=100.0;v/=100.0
    h/=60.0;i=int(math.floor(h))
    f=h-i;p=int(v*(1-s)*255)
    q = int(v*(1-(s*f))*255)
    t = int(v*(1-(s*(1-f)))*255)
    v = int(math.floor(v*255))
    return [[v,t,p],[q,v,p],[p,v,t],[p,q,v],[t,p,v],[v,p,q]][i]
[/php]

I made it as compressed as possible, because this is a very minor part of my script...

---

