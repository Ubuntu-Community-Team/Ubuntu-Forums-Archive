---
title: "Convert C to Python code"
date: 2009-05-17
forum: Programming Talk
---

### Post by smmohsin.reza on 2009-05-17
I am a very beginer on Python Language. I would like to convert a small C source code to Python. I walked through Python Documents and I understood that it is not possible to use C/C++ pointer to python.

This is my C code that I tried to convert to Python: 

#include <stdio.h>
#include <stdlib.h>

float *a, *b;

int main(){

    printf ("\nLookup Table Access:\n");

    a = (float *)malloc(32768 * sizeof(float));
    b = (float *)malloc(32768 * sizeof(float));

    int i, count;

    for (i = 0; i < 16384; i++)
        a[i] = ((float)(rand() % 16384)) / 16384.0F;

    for (count = 0; count < 1000; count++){
        for (i = 0; i < 16384; i++)
            b[i] = a[(int)(a[i] * 16384.0F)];
    }

    return 0;
}

Is there anybody can help me to convert this code to python then it would be really great to me.

Basically, here following 2 lines is difficult for me convert to Python:

float *a, *b;

 a = (float *)malloc(32768 * sizeof(float));

Have a nice time with Python program.

With best regards,

Mohsin Reza

---

### Post by Sockerdrickan on 2009-05-17
Yeah allocating memory is somehing you don't have to deal with in Python ;)

---

### Post by simeon87 on 2009-05-17
Forget about memory and focus on what the program actually calculates. Then rewrite that in Python.

---

### Post by dwhitney67 on 2009-05-17
> **smmohsin.reza said:**
> ...

Basically, here following 2 lines is difficult for me convert to Python:

float *a, *b;

 a = (float *)malloc(32768 * sizeof(float));

Have a nice time with Python program.

With best regards,

Mohsin Reza

Ask yourself this question... why did you allocate memory for the arrays in the C program?  The following would have sufficed for your needs in C:
```

float a[16384];
float b[16384];

...

```
In Python, you do not need to explicitly allocate memory; you just define your array, and then do whatever is needed by your app.
```

import array

alen = 16384
a    = array.array('f', range(alen))

for i in range(0, alen):
        # initialize a (or whatever)...
        a[i] = 3.14 * (i+1 / 3.333)

```

---

### Post by smmohsin.reza on 2009-05-17
Hello dwhitney67,

Thanks a lot, it could helped. Form your reply I got the solution of my problem. Now at least I can write my code in Python. 

Actually, I wrote this code for Compiler BenchMarking with different programming language. Honestly we have our own script language named (Pluk), and I have to benchmark with Python, Perl and Shell script.

So I need exactly same code for each language. If pointer + memory allocation is same as a fixed array then it would be still fine for me. Otherwise I will not get exact result with my BenchMark test.

So please let me know, is it same or different.

I am sorry for my bad English.

Mohsin
Dresden, Germany

---

### Post by CptPicard on 2009-05-17
From what I can gather from your C code (it's pretty hard to read), it's going to be really difficult to get that to serve as a meaningful benchmark in any way... a lot of the stuff just works rather differently in python, and any differences in performance don't just "mean" much. Good benchmarks are hard to come by. 

You would do much better with some real algorithm that takes some time to run, and then implementing that using language-specific idioms...

---

### Post by sujoy on 2009-05-17
benchmark or no benchmark, you allocated twice the memory needed for each of the floats a and b :confused:

---

### Post by smmohsin.reza on 2009-05-18
Actually I wanted to know, is there any chance to declare a pointer and allocate the memory for this  pointer in Python like C/C++. I got the idea that it seems to be impossible in python. Any way I am going to change my C code in order to convert in python.

Thanks to all. It could helps me a lot to understand about pointer and array in C and in different language.

Still I would like to know that if any body knows about this technique then it would be a great to me.

Thank you.

---

### Post by Yacoby on 2009-05-18
> **smmohsin.reza said:**
> Actually I wanted to know, is there any chance to declare a pointer and allocate the memory for this  pointer in Python like C/C++. I got the idea that it seems to be impossible in python. Any way I am going to change my C code in order to convert in python.
Not that I know of. Python removed the need to think about memory allocation and deallocation.

---

### Post by ajackson on 2009-05-18
> **smmohsin.reza said:**
> Actually I wanted to know, is there any chance to declare a pointer and allocate the memory for this  pointer in Python like C/C++.
I don't quite see why you'd want to do that in Python. C requires you to do all the leg work when it comes to creating/removing arrays and other such things in memory. In Python (and a lot of other languages) you don't need to jump through hoops to get an array.

> I got the idea that it seems to be impossible in python. Any way I am going to change my C code in order to convert in python.
Apart from allocating twice as much memory as needed your C was OK.

> Still I would like to know that if any body knows about this technique then it would be a great to me.
I ask again why would you need to use such a technique. C != Python, they do things in different ways, learn to understand the differences and it will help you select the right tool (language) for the task at hand.

---

### Post by unutbu on 2009-05-18
I have a feeling if you try to convert that C code statement-for-statement into Python, you're going to get the impression that Python is incredibly slow.

However, if you install python-numpy package, then you could do this:

[PHP]#!/usr/bin/env python
import numpy as np
maxnum=16384

# # Uncomment this if you want to print the full array
# np.set_printoptions(threshold=maxnum)

a=np.random.random(maxnum,)
# print(a)
# # [ 0.35158836  0.7395052   0.17100169 ...,  0.87758796  0.44773525
# #   0.53438997]
# print(a.dtype)
# # float64
c=(a*maxnum).astype(int)
# print(c)
# # [ 5760 12116  2801 ..., 14378  7335  8755]
for i in range(1000):
    b=a[c]
# print(b)
# # [ 0.83000539  0.22330199  0.84449601 ...,  0.33324092  0.13818881
# #   0.92307331][/PHP]

The python code above ran in 0.575 seconds, versus 0.327 seconds for the C code.

numpy arrays are allocated in a contiguous block of memory, and each element has a fixed and uniform size. This allows for fast indexing. I don't think standard Python lists work this way, which is why whenever you are working with large numerical arrays, numpy arrays are faster.

---

### Post by shaloken on 2009-05-18
The advantage of python toward java, c or any other language is that like the example unutbu gave, python needs 3 times less line of code. And I'm generous when I say that it just 3 times.

---

### Post by R33D3M33R on 2010-07-31
/EDIT: I have solved my problem.

NEVER EVER use code like this for allocating arrays

```
myarr=[0.0]*5
```

this copies the keys. If you later do something like this:

```
myarr[0]=1
```

it will set all the keys to 1, not just the first one!

---

