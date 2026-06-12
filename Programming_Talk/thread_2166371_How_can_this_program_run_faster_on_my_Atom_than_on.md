---
title: "How can this program run faster on my Atom than on my i7?"
date: 2013-08-09
forum: Programming Talk
---

### Post by JRV on 2013-08-09
The program is a version of Conway's game of life that I wrote.

It runs faster on my Atom 330 running Ubuntu 13.10 alpha 64 bit
than it does on my i7 running Ubuntu 12.04 64 bit..

The program compiles instantly on each machine.

I copied the executable compiled on the Atom to the i7 and it ran the same speed as the version compiled on the i7.

On everything else I have ever run the i7 seems fast and the Atom dog slow.

How can this be?

```



/*
  Filename: life.c

  Conway's game of life
*/

#include <stdio.h>
#include <stdlib.h>

#define clrscr() printf("\e[1;1H\e[2J")

//                                         1                   2                   3                   4                   5                   6                   7                   8
//                     0,1,2,3,4,5,6,7,8,9,0,1,2,3,4,5,6,7,8,9,0,1,2,3,4,5,6,7,8,9,0,1,2,3,4,5,6,7,8,9,0,1,2,3,4,5,6,7,8,9,0,1,2,3,4,5,6,7,8,9,0,1,2,3,4,5,6,7,8,9,0,1,2,3,4,5,6,7,8,9,0,1

int start[24][82] = { {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,1,1,0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,1,1,0,0,0,0,0,0,0,0,1,0,0,0,1,0,1,1,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
	   	      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
	  	      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
	  	      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0},
		      {0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0} };



int count[24][82];


int firstTime = 1;

/*
 The loop function.

/*******************************************************/

void loop(void)
{
  int i,j;
  long k;
  long waitTime = 50000000;

  clrscr();

  for(i=1;i<24;i++)      // Display starting point.
  {
    for(j=1;j<81;j++)
    {
      if(start[i][j]==0) printf(" ");  
      else  printf("0");
    }
    printf("\n");
  }

  if(firstTime == 1)
  {
    for(k=0;k<waitTime*5;k++);
    firstTime = 0;
  }
  else
  {
    for(k=0;k<waitTime;k++);
  }

  for(i=0;i<24;i++)     // Zero counts from previous iteration.
  {
    for(j=0;j<81;j++)
    {
      count[i][j]=0;
    }
  }

/*******************************************************/

  for(i=1;i<24;i++)     // Count adjacent live cells.
  {
    for(j=1;j<81;j++)
    {
      if(start[i-1][j-1]==1) count[i][j]++;
      if(start[i-1][j]==1) count[i][j]++;
      if(start[i-1][j+1]==1) count[i][j]++;

      if(start[i][j-1]==1) count[i][j]++;
      if(start[i][j+1]==1) count[i][j]++;

      if(start[i+1][j-1]==1) count[i][j]++;
      if(start[i+1][j]==1) count[i][j]++;
      if(start[i+1][j+1]==1) count[i][j]++;
    }
  }

/*******************************************************/

  for(i=1;i<24;i++)     // Switch on/off cells.
  {
    for(j=1;j<81;j++)
    {
      if (count[i][j]<2) start[i][j]=0;
      if (count[i][j]>3) start[i][j]=0;
      if (count[i][j]==3) start[i][j]=1;
    }
  }

}


int main(void)
{

  while(1)
  {
    loop();
  }

  return(0);
} 

```

---

### Post by pqwoerituytrueiwoq on 2013-08-09
are you running 32bit on the i7?
how many samples did you do on each system?
how much of a difference are we talking about as a percentage?
which i7 and which atom

the power state manager is different on 13.10, so the i7 may be runinng at 800Mhz on the i7 and at the atoms max speed

---

### Post by JRV on 2013-08-09
> **pqwoerituytrueiwoq said:**
> are you running 32bit on the i7?
No, it's 64 bit.
> 
how many samples did you do on each system?

5 or 6
> 
how much of a difference are we talking about as a percentage?

The i7 is ~70% as fast.
> 
which i7 and which atom

Atom 330 with Intel 945G chipset at 1600MHz. (1600MHz is max.) Intel D945GCLF2 motherboard.
I7-920 with Intel X58 chipset - Conky says it's running at 1600MHz. (2600MHz is max.)
Forcing it to 2600MHZ does not seem to make a difference.

---

### Post by Bachstelze on 2013-08-09
Processors are very complicated beasts. Arguably the most complicated things ever built by man, to the point that it is often said to be a miracle that they work at all. So sometimes, they do weird things, and such performance discrepancies are somewhat common. Unless you want to dig very deep in their insides, it's probably better to not give it too much thought. :p

