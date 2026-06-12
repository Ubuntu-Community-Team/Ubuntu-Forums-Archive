---
title: "How Do You Allocate A Large Triple Array in C/C++?"
date: 2009-09-22
forum: Programming Talk
---

### Post by jsmidt on 2009-09-22
Hi, I have C code with the following:

```

#include <stdio.h>
#define N 2000

int main()
{

        double alpha[N][N][N];

        alpha[0][2][3] = 5;
}

```

The problem is a 2000x2000x2000 static array is too large for the memory yielding a segmentation fault.

I was told I need to make a dynamical triple array using either malloc or new depending on whether I want C or C++ code.

I see examples for 2d arrays but on the web but for whatever reason I can't generalize this in ways that seem to work.

Is there anyone who could show me how to declare the above array using either malloc or new I would really appreciate it?  Thanks.

---

### Post by MadCow108 on 2009-09-22
there are 2 ways using c arrays, pointer to pointer to pointer and large block with arithmetic to index the elements (this is how the compiler handles multidimensional stack arrays)
```

double *** ar = new double**[N];
for (i<N) {
ar[i] = new double*[N];
for (j<N) {
ar[i][j] = new double[N];
}
}
ar[i][j][k]=5;

```
deleting is equivalent also with loops

or:
```

double * ar = new double[N*N*N];
ar[i*N*N + j*N + k] = 5;
delete [] ar;

```

in C++ you should use the provided containers like vector or the boost multi dimensional arrays

---

### Post by geirha on 2009-09-22
And in C, with malloc, would look something like this:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    double ***alpha;
    int i, j;

    // allocate an array that can hold 3 arrays of arrays of doubles
    alpha= malloc(sizeof(double**)*3);
    for (i= 0; i < 3; i++)
    {
        //allocate an array that can hold 3 arrays of doubles
        alpha[i]= malloc(sizeof(double*)*3);
        for (j= 0; j < 3; j++)
        {
            // allocate an array of 3 doubles
            alpha[i][j]= malloc(sizeof(double)*3);
        }
    }

    alpha[0][1][0]= 5.0;
    printf("%f\n", alpha[0][1][0]);

    // remember to free() in reverse
    for (i= 0; i < 3; i++)
    {
        for (j= 0; j < 3; j++)
        {
            free(alpha[i][j]);
        }
        free(alpha[i]);
    }
    free(alpha);
    return 0;
}

```

Make sure to run your program through [valgrind](apt://valgrind). It'll tell you if your program has memory holes.
```
gcc -Wall myprog.c
valgrind ./a.out

```

I do recommend the second option MadCow108 shows; using a 1D-array to represent a 3D-array. While it is somewhat less intuitive, it sure is easier to allocate and deallocate.

---

### Post by jsmidt on 2009-09-22
geirha and MadCoW108,

Thank you both so much.

---

### Post by Can+~ on 2009-09-22
I like having a big chunk of memory and using functions to access it (like madcow pointed out). But the question is, do you really need that much?

```
8*(2000³) = 59.605[GB]
```

---

### Post by jsmidt on 2009-09-22
> **Can+~ said:**
> I like having a big chunk of memory and using functions to access it (like madcow pointed out). But the question is, do you really need that much?

```
8*(2000³) = 59.605[GB]
```

Unfortunately yes.  This happens a lot in numerical physics. (But first time I personally had to deal with it.)

To do the right calculation for the bispectrum of the cosmic microwave background (CMB) you have to do various summings over a 3 index object which has 2000 entries for each index for the new Planck satellite data.  

If you don't properly keep track of each entry we might not have good physics at the end of the day. :)

---

### Post by phrostbyte on 2009-09-23
Wow that's a massive stack allocation. :)

---

### Post by dribeas on 2009-09-23
In general it is better to allocate a linear segment of memory and then interpret it as an N dimensional array by using some arithmetic conversions. Now, in your case, where just below 56Gb of memory must be requested, you might need to use a file and mmap it into memory, or maybe you can just deal with a huge amount of swap space. Anyway, you will need to understand how your particular hardware platform and algorithms behave as you will be doing huge amounts of swapping (OS or yourself with mmap), and the way you decide to store the data will greatly affect performance.

---

### Post by MadCow108 on 2009-09-23
you should probably check if you can split the data into smaller chunks and use your universities/institutes supercomputer/computing cluster
otherwise it will take quite a long time

---

### Post by jsmidt on 2009-09-23
By the way, this worked, the calculations done everything worked out. (We have computers at our disposal such that 56GB isn't a problem.)

The data matches theory pretty well. Thanks everyone. (I'd post plots but that would be against the rules. :))

---

### Post by ve4cib on 2009-09-23
Glad to hear everything worked out (despite the fact that I did nothing to help).  In this particular instance I would probably also have leaned towards creating a single-dimensional array and simply interpreting it as if it were three-dimensional with a few extra functions.  Something like this would work: 

```

