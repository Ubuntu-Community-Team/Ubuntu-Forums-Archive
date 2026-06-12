---
title: "When ulimit is set to unlimited heap memory is not freed"
date: 2008-08-05
forum: Programming Talk
---

### Post by masebase on 2008-08-05
On Ubuntu 8.04 if I run the following code after compiling with g++ 4.2.3

```

#include <iostream>

using namespace std;

int main()
{
   int size = 100000000;
   double *data = new double[size];
   for(int i=0; i<size; i++)
   {
      data[i] = 0.0;
   }
   sleep (4);
   delete [] data;

   sleep (10);
     
}

```

I see a large amount of memory used for about 4s and then the program releases it and sleeps for 10s more. This the what I would expect. Now if the stack size is set to unlimited with

```
ulimit -s unlimited
```

Then the program uses a large amount of memory and does not release it back to the kernel until it terminates. I don't understand why changing the stack size has this effect. The new and delete in the program deal with heap memory. Why does delete not return the memory to the kernel with stack size set to unlimited? 

Thanks for your time.

---

### Post by Zugzwang on 2008-08-06
How did you check this? It works as expected (by you) here.

---

### Post by masebase on 2008-08-06
I watched top to see how much memory the program uses. I don't know if saying the memory is not returned to the kernel is correct or not. What I should of said is according to top the program hangs on to the memory. 

When I say "works as expected" I mean, if delete is called on some memory then I would expect the program's memory footprint to reduce by about how much memory I delete.

One last note, when the stack size is set to unlimited and delete is called like in the example code the programs memory footprint does not get smaller, but if new is called after delete to reallocate more memory (that is less then or equal the first new) the memory footprint of the program does not grow. So clearly the program knows the memory was deleted and can reuse it, but I still don't see why when delete is called the program's footprint does not decrease when the stack size is unlimited while it does when it is limited.

---

### Post by Zugzwang on 2008-08-06
I used "top" here as well and the footprint decreases a couple of seconds before the program actually terminates (as one might expect). So I can't help you on this because the "problem" (if any) occurs here as well.

Just a guess: Try starting programs until your memory is full. Maybe the memory management part of the kernel sometimes frees the memory in a lazy way (but I have no clue how this might interact with the stack size). Also note that the stack size is *always* limited, it might just be the case that it grows dynamically (I don't know if x86 processors allow this) and this causes side-effects?

---

### Post by masebase on 2008-08-06
Zugzwang am I sorry I simplified my code that I post thinking it behaved the same and forget to retest it until now. The code I posted does behave as I would expect, which is changing the stack size does not effect the how the programs memory footprint.

The code below however should show the behave I was describing.
```

#include <iostream>

using namespace std;

int main()
{
   int size = 200000;
   double **data = new double*[size];
   for(int i=0; i<size; i++)
   {
      data[i] = new double[1000];
      for(int j=0; j < 1000; j++)
      {
         data[i][j] = 5.4;
      }
   }
   sleep (2);
   for(int i=0; i<size; i++)
      delete [] data[i];

   delete [] data;
   sleep(500);

      
}

```

Note this takes over 1Gb of memory. If I changed the variable size to be 100000 instead of 200000 the behave changes back to as expected. So the issue I am talking about only happens when a lot of memory is use and in this code. I used more memory with the first code and it is still ok. So this leaves me more confused. Sorry about not checking my first explain.

---

### Post by Zugzwang on 2008-08-06
Which column in "top" are you looking at? Don't look at anything else than "DATA" for your program. You can enable/disable showing it by pressing f - S - <ENTER>.

---

### Post by masebase on 2008-08-06
I did not know that about top thanks!

With DATA on in top I run the code with the stack size at its default of 8192 Kb and top shows 1.1g of DATA for a few seconds then it drop to 272 kb. If I then set the stack size to unlimited then run the program the DATA size goes up to 1.5 and remains that way until the program ends.

---

### Post by Zugzwang on 2008-08-06
That program doesn't show the behaviour here either (and I don't have enough RAM to go to 200000, just to 100000). So I'm afraid that I can't help you.

