---
title: "C Programming: Cast double to void?"
date: 2008-10-07
forum: Programming Talk
---

### Post by smarkmoses on 2008-10-07
Hello,

I was just wondering if it's possible to cast a double value into a void pointer.  For example, I've used the code below to do it with int values, which seems to work fine, but for some reason I can't get it to work for doubles.  Does anyone have any suggestions?

Thanks!

```
#include <stdlib.h>

#include <stdio.h>

int main () {
void **p;
int q;

p = calloc(3, sizeof(int*));

q = 1;

p[0] = (void*)q;
p[1] = (void*)2;

printf("%d\n", (int)p[0]);
printf("%d\n", (int)p[1]);

return EXIT_SUCCESS;

}
```

---

### Post by nvteighen on 2008-10-07
> **smarkmoses said:**
> Hello,

I was just wondering if it's possible to cast a double value into a void pointer.  For example, I've used the code below to do it with int values, which seems to work fine, but for some reason I can't get it to work for doubles.  Does anyone have any suggestions?

Thanks!

```
#include <stdlib.h>

#include <stdio.h>

int main () {
void **p;
int q;

p = calloc(3, sizeof(int*));

q = 1;

p[0] = (void*)q;
p[1] = (void*)2;

printf("%d\n", (int)p[0]);
printf("%d\n", (int)p[1]);

return EXIT_SUCCESS;

}
```

That's pointless. You declare p as (void **), i.e. as an array of (void *). So, any element inside will have to be (void *), but (void *) is just a joker for any kind of **pointer** type, so you don't need any cast to **write a (void *)**, but you have to cast to [B]read from a (void *)
[/B]

---

### Post by smarkmoses on 2008-10-07
I always seem to get the error message "warning: assignment makes pointer from integer without a cast", so that's why i was trying to cast both.

I'm just trying to get the void pointer to accept any kind of value, whether it be int or double...

---

### Post by Canis familiaris on 2008-10-07
Did a certain amount of rewriting:

```
[color=#BC7A00]#include <stdio.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color] () {
[color=#B00040]void[/color] [color=#666666]**[/color]p;
[color=#B00040]int[/color] q;

p [color=#666666]=[/color] calloc([color=#666666]3[/color], [color=#008000]**sizeof**[/color]([color=#B00040]int[/color][color=#666666]*[/color]));

q [color=#666666]=[/color] [color=#666666]1[/color];

p[[color=#666666]0[/color]] [color=#666666]=[/color] ([color=#B00040]void[/color][color=#666666]*[/color])q;
p[[color=#666666]1[/color]] [color=#666666]=[/color] ([color=#B00040]void[/color][color=#666666]*[/color])[color=#666666]2[/color];

printf([color=#BA2121]"%d[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], ([color=#B00040]int[/color])p[[color=#666666]0[/color]]);
printf([color=#BA2121]"%d[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], ([color=#B00040]int[/color])p[[color=#666666]1[/color]]);

[color=#008000]**return**[/color] [color=#666666]0[/color];

}

```

Is this the output you want?
```
1
2


```

Corrected now.

---

### Post by smarkmoses on 2008-10-07
Yes it is, thanks, but how would I do that for a double value?  I've tried something like below, but I just get "error: cannot convert to a pointer type."

```
#include <stdlib.h>

#include <stdio.h>

int main () {
void **p;
double q;

p = calloc(3, sizeof(double*));

q = 1.00;

p[0] = (void*)q;
p[1] = (double*)2;

printf("%lf\n", *(double*)p[0]);
printf("%lf\n", *(double*)p[1]);

return EXIT_SUCCESS;

}
```

---

### Post by bfhicks on 2008-10-07
You'll need to create your own type to be able to cast it. It's a pain to do and I'm not exactly sure of why we have to do it.

Anyhow, here's a little example that casts as a void* and reinterpret_cast as a double*

```
[color=#BC7A00]#include <stdlib.h>
#include <stdio.h>
[/color]
class DOUBLE
{
[color=#A0A000]public:[/color]
	[color=#B00040]double[/color] val;
};

[color=#B00040]int[/color] [color=#0000FF]main[/color] () 
{
	DOUBLE[color=#666666]*[/color] D [color=#666666]=[/color] new DOUBLE;
	D[color=#666666]->[/color]val [color=#666666]=[/color] [color=#666666]1.30[/color];
	
	[color=#B00040]void[/color][color=#666666]*[/color] p [color=#666666]=[/color] ([color=#B00040]void[/color][color=#666666]*[/color])D;
	
	DOUBLE[color=#666666]*[/color] P [color=#666666]=[/color] (DOUBLE[color=#666666]*[/color])p;
	[color=#008000]**if**[/color] (P)
		printf([color=#BA2121]"%lf[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color],P[color=#666666]->[/color]val);
		
	[color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

```

>./voidpointer
1.300000
>Exit code: 0

```
You'll have to essentially overload all the operators also to be of any use.

---

### Post by gnusci on 2008-10-07
Check this out, it seems an step forward :)

[PHP]
#include <stdlib.h> 
#include <stdio.h> 

int main (void) {

 void **p;
 double q;
 double m;
 double * s;

 p = (void*) calloc(3, sizeof(double*));

 q = 1.234;
 p[0] = (double*)&q;

 m = 3.246;
 p[1] = (double*)&m;

 s = (double*)p[0];
 printf("%lf\n",*s);
 s = (double*)p[1];
 printf("%lf\n",*s);

 free(p);

 return EXIT_SUCCESS;
}

[/PHP]

---

### Post by bfhicks on 2008-10-07
Forget my previous post, it was incorrect.

```

double* d = new double(1.00);
void* p = (void*)d;

printf("%ld\n",(*(double*)p));

```

That will work.

---

### Post by smarkmoses on 2008-10-08
Thanks everyone for the help!  gnusci, that's exactly what I needed!!

---

### Post by dwhitney67 on 2008-10-08
> **smarkmoses said:**
> ...

I'm just trying to get the void pointer to accept any kind of value, whether it be int or double...

In some circles, it is considered bad programming to rely on void types.  Yet the C library seems to use them on occasion (e.g. the memcpy function).

Here's some working code you can play with:
[PHP]
#include <string.h>
#include <assert.h>


void my_memcpy( void *dest, const void *src, const size_t bytes )
{
  for ( register size_t i = 0; i < bytes; ++i )
  {
    ((char*)dest)[i] = ((const char*)src)[i];
  }
}


int main()
{
  int val1;
  int val2 = 20;

  double val3;
  double val4 = 10.0;

  my_memcpy( &val1, &val2, sizeof(int) );
  my_memcpy( &val3, &val4, sizeof(double) );

  assert( val1 == val2 );
  assert( val3 == val4 );

  return 0;
}[/PHP]

---

