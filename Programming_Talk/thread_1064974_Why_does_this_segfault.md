---
title: "Why does this segfault?"
date: 2009-02-09
forum: Programming Talk
---

### Post by tom66 on 2009-02-09
Can't work out why this segfaults:

```

/**
 * Returns a basic fill color as a pointer.
 * @params	red, green, blue, alpha
 * @returns	fill style pointer
 */
struct P_FillStyle *create_fill_color(double red, double green, double blue, double alpha)
{
    struct P_FillStyle *fillPtr;
    
    fillPtr->type = FILL_SOLID;
    fillPtr->fillColor->cRed = red;
    fillPtr->fillColor->cGreen = green;
    fillPtr->fillColor->cBlue = blue;
    fillPtr->fillColor->alpha = alpha;
    
    return fillPtr;
}

```

Segmentation fault occurs at [FONT="Courier New"]fillPtr->type = FILL_SOLID;[/FONT].

Any help appreciated...!

---

### Post by Simian Man on 2009-02-09
You create a pointer "fillPtr" on the stack.  This is a local variable that holds a memory location.  Since you don't initialize this pointer, it could have *any* memory address stored in it.  You then attempt to dereference this pointer and put stuff there.  This is basically writing to random memory - of course you get a segfault!

I'd suggest reading up on how pointers work a bit.  To store something in a pointer, you have to point it at a valid location (either an object on the stack or at memory returned from malloc).

Hope that makes sense.

---

### Post by tom66 on 2009-02-09
Huh. Well, a manual I read somewhere said that a basic pointer is initialized with a random (and free) address when first created, unless it is explicitly set. I guess it's wrong, or I didn't understand it correctly.

---

### Post by tom66 on 2009-02-09
It still segfaults, even if the memory is [FONT="Courier New"]malloc()'d[/FONT]:

```

/**
 * Returns a basic fill color as a pointer.
 * @params	red, green, blue, alpha
 * @returns	fill style pointer
 */
struct P_FillStyle *create_fill_color(double red, double green, double blue, double alpha)
{
    struct P_FillStyle *fillPtr;
    fillPtr = (struct P_FillStyle *)malloc(sizeof(struct P_FillStyle) * 1);
    
    fillPtr->type = FILL_SOLID;
    fillPtr->fillColor->cRed = red;
    fillPtr->fillColor->cGreen = green;
    fillPtr->fillColor->cBlue = blue;
    fillPtr->fillColor->alpha = alpha;
    
    return fillPtr;
}

```

Thanks for your help...

---

### Post by sujoy on 2009-02-09
you need to allocate memory before you can go around pointing at them.
EDIT: nevermind... too late :P

---

### Post by PandaGoat on 2009-02-09
> **tom66 said:**
> It still segfaults, even if the memory is [FONT="Courier New"]malloc()'d[/FONT]:

```

/**
 * Returns a basic fill color as a pointer.
 * @params	red, green, blue, alpha
 * @returns	fill style pointer
 */
struct P_FillStyle *create_fill_color(double red, double green, double blue, double alpha)
{
    struct P_FillStyle *fillPtr;
    fillPtr = (struct P_FillStyle *)malloc(sizeof(struct P_FillStyle) * 1);
    
    fillPtr->type = FILL_SOLID;
    fillPtr->fillColor->cRed = red;
    fillPtr->fillColor->cGreen = green;
    fillPtr->fillColor->cBlue = blue;
    fillPtr->fillColor->alpha = alpha;
    
    return fillPtr;
}

```

Thanks for your help...

You have to allocate memory for all pointers, including the pointers in the struct.  The initial allocation only allocated memory to store the pointer (4 bytes)--not what it points to.

So, you have to do fillPtr->fillColor = (. . .)malloc(. . .);

---

### Post by stroyan on 2009-02-09
Now you assign to the address pointed to by fillPtr->fillColor
fillPtr->fillColor->cRed = red;
But you don't initialize fillColor to any valid address.

---

### Post by tom66 on 2009-02-09
Thanks, didn't think of that! :)

---

### Post by weresheep on 2009-02-09
Just for completeness, its good practice to check the return value of system/library calls (well, ALL function calls that might not succeed). Malloc might not return a valid pointer.

```

int *p = malloc(100 * sizeof(int));

if (!p) {
  perror("Failed to allocate memory");
  exit(EXIT_FAILURE);
}

```

I guess you could argue about the usefulness of checking for memory allocation in linux but I still think its a good habbit.

In addition, whenever you malloc some memory, you have to remember to free it. In the above case the code calling the create_fill_color() function has the responsibility of releasing the memory once it is no longer required (this should be noted in the nice JavaDoc style function description comment).

Again, get into the habit of doing the right thing. Memory leaks are a real pain to track down.

I give you my standard advice. Install manpages-dev and read the manuals for these library calls e.g.

```

man 3 malloc

```

-weresheep

---

