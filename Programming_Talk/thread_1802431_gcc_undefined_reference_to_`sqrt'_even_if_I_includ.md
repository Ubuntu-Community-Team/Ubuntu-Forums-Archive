---
title: "gcc: undefined reference to `sqrt' even if I included math.h"
date: 2011-07-11
forum: Programming Talk
---

### Post by skytreader on 2011-07-11
So I have this C code:

```

#include<stdio.h>
#include<stdlib.h>
#include<math.h>

double dist(int x1, int y1, int x2, int y2){
	double dx = (double) (x1 - x2);
	double dy = (double) (y1 - y2);
	double xx = pow(dx, 2.0);
	double yy = pow(dy, 2.0);
	double distance = sqrt(xx + yy);
	return distance;
}

```

But gcc complains that:

```

/tmp/cck84m3o.o: In function `dist':
astar.c:(.text+0x5d): undefined reference to `sqrt'
collect2: ld returned 1 exit status

```

I don't get why gcc would say that. Anything I missed?

---

### Post by JupiterV2 on 2011-07-11
You need to link the math library. Use -lmath or -lm (short-hand) flags.

---

### Post by dwhitney67 on 2011-07-12
> **skytreader said:**
> 
I don't get why gcc would say that. Anything I missed?

That's because math.h is merely a header file with function declarations.  It does NOT include the implementation of the functions themselves; those are located elsewhere, namely in libm.so

If you read the man-page for sqrt, you will note that it states to link with -lm (as JupiterV2 has already indicated).

---

