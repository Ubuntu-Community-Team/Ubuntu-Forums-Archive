---
title: "C problems..."
date: 2009-02-17
forum: Programming Talk
---

### Post by tom66 on 2009-02-17
I'm having a lot of problems with C. I know python might be an alternative, and I do know python quite well, but for what I'm doing it would be best to squeeze every tiny bit of speed out of my program.

Question: Do I need to malloc each character string if I am to resize it? Or if I have an empty string, is it necessary that I malloc it before I sprintf something into it?

Question: Why does this 

```

    cairo_line_to(cr, object->textAreaRef->canvasX1, object->textAreaRef->canvasY1);
    cairo_line_to(cr, object->textAreaRef->canvasX2, object->textAreaRef->canvasY1);
    cairo_line_to(cr, object->textAreaRef->canvasX2, object->textAreaRef->canvasY2);
    cairo_line_to(cr, object->textAreaRef->canvasX1, object->textAreaRef->canvasY2);

```

segfault, in this function:

```

/**
 * Handles drawing a text area.
 * @params	cairo resource, object, zoom (0.0 to +Inf), 
 *              pageToCanvasMargin, inverted pageToCanvasMargin, 
 *              viewport X (0.0 .. 1.0), viewport Y (0.0 .. 1.0), 
 *              render size X, render size Y
 * @returns	nothing (void)
 */
void draw_text_area(cairo_t *cr, struct P_Object *object, 
    double zoom, double pageToCanvasMargin, double pageToCanvasMarginInv,
    double viewX, double viewY,
    double rsx, double rsy
    )

```

with this call:

```

                    draw_text_area(cr, to_render[idx].object, 
                    	    zoom, pageToCanvasMargin, pageToCanvasMarginInv, viewX, viewY, RENDER_SIZE_X, RENDER_SIZE_Y);

```

?

Any help appreciated if people could answer these two questions!

---

### Post by Zugzwang on 2009-02-17
> **tom66 said:**
> I'm having a lot of problems with C. I know python might be an alternative, and I do know python quite well, but for what I'm doing it would be best to squeeze every tiny bit of speed out of my program.

Question: Do I need to malloc each character string if I am to resize it? Or if I have an empty string, is it necessary that I malloc it before I sprintf something into it?


With regards to your first question: Yes, you have to malloc the memory every time (or re-use other allocated memory chunks no longer in use). Note that you can switch to C++ and just use some of the concepts you like from C++ and program the rest "like in C". In particular, string streams and similar objects allow more efficient writing of such "printing" code. However, there are people around here that would consider such a combination as "evil" (In particular, you might run into trouble with name mangling if you are writing a library in this mixed form).

With regards to your second question: Learn how to use valgrind -- This is a nice tool to find out why programs are seg-faulting.

---

### Post by tom66 on 2009-02-17
```

==7452== Memcheck, a memory error detector.
==7452== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==7452== Using LibVEX rev 1854, a library for dynamic binary translation.
==7452== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==7452== Using valgrind-3.3.1-Debian, a dynamic binary instrumentation framework.
==7452== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==7452== For more details, rerun with: -v
==7452== 
==7452== Use of uninitialised value of size 4
==7452==    at 0x40264AA: strcpy (mc_replace_strmem.c:268)
==7452==    by 0x804B231: create_shape_rectangle (object.c:415)
==7452==    by 0x804EB67: main (main.c:319)
==7452== 
==7452== Invalid read of size 1
==7452==    at 0x40264AA: strcpy (mc_replace_strmem.c:268)
==7452==    by 0x804B231: create_shape_rectangle (object.c:415)
==7452==    by 0x804EB67: main (main.c:319)
==7452==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==7452== 
==7452== Process terminating with default action of signal 11 (SIGSEGV)
==7452==  Access not within mapped region at address 0x0
==7452==    at 0x40264AA: strcpy (mc_replace_strmem.c:268)
==7452==    by 0x804B231: create_shape_rectangle (object.c:415)
==7452==    by 0x804EB67: main (main.c:319)
==7452== 
==7452== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 89 from 1)
==7452== malloc/free: in use at exit: 1,592 bytes in 39 blocks.
==7452== malloc/free: 63 allocs, 24 frees, 4,516 bytes allocated.
==7452== For counts of detected errors, rerun with: -v
==7452== searching for pointers to 39 not-freed blocks.
==7452== checked 295,280 bytes.
==7452== 
==7452== LEAK SUMMARY:
==7452==    definitely lost: 0 bytes in 0 blocks.
==7452==      possibly lost: 0 bytes in 0 blocks.
==7452==    still reachable: 1,592 bytes in 39 blocks.
==7452==         suppressed: 0 bytes in 0 blocks.
==7452== Rerun with --leak-check=full to see details of leaked memory.
Segmentation fault

```

It doesn't seem to go into much depth about why the segfault occurred. GDB tells me that it was in the *cairo_line_to* routine.

---

### Post by Can+~ on 2009-02-17
> **tom66 said:**
> Question: Do I need to malloc each character string if I am to resize it?

If you need to expand a string, yes, you can even use realloc, but it's quite expensive. Better is to use a big string space and reuse it, since memory space is quite cheap. If you need to make it "smaller" then there's no point on mallocing or reallocing a smaller space.

> **tom66 said:**
> Or if I have an empty string, is it necessary that I malloc it before I sprintf something into it?


Nope. Malloc is to request a memory address, you should have no problem if you sprintf in an already existing, empty string. And you can clear a string by just replacing the starting character with a '\0' (end of string). Btw, if you're mallocing over an existing reference, that means you're reserving a new space of memory, without freeing the previous one, that's a memory leak.

> **tom66 said:**
> Question: Why does this 
<big chunk of code>

segfault, in this function:
<big chunk of code>

with this call:
<big chunk of code>

Any help appreciated if people could answer these two questions!

Please use a debugger, I bet you're passing a null reference. Start adding variable to watch.

---

### Post by Zugzwang on 2009-02-17
> **tom66 said:**
> 
It doesn't seem to go into much depth about why the segfault occurred. GDB tells me that it was in the *cairo_line_to* routine.

Look! Valgrind says that in your "create_shape_rectangle" function in line 415, you are calling strcpy and in that function, a NULL pointer and also possible something you haven't initialised correctly is used. It's highly likely that you (in object.c) are passing the NULL pointer and the uninitialised value. 

That is some different result. You should always try to fix the first error first.

---

### Post by wmcbrine on 2009-02-17
> **Can+~ said:**
> Nope. Malloc is to request a memory address, you should have no problem if you sprintf in an already existing, empty string.That depends what he means by "an empty string". In context, I'm guessing that he means a pointer with nothing assigned to it, like this:

```
char *foo;
```

or perhaps a pointer to an empty string, like this:

```
char *foo = "";
```

In either case, yes, one would need to malloc() space for a new string.

In this (and only this) case:

```
char foo[20];
```

one would not.

Seeing some actual code from the OP would help...

---

