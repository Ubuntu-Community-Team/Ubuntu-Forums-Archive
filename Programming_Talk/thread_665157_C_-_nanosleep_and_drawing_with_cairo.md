---
title: "C - nanosleep and drawing with cairo"
date: 2008-01-11
forum: Programming Talk
---

### Post by xl_cheese on 2008-01-11
I can't figure out how to use the nanosleep function when drawing with the cairo lib.

Basically I want to draw a line, sleep ~.5s, and then draw another line.  What I'm seeing is there is no delay at all.  Both lines are drawn at the same time.

Any help would be appreciated and I'll note that I'm a total coding noob so if you could dumb it down for that that would be great.

```
			ge_cairo_rounded_rectangle (cr, 0, 0, width-1, height-1, radius+1, params->corners);
			ge_shade_color (&params->parentbg, 0.96, &glow);
			ge_cairo_set_color (cr, &glow);
			cairo_stroke (cr);
nanosleep (500000000, NULL);
			ge_cairo_rounded_rectangle (cr, 1, 1, width-2, height-2, radius+1, params->corners);
			ge_shade_color (&params->parentbg, 0.92, &glow);
			ge_cairo_set_color (cr, &glow);
			cairo_stroke (cr);

```
Thanks!

---

### Post by wolfbone on 2008-01-12
500000000 is not a 'struct timespec *'

[PHP]
struct timespec * intvl = (struct timespec *) malloc(sizeof(struct timespec));
 
intvl->tv_sec = 0L;

intvl->tv_nsec = 500000000L;

....

nanosleep(intvl,NULL);
[/PHP]

---

### Post by wdk on 2008-01-12
If you really want/need to use nanosleep, you will first need to initialize a timespec structure containing the appropriate sleep value.

The timespec struct is defined as:

```

struct timespec {
time_t     tv_sec;     /*seconds*/
long        tv_nsec;   /*nanoseconds*/
}

```

so, you will need to insert something to the effect of:

```

struct timespec t;

/* other code */

t.tv_sec = 0.0
t.tv_nsec = 500000000;
nanosleep(&t, NULL);

```

check the nanosleep man page for more exciting details...

Hope this helps!

---

### Post by xl_cheese on 2008-01-12
Thanks guys!

The delay works.  Only problem is that it delays then draws both rectangles at the same time instead of 1st rectangle, delay, and 2nd rectangle.

---

### Post by amo-ej1 on 2008-01-12
perhaps usleep would be a simpler solution (man usleep) this simply eats the amount of microseconds to sleep as a first parameter.

---

### Post by wolfbone on 2008-01-12
> **xl_cheese said:**
> Thanks guys!

The delay works.  Only problem is that it delays then draws both rectangles at the same time instead of 1st rectangle, delay, and 2nd rectangle.

Probably because the 'drawing' is being done to the 'cr', which will be just some piece of memory. I don't know cairo (or ge_cairo, whatever that is) so I don't know how you'd  force an on-screen update before the nanosleep with it.

---

