---
title: "Extern variable"
date: 2010-02-10
forum: Programming Talk
---

### Post by newport_j on 2010-02-10
When I compile my multiple module program I get the following error:

errol@fermi:~/Desktop/desktop_cleanup/WEGtest$ ./compile.sh 
vrt_btm2.c:27: error: ‘repcount’ undeclared here (not in a function) 

Now the line that the error is referring to is in vrt_btm2.c

extern struct   timeval t1_start, t1_end;
extern double   time_sum, time_avg, time[repcount];
extern int      repcount;  

and line 27 is:

extern double   time_sum, time_avg, time[repcount];



I originally defined repcount as a global variable in the main module and I initialized it to 0 there.
I am showing the first few lines of the main program, that shows where I initialized it and typed it as an int.

int main(int argc, char *argv[]){

  int repcount = 0;

  int i, NumThreads, NumWorkers;

  static TEST_RAY_DATA TRD[MAX_NUM_TESTRAYS * MAX_NUM_TARGETS];
  static TEST_RAY_SEG_DATA TRSD[MAX_NUM_TESTRAYS];
  
  static WEG_P_PASS WPP;


However, I am still getting the error as shown above. I am using repcount over several subprograms so I typed it as a global variable. I then used it first in vrt_btm2.c and typed it as a int and tagged it as extern variable. So why am I still getting the error?

Newport_j

---

### Post by Zugzwang on 2010-02-10
Swap these lines: "extern double time_sum, time_avg, time[repcount];" and
"extern int repcount;" - You need to declare "repcount" before using it. However, in your code snipplet, you first use it and then declare it.

Depending on the compiler and the C or C++ language version used, your code might still not compile as the array sizes for "explicit arrays" might need to be known at compile time.

---

### Post by talonmies on 2010-02-10
```
extern double   time_sum, time_avg, time[repcount];  
```I very much doubt that can ever work. *repcount* is not know to the compiler within the scope of the file you are compiling and it isn't a constant. C90 does not support dynamic array declarations like that. Further to that, *repcount* isn't declared at global scope, and you are initializing it to zero. So even if you fix the scope of the declaration and try compiling it as C++ or C99, you would be requesting an array of length 0, which is also illegal.

---

### Post by newport_j on 2010-02-10
I did that, I interchanged the lines as you suggested. I also modified the time{repcount] typing to time_x[repcount[ to avoid problems with bumping into a reserved word. However, when I did that I got the very inscrutable message I show now:

errol@fermi:~/Desktop/desktop_cleanup/WEGtest$ ./compile.sh
vrt_btm2.c:28: error: variably modified ‘time_x’ at file scope

I will now show the changed code.

#include "ModsFunDefs.h"
#include "sys/time.h"
extern struct   timeval t1_start, t1_end;
extern int      repcount;
extern double   time_sum, time_avg, time_x[repcount];

Notice that time[repcount] is now time_x[repcount]. This is so I do not bump into any reserved words (like time).

I also show where I used this in 

vrt_btm2.c

gettimeofday(&t1_start,0);

    INT_BND2( ZTRG, PTRG, SCST, APER,
	      TRD, IRAY1, IRAY2, ZVRT1, ZVRT2,
	      RRAY,   ZRAYu, TRAYu,  PCOSu, PSINu, NSRFo, MBTMo,  NUPRu,  
	      NLWRu, MCRSo, URAYu,  FRAYu,  
	      ORAYu, &UPRSUM, &LWRSUM, &SRCSUM, &RCVSUM, PWRSUM, &TIMSUM, 
	      PHSSUM, &PCSSUM, &PSNSUM, &IMAFLG, Env );

    gettimeofday(&t1_end,0);
    time_x[repcount] = (t1_end.tv_sec-t1_start.tv_sec)*1000000 - t1_end.tv_usec -t1_start.tv_usec;
    time_sum = time_sum + time_x[repcount]; 

Again everything should be fine. 

The code in the main program is unchanged. Thus I will not show it. I need to know how to fix this error?

Newport_j

One more thing. It is true in the original I use it and then I define it, in that c module. Please note that I 
did type repcount and I defined it as a extern variable. I would think that should be enough. It was already defined in main.c and it was tagged extern in vrt_btm2.c so why would that not work?

---

### Post by talonmies on 2010-02-10
```
extern int      repcount;
extern double   time_sum, time_avg, time_x[repcount];

```As I already explained, you cannot do that. Dynamically sized array are illegal in C. So are zero sized declarations.

Further, if you haven't defined *repcount* at global scope (hint: in main() is not global scope), you will still get a undefined symbol for *repcount*.

---

### Post by dwhitney67 on 2010-02-10
newport_j

If I understood correctly, from your earlier posts, you are interested in obtaining a ball-park figure of how much time a function takes to accomplish its task.

Below is some code that demonstrates a way to accomplish this to some degree of accuracy.  Note that when calling functions, there is overhead involved, along with the possibility that the program could be interrupted at any time by the OS so as to allow other applications to run.  This affects delta-time computations derived from time values obtained from gettimeofday(), or for that matter, any utility that offers the current system time.

See if you can use this code, as demonstrated here...

TimeCollector.h:
```

#ifndef TIME_COLLECTOR_H
#define TIME_COLLECTOR_H

int init_metrics(const unsigned int size);
void destroy_metrics();

int mark_begin();
int mark_end();

void print_metrics_report();

#endif

```

TimeCollector.c:
```

#include "TimeCollector.h"
#include <stdlib.h>
#include <sys/time.h>
#include <stdio.h>

struct Metric
{
   struct timeval begin;
   struct timeval end;
};

static struct Metric* metrics    = 0;
static unsigned int   numMetrics = 0;
static unsigned int   index      = 0;

int init_metrics(const unsigned int size)
{
   metrics = calloc(size, sizeof(struct Metric));

   if (!metrics)
   {
      return -1;
   }

   numMetrics = size;
   return 0;
}

void destroy_metrics()
{
   free(metrics);

   metrics    = 0
   numMetrics = 0;
   index      = 0;
}

int mark_begin()
{
   if (index == numMetrics)
   {
      return -1;
   }

   gettimeofday(&(metrics[index].begin), 0);

   return 0;
}

int mark_end()
{
   if (index == numMetrics)
   {
      return -1;
   }

   gettimeofday(&(metrics[index].end), 0);
   ++index;

   return 0;

}

void print_metrics_report()
{
   struct timeval total = {0, 0};

   for (unsigned int i = 0; i < numMetrics; ++i)
   {
      struct timeval delta = {0, 0};

      delta.tv_sec  = metrics[i].end.tv_sec  - metrics[i].begin.tv_sec;
      delta.tv_usec = metrics[i].end.tv_usec - metrics[i].begin.tv_usec;

      if (delta.tv_usec < 0)
      {
         --delta.tv_sec;
         delta.tv_usec += 1000000;
      }

      printf("Metric %d: %d seconds, %d us\n", (i+1), (int)delta.tv_sec, (int)delta.tv_usec);

      total.tv_sec  += delta.tv_sec;
      total.tv_usec += delta.tv_usec;

      if (total.tv_usec >= 1000000)
      {
         ++total.tv_sec;
         total.tv_usec -= 1000000;
      }
   }

   printf("Total Metric: %d seconds, %d us\n", (int)total.tv_sec, (int)total.tv_usec);
}

```

Main.c:
```

#include "TimeCollector.h"
#include <unistd.h>

void special_function()
{
   usleep(1500);
}

int main(void)
{
   /* provide the number of measurement samples that are required */
   init_metrics(10);

   /* simulate calling special function 10 times */
   for (int i = 0; i < 10; ++i)
   {
      mark_begin();

      special_function();

      mark_end();
   }

   /* print report (to stdout) */
   print_metrics_report();

   /* clean up */
   destroy_metrics();

   return 0;
}

```
To build this test program, do something like:
```

gcc Main.c TimeCollector.c -o metrics

```
Then to run:
```

./metrics

```
You should be able to adapt something similar for your needs, without having to fiddle with global variables out of the ying-yang.

---

### Post by talonmies on 2010-02-10
This is all in aid of collecting timing data? I might be missing something, but why not just use the profiler? *gprof* can provide call statistics and timing without needing to write a single line of code.

---

