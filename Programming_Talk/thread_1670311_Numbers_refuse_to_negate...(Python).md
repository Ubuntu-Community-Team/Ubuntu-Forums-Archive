---
title: "Numbers refuse to negate...(Python)"
date: 2011-01-18
forum: Programming Talk
---

### Post by grantbdev on 2011-01-18
So I made a program in Python to find the circumcenter (the point of concurrency where all perpendicular bisectors of a triangle's sides intersect) and it has worked pretty well for me so far in most cases. Yet for some reason, when it goes through one of the possible outcomes I cannot get it to negate the numbers (num * -1)yet I can negate numbers most of the time and in other programs.

Code: [http://paste.ubuntu.com/555599/](http://paste.ubuntu.com/555599/)

Points I'm using that it won't work:
Point A (-4,0)
Point B (0, 4)
Point C (4, 0)

I'm really hoping this is an obvious mistake that I just couldn't see :p

---

### Post by Vox754 on 2011-01-18
> **grantbdev said:**
> So I made a program in Python to find the circumcenter (the point of concurrency where all perpendicular bisectors of a triangle's sides intersect) and it has worked pretty well for me so far **in most cases.** ...

I'm really hoping this is an obvious mistake that I just couldn't see :p

Code this small you can post it here in the forum instead of having to use a pastebin. Use "code" tags:
```

if slopeABy and slopeABx < 0:
    slopeABy * -1
    slopeABx * -1
    midABx2 = midABx + slopeABy
    midABy2 = midABy + slopeABx

```

The variables "slopeABy" and "slopeABx" are indeed negated, but the results are not stored back into variables.
```

if slopeABy and slopeABx < 0:
    slopeABy = slopeABy * -1
    slopeABx = slopeABx * -1
    midABx2 = midABx + slopeABy
    midABy2 = midABy + slopeABx

```

---

### Post by grantbdev on 2011-01-18
> **Vox754 said:**
> Code this small you can post it here in the forum instead of having to use a pastebin. Use "code" tags:
```

if slopeABy and slopeABx < 0:
    slopeABy * -1
    slopeABx * -1
    midABx2 = midABx + slopeABy
    midABy2 = midABy + slopeABx

```

The variables "slopeABy" and "slopeABx" are indeed negated, but the results are not stored back into variables.
```

if slopeABy and slopeABx < 0:
    slopeABy = slopeABy * -1
    slopeABx = slopeABx * -1
    midABx2 = midABx + slopeABy
    midABy2 = midABy + slopeABx

```

Oh wow, thank you. It was a dumb mistake indeed. I've fixed several errors including those. I will keep running through triangles until it's reliable! :)

---