#define ARRAY_SIZE_X 2000
#define ARRAY_SIZE_Y 2000
#define ARRAY_SIZE_Z 2000

// lots of extra parentheses around everything since I've always been
// taught that that's a good practice when using macro functions
#define GET_INDEX(x,y,z) ((ARRAY_SIZE_X*ARRAY_SIZE_X*(x)) + (ARRAY_SIZE_Y*(y))+(z))

...

int* alpha = (int*)malloc(sizeof(int) * ARRAY_SIZE_X * ARRAY_SIZE_Y * ARRAY_SIZE_Z);

int i,j,k;
for (i=0; i<ARRAY_SIZE_X; i++)
    for (j=0; j<ARRAY_SIZE_Y; j++)
        for (k=0; k<ARRAY_SIZE_Z; k++)
            alpha[GET_INDEX(i,j,k)] = ...

```


It's maybe not the prettiest-looking, but it does simplify the creation of the array, but it still gives you the illusion of dealing with three-dimensional data.

Another thing to consider (and again, it's a bit late for this) but if you know that much of the data will have a fixed-value (i.e. 73% of the data is very likely to be zero) you could create a sparse-matrix to store the data.  Basically it's an n-dimensional linked-list-style structure that stores only the non-background data.  Every node in the sparse matrix stores its coordinates (x,y,z in this case).  When you're looking up a point you linearly search through the appropriate row/column.  If you hit a node with the correct indices you return its value.  Otherwise you return the default value.

This only really offers a benefit if you have large amounts of identical data to store.  The linear-searching will cause a massive hit in performance if the sparse matrix isn't, well, sparse.  But provided the data is sparse enough you'll save massive amounts of memory (very useful if you don't have access to super-computers with ginormous amounts of memory).

---

### Post by ariadne3s on 2010-06-22
MadCow108--Thank you for that code (below)!    I thought I'd post something similar, as a complete program that can be compiled and run, since it took me a while to get the delete loop functional & to figure out what could be used to replace N for a triple array of three different dimensions. 


> **MadCow108 said:**
> there are 2 ways using c arrays, pointer to pointer to pointer and large block with arithmetic to index the elements (this is how the compiler handles multidimensional stack arrays)
```

double *** ar = new double**[N];
for (i<N) {
ar[i] = new double*[N];
for (j<N) {
ar[i][j] = new double[N];
}
}
ar[i][j][k]=5;

```deleting is equivalent also with loops

or:
```

double * ar = new double[N*N*N];
ar[i*N*N + j*N + k] = 5;
delete [] ar;

```in C++ you should use the provided containers like vector or the boost multi dimensional arrays


```

#include<iostream>
using namespace std;

double ***blue(){

  
  int I=4;
  int J=5;
  int K=6;

  //Allocate memory for triple array
  double***A=(double***)new double**[I];
  for(int i=0; i<I; i++){
    A[i]=(double**)new double*[J];
    for (int j=0; j<J; j++){
      A[i][j]=(double*)new double[K];
    }
  }

 
  //Assign a value to one "cell" in A, and return the full triple array
 A[3][4][5]=12; //this is A[i][j][k]
  return A;


  //Delete 
 for(int i=0; i<I; i++){
    for (int j=0; j<J; j++){
      delete A[i][j];
    }
 delete A[i];
  }
 delete []A;
}



int main(){

 double***BLUE=blue();
 std::cout<<endl<<BLUE[3][4][5]<<std::endl;
  return 0;
}


```

---

### Post by Emill on 2010-06-22
Do you need to have the array declared as local?
If you declare it outside main(), you won't get Stack Overflow/Segmentation fault.

```

#include <stdio.h>
int large_array[4000][6000][100];

int main(){
    large_array[42][6][99] = 1337;
}

