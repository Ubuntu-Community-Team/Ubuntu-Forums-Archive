---
title: "Measuring the time of functions"
date: 2010-09-20
forum: Programming Talk
---

### Post by gaurish108 on 2010-09-20
I am a beginner to C and C++ and so far I have learned two ways to measure the time my program takes to run.

[COLOR=Red]Method 1[/COLOR]: Just compile your C file and if the executable is say a.out just type **time ./a.out**

[COLOR=Red]Method 2[/COLOR]: Here the general structure of the code is 
```
#include<stdio.h>
#include<time.h>

int main(void)

{
clock_t start, stop;

start= clock();
//Do whatever you want to do
stop=clock();

printf("Time taken is %f milliseconds", ((double) (stop-start)) / CLOCKS_PER_SEC);
}


```My questions are: 

[COLOR=Green]Question 1[/COLOR] Do Method 1 and Method 2 return the same times?

[COLOR=Green]Question 2[/COLOR] Method 1 gives three times ***real, usr*** and ***sys  ***. Is it true that USR+SYS= TIME GIVEN BY METHOD 2

I have performed some experiments with small codes which return the squares of numbers uptill 36000 and  I **feel **the answer to question 2 is yes

Since I am a beginner a detailed answer will be most appreciated. Thank you very much!!

---

### Post by Zugzwang on 2010-09-21
> **gaurish108 said:**
> [COLOR=Green]Question 1[/COLOR] Do Method 1 and Method 2 return the same times?


Hard to say. Method 1 will probably include the times to load your application and the necessary libraries in SYS and the times spent in library functions at program startup in REAL.

> **gaurish108 said:**
> 
[COLOR=Green]Question 2[/COLOR] Method 1 gives three times ***real, usr*** and ***sys  ***. Is it true that USR+SYS= TIME GIVEN BY METHOD 2


No, this is certainly not true. If an application is waiting for I/O or sleeping, then this counts for the wall clock time ("REAL") but neither for USR nor for SYS. Example:

[PHP]
#include <iostream>

int main() {
    std::cout << "Give me a number" << std::endl;
    int i;
    std::cin >> i;
    std::cout << "Ok, thanks for giving me a " << i << std::endl;
}
[/PHP]

Running & compiling the program yields:

```

me@my-computer:/tmp$ g++ test.cpp
me@my-computer:/tmp$ time ./a.out 
Give me a number
515
Ok, thanks for giving me a 515

real    0m2.351s
user    0m0.000s
sys     0m0.010s

```

---

### Post by dwhitney67 on 2010-09-21
I agree.  A simple solution to gauging the time it takes to execute a function is to capture the time before and after the call to the function.  Using gettimeofday() one such way to do this.

For example (and forgive me if my mathematical prowess is off)...
```

#include <iostream>
#include <unistd.h>
#include <sys/time.h>

void function()
{
   sleep(1);   // artificial load
}

double computeDelta(const timeval& begin, const timeval& end)
{
   timeval delta;

   delta.tv_sec  = end.tv_sec - begin.tv_sec;
   delta.tv_usec = end.tv_usec - begin.tv_usec;

   if (delta.tv_usec < 0)
   {
     --delta.tv_sec;
     delta.tv_usec += 1000000000L;    // add 1E9 usec
   }

   return delta.tv_sec + double(delta.tv_usec) / 1000000000.0;
}

int main()
{
   using namespace std;

   timeval begin, end;

   gettimeofday(&begin, 0);
   function();
   gettimeofday(&end, 0);

   cout.precision(12);
   cout << "It took " << computeDelta(begin, end) << " seconds to execute function()." << endl;
}

```

---

### Post by Mordred on 2010-09-21
Try profiling if you want to find out how much time your program is
spending in each of the functions.
This should give you a more acurate view on where to optimize.

One profile for gcc is gprof:

[http://www.cs.utah.edu/dept/old/texinfo/as/gprof_toc.html]("http://www.cs.utah.edu/dept/old/texinfo/as/gprof_toc.html")

---

