---
title: "Segmentation Fault in C"
date: 2013-08-28
forum: Programming Talk
---

### Post by rushikesh988 on 2013-08-28
I am trying to create the hamming window function ,I am unable to see why I am getting segmentation fault

```
#include <math.h>
#include <stdio.h>

int debug=1;
void hamming(int n)
{
double hamm[1][n],x[1][n];
int half,i;

if(n%2)
{
 half = (n+1)/2;
}

else{
 half = (n+1)/2;
}
for(i=0;i<half;i++)
{
  x[1][i]=i/((double)n-1);
  hamm[1][i]=0.54 - 0.46 * cos (2.0*M_PI*x[1][i]/((double)half-1)) ;
}
if(debug)
for(i=0;i<half;i++)
    {
         printf(" hamming window=%g \n",hamm[1][i]);

        }
}
int main()
{
hamming(100);


return 0;
}






```


Please tell me where I am wrong

---

### Post by edouardtavinor on 2013-08-28
You need to malloc space in the arrays before using them :)

```

hamm = malloc(n*sizeof(int));

```

otherwise hamm in just a pointer to nothing.

---

### Post by spjackson on 2013-08-28
Are you new to C or to arrays in C?

```

double hamm[1][n],x[1][n];

```Each of hamm and x is a 2 dimensional array of double. The maximum valid subscripts are hamm[0][n-1].

So when you write
```

  x[1][i]=i/((double)n-1);

```you are writing outside the array bounds.

The simplest correction is
```

double hamm[2][n],x[2][n];

```but that isn't really a good choice because the first element of each array is never used. It's better to leave this decaration as it is and replace all other occurrences of hamm[1] with hamm[0], and x[1] with x[0].

Better still, why use a 2 dimensional array when a single dimension is all you need? Thus:
```

#include <math.h>
#include <stdio.h>

int debug=1;
void hamming(int n)
{
double hamm[n],x[n];
int half,i;

if(n%2)
{
 half = (n+1)/2;
}

else{
 half = (n+1)/2;
}
for(i=0;i<half;i++)
{
  x[i]=i/((double)n-1);
  hamm[i]=0.54 - 0.46 * cos (2.0*M_PI*x[i]/((double)half-1)) ;
}
if(debug)
for(i=0;i<half;i++)
    {
         printf(" hamming window=%g \n",hamm[i]);

        }
}
int main()
{
hamming(100);


return 0;
}

```

Finally, what is the purpose of this conditional when both branches do exactly the same thing?
```

if(n%2)
{
 half = (n+1)/2;
}

else{
 half = (n+1)/2;
}

```I am not familiar with this function, so I don't know what should be happening here.

---

### Post by trent.josephsen on 2013-08-28
@edouard: Those are VLAs, not pointers, and are allocated automatically on the stack. Assigning to one of them is a constraint violation.

Format your code for readability, especially when asking for help with it. I'll assume you meant something like this:
```
#include <math.h>
#include <stdio.h>

int debug = 1;
void hamming(int n)
{
    double hamm[1][n], x[1][n];
    int half, i;

    if (n % 2) {
        half = (n + 1) / 2;
    } else {
        half = (n + 1) / 2;
    }
    for (i = 0; i < half; i++) {
        x[1][i] = i / ((double) n - 1);
        hamm[1][i] =
            0.54 - 0.46 * cos(2.0 * M_PI * x[1][i] / ((double) half - 1));
    }
    if (debug) {
        for (i = 0; i < half; i++) {
            printf(" hamming window=%g \n", hamm[1][i]);
        }
    }
}

int main()
{
    hamming(100);
    return 0;
}
```

In addition to what spjackson said already, I'll observe that x is never used outside of the loop, and so you could as easily use a regular double for that temporary value -- unless x is to eventually be part of your output -- it's been a few years since I took DSP. Furthermore, your loop only goes from 0 to half, and so for n=100 you fill only hamm[0] through hamm[49]. Did you mean to loop over n instead?

---

### Post by rushikesh988 on 2013-08-28
Thank You all !
by using your replies I got my program solved.

---

### Post by ofnuts on 2013-08-29
> **rushikesh988 said:**
>  I got my program solved.
Nice freudian slip :)

---

### Post by edouardtavinor on 2013-09-02
I've never understood the difference between VLAs and pointers in C. is it that a pointer has the address NULL before a value is assigned to it, while the VLA has an (admittedly useless) address on the stack before space is malloced?

--edit--

nope, that can't be it. a pointer is an address containing an address... odd.  so what is the difference then?

--edit--

oh, just read up on VLAs on stackoverflow. I didn't know C supported anything that complicated. They seem to support a sizeof() function (which i didn't know existed--i thought that was dealt with by the pre-processor) and memory allocated for a VLA is automatically freed when the function ends, which seems to make it impossible to return a VLA as an argument.

---

### Post by ofnuts on 2013-09-02
A pointer can point to many things, including a VLA. These things usually need to be allocated (malloc) and their address stored in the pointer variabl[B]e.

sizeof[/B] is not a function but an operator (and can be used without parentheses).

---

### Post by trent.josephsen on 2013-09-02
> **edouardtavinor said:**
> oh, just read up on VLAs on stackoverflow. I didn't know C supported anything that complicated. They seem to support a sizeof() function (which i didn't know existed--i thought that was dealt with by the pre-processor) and memory allocated for a VLA is automatically freed when the function ends, which seems to make it impossible to return a VLA as an argument.

VLAs (variable length arrays, for anyone just joining the conversation) are a little weird. Basically they're just like ordinary arrays, but...

1) VLAs can only be **automatic** -- which means declared inside a function without the 'static' keyword. Like any other automatic array, a VLA's memory becomes indeterminate when it goes out of scope, so a function must not return a (pointer to a) local VLA. It's still perfectly acceptable to pass a (pointer to a) VLA as an argument to a function, because pointers don't care what kind of memory they point to. (VLAs also cannot be struct members, which disallows one trick that can be used for returning regular arrays.)

2) VLAs use the same declaration syntax as "ordinary" arrays, so the only way to tell if an array declaration declares a VLA is to see if the thing between the [brackets] is a constant expression. This is not always straightforward; for instance,
```
int array[foo() + 1];
```
declares array as a VLA if foo() is a function call, but as an ordinary array if foo() is a macro that expands to a compile-time constant.

3) As you discovered, VLAs defer execution of the **sizeof** operator to runtime, because the compiler can't know the size of the array during compilation and has to insert code to figure it out. Among other things, this means that VLAness is kind of "contagious" -- consider this declaration, which reserves space for a bytearray the same size as array1:
```
unsigned char array2[sizeof array1];
```
If array1 is an ordinary array, sizeof array1 is a constant expression, and array2 is an ordinary array. If array1 is a VLA, sizeof array1 is deferred until runtime, and array2 is also a VLA.

VLAs are useful in certain situations, but they make it more difficult to reason about the performance of your program, and can make it easier to overflow the stack by accident. They were added in C99 (which is widely regarded as having been a mistake) and are now optional in the latest version of the C standard. My advice is to use malloc() instead for data that could become very large based on user input, except in toy programs (which this one may be).

Incidentally, the fact that they are VLAs has nothing to do with them not being assignable (i.e. my original comment to edouard) -- the same is true of ordinary C arrays.

Edit -- it seems to me on re-reading that maybe you were more puzzled about *arrays in general* than *VLAs in particular*. Hope this still helps a bit. Feel free to ask any follow-up questions you may have.

---