```

But gcc is kinda wierd. If you have such large arrays, more than one GB, the compile time will be longer for some odd reason.

---

### Post by mbsullivan on 2010-06-22
> Do you need to have the array declared as local?
If you declare it outside main(), you won't get Stack Overflow/Segmentation fault.


Agreed. Global arrays are allocated on the heap, just like dynamically allocated memory. Hacking it up this way is SO much less work, especially in C! :)

For a quick experiment, this is how I would do it. You can't possibly have multiple local MASSIVE contiguous arrays floating around, so having a single global one shouldn't matter (unless it rapes some of the compiler's inter-procedural optimizations).

Declaring it **static** will also allocate it on the heap, and may help with the compiler optimizing things.

```
#include <stdio.h>

int main(){
    static int large_array[2000][2000][100];
    large_array[42][6][99] = 1337;
    printf("%d", large_array[42][6][99]);
}
```


> But gcc is kinda wierd. If you have such large arrays, more than one GB, the compile time will be longer for some odd reason.

You're right. At least on my machine, gcc takes so long because it's eating up HUGE GOBS of memory and begins to swap. It may be that if you allocate it contiguously on the heap, you might have to compile it on the same machine you run on (the one with all the memory).

OR, there is another (hackish) way, too: you could always just up your allowable stack size and not worry about it! To do so:

```
ulimit -s unlimited
```

And you should be able to run the (unmodified) code:

```
#include <stdio.h>

int main(){
    int large_array[2000][2000][100];
    large_array[42][6][99] = 1337;
    printf("%d", large_array[42][6][99]);
}
```

While this probably isn't good practice in general, for a quick experiment it would work too.

Mike

---

### Post by Can+~ on 2010-06-22
> **mbsullivan said:**
> Agreed. Global arrays are allocated on the heap, just like dynamically allocated memory. Hacking it up this way is SO much less work, especially in C! :)

Declaring it **static** will also allocate it on the heap, and may help with the compiler optimizing things.

Actually, it gets stored on the ["Data" section]("http://en.wikipedia.org/wiki/Data_segment") of the program's memory (BSS if uninitialized).

> **mbsullivan said:**
> OR, there is another (hackish) way, too: you could always just up your allowable stack size and not worry about it! To do so:

```
ulimit -s unlimited
```

Indeed hackish. Should not be used at all in this case. [Stack space is precious]("http://en.wikipedia.org/wiki/Stack-based_memory_allocation"), and should be used as minimal as possible, and for what it was intended, temporary and local variables.

> **mbsullivan said:**
> For a quick experiment, this is how I would do it. You can't possibly have multiple local MASSIVE contiguous arrays floating around, so having a single global one shouldn't matter (unless it rapes some of the compiler's inter-procedural optimizations).

When dealing with the amounts of memory that the OP was using, there's simply no good solution. Already the OS is dividing memory space into chunks (named frames), so fragmentation is already happening, like it or not. Just stick to the Heap.

---

### Post by mbsullivan on 2010-06-23
> 
Actually, it gets stored on the "Data" section of the program's memory (BSS if uninitialized).

Okay, fine. It's not actually the heap (literally where dynamically allocated memory is given). I think this is an overshare, though. The point is that neither of these techniques runs up against the stack size limit! 

Looking at the assembly, it seems that the (uninitialized) global variable is initialized in the .bss segment, as expected. The static local variable is placed with the .comm directive. This appears to put it in a segment [between .data and .bss]("http://coding.derkeiler.com/Archive/Assembler/comp.lang.asm.x86/2006-05/msg00085.html").

> 
When dealing with the amounts of memory that the OP was using, there's simply no good solution. Already the OS is dividing memory space into chunks (named frames), so fragmentation is already happening, like it or not. Just stick to the Heap.

I'm WAY more worried about ease of programming than anything else -- this sounds like something he's going to run ONCE. Minimizing bugs and the time spent coding is the most important thing. I'd do it with a global or static variable. 

> Indeed hackish. Should not be used at all in this case. Stack space is precious, and should be used as minimal as possible, and for what it was intended, temporary and local variables.

Yeah, I'd stay away from it, too. Handy in some situations, though... Like with some managed languages where you have little control where things go. Again, I get the feeling that he's interested in the results, not creating a perfect program for progeny. I can relate. I also like very high level languages, so the sight of so much cludge for the dynamically allocated memory makes me feel ill.

Mike

---

