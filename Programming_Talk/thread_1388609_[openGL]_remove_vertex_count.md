---
title: "[openGL] remove vertex count"
date: 2010-01-23
forum: Programming Talk
---

### Post by BramWillemsen on 2010-01-23
Hi,

This is probably an easy question for the more experienced openGL programmer. I just started a webcourse called 'computer graphics fundamentals'. For an assignment i have to read and display an arbitrary object from a .OBJ file. The easiest thing would be to just display each of the triangles with GL_TRIANGLES. The problem is that most of the triangles will share edges. By using GL_TRIANGLES certain vertices will be multiplied since they are shared by many several surrounding triangles. This seems like a waste of resources and i would like to program effectively right from the start.

I know GL_TRIANGLE_FAN or GL_TRIANGLE_STRIP is a way to reduce the vertex count. Since i have to construct a 3D-structure from a .OBJ file i'm not sure if the fan or the strip will be able to do this. Complicated geometries could be impossible to generate with a single strip or fan. Flexibility is also lost when you don't use GL_TRIANGLES, it is harder to work with textures for example since some coordinates are fixed by your previous triangles.

Right now i'm trying to find out what the most efficient way is to construct an arbitrary object. I assume that a GL_TRIANGLE_FAN is more efficient than GL_TRIANGLE because there are less vertices. Therefore the shading equations for diffuse/specular light have to be evaluated at less points i guess which results in a performance increase. **Are there other effective methods to reduce vertex counts besides GL_TRIANGLE_STRIP / GL_TRIANGLE_FAN ?**. It would ideal to use GL_TRIANGLES if there is a way to 'explain to the computer' that certain vertices are shared so to say.

kind regards and thanks for the input!,

Bram Willemsen

edit: title reads 'remove vertex count'. It should be 'reduce vertex count' of course.

---

### Post by BramWillemsen on 2010-01-24
I;d like to give this problem one bump. if it dies again i won't try to resurrect it anymore. I guess my mispelled title is a bit confusing. I edited it but it won't update in the thread list.

---

### Post by DougB1958 on 2010-01-24
Look into vertex arrays. I can't say I've written anything that really uses them for more than dabbling, but they give you a way to define a vertex once and then use it multiple times.

---

