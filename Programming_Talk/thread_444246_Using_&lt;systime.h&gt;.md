---
title: "Using &lt;sys/time.h&gt;"
date: 2007-05-15
forum: Programming Talk
---

### Post by sreagvle on 2007-05-15
To get the system time in milliseconds in my c++ program I want to use gettimeofday() from <sys/time.h>. I have implemented this in a small test program O.K. but I can't get it to work in a larger program I'm working on. The problem is I can't create a pointer to a timeval object. When I run:

[I]timeval *my_time;
cout << "my_time is: " << mytime << endl;[/I]

in the small test program the output is something like:

*my_time is 0xbfc0fc28*

which is fine. In my larger program the output is:

*my_time is: 0*

I think the relevant differences in the test program and the larger one is that the larger one is using OpenGL for graphics and RtAudio which allows me to create sound. Would this make a difference? Here is the command I use to compile the larger program:

g++ -Wall -I/usr/include/ -I/home/eoin/stk-4.2.1/include/ -o bouncing_ball -L/usr/X11R6/lib  bouncing_ball.cpp /home/eoin/stk-4.2.1/src/Release/RtAudio.o /home/eoin/stk-4.2.1/src/Release/BiQuad.o /home/eoin/stk-4.2.1/src/Release/Filter.o /home/eoin/stk-4.2.1/src/Release/Stk.o -lX11 -lXi -lXmu -lglut -lGL -lGLU -lm -lasound

The four .o files are required for creating audio. Maybe the problem is in something I'm including, or the libraries I'm linking to?

Many thanks,

Eoin

---

### Post by lloyd_b on 2007-05-15
I'm a C programmer, rather than C++, but one thing jumps out at me:
```
timeval *my_time;
```
would normally be declared as
```
struct timeval *my_time;
```

I had a quick looks through the various "time.h" files (<time.h>, <sys/time.h> and <bits/time.h>", and I don't see it being typedef'ed anywhere.  Though I would have expected a compile-time error if this were the problem.

One other thing that doesn't look right (I'm assuming this is just a typo in the post, but you never can tell):
```
timeval *my_time;
cout << "my_time is: " << mytime << endl;
```
You're declaring "my_time", but using "mytime"...

Lloyd B.

---

### Post by sreagvle on 2007-05-15
mytime/my_time was indeed a typo in the post, I've used my_time consistently in my code.

I've changed:

*timeval my_time;*

to:

*struct timeval my_time;*

but it hasn't helped. There is no compiler error, but my_time is not being created correctly. If I try to access my_time->tv_sec or my_time->tv_usec then I get a segmentation fault (because my_time is 0 when it should be the address of a timeval structure).

Eoin

---

### Post by WW on 2007-05-15
You changed more than the use of "struct" in your two posts.  Is your declaration
```

struct timeval mytime;

```
or
```

struct timeval *mytime;

```
If it is the latter, then you have not actually created a timeval struct, but only a pointer to one.  No memory for the actual timeval struct has been declared.  The value of the pointer might be zero, or it might be garbage, depending on where the variable is declared. Here's an example:

**stest.cpp**
```

#include <sys/time.h>
#include <iostream>

struct timeval *t1;

using namespace std;

void func()
    {
    struct timeval *t3;

    cout << "t3 = " << t3 << endl;
    }


int main()
    {
    struct timeval *t2;

    cout << "t1 = " << t1 << endl;
    cout << "t2 = " << t2 << endl;
    func();
    return 0;
    }

```
The result:
```

$ ./stest
t1 = 0
t2 = 0
t3 = 0xbfe7ff40
$

```
The value of t3 is garbage; it does not point to a timeval structure that you can actually use.

P.S. In C++, the use of the "struct" keyword in a declaration is optional.

---

### Post by lloyd_b on 2007-05-15
Hang on a sec - something doesn't add up...

Are you using
```
struct timeval * my_time;
```
or
```
struct timeval my_time;
```

The latter is (probably) the one you want.  If you just declare "struct timeval * my_time", then you're just getting a pointer, with no actual data area attached (in which case a null pointer is not at all unreasonable).  The "gettimeofday()" function does NOT allocate any memory - it's up to you to do this.  

Here's a short example program (sorry, in straight C):
```
#include <stdio.h>
#include <sys/time.h>

void main()
{
     struct timeval my_time;

     gettimeofday(&my_time, NULL);

     printf("%d seconds, %d microseconds\n", my_time.tv_sec, my_time.tv_usec);
}
```

Hope this helps....

Lloyd B.

---

### Post by sreagvle on 2007-05-15
Yep that's it. gettimeofday() requires a pointer to a timeval structure to be passed to it, so i created one and passed it to it. But you're both right, i didn't actually create the structure. I have fixed this and It's all working now, many thanks. Apologies for the confusing typos, i did proof read my own posts a few times, but didn't see my own mistakes.

I'm still a little confused as in my small test program I only created a pointer to a timeval structure object but I *could* use it as if it was pointing to an actual timeval structure. Maybe because I didn't create any other variables I didn't use up any more memory and so the memory next to my timeval pointer was used for the structure? Maybe not?

Either way thanks for the help.

Eoin

---

