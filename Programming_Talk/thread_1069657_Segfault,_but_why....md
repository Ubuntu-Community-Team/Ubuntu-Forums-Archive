---
title: "Segfault, but why...?"
date: 2009-02-14
forum: Programming Talk
---

### Post by tom66 on 2009-02-14
Any of the cairo lines segfaults:

```

/**
 * Sets up the cairo structure for a stoke style, ready for stroking the path.
 * @params	cairo struct, stroke style
 * @returns	nothing (void)
 */
void setup_cairo_for_stroke(cairo_t *cr, struct P_StrokeStyle *strokeStyle)
{
    double *dashes;
    int num_dashes;
    
    if(strokeStyle == NULL)
    {
        __WARNING("Stroke style is NULL, doing no setup. ");
    }
    else
    {
        get_dash_array(strokeStyle->dash, &dashes, &num_dashes);
        cairo_set_source_rgba(cr, 0.0, 0.0, 0.0, 1.0);
        cairo_set_line_width(cr, strokeStyle->lineWidth);
        cairo_set_dash(cr, dashes, num_dashes, 0.0);
    }
}

```

All other cairo lines are fine, they have no problem. This is how the function is called:

```

/**
 * Handles drawing a basic shape which contains points in a polygon.  
 * @params	cairo resource, object, zoom (0.0 to +Inf), 
 *              pageToCanvasMargin, inverted pageToCanvasMargin, 
 *              viewport X (0.0 .. 1.0), viewport Y (0.0 .. 1.0), 
 *              render size X, render size Y
 * @returns	nothing (void)
 */
void draw_shape(cairo_t *cr, struct P_Object *obj, 
    double zoom, double pageToCanvasMargin, double pageToCanvasMarginInv, 	/* Margin & Zoom */
    double viewX, double viewY, 						/* Viewport X/Y */
    double rsx, double rsy							/* Render Size X/Y */
    )
{
    int idx;
    double x, y;
    
    switch(obj->type)
    {
        case O_SHAPE:
            __DEBUG("Rendering shape. ");
            
            /* Run through every point in the shape, and create a path for it using cairo. */
            for(idx = 0; idx < obj->shapeRef->pointCount; idx++)
            {
                /* This has to take everything into account: zoom, viewport X, width/height of the
                   shape, page -> canvas margins, shape coordinates... that's why it's so complicated. */
                x = (viewX * rsx * zoom) + 
                    ((((obj->shapeRef->polygon->pointsX[idx] * obj->shapeRef->width) * rsx) * zoom) *
                        pageToCanvasMarginInv) + (pageToCanvasMargin * zoom * rsx);
                y = (viewY * rsy * zoom) + 
                    ((((obj->shapeRef->polygon->pointsY[idx] * obj->shapeRef->height) * rsy) * zoom) *
                        pageToCanvasMarginInv) + (pageToCanvasMargin * zoom * rsy);
                
                sprintf(__buffer, "For point #%d, going to coordinates (X: %f, Y: %f)", idx, x, y);
                __DEBUG(__buffer);
                
                if(idx == 0)
                    cairo_move_to(cr, x, y);
                else
                    cairo_line_to(cr, x, y);
            }
            
            if(obj->fStyleRef != NULL)
            {
                if(obj->fStyleRef->type == FILL_SOLID)
                {
                    cairo_set_source_rgba(cr, obj->fStyleRef->fillColor->cRed,
                                              obj->fStyleRef->fillColor->cGreen,
                                              obj->fStyleRef->fillColor->cBlue,
                                              obj->fStyleRef->fillColor->alpha);
                }
                
                cairo_fill_preserve(cr);
            }
            
            if(obj->sStyleRef != NULL)
            {
                setup_cairo_for_stroke(cr, obj->sStyleRef);
                cairo_stroke(cr);
            }
            
            break;
    }
}

```

(and this function has no problem with the cairo functions)

Any help appreciated...
Thanks!

---

### Post by dwhitney67 on 2009-02-14
I am not familiar with cairo; could you please post the API for the function get_dash_array()?

