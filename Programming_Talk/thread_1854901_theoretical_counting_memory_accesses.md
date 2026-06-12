---
title: "theoretical: counting memory accesses"
date: 2011-10-05
forum: Programming Talk
---

### Post by zaebo on 2011-10-05
Hello,

I'm sorry if this is the wrong sub forum,
because this is a very general question,
but I don't know exaclty where else to ask it.

I need to count private memory accesses in a for-loop
of an OpenCL fragment (I need just the basic accesses,
independet from the amount of work-items.)

The loop:
```
for(int k = 0; k < width; ++k)
    sum += M[row * width + k] * N[k * width + col];
```

M, N are global arrays, so variables of interest for me are 
k, width, sum, row, col.
My lecture script tells me, that it should be 11 private memory
accesses for every iteration
k     = 3 x read, 1 x write
width = 3 x read
row   = 1 x read
col   = 1 x read
sum   = 1 x read, 1 x write.

BUT, aren't it more accesses for k?

k=0          -> write (only one time)

k < width    -> read
++k          -> read and write
... +k       -> read
k * ...      -> read

Sorry to bother you with such a basic question.

---

### Post by Arndt on 2011-10-05
> **zaebo said:**
> Hello,

I'm sorry if this is the wrong sub forum,
because this is a very general question,
but I don't know exaclty where else to ask it.

I need to count private memory accesses in a for-loop
of an OpenCL fragment (I need just the basic accesses,
independet from the amount of work-items.)

The loop:
```
for(int k = 0; k < width; ++k)
    sum += M[row * width + k] * N[k * width + col];
```

M, N are global arrays, so variables of interest for me are 
k, width, sum, row, col.
My lecture script tells me, that it should be 11 private memory
accesses for every iteration
k     = 3 x read, 1 x write
width = 3 x read
row   = 1 x read
col   = 1 x read
sum   = 1 x read, 1 x write.

BUT, aren't it more accesses for k?

k=0          -> write (only one time)

k < width    -> read
++k          -> read and write
... +k       -> read
k * ...      -> read

Sorry to bother you with such a basic question.

No question is too basic for this forum.

I'm not sure what you mean by "private memory accesses". All of k, width, row, col and sum are likely to be put into registers by the compiler, and so the only memory accesses will be to the two arrays M and N.

---

### Post by karlson on 2011-10-05
> **zaebo said:**
> Hello,

I'm sorry if this is the wrong sub forum,
because this is a very general question,
but I don't know exaclty where else to ask it.

I need to count private memory accesses in a for-loop
of an OpenCL fragment (I need just the basic accesses,
independet from the amount of work-items.)

The loop:
```
for(int k = 0; k < width; ++k)
    sum += M[row * width + k] * N[k * width + col];
```

M, N are global arrays, so variables of interest for me are 
k, width, sum, row, col.
My lecture script tells me, that it should be 11 private memory
accesses for every iteration
k     = 3 x read, 1 x write
width = 3 x read
row   = 1 x read
col   = 1 x read
sum   = 1 x read, 1 x write.

BUT, aren't it more accesses for k?

k=0          -> write (only one time)

k < width    -> read
++k          -> read and write
... +k       -> read
k * ...      -> read

Sorry to bother you with such a basic question.

What is counted as a private memory access in your case?  For the purpose of your lecture ++k may not be counted as a memory access because it simply may be an increment operation, which logically writes to memory.

I would have to assume that the lecture is for an instructor led class so I would ask him for a break down of these 11 accesses.  If you want to see what a compiler would do I suggest creating a simple C program and running:
```

gcc -S test.c

```

where test.c is your program.  You would see how this breaks down into low level machine code and provide you with how memory would be accessed.

> 
AND another question:

When I got

```
float* a_d = &somewhere;
int width = something;

float* a = a_d + width;
```

Is a memory access from a or a_d involved?

I am not sure I even understand the question here.:confused:

---

### Post by zaebo on 2011-10-05
I have unfortunetly no time to ask my instructor in time
as I need the answers.

So yeah..
This questions are regarding OpenCL.
With private memory access, I mean register accesses, yes.
And I would say that there are 5 accesses for k:

k < width -> one access
++k -> two acesses
...+k -> one access
k*... -> one access

So I think that one access was forgotten in the lecture notes.
I'm just asking, because it is already the corrected version,
and the register accesses was corrected from 7 to 11 :)

And concerning the second question..it's a bit complicated to
formulate.

Global memory accesses per work-item were counted.
My problems with the kernel are here:

```
__kernel void scalarProd(__global float* d_c, __global float* d_a, __global float* d_b, int elements) {
   __local float accumResult[ELEMENT_N];
   __global float* a = d_a + elements * get_group_id(0);
   __global float* b = d_b + elements * get_group_id(0);
```

In this part was no global memory access counted for a work-item. So my last guess was, that ```
__global float* a = ...
``` and
```
__global float* b = ...
``` are executed once for every
work-group, and not by every work-item, as I know that ```
__local float accumResult[ELEMENT_N];
``` is only executed once for every work-group.
But I'm not sure, and I couldn't find any information for that yet...

---

### Post by Arndt on 2011-10-05
> **zaebo said:**
> I have unfortunetly no time to ask my instructor in time
as I need the answers.

So yeah..
This questions are regarding OpenCL.
With private memory access, I mean register accesses, yes.
And I would say that there are 5 accesses for k:

k < width -> one access
++k -> two acesses
...+k -> one access
k*... -> one access

So I think that one access was forgotten in the lecture notes.
I'm just asking, because it is already the corrected version,
and the register accesses was corrected from 7 to 11 :)


k++ can be written as k = k+1, but in many cases, there are machine instructions which increment a register in one operation. Why exactly are the number of register accesses interesting, and not the number of instructions?

(Maybe I'm just showing my ignorance of OpenCL. I see now why the word "private" is used, since it deals with parallelism.)

---

### Post by karlson on 2011-10-05
> **zaebo said:**
> I have unfortunetly no time to ask my instructor in time
as I need the answers.

Procrastination huh? :p
> 
So yeah..
This questions are regarding OpenCL.
With private memory access, I mean register accesses, yes.
And I would say that there are 5 accesses for k:

k < width -> one access
++k -> two acesses

++k may not be 2 accesses as one might think.  ++k could be interpreted as INC instruction which doesn't move the registers just increments the content of it by 1, hence, the instructor necessity...
> 
...+k -> one access
k*... -> one access

So I think that one access was forgotten in the lecture notes.
I'm just asking, because it is already the corrected version,
and the register accesses was corrected from 7 to 11 :)


OK

> 
And concerning the second question..it's a bit complicated to
formulate.

Global memory accesses per work-item were counted.
My problems with the kernel are here:

```
__kernel void scalarProd(__global float* d_c, __global float* d_a, __global float* d_b, int elements) {
   __local float accumResult[ELEMENT_N];
   __global float* a = d_a + elements * get_group_id(0);
   __global float* b = d_b + elements * get_group_id(0);
```

In this part was no global memory access counted for a work-item. So my last guess was, that ```
__global float* a = ...
``` and
```
__global float* b = ...
``` are executed once for every
work-group, and not by every work-item, as I know that ```
__local float accumResult[ELEMENT_N];
``` is only executed once for every work-group.
But I'm not sure, and I couldn't find any information for that yet...

I am by no means expert in OpenCL but from what you describe the memory access counts the number of times the value in global memory is accessed and
```

__global float *a = 

```
may not touch global memory until the value is accessed by dereferencing the address a currently has.

---

### Post by zaebo on 2011-10-05
> Why exactly are the number of register accesses interesting, and not the number of instructions?

For performance purposes, it was just important to regard the 
proportion of global memory accesses to instructions.
The amout of register accesses was just an additional information.

But I thought I missed out on something, because if I had to
count the register accesses, I would have guessed that ++k needs
2 register accesses, one two get to know the original value, and
then to overwrite it with the incremented value.

I think it is not essential, but I'm freaking a bit out atm, because
I can't get some simple things right ;)


Edit:
> Procrastination huh? 
Yeah, I'm pretty good in that ;)

---

### Post by zaebo on 2011-10-05
> I am by no means expert in OpenCL but from what you describe the memory access counts the number of times the value in global memory is accessed and
```

__global float *a = 

```
may not touch global memory until the value is accessed by dereferencing the address a currently has.

This could be, I must admit that my understanding of pointers
is not that advanced to comment on that ;)

But maybe I just found a solution.
I found in a nvidia paper concerning opencl (not cuda), that
global memory access is only granted per kernel.
Though they seem to use 'thread' to describe a work-item, I think
they mean that this pointer is created once for the whole device.

That would explain this latter access:
```
int id = get_global_id(0);
accumResult[id] = a[id] * b[id];
```
where the lecture notes mentions two global memory accesses, one
by a[id] and one by b[id]. 

Sorry, this information might have helped you also to understand
it better, but my thoughts are very confuzed atm.

Thanks a lot guys :)

Edit:
And with the incrementation..I'll maybe go with one access..

Edit2:
Ok. It's wrong what I've said. Every Work-item can access the global
memory.

---

