---
title: "Problems with inline functions"
date: 2009-04-15
forum: Programming Talk
---

### Post by tneva82 on 2009-04-15
There's certain class member function that needs to be called a lot but not in many places in code(specifically in one place really). Sounds like good place for inline function as that could remove overhead for calling function repeatedly. When you have function that gets called thousands of times per second that just might add up noticably.

However I can't get it compiling. I tried it like this: [http://www.java2s.com/Code/Cpp/Class/Inlinefunctionsmaybeclassmemberfunctions.htm]("http://www.java2s.com/Code/Cpp/Class/Inlinefunctionsmaybeclassmemberfunctions.htm") but in return I get following compiler issues(note that url seems to be saying it's java but code sure looks like C++ to me) 

```
obj/terrainpiece.o: In function `terrainPiece::draw()':
/home/tnevalainen/Documents/project/src/terrainpiece.cpp:40: undefined reference to `terrain::draw()'
collect2: ld returned 1 exit status
make: *** [client] Error 1

```

And the function definition in .cpp file is:

```
inline void terrain::draw() { 
// do stuff
}
```

If I remove the inline it works great(except the relatively slow FPS).

Does it interfere that the place I try to call it is for loop? Or something else? Slight annoyance if this doesn't work and might end up having to redesign terrain system yet again if this can't work :-/

---

### Post by Lux Perpetua on 2009-04-15
Inline functions should be defined in a header file and #included in your source file. An inline function needs to be visible in the source file it's used in in order for the compiler to inline the call. If it's in source file B, then the compiler doesn't see it while it's compiling source file A.

---