---

### Post by ssam on 2013-08-09
what command are you using to compile it?

it looks like the code uses empty loops as delays
```
for(k=0;k<waitTime;k++);
```
the compiler ought to optimise these out, basically optimise it to
```
k=waitTime
```

but maybe you have optimisation disabled on the i7

---

### Post by JRV on 2013-08-09
> **ssam said:**
> what command are you using to compile it?


```

gcc -o life life.c

```

---

### Post by ssam on 2013-08-09
try:
```
gcc -O2 -o life life.c
```
or
```
gcc -O3 -o life life.c
```

you might also want to put a 
```
-march=native
```
in there so that gcc can take full advantage of the cpu.

if you actually need delays in there, then you'll have to put a proper time based delay. spinning loops just waste CPU (though sometimes in kernel code spinlocks can be useful).

---

### Post by JRV on 2013-08-09
> **ssam said:**
> 
if you actually need delays in there, then you'll have to put a proper time based delay.

Both the -O2 and -O3 options remove the delay and make it too fast.

How do I write a time based delay of about 1/5 second.
I've never needed to slow a program down before.

Except an an Arduino which has a command for it.

---

### Post by Tony Flury on 2013-08-09
at least fetch the current clock time each loop iteration and check if you have advanced the time. the optimiser wont remove those calls, and therefore wont optimise the loop away - even when you turn on optimisation on.

---

### Post by Bachstelze on 2013-08-09
I might be missing something, but why not just use sleep() et al.?

---

### Post by King Dude on 2013-08-10
> **Bachstelze said:**
> Processors are very complicated beasts. Arguably the most complicated things ever built by man, to the point that it is often said to be a miracle that they work at all. So sometimes, they do weird things, and such performance discrepancies are somewhat common. Unless you want to dig very deep in their insides, it's probably better to not give it too much thought. :p
Processors aren't that complicated. Just a mess load of millions of transistors and resistors. You can make them from scratch if one had the time and Assembly programming skills (of course, don't expect it to be super fast).

---

### Post by Boab1993 on 2013-08-10
Possible problem on multicore optimisation?

---

### Post by JRV on 2013-08-10
> **Bachstelze said:**
> I might be missing something, but why not just use sleep() et al.?

sleep(), delay() work in one second increments, too slow, I want a delay of ~ 1/5 second.

---

### Post by r-senior on 2013-08-10
Have a look at nanosleep.

[https://www.gnu.org/software/libc/manual/html_node/Sleeping.html](https://www.gnu.org/software/libc/manual/html_node/Sleeping.html)

---

### Post by ofnuts on 2013-08-10
> **King Dude said:**
> Processors aren't that complicated. Just a mess load of millions of transistors and resistors. You can make them from scratch if one had the time and Assembly programming skills (of course, don't expect it to be super fast).

Yeah, just a SMOP... really :)

---

### Post by trent.josephsen on 2013-08-10
> **King Dude said:**
> Processors aren't that complicated. Just a mess load of millions of transistors and resistors.
Antennas aren't that complicated. Just a mess load of conductive line segments.
Cars aren't that complicated. Just a mess load of iron, copper and rubber pieces.
Steel isn't that complicated. Just a mess load of iron and carbon.
DNA isn't that complicated. Just a mess load of adenine, cytosine, guanine and thymine.
Brains aren't that complicated. Just a mess load of millions of neurons.

It's not the individual components, but how they're put together. This is my specific field; I'm certainly capable of implementing a general-purpose processor, but if I had to design my own I'd expect to take 10+ years to match the quality of (say) the original 68k. Fortunately the state of the art has advanced since the 68k came out, or it would take centuries to put today's more complex chips (ARM included) into production.

