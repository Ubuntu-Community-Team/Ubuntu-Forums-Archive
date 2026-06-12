---
title: "generating random numbers"
date: 2011-01-24
forum: Programming Talk
---

### Post by manish411 on 2011-01-24
I want to generate 5 random numbers using c++ and everytime I run the program I need 5 different random numbers. I used rand() but everytime I run the program I get similar results. However someone told me about random() and randomize().and I used the code below
for(int j=0;j<5;j++)
{
long k = randomize(10)+1;
cout<<a[k].s<<endl;
}
}
however I get compilation error stating that I cannot recognize the function. I even used#include<cstdlib>

---

### Post by worksofcraft on 2011-01-24
> **manish411 said:**
> I want to generate 5 random numbers using c++ and everytime I run the program I need 5 different random numbers. I used rand() but everytime I run the program I get similar results. However someone told me about random() and randomize().and I used the code below
for(int j=0;j<5;j++)
{
long k = randomize(10)+1;
cout<<a[k].s<<endl;
}
}
however I get compilation error stating that I cannot recognize the function. I even used#include<cstdlib>

Computers are deterministic machines. As such they are not capable of producing a truly random number. (Well not without special hardware which I doubt you have).

Thus computers use pseudo random sequences to simulate random numbers. What you do is you seed the sequence with something unpredictable (like the current time) and then that sets the pseudo random sequence to an initial state that will not likely be repeated. You can then generate successive pseudo random numbers and nobody will ever know that they are not truly random.

Here [learn more about th C/C++ pseudo random sequence functions]("http://www.daniweb.com/forums/thread1769.html").

---

### Post by fct on 2011-01-24
> **manish411 said:**
> 
for(int j=0;j<5;j++)
{
long k = randomize(10)+1;
cout<<a[k].s<<endl;
}
}


It's "srand()", not "randomize()". Plus it returns nothing, you still use "rand()" to get a random number.

Also, "srand()" resets the random number generator according to the seed you input as a param. So if the first random number a seed of "10" generates is "1", then "2", then "3", etc. what your code would be doing is resetting to "1" in each loop iteration.

So use, for example:

srand(a_seed); // before loop!

rand(10); // in loop

---

### Post by Arndt on 2011-01-24
> **manish411 said:**
> I want to generate 5 random numbers using c++ and everytime I run the program I need 5 different random numbers. I used rand() but everytime I run the program I get similar results. However someone told me about random() and randomize().and I used the code below
for(int j=0;j<5;j++)
{
long k = randomize(10)+1;
cout<<a[k].s<<endl;
}
}
however I get compilation error stating that I cannot recognize the function. I even used#include<cstdlib>

Most things you need to know about 'rand' are described in its manual page. Do the command "man rand". It will also tell you about 'srand'.

'random' exists, and it has a manual page, but not 'randomize'.

(Of course, if someone writes a function called 'randomize', it will exist, but the manual pages show you the library functions that are always there in Linux, and can be used directly from C or C++. Or system calls, which have much the same properties.)

What people often do to get different seeds is srand(time(0)), once, in the beginning of the program. (You need to include time.h too, see "man time".) If you are going to run the program more often than once a second, you will have to do something else.

---

