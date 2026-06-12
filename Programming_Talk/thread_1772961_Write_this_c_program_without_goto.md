---
title: "Write this c program without goto"
date: 2011-06-01
forum: Programming Talk
---

### Post by adit on 2011-06-01
This is my c program
```
#include <stdio.h>
int main (void) {
  int i,j,k;
  for (i=1;i<=3;i++) {
    for (j=1;j<=3;j++) {
      for (k=1;k<=3;k++) {
        if (i==3 && j==3 && k==3) {
          goto out;
        }
        else {
          printf ("%d%d%d\n",i,j,k);
        }
      }
    }
  } 
  out:
  printf ("Out of the loop at last!\n");
  return 0;
}

```This is the output from the program
```
111
112
113
121
122
123
131
132
133
211
212
213
221
222
223
231
232
233
311
312
313
321
322
323
331
332
Out of the loop at last!
```
How to write the same program without goto?

---

### Post by dwhitney67 on 2011-06-01
Set each of your indexes to 4.

---

### Post by Arndt on 2011-06-01
> **adit said:**
> This is my c program
```
#include <stdio.h>
int main (void) {
  int i,j,k;
  for (i=1;i<=3;i++) {
    for (j=1;j<=3;j++) {
      for (k=1;k<=3;k++) {
        if (i==3 && j==3 && k==3) {
          goto out;
        }
        else {
          printf ("%d%d%d\n",i,j,k);
        }
      }
    }
  } 
  out:
  printf ("Out of the loop at last!\n");
  return 0;
}

```This is the output from the program
```
111
112
113
121
122
123
131
132
133
211
212
213
221
222
223
231
232
233
311
312
313
321
322
323
331
332
Out of the loop at last!
```
How to write the same program without goto?

Put the loops in a separate function, and return from it.

---

### Post by adit on 2011-06-01
> Put the loops in a separate function, and return from it.
Can you post the complete solution?

---

### Post by gusnan on 2011-06-01
This smells a whole lot like homework.

---

### Post by adit on 2011-06-01
> This smells a whole lot like homework.
Not a homework.  I am a beginner.  If I have the complete source code it will be easy to understand how to
"put the loops in a separate function, and return from it."

---

### Post by doas777 on 2011-06-01
the traditional answer for short-circuiting a loop is with teh break statement, but that can be dangerous in some cases, and worthless in yours due to the way the loops nest.

as dwhitney says, if you find what you are looking for, set i/k/j all to 4. that way it will stop looping on the subsequent iteration. then just print your message. drop the goto and the label, and it should work fine.

---

### Post by adit on 2011-06-01
These quotes taken from some online tutorials.> Use of the goto statement violates the rules of structured programming.
> The only place in C where to use goto is to break out of some large nested loop
What is more elegant way (as far as the above c program is concerned)
1) To use goto
2) Not to use goto
What will a good programmer do in my case?

---

### Post by dwhitney67 on 2011-06-01
> **adit said:**
> These quotes taken from some online tutorials.

What is more elegant way (as far as the above c program is concerned)
1) To use goto
2) Not to use goto
What will a good programmer do in my case?

I was being a little sarcastic with my previous comment.

However, I need to know why are you checking to see if _each_ of the indexes are 3?  Typically one breaks from a loop if a single condition is met.  Since you are checking all indexes for the value 3, it would seem best to do something like:
```

for (int i = 1; **i < 3**; ++i)
{
   for (int j = 1; **j < 3**; ++j)
   {
      for (int k = 1; **k < 3**; ++k)
      {
         printf("%d%d%d\n", i, j, k);
      }
   }
}

```
To summarize, the goto is not necessary if you correct the condition statements to use less-than in lieu of less-than-or-equal.

---

### Post by JupiterV2 on 2011-06-01
dwhitney67 does a good job of showing you a better solution. You'll note that the loop is easier to read and therefore more clear about what it does. Additionally, with your code, you actually miss a final iteration. I would suspect your final number should have been 333 and not 332.

[EDIT]
Actually, dwhitney67's solution would print 222-333 instead of the intended 111-333. Each loop could be one of the following:
```
for (i = 0; i < 3; ++i) /* method 1 */
for (k = 1; k <= 3; k++) /* method 2 */
for (j = 1; j < 4; j++) /* method 3 */
```
[/EDIT]

There is an alternative to your method too, which uses a single loop:

```

for (i = 1; i <= 27; i++)
  {
    int j = (i % 3) + 1;
    int k = (i % 9) + 1;

    printf ("%d%d%d\n", k, j, i);
  }
```

I THINK that should work. I can't test it right now. It's just a silly example but there are often multiple ways to solve a single problem. It strikes me that there could be a fun recursive way of doing it too.

And I can't think of any time where I'd ever use a goto...makes code too confusing.

---

### Post by StephenF on 2011-06-01
The loops all end on the next iteration anyway so you can just use the if condition to short circuit the print statement and let all the loops end naturally.
```

#include <stdio.h>
int main (void) {
  int i,j,k;
  for (i=1;i<=3;i++)
    for (j=1;j<=3;j++)
      for (k=1;k<=3;k++)
        if (i + j + k < 9)
          printf ("%d%d%d\n",i,j,k);

  printf ("Out of the loop at last!\n");
  return 0;
}

```

---

### Post by zobayer1 on 2011-06-01
Looks like you have forgot that C has something called function and that can return from any situation.... just do that in a function and replace goto with a return...

---

### Post by Reiger on 2011-06-01
Just an observation, what if we comment the code with a few reminders:
```

int i,j,k;
  /* impose limit: 1<=i<=3 */
  for (i=1;i<=3;i++) {
    /* impose limit: 1<=j<=3 */
    for (j=1;j<=3;j++) {
      /* impose limit: 1<=k<= 3 */
      for (k=1;k<=3;k++) {
        /*
         * this condition is evaluated every time and 
         * will be true only once so we can
         * incorporate it in the for() loop condition itself...
         */
        if (i==3 && j==3 && k==3) {
          goto out;
        }
        else {
          printf ("%d%d%d\n",i,j,k);
        }
      }
    }
  }

```

Leads to:
```

int i,j,k;
  for (i=1;i<=3;i++) {
    for (j=1;j<=3;j++) {
      for (k=1;k<3 || (k==3 && i!=3 && j!=3);k++) {
        printf ("%d%d%d\n",i,j,k);
      }
    }
  }

```

Or (given i,j and k are all <=3):
```

int i,j,k;
  for (i=1;i<=3;i++) {
    for (j=1;j<=3;j++) {
      for (k=1;k<=3 && (k+i+j)<9;k++) {
        printf ("%d%d%d\n",i,j,k);
      }
    }
  }

```

---

