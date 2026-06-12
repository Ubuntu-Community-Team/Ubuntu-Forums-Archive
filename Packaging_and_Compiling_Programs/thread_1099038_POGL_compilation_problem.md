---
title: "POGL compilation problem"
date: 2009-03-17
forum: Packaging and Compiling Programs
---

### Post by oniric on 2009-03-17
Hi all, this is my first post, and a pretty technical one :-)

I downloaded OpenGL 0.57 Perl Module from CPAN and tried to build giving the command

```
perl Makefile.PL interface=FREEGLUT
```

I have freeglut and all its dev headers installed. Then i run

```
make
```

and some warnings apperead like:

```
warning: cast to pointer from integer of different size
```

Since those were only warnings and compilation went fine i tried

```
make test
```

and I could see a 3D animation but not a "supposed to be there" text. So I digged down a bit and found that the problem it's probably in those warnings, and since I'm running Ubuntu Intrepid Ibex for **AMD64 architecture** the problem is probably caused by different sizes of (void *) and int but I'm not sure about that. Anyone has a solution for this? I think this could be really a simple fix but I don't really know C so match :oops: Thanks for your help!

If you need more details let me know!

EDIT: here the suspected code snippet:

```

    extern void* glutStrokeRoman;
    extern void* glutStrokeMonoRoman;
    extern void* glutBitmap9By15;
    extern void* glutBitmap8By13;
    extern void* glutBitmapTimesRoman10;
    extern void* glutBitmapTimesRoman24;
    extern void* glutBitmapHelvetica10;
    extern void* glutBitmapHelvetica12;
    extern void* glutBitmapHelvetica18;

    /*
     * Those pointers will be used by following definitions:
     */
#   define  GLUT_STROKE_ROMAN               ((void *) &glutStrokeRoman)
#   define  GLUT_STROKE_MONO_ROMAN          ((void *) &glutStrokeMonoRoman)
#   define  GLUT_BITMAP_9_BY_15             ((void *) &glutBitmap9By15)
#   define  GLUT_BITMAP_8_BY_13             ((void *) &glutBitmap8By13)
#   define  GLUT_BITMAP_TIMES_ROMAN_10      ((void *) &glutBitmapTimesRoman10)
#   define  GLUT_BITMAP_TIMES_ROMAN_24      ((void *) &glutBitmapTimesRoman24)
#   define  GLUT_BITMAP_HELVETICA_10        ((void *) &glutBitmapHelvetica10)
#   define  GLUT_BITMAP_HELVETICA_12        ((void *) &glutBitmapHelvetica12)
#   define  GLUT_BITMAP_HELVETICA_18        ((void *) &glutBitmapHelvetica18)

```

gcc is giving me a warning for every "define" row.

---

### Post by oniric on 2009-03-18
Nevermind, I found it out :D

I changed line 220 in OpenGL.xs from

```
#define i(test) if (strEQ(name, #test)) return newSViv((int)test);
```

to

```
#define i(test) if (strEQ(name, #test)) return newSVnv((long)test);
```

and the compilation went fine with no other warnings ( at least in part related to text drawing functions ). Now I can see text in "make test"!!

I still have a good coding instinct \\:D/ Hope that will help others too!

---

