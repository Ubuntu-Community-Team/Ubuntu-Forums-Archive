---
title: "Good 3d Math library"
date: 2010-05-22
forum: Programming Talk
---

### Post by vek on 2010-05-22
I'm looking for a good 3d math library for linux.  You know... vector3's, vector4's, 3x4's, 4x4's, 3x3's, all the various concatenations, inverses, etc.  Quaternions, slerp, squad, the usual, y'know?  Nothing too fancy...

I notice that ogre3d has a decent library but nothing is SIMD/vectorized (is it?).  And it seems wasteful to require the whole of ogre3d just to do some custom 3d stuff... any suggestions?  I'm trying to avoid a whole series of dependencies.

---

### Post by tookyourtime on 2010-05-22
Does boost not have some matrix stuff?

---

### Post by vek on 2010-05-22
Looks like it has a quaternion library, and a matrix library, but they're not optimized for 3d games.  They're also very bare unless I'm missing something - for example, the quaternion library deals only with single quaternions and doesn't appear to provide slerp, squad, and other computations of that nature, such as inner quadrangle quaternion computations as part of a quaternion SQUAD setup.  

There also appears to be another boost library to do with linear algebra, but its formal linear algebra and computation.  Also, none of these are optimized for vectorized computation on modern CPUs, so will perform slower than, say, Microsoft's DirectX D3DX, which is vectorized when available.

The matrix library in boost appears to be meant more for storing data than using to compute things.  E.g. you can set the type of elements to be other things like strings.  So it doesn't provide matrix-matrix multiplication by template (as far as I can tell).  Even if it did, it would be way slower than it could be since its using a template based container which is unaware of SIMD / SIMD2 / any kind of special CPU features designed for this kind of thing.

It's not like I can't rewrite all those things, its just a matter of time and how much of it I don't currently have in my current project.  There has to be a decent 3d math library out there, made for games and not math... or maybe there isn't?  

If I have to write one, I will!  ... it just seemed silly that there wasn't one already since its freakin' 2010 and we've been making 3d games for nearly 20 years now.

---

### Post by c174 on 2010-05-22
Maybe [eigen]("http://eigen.tuxfamily.org/") is something for you

---

### Post by vek on 2010-05-22
That does look promising.  It takes vectorization into account via alignment.  I might have to do my own SQUAD setup and SQUAD but that's easy math.  Thank you muchly!

---

