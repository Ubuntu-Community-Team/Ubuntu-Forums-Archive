---
title: "[SOLVED] Generic Polygon Clipper help?"
date: 2008-03-27
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-27
Does anyone know anything about Generic Polygon Clipper (gpc), its some code released by the University of Manchester? Its been around for years so I would hope it has sufficient saturation for someone to help me. *I cant figure out how it works*, or rather, how to use it (I know what it does, just not how to use it). Does anyone know of any tutorials for it?

---

### Post by baumgc on 2008-03-27
[http://www.cs.man.ac.uk/~toby/alan/software/]("http://www.cs.man.ac.uk/~toby/alan/software/")

Try here maybe?

---

### Post by Zeotronic on 2008-03-27
Right... I should have read that... now I feel dumb...*even so* I still don't understand completely, does this mean that the only way I can introduce new shapes is if their in a file? If so, that is the worst way this could possibly work in relation to my program.

So basically, if I can introduce shapes, how can I do it... the only way I saw to do it was from a file.

---

### Post by WW on 2008-03-27
Take a look at the [online documentation](http://www.cs.man.ac.uk/~toby/alan/software/gpc.html).  The data structure is pretty simple.  Here is a modification of the sample code that builds two simple polygons in the C code instead of reading them from files:

**gpctest.c**
```

#include <stdio.h>
#include <stdlib.h>
#include "gpc.h"

int main(void)
    {
    gpc_polygon poly1, poly2, result;
    FILE *ofp;
    
    //
    // poly1 is a square with vertices (0,0),(1,0),(1,1),(0,1)
    //
    poly1.num_contours = 1;
    poly1.hole = (int *) malloc(sizeof(int));
    poly1.hole[0] = 0;
    poly1.contour = (gpc_vertex_list *) malloc(sizeof(gpc_vertex_list));
    poly1.contour->num_vertices = 4;
    poly1.contour[0].vertex = (gpc_vertex *) malloc(4*sizeof(gpc_vertex));
    poly1.contour[0].vertex[0].x = 0.0;
    poly1.contour[0].vertex[0].y = 0.0;
    poly1.contour[0].vertex[1].x = 1.0;
    poly1.contour[0].vertex[1].y = 0.0;
    poly1.contour[0].vertex[2].x = 1.0;
    poly1.contour[0].vertex[2].y = 1.0;
    poly1.contour[0].vertex[3].x = 0.0;
    poly1.contour[0].vertex[3].y = 1.0;

    //
    // poly2 is a triangle with vertices (0.25,0.25),(1.25,0.25),(0.25,1.25)
    //
    poly2.num_contours = 1;
    poly2.hole = (int *) malloc(sizeof(int));
    poly2.hole[0] = 0;
    poly2.contour = (gpc_vertex_list *) malloc(sizeof(gpc_vertex_list));
    poly2.contour->num_vertices = 3;
    poly2.contour[0].vertex = (gpc_vertex *) malloc(3*sizeof(gpc_vertex));
    poly2.contour[0].vertex[0].x = 0.25;
    poly2.contour[0].vertex[0].y = 0.25;
    poly2.contour[0].vertex[1].x = 1.25;
    poly2.contour[0].vertex[1].y = 0.25;
    poly2.contour[0].vertex[2].x = 0.25;
    poly2.contour[0].vertex[2].y = 1.25;

    gpc_polygon_clip(GPC_UNION, &poly1, &poly2, &result);

    ofp = fopen("outfile", "w");
    gpc_write_polygon(ofp, 0, &result);

    gpc_free_polygon(&poly1);
    gpc_free_polygon(&poly2);
    gpc_free_polygon(&result);

    fclose(ofp);
    return 0;
    }

```

Compile and run:
> 
$ gcc -c gpc.c
$ gcc -c gpctest.c
$ gcc gpctest.o gpc.o -o gpctest
$ ./gpctest 
$ cat outfile 
1
10
 0.500000000000000  1.000000000000000
 1.000000000000000  1.000000000000000
 1.000000000000000  0.500000000000000
 1.250000000000000  0.250000000000000
 1.000000000000000  0.250000000000000
 1.000000000000000  0.000000000000000
 0.000000000000000  0.000000000000000
 0.000000000000000  1.000000000000000
 0.250000000000000  1.000000000000000
 0.250000000000000  1.250000000000000
$ 


---

### Post by Zeotronic on 2008-03-28
Good good... now I know how... but I get the following error on build (with Geany):
> g++ -Wall -lSDL -lSDL_image -lSDL_gfx -lgpcl "main.cpp" -o main (in directory: /home/dusk/Projects/New B2D Implementation)
/tmp/ccCSTesb.o: In function `main':
main.cpp: (.text+0xf42): undefined reference to `gpc_polygon_clip(gpc_op, gpc_polygon*, gpc_polygon*, gpc_polygon*)'
main.cpp: (.text+0xf54): undefined reference to `gpc_polygon_to_tristrip(gpc_polygon*, gpc_tristrip*)'
collect2: ld returned 1 exit status
Compilation failed.
Generally I get something like this when I need to include a library (and if you look up there, you'll see -lgpcl, my attempt at it)... looking at your commands, I don't see you linking to a library... ? Am I missing something?

---

### Post by stroyan on 2008-03-28
The "-lgpcl" needs to appear after "main.cpp" in the compiler arguments.
If you put the library first then ld looks at the library and decides to leave it
out of the linked a.out because there was no reference to its symbols at
the moment.  Later it complains when your main references some of those
symbols.

---

### Post by WW on 2008-03-28
I downloaded the source; the file that I downloaded had just the files gpc.c and gpc.h.  There is no configure script to build and install a library.  So I just worked with these files in the same directory as my test program.  Instead of giving a **-l** option, I just added gpc.o to the command that links my test program.

If you installed the package **libgpcl-dev**, you should use the option **-lgpcl**, as you have done.

---

### Post by Zeotronic on 2008-03-28
> g++ -Wall -lSDL -lSDL_image -lSDL_gfx "main.cpp" -lgpcl -o main (in directory: /home/dusk/Projects/New B2D Implementation)
Right? I still get the rest of the error too though.

---

### Post by WW on 2008-03-28
The rest of what error?  The one about missing references to `gpc_polygon_...`?

---

### Post by Zeotronic on 2008-03-28
Yea

---

### Post by WW on 2008-03-28
I just noticed that you are using g++; gpc is a C library, but g++ doesn't know that.  A quick fix is to include the header like this:
```

extern "C" {
#include <gpcl/gpc.h>
}

```
I don't know if this is the best way to do this, but it worked for my simple example. To convert my example to C++, I changed the other includes to cstdio and cstdlib instead of stdio.h and stdlib.h, respectively.  Then this worked:
> 
$ g++ gpctest2.cpp -lgpcl -o gpctest2
$

Note that my earlier comment about using the **-lgpcl** argument before the the main file was not correct.  This also works:
> 
g++ -lgpcl gpctest2.cpp -o gpctest2


---

### Post by stroyan on 2008-03-28
WW's example was C code.  You are compiling main.cpp as C++ code.
Unlike most system library header files, the gpc.h file does not have any
wrapper declaration for C++ to see the C binding to the functions in libgpcl.so.0.

You need to add an 'extern "C"' declaration around the include line yourself-
```

#include <stdio.h>
#include <stdlib.h>
extern "C" {
#include "gpc.h"
}

```

Without that change the g++ compiler creates a reference to a 'mangled name'
that encodes the parameters and return type of the called functions.  The error
message then helpfully demangles the name to look like-
> 
undefined reference to `gpc_polygon_to_tristrip(gpc_polygon*, gpc_tristrip*)'

The only tell-tale clue is that the error message knows too much about types.
A normal missing function in C would be reported as plain '`gpc_polygon_to_tristrip'.

---

### Post by Zeotronic on 2008-03-28
Alright! Thank you! Finally, it looks like I can get past fiddling with this library, and on to work on my game!

---

