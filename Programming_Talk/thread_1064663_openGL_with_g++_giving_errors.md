---
title: "openGL with g++ giving errors"
date: 2009-02-09
forum: Programming Talk
---

### Post by tneva82 on 2009-02-09
What am I doing wrong? Makefile is below. If I try to compile with gcc GLvoid issues dissapear but since I would like to use c++ features I want to use g++(it's the c++ compiler right?). Also error for line 83 in model.cpp stays same so no help there.

I'm pretty sure I have both SDL and openGL properly installed. Have apt-get'ed build-essentials and synaptic packet manager has packets needed marked in green.

Any help?

```
CC = g++ -Wall -ansi

all:
        $(CC) main.cpp model.cpp -o main -lGL -lGLU -lSDL
```

When I compile I get(among others) following error messages:

main.cpp:110: error: ‘<anonymous>’ has incomplete type
main.cpp:110: error: invalid use of ‘GLvoid’
main.cpp: In function ‘int main(int, char**)’:
main.cpp:181: warning: deprecated conversion from string constant to ‘char*’
main.cpp:110: error: too few arguments to function ‘int initGL(<type error>)’
main.cpp:243: error: at this point in file
model.cpp: In function ‘void FreeModel(model3d*)’:
model.cpp:83: error: base operand of ‘->’ has non-pointer type ‘polygon’
make: *** [all] Error 1

And relevant codes.

```
Main.cpp Line 110

int initGL( GLvoid )
```

And model.cpp line 83:

```
free(model->polygons[i]->vertexes);
```

Also the model is struct defined like this(and struct inside it):

```
typedef struct vertex3d {
    float x, y, z;
} vertex3d;

typedef struct polygon {
    int vertexCount;
    vertex3d *vertexes;
} polygon;

typedef struct model3d {
    int polygonCount;
    int vertexCount;
    polygon* polygons;
    vertex3d* vertexes;
} model3d;
```

---

### Post by eye208 on 2009-02-09
If you use C headers in a C++ program, make sure to include them like this:
```
extern "C" {
    #include <...>
}
```

Regarding line 83, something like this would be correct:
```
free(model->polygons[i].vertexes);
```

---

### Post by stroyan on 2009-02-09
The extern "C" declaration should not be necessary because /usr/include/GL/gl.h from the mesa-common-dev package includes that for c++ code.  You should be able to use g++ to compile a C program calling OpenGL functions.

I wonder if your program is getting it's definition of GLvoid from a very unusual source.  You could check the details of header files by compiling with a -E directive to save preprocessed source code.
```
g++ -E -Wall -ansi main.cpp model.cpp -o main.i

```
Then look for the declaration of GLvoid in main.i.

---

### Post by tneva82 on 2009-02-10
> **stroyan said:**
> I wonder if your program is getting it's definition of GLvoid from a very unusual source.

Not sure. I just copied the text from Nehe-guides to work as openGL drawing platform to test object loader and drawer code.

However I fixed the issue by deleting whole GLvoid thing. Not sure what the heck it does but removing it solved the issue and now I have nice object reader that reads object and it's polygons+vertexes(plus different frames in case it has animation) and draws it.

---