> You can make them from scratch if one had the time and Assembly programming skills (of course, don't expect it to be super fast).
This statement confuses me. How does knowing assembly language relate to implementing a processor? That's like saying that you could build a car from scratch if you know how to drive one. Or did you mean HDL skills?

---

### Post by King Dude on 2013-08-10
> **trent.josephsen said:**
> Antennas aren't that complicated. Just a mess load of conductive line segments.
Cars aren't that complicated. Just a mess load of iron, copper and rubber pieces.
Steel isn't that complicated. Just a mess load of iron and carbon.
DNA isn't that complicated. Just a mess load of adenine, cytosine, guanine and thymine.
Brains aren't that complicated. Just a mess load of millions of neurons.

It's not the individual components, but how they're put together. This is my specific field; I'm certainly capable of implementing a general-purpose processor, but if I had to design my own I'd expect to take 10+ years to match the quality of (say) the original 68k. Fortunately the state of the art has advanced since the 68k came out, or it would take centuries to put today's more complex chips (ARM included) into production.

Making a processor does not mean reinventing the wheel. Also, you cannot put together DNA and Brains from scratch like you can with processors. And for the record, I have made steel and built cars before.

---

### Post by trent.josephsen on 2013-08-11
> **King Dude said:**
> Making a processor does not mean reinventing the wheel.
Quite so; there are certainly tools available to make digital design much more accessible than it was in the 1980s. The fact that the modern silicon industry relies so heavily on powerful computers running specialized software is a testimony to the complexity of modern processors.

It's not right to dismiss the complexity of a system by reducing it to a bunch of component parts, be they transistors, cells, hydrocarbons, elements, whatever. Your earlier post did just that, implying that processors are simple because they are made of simple building blocks, when that is at best misleading. Despite being made of simple building blocks, processors like the Atom or the i7 *are* vastly complex and it *is* very difficult to reason about their performance on a cycle-to-cycle basis.

---

### Post by King Dude on 2013-08-11
> **trent.josephsen said:**
> Quite so; there are certainly tools available to make digital design much more accessible than it was in the 1980s. The fact that the modern silicon industry relies so heavily on powerful computers running specialized software is a testimony to the complexity of modern processors.

It's not right to dismiss the complexity of a system by reducing it to a bunch of component parts, be they transistors, cells, hydrocarbons, elements, whatever. Your earlier post did just that, implying that processors are simple because they are made of simple building blocks, when that is at best misleading. Despite being made of simple building blocks, processors like the Atom or the i7 *are* vastly complex and it *is* very difficult to reason about their performance on a cycle-to-cycle basis.
I don't believe in complexity. As silly as it may sound, every "complex" thing can be broken up into simple things. Those simple things are what matter, because if you get discouraged by looking at it as a whole you will never go anywhere with it. No successful person ever achieved success by saying something is too complex to work with.

---

### Post by Bachstelze on 2013-08-11
> **King Dude said:**
> I don't believe in complexity. As silly as it may sound, every "complex" thing can be broken up into simple things. Those simple things are what matter, because if you get discouraged by looking at it as a whole you will never go anywhere with it. No successful person ever achieved success by saying something is too complex to work with.

You are now hitting a straw man. Nobody said processors were "too complex to work with", they obviously are not since there are people out there who design them. However :

1. Processors can still in some conditions behave in ways that even their designers must spend a lot of time and effort comprehending. This is called bugs, and they are present in some form or other in all systems which are at least moderately complex.

2. I think it is safe to assume, without any offense meant of course, that OP does not know a lot about the internals of a CPU, and might not be interested in them at all. Then, clearly, speding the time and effort necessary to understand what is going on here would be a waste.

---

### Post by JRV on 2013-08-28
I found the solution to my problem.
This better_sleep.c function that I found makes it run at the speed I Want:

```

/***********************************
 better_sleep.c
***********************************/
#include <errno.h>
#include <time.h>
int better_sleep (double sleep_time)
{
  struct timespec tv;
  /* Construct the timespec from the number of whole seconds... */
  tv.tv_sec = (time_t) sleep_time;
  /* ... and the remainder in nanoseconds. */
  tv.tv_nsec = (long) ((sleep_time - tv.tv_sec) * 1e+9);
  while (1)  
  {
    /* Sleep for the time specified in tv. If interrupted by a
    signal, place the remaining time left to sleep back into tv. */
    int rval = nanosleep (&tv, &tv);
    if (rval == 0)
    /* Completed the entire sleep time; all done. */
    return 0;
    else if (errno == EINTR)
    /* Interrupted by a signal. Try again. */
    continue;
    else
    /* Some other error; bail out. */
    return rval;
  }
return 0;
}

```

Thread marked solved, thanks to all.

---

### Post by ofnuts on 2013-08-29
Can we politely make you notice that this is just a wrapper over the nanosleep() function that was recommended to you 2 weeks ago? (see post #14)

---

### Post by JRV on 2013-08-29
> **ofnuts said:**
> Can we politely make you notice that this is just a wrapper over the nanosleep() function that was recommended to you 2 weeks ago? (see post #14)

Duly noted.

I am just getting started programming in C again after about 20 years.
I learned C with the Borland Turbo C compiler for DOS.
It had a lot of high level functions I was using, so I am just now finding that I didn't know C as well as I thought I did.

Thank you all for you help, and patience.

---