However, normally, you shouldn't worry about that. As long as valgrind doesn't report a memory leak, you should be fine. The memory allocation scheme might be a bit lazy sometimes.

---

### Post by masebase on 2008-08-06
I am not worried about a memory leak. It is that I have an application that must have stack size to unlimited to run. The application then varies in how much memory it uses, but because of this issue once it grows to the max memory footprint in never gets smaller. If you try to use that memory you know is free but the program is hanging onto it you run about of memory and start swapping. Anyway, I will check looking into it see if I can make sense of it. Thank for help.

---

### Post by Zugzwang on 2008-08-06
> **masebase said:**
> If you try to use that memory you know is free but the program is hanging onto it you run about of memory and start swapping. 

..not necessarily. The collection of unused memory blocks might simple be delayed until they are actually needed. In that case, there's no problem at all. You might want to check this by running a lot of programs once your program enters the "waiting" phase near the end of the program.

---

### Post by Cygnus on 2008-08-06
> **Zugzwang said:**
> ..not necessarily. The collection of unused memory blocks might simple be delayed until they are actually needed. In that case, there's no problem at all. You might want to check this by running a lot of programs once your program enters the "waiting" phase near the end of the program.

Yes... 

by the way I made a massif graph over the memory usage in the program and there was no difference at all between the different settings of ulimit.

---

### Post by masebase on 2008-08-06
It appears the memory cannot be collected as you say. I ran the code and then ran other code and the memory was not given up, but swapped. So it is a funny deal.

I have learn a lot and found that you can replace the glibc allocator and one replacement option is [tcmalloc]("http://code.google.com/p/google-perftools/") from google. You then just link this library in and it overrides the new and malloc and delete and free and others. The google library was designed for speed so it never gives up the memory to the OS by default, but I [found out]("http://groups.google.com/group/google-perftools/browse_thread/thread/c75b178134a68a6a/a1bc9332d1052cf1?lnk=raot") that the google library api has a function called ReleaseFreeMemory() which you can use to return freed memory to the OS. So I did

```

#include <iostream>
#include <google/malloc_extension.h>
using namespace std;

int main()
{
   int size = 200000;
   double **data = new double*[size];
   for(int i=0; i<size; i++)
   {
      data[i] = new double[1000];
      for(int j=0; j < 1000; j++)
      {
         data[i][j] = 0.0;
      }
   }
   sleep (2);
   for(int i=0; i<size; i++)
      delete [] data[i];

   delete [] data;
   MallocExtension::instance()->ReleaseFreeMemory();
   sleep(500);
}

```

This works. I am sure there is more to this story, but this solves the problem for the moment.

Thanks again for your help Zugzwang!

---

### Post by masebase on 2008-08-06
Cygnus,

From what I learned it is the allocator in the glibc library that is causing the issue. I am just guessing but I think massif is only watching new and delete and not what the allocator does. Somehow the glibc allocator must be effected by the unlimited stack size.
Thanks for looking into it and tell me if you think I am wrong.

---

### Post by Cygnus on 2008-08-06
> **masebase said:**
> Cygnus,

From what I learned it is the allocator in the glibc library that is causing the issue. I am just guessing but I think massif is only watching new and delete and not what the allocator does. Somehow the glibc allocator must be effected by the unlimited stack size.
Thanks for looking into it and tell me if you think I am wrong.

But it might just be how the usage is reported, you could try to allocate memory again between the delete and the final sleep and watch if that actually makes memory usage go up or not. 

Measuring memory usage is not straight forward, it was a while since I was involved with this so I do not remember all the details; but you can read some more info [here]("http://www.kdedevelopers.org/node/1445") and [here]("http://www.kdedevelopers.org/node/1567").

---

### Post by masebase on 2008-08-06
> **Cygnus said:**
> But it might just be how the usage is reported, you could try to allocate memory again between the delete and the final sleep and watch if that actually makes memory usage go up or not. 


I have done this and the memory usage of the program does not go up. The program can use the memory space it has freed up, but the issue is it is not returning the freed memory back to the kernel. This, I think, is because the allocator has decided not to give it back. I am guessing the allocator has decided that it is of effective to hold onto the memory for some reason.

---