Also, in draw_shape(), you access 'obj' without even checking to see if it is non-null.

Anyhow, use 'gdb', or it's GUI front-end, 'ddd', to debug your program.  There are too many unanswered possibilities with the code you posted.

---

### Post by tom66 on 2009-02-14
I debugged using gdb, it says SIGSEGV in *cairo_set_source_rgba* or any other cairo function (in the *setup_cairo_for_stroke* function) if the other cairo lines are commented out. 

Here is the dash array function. SAFE_MALLOC is a malloc statement which checks to see if the pointer is valid. If it is not, it exits the program to prevent a later crash.

```

/**
 * Get the dash array for a particular stroke style.
 * @params	dash type, pointer to dash array, pointer to size of dash array
 * @returns	nothing (void)
 */
void get_dash_array(int dashType, double *dashArray, int *sizeOfDashArray)
{
    SAFE_MALLOC(myDashArray, double, 25);
    
    if(dashType == ST_SOLID)
        sizeOfDashArray = 0;
    else
    {
        switch(dashType)
        {
            case ST_DASH_1_2:
                sizeOfDashArray = 2;
                dashArray[0] = 1.0;
                dashArray[1] = 1.0;
                break;
            
            case ST_DASH_1_3:
                sizeOfDashArray = 2;
                dashArray[0] = 0.33;
                dashArray[1] = 0.67;
                break;
        }
    }
    
    dashArray = &myDashArray;
}

```

Here is the gdb output:

```

GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) run
Starting program: /home/thomas/GtkPresentationProgram/a.out 
[Thread debugging using libthread_db enabled]
  Debug (draw.c:25 [zorder_sort]): o1 (0x9610700) and o2 (0x9610804) have the same zOrder, sorting by address. 
  Debug (draw.c:317 [render_objects_in_slide]): zo: -9999999, t: 2
  Debug (draw.c:323 [render_objects_in_slide]): Rendering page... 
  Debug (draw.c:317 [render_objects_in_slide]): zo: -9999998, t: 1
  Debug (draw.c:333 [render_objects_in_slide]): Rendering slide canvas... 
  Debug (draw.c:317 [render_objects_in_slide]): zo: -9999997, t: 3
  Debug (draw.c:354 [render_objects_in_slide]): Rendering background... 
  Debug (draw.c:101 [fill_to_rectangle]): Offset: 0.000000, offZ 1, offO 0
  Debug (draw.c:101 [fill_to_rectangle]): Offset: 1.000000, offZ 1, offO 1
  Debug (draw.c:111 [fill_to_rectangle]): Adding stop 0, offset 0.000000. 
  Debug (draw.c:111 [fill_to_rectangle]): Adding stop 1, offset 1.000000. 
  Debug (draw.c:317 [render_objects_in_slide]): zo: 0, t: 0
Warning (draw.c:383 [render_objects_in_slide]): Unknown render object of type 0, in zOrder level of 0. Ignoring. 
  Debug (draw.c:317 [render_objects_in_slide]): zo: 0, t: 4
  Debug (draw.c:217 [draw_shape]): Rendering shape. 
  Debug (draw.c:232 [draw_shape]): For point #0, going to coordinates (X: 116.000000, Y: 87.000000)
  Debug (draw.c:232 [draw_shape]): For point #1, going to coordinates (X: 884.000000, Y: 87.000000)
  Debug (draw.c:232 [draw_shape]): For point #2, going to coordinates (X: 884.000000, Y: 663.000000)
  Debug (draw.c:232 [draw_shape]): For point #3, going to coordinates (X: 116.000000, Y: 663.000000)
[New Thread 0xb7421700 (LWP 3148)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7421700 (LWP 3148)]
0xb79deb4a in cairo_set_source_rgba () from /usr/lib/libcairo.so.2
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```

Thanks for pointing out that I didn't check for NULL in the draw_shape function. I'll sort that out after I sort this out.

---

### Post by dwhitney67 on 2009-02-14
I believe I see the problem; it's the declaration and the implementation of get_dash_array().

I do not have much time to dwell on an explanation on the code below, but try to give it a shot:

```

#include <stdlib.h>


#define ST_SOLID       0       // I made this up
#define ST_DASH_1_2    1       // I made this up
#define ST_DASH_1_3    2       // I made this up


void get_dash_array(int dashType, double** dashArray, int* sizeOfDashArray)
{
  *sizeOfDashArray = 0;

  if (dashType == ST_SOLID) return;

  *dashArray = calloc(2, sizeof(double));

  if (*dashArray == 0) return;

  *sizeOfDashArray = 2;

  switch (dashType)
  {
    case ST_DASH_1_2:
        (*dashArray)[0] = 1.0;
        (*dashArray)[1] = 1.0;
         break;

    case ST_DASH_1_3:
        (*dashArray)[0] = 0.33;
        (*dashArray)[1] = 0.67;
        break;   
  }
}

int main()
{
  int     dashType = ST_DASH_1_2;
  double* dashArray = 0;
  int     dashArraySize = 0;

  get_dash_array(dashType, &dashArray, &dashArraySize);

  ...

  if (dashArray && dashArraySize > 0) free(dashArray);
}

```

---

### Post by tom66 on 2009-02-14
I modified the code according to your help. It no longer segfaults, but it never gets past the draw_shape function and gets stuck there... 

```

/**
 * Get the dash array for a particular stroke style.
 * @params	dash type, pointer to dash array, pointer to size of dash array
 * @returns	nothing (void)
 */
void get_dash_array(int dashType, double *dashArray, int *sizeOfDashArray)
{
    SAFE_MALLOC(myDashArray, double, 25);
    
    if(dashType == ST_SOLID)
        sizeOfDashArray = 0;
    else
    {
        switch(dashType)
        {
            case ST_DASH_1_2:
                *sizeOfDashArray = 2;
                myDashArray[0] = 1.0;
                myDashArray[1] = 1.0;
                break;
            
            case ST_DASH_1_3:
                *sizeOfDashArray = 2;
                myDashArray[0] = 0.33;
                myDashArray[1] = 0.67;
                break;
        }
    }
    
    dashArray = &myDashArray;
}

```

---

### Post by dwhitney67 on 2009-02-14
Use gdb, or ddd (I strongly suggest using this app over plain-vanilla gdb), and step through your code.  Perhaps the problem will reveal itself.

Your new code, for get_dash_array(), looks better.  I'm still not sure what the hard-coded numeral 25 is supposed to represent.

Anyhow, I do not have the experience with cairo, nor do I have any desire to become intimate with it.  You will need to solve this problem on your own, step-by-step; with all of the memory allocations, it is no wonder there's lots of trouble.  I wouldn't be half surprised if your application also has memory leaks.

---

### Post by tom66 on 2009-02-14
I use 25 because that's likely to be the maximum dash size I'll need. It's a bit of 'safety', if you know what I mean.

---

### Post by tom66 on 2009-02-14
Fixed...

```

/**
 * Sets up the cairo structure for a stoke style, ready for stroking the path.
 * @params	cairo struct, stroke style
 * @returns	nothing (void)
 */
void setup_cairo_for_stroke(cairo_t *cr, struct P_StrokeStyle *strokeStyle)
{
    double *dashes;
    int num_dashes;
    
    if(strokeStyle == NULL)
    {
        __WARNING("Stroke style is NULL, doing no setup. ");
    }
    else
    {
        get_dash_array(strokeStyle->dash, &dashes, &num_dashes);
        cairo_set_source_rgba(cr, 0.0, 0.0, 0.0, 1.0);
        cairo_set_line_width(cr, strokeStyle->lineWidth);
        cairo_set_dash(cr, &dashes, num_dashes, 0.0);
    }
}

```

Note the '&' before *dashes* in the *cairo_set_dash* function.

---

### Post by dwhitney67 on 2009-02-14
Now that you point it out, it seems so obvious.

I presume that you fixed/changed the declaration of get_dash_array to be:
```

void get_dash_array(int dashType, double **dashArray, int *sizeOfDashArray)
{
  ...

  *dashArray = myDashArray;
}

```

---

