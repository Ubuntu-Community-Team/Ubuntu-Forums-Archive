---
title: "gcc is wrong... right?"
date: 2009-02-15
forum: Programming Talk
---

### Post by tom66 on 2009-02-15
```

In file included from main.c:16:
textarea.c: In function &#8216;create_text_area&#8217;:
textarea.c:32: error: &#8216;struct P_TextAreaData&#8217; has no member named &#8216;lineSpacing&#8217;
textarea.c:33: error: &#8216;struct P_TextAreaData&#8217; has no member named &#8216;paraSpacing&#8217;
textarea.c:34: error: &#8216;struct P_TextAreaData&#8217; has no member named &#8216;textAlign&#8217;
textarea.c:34: error: &#8216;AL_LEFT&#8217; undeclared (first use in this function)
textarea.c:34: error: (Each undeclared identifier is reported only once
textarea.c:34: error: for each function it appears in.)
textarea.c:35: error: &#8216;struct P_TextAreaData&#8217; has no member named &#8216;textAreaFloat&#8217;
textarea.c:35: error: &#8216;FLOAT_ABOVE&#8217; undeclared (first use in this function)
textarea.c:39: error: &#8216;struct P_TextAreaData&#8217; has no member named &#8216;canvasY2&#8217;
textarea.c:40: error: &#8216;struct P_TextAreaData&#8217; has no member named &#8216;width&#8217;
textarea.c:41: error: &#8216;struct P_TextAreaData&#8217; has no member named &#8216;height&#8217;
In file included from main.c:17:
draw.c: In function &#8216;render_objects_in_slide&#8217;:
draw.c:423: warning: passing argument 4 of &#8216;qsort&#8217; from incompatible pointer type

```

But I do have a struct:

```

/* Structure for a text area. */
struct P_TextAreaData
{
    /* Coordinates relative to the origin, which is in the centre of the object. */
    double lastX, lastY; 
    double goalX, goalY;
    
    /* Geometry of the text area. */
    double canvasX1, canvasY1, canvasX2, canvas Y2;
    double width, height;
    
    /* Each text area can only have one of the following properties. */
    enum P_TextAlign 
    {
        AL_LEFT = 1,
        AL_RIGHT = 2,
        AL_CENTER = 3,
        AL_JUSTIFY = 4
    } textAlign;
    
    double lineSpacing; /* Default: 1 */
    double paraSpacing; /* Default: 2 */
    
    enum P_AreaFloat 
    {
        FLOAT_ABOVE = 1,
        FLOAT_BELOW = 2,
        FLOAT_INLINE = 3
    } textAreaFloat;
    
    /* The various text elements in the text area. */
    struct P_TextAreaElement *elements;
    
    /* Margins of the text area. */
    struct P_Margins *margins;
};

```

And it's included before the function, if that matters. I don't understand. Here are the troublesome lines:

```

    /* Create a text area, and associate it with our object. */
    SAFE_MALLOC(ta, struct P_TextAreaData, 1);
    ta[0].lineSpacing = 1.0; 
    ta[0].paraSpacing = 2.0; 
    ta[0].textAlign = AL_LEFT;
    ta[0].textAreaFloat = FLOAT_ABOVE; 
    ta[0].canvasX1 = x1;
    ta[0].canvasY1 = y1;
    ta[0].canvasX2 = x2;
    ta[0].canvasY2 = y2;
    ta[0].width = 1.0;
    ta[0].height = 1.0;
    ta[0].lastX = 0.0;
    ta[0].lastY = 0.0;
    ta[0].goalX = ((x1 + x2) / 2.0);
    ta[0].goalY = ((y1 + y2) / 2.0);

```

SAFE_MALLOC is a macro which maps to malloc but checks for NULL pointers. And I don't think that's the cause, because with a similar line of code (but no malloc):

```

    struct P_TextAreaData *ta;
    ta[0].lineSpacing = 1.0; 
    ta[0].paraSpacing = 2.0; 
    ta[0].textAlign = AL_LEFT;
    ta[0].textAreaFloat = FLOAT_ABOVE; 
    ta[0].canvasX1 = x1;
    ta[0].canvasY1 = y1;
    ta[0].canvasX2 = x2;
    ta[0].canvasY2 = y2;
    ta[0].width = 1.0;
    ta[0].height = 1.0;
    ta[0].lastX = 0.0;
    ta[0].lastY = 0.0;
    ta[0].goalX = ((x1 + x2) / 2.0);
    ta[0].goalY = ((y1 + y2) / 2.0);

```

the same errors are thrown.

Any help appreciated!

---

### Post by dwhitney67 on 2009-02-15
I so hate using macros!  Anyhow, you did not present enough evidence to show if you are indeed including the definition of the structure in the file that is attempting to allocate the memory for the structure.

Since you are only allocating one structure (not an array of structures), consider accessing it the "normal" way.
```

ta->lineSpacing = 1.0;
...

```

Also, try allocating the memory yourself to see if that makes a difference:
```

struct P_TextAreaData* ta = malloc(sizeof(struct P_TextAreaData));

```

---

### Post by tom66 on 2009-02-15
Same result. What's odd, is that only some of the identifiers aren't being recognized... any clue why this is? Any more suggestions appreciated!

---

### Post by tom66 on 2009-02-15
Fixed. There was a space in one of the variables and it causes this mess. Thanks for your help.

---

### Post by dwhitney67 on 2009-02-15
> **tom66 said:**
> Same result. What's odd, is that only some of the identifiers aren't being recognized... any clue why this is? Any more suggestions appreciated!
Look at this line; it has a syntax error in it.
```

double canvasX1, canvasY1, canvasX2, canvas Y2;   <-  Should not be a space there!

```

---

### Post by Simian Man on 2009-02-15
The problem is probably that you have forward declared your struct but not included the header file.  Check that textarea.c includes whatever header the second snippet is from.
<edit>Nevermind, you got it</edit>

BTW compilers are very, very, very rarely wrong.  When they are, 9 times out of 10 it is an optimization error.  SO I am sure that gcc is right here and you are wrong.  Programming as a beginner is easier if you don't blame the compiler for your problems.

---

### Post by wmcbrine on 2009-02-16
> **Simian Man said:**
> BTW compilers are very, very, very rarely wrong.+1

It is often tempting to blame the compiler. But unless it segfaults, or says "Internal compiler error", it's probably you.

---

