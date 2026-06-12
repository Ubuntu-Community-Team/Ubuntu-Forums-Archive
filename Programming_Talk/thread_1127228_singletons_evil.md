---
title: "singletons evil?"
date: 2009-04-16
forum: Programming Talk
---

### Post by tneva82 on 2009-04-16
That's what I was told but they didn't bother to explain why(I hate "XXX is evil" without any explanation to why). Maybe somebody here could give quick explanation as to why they are evil? Here's where I'm using them ATM:

Program has world. World is composed of many sectors. Each sector is composed of X number of terrain pieces(in x*z grid). Each piece has certain parameters like position within sector and which direction particular piece is looking(this way I can use same piece for all 4 directions this system allows). These are obviously unique for every piece. Each piece also needs access to vertex/uv/normal arrays for openGL drawing. It also needs access to GLuint variable that holds openGL's texture index. These aren't unique for every terrain piece. Afterall more than 1 terrain piece could be flat ground. Therefore I have split these into own class terrain.

So when world is created I load all the textures and terrain pieces into vector. So far so good. World however doesn't create terrainpieces. That's the job for sector. However sector doesn't know about this library. First idea was to toss a pointer to sector so it could give pointers to terrain as sector file was read(this way there wouldn't be duplicates of all those floats for vertexes, normals and uv-coordinates. Each sector has 32*32 terrainpieces(which can be configured) so if those takes say 50 floats total that's 51,2k floats if they get duplicated and whole sector happens to be same terrain type(okay unlikely but idea is same). And that's just terrain for one sector...Server in particular would be screaming bloody murder as it needs whole map in memory. Client atleast needs only immediate surroundings).

Problem: Lots of pointers, not nice code to read. Then I figured I could use singleton pattern to replace this. Instead of previous I create library of pieces and textures into class implementing singleton pattern. Then sector points out indexes it reads from sector file into terrain pieces. Terrain piece can then when it needs ask the library to draw right terrain piece/texture combination.

Neat. Less code, cleaner code, less pointers tossed around and it works. And the above duplication issue just gets worse when we think about second place where I applied this ie the models where number of floats/ints in ONE piece can be over 10k(and this with just frames for walking...Actually I am thinking of trying to figure out alternative animation but that's bit much of a work). If I would duplicate this for every creature(potentially hundreds) which needs...Well just not pretty idea for memory usage. Therefore I need simple pointer or equilavent which ensures no duplicate data is created for those numbers. So again singleton seemed like great idea.

Yet they are supposedly evil. Why? And any better ideas then how to implement above? No pointers, no duplication of data and no singleton. I'm out of ideas how to implement with those 3 rules followed.

---

### Post by eye208 on 2009-04-16
Singletons are considered evil because they make unit testing impossible.

---

### Post by cabalas on 2009-04-16
Singletons are also considered evil by some because essentially they are a global variable with all the inherent issues.

---

### Post by tneva82 on 2009-04-16
> **cabalas said:**
> Singletons are also considered evil by some because essentially they are a global variable with all the inherent issues.

Yes but alternative is passing same thing around through multiple method calls. Possibly to classes that don't themselves need it but classes they create need. Doesn't sound that good idea either. Plus since pointers seems to be evil as well this evil reduces other evil so maybe we'll end up with less evil overall :D

Dunno. Code cleared up nicely and reduced number of pointers which might cause segfaults. I'm hard pressed to figure out alternative that would result in as clear code with least amount of pointers(or worse duplicate data) tossed around.

---

### Post by eye208 on 2009-04-16
> **tneva82 said:**
> Yes but alternative is passing same thing around through multiple method calls.
The alternative is to let the sector object hold a weak_ptr referencing the shared terrain data object owned by the world object. No pointers, no duplication of data, no singleton, no segfault, no evil.

---

### Post by Yacoby on 2009-04-16
> **cabalas said:**
> Singletons are also considered evil by some because essentially they are a global variable with all the inherent issues.
Except they don't pollute the namespace, and they don't always consume resources.

---

### Post by monkeyking on 2009-04-16
is singletons this designpattertn stuff with only on object of a class?

---

### Post by dburnett77 on 2009-04-16
why not use a complex number system array.  Where the I^2 elements eliminate themselves, I have...

main...
index{[i==imaginary, inf_range]=!NULL};
Simplifi.

---

