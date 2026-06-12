---
title: "Bump mapping, how it works?"
date: 2008-10-07
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-07
I was wondering how the hell can this work:
[http://www.neilwallis.com/java/bump2.htm](http://www.neilwallis.com/java/bump2.htm)
It is 2d bump mapping. Looks awesome! But how
is that thing calculated? I am not very good at
maths but perhaps you could explain it to me?

---

### Post by CptPicard on 2008-10-07
Been a long time since I took my graphics class, but IIRC the essential idea is that when you're doing your shadow/lighting computation for a surface, you have the normal vector for that surface that the light ray is reflected around. Now, you create a displacement map for the surface -- essentially, it's a bit like a "texture" that doesn't produce color, but an actual normal vector difference for either your ray tracing or shadowing algorithm, for each pixel in the image.

The simplest bump map is just a "height map texture" like this -- each pixel in the bump map tells you how much up or down from the actual surface  the mapped surface is displaced. Then you just simply compute the vector for your lighting/shadowing.

---

### Post by hod139 on 2008-10-07
Said another way, bump mapping is a method for modeling surface "bumpiness".  The idea is to apply a perturbation function to the surface normals stored in the textures, and to use the perturbed normals in the illumination calculations.  This perturbation function is often called the bump function, and that is where the term bump mapping comes from.  Usually the map is stored in a lookup table (along the lines of what CptPicard was saying), though you could use an analytical bump function if you want.

Any more details will require some math (basic linear algebra).  If you are interested just post back and I can provide more details.

---

