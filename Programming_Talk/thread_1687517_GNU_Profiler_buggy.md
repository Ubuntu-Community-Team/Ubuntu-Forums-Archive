---
title: "GNU Profiler buggy?"
date: 2011-02-14
forum: Programming Talk
---

### Post by pommessemmel on 2011-02-14
[SIZE=2][B]Hi,

I've got the following program:[/B][/SIZE]

```

#include<cmath>
#include<iostream>

using namespace std;
const int count=100000000; const double f=0.00000042;
void times() { for(int c=0;c<count;c++) c*f*c; }
void sqrts() { for(int c=0;c<count;c++) sqrt(c*f); }

int main() {
    double d;
    cout << 0; cout.flush();
    times();
    cout << 0; cout.flush();
    sqrts();
    cout << 0 << endl; cout.flush();
    return(0);
}
```[SIZE=2]**When profiling using the commands:**[/SIZE]
```

g++ prog.cpp -pg
./a.out
gprof a.out > a
vim a
```[SIZE=2]**I get among other stuff the following:**[/SIZE]
```

  %   cumulative   self              self     total    
 time   seconds   seconds    calls  ms/call  ms/call  name    
 54.17      0.39     0.39        1   390.00   390.00  times()
 45.83      0.72     0.33        1   330.00   330.00  sqrts()
```[SIZE=2]**This information seems wrong because when executing the program the output shows that the function sqrts() takes about 10 times longer to execute than the function times().**[/SIZE]

[SIZE=2]**Any ideas or suggestions?**[/SIZE]

---

### Post by pommessemmel on 2011-02-14
I discovered another obscurity. When using sqrt(float) instead of sqrt(double) I get a reasonable output:

```

  %   cumulative   self              self     total    
 time   seconds   seconds    calls   s/call   s/call  name    
 88.23      6.97     6.97 100000000     0.00     0.00  std::sqrt(float)
  6.58      7.49     0.52        1     0.52     7.49  sqrts()
  5.19      7.90     0.41        1     0.41     0.41  times()

```**(**You can change *double f=0.00000042;* to *float f=0.00000042; *or use *sqrt((float)(c*f));***)**

---

### Post by MadCow108 on 2011-02-14
the default libm installation is compiled without profile information which seems to be the cause of the screwup here
you need to install libc6-prof and then link with /usr/lib/libm_p.a
then it also works for doubles

the reason it works for floats is that in that case part of the function is implemented inline which gets compiled with profiling information by you.
(see the machine code with objdump -S)
the same seems to be the case for long doubles.
But I have no idea why

the callgrind profiler also gets it right

---

### Post by pommessemmel on 2011-02-14
Thank you for the quick and competent response.
Using aptitude I installed the package libc6-prof.
I compiled using the following commands separately:

g++ /usr/lib/libm_p.a test.cpp -pg
g++ -l m_p test.cpp -pg

In both cases the problem remains exactly as it is. 
(Works for float but not for double)

---

### Post by MadCow108 on 2011-02-14
when using static libraries the result is dependent on the order on the command line.
the library must be after the object that uses it. This is correct:
```
g++ test.c /usr/lib/libm_p.a
```
Otherwise it will use the symbols from the shared non-profiled library

here my output for all three variants. libm_p wrong order, no libm_p, libm_p right order
```

~/prog$ g++ /usr/lib/libm_p.a test.c -pg && ./a.out && gprof a.out | head a
000
Flat profile:

Each sample counts as 0.01 seconds.
  %   cumulative   self              self     total           
 time   seconds   seconds    calls  ms/call  ms/call  name    
 63.43      0.22     0.22        1   222.02   222.02  times()
 37.48      0.35     0.13        1   131.19   131.19  sqrts()
  0.00      0.35     0.00        1     0.00     0.00  global constructors keyed to times()
  0.00      0.35     0.00        1     0.00     0.00  __static_initialization_and_destruction_0(int, int)

~/prog$ g++ test.c  -pg && ./a.out && gprof a.out | head a
000
Flat profile:

Each sample counts as 0.01 seconds.
  %   cumulative   self              self     total           
 time   seconds   seconds    calls  ms/call  ms/call  name    
 57.28      0.21     0.21        1   211.93   211.93  times()
 43.64      0.37     0.16        1   161.47   161.47  sqrts()
  0.00      0.37     0.00        1     0.00     0.00  global constructors keyed to times()
  0.00      0.37     0.00        1     0.00     0.00  __static_initialization_and_destruction_0(int, int)

~/prog$ g++ test.c /usr/lib/libm_p.a  -pg && ./a.out && gprof a.out | head a
000
Flat profile:

Each sample counts as 0.01 seconds.
  %   cumulative   self              self     total           
 time   seconds   seconds    calls   s/call   s/call  name    
 44.66      0.83     0.83 100000000     0.00     0.00  __ieee754_sqrt
 18.29      1.17     0.34 100000000     0.00     0.00  sqrt
 17.76      1.50     0.33        1     0.33     1.63  sqrts()
 11.84      1.72     0.22        1     0.22     0.22  times()
  6.73      1.85     0.13 100000000     0.00     0.00  isnan
```

I still find it strange that the output without libm_p is so completely wrong. Maybe someone else can shed some light on this.

---

### Post by pommessemmel on 2011-02-16
Same results here. 
Thanks a lot. I was quite surprised to get such a superb quality response.

Having tried Valgrind now I decided it's probably best to switch profiling tools. 
Valgrind seems much more sophisticated than gprof.

Again thanks.

---

### Post by MadCow108 on 2011-02-16
you should check out the kcachegrind gui for callgrind.
It makes profiling a lot easier.

another tool you might be interested in is oprofile. It is much more complicated but also more "powerful". It has complete kernel profiling so it includes system calls.
But it is overkill for simple tasks.

---

