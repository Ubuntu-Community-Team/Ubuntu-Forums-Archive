---
title: "I screwed up my include path I think"
date: 2007-01-19
forum: Programming Talk
---

### Post by dumbsnake on 2007-01-19
I am sorry to be posting for help, but I have spent 2-3 hours trying to figure this out so I think it is worth it.  I tried to find the answer online, but couldn't.  And I didn't know what to search for here on the forums so that failed too.

My problem is that when I try to compile programs (using g++ under KDevelop) they don't work if I include <algorithm> or <vector> or presumably any other header like that.  They work otherwise.  I get the following output:

cd '/home/nick/Projects/taogo/debug/src' && WANT_AUTOCONF_2_5="1" make taogo.lo
compiling taogo.cpp (g++)
mkdir .libs
compiling taogo.o (g++)
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:66: error: '::clock_t' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:67: error: '::time_t' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:68: error: '::tm' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:70: error: '::clock' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:71: error: '::difftime' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:72: error: '::mktime' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:73: error: '::time' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:74: error: '::asctime' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:75: error: '::ctime' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:76: error: '::gmtime' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:77: error: '::localtime' has not been declared
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/ctime:78: error: '::strftime' has not been declared
make: *** [taogo.lo] Error 1
*** Exited with status: 2 ***


My sourcecode is simply:

#include <vector>


I stripped down the sourcecode to find the problem.  I think there is something wrong with my include paths, but I am helpless (too many years of visual studio).  Thanks in advance.  If there is something I could read that explains how all this stuff works, I would love to read it because I think it would be worth learning.

---

### Post by hod139 on 2007-01-19
> **dumbsnake said:**
> I am sorry to be posting for help, but I have spent 2-3 hours trying to figure this out so I think it is worth it.  I tried to find the answer online, but couldn't.  And I didn't know what to search for here on the forums so that failed too.

Don't ever feel sorry for posting for help, that's what the forums are for.  Have you installed the package build-essential.

---

### Post by dumbsnake on 2007-01-19
Yeah,

   I installed build-essential.  All the headers are on my system.  I can't really figure out why g++ is including <ctime> at all...   Kind of unnecessary, actually since <vector> doesn't need it.

---

### Post by dumbsnake on 2007-01-19
Apparently if you have a header called "time.h", the library header files I was using find that file in their internal code.  There are 3 problems with this behavior:

1) I have no need for the time header so GCC shouldn't have gone out and included it.

2) The internal implementation of the headers should not use:  #include "time.h", but rather:  #include <time.h>

3) I should not have named a header "time.h", oh well.


Turns out I am a moron, but it does reveal problems in the design of both g++ and the standard library's implementation under g++.  Sorry for the posts.  I hope that this can help someone else that is stupid enough to name a header file "time.h"

---

### Post by swerner on 2008-01-28
Thanks for the post.  I was actually stupid enough to make my own "time" class with a time.cpp and a time.h.  My reaction was "doh how can I be so stupid" after reading your post to the end.

---

### Post by bostonvaulter on 2008-05-15
I had a similar problem.  Although this was on a Mac Mini running OS X it may help others reading this thread.

We did have a time.h file, but it wasn't that that was causing the problem.  It was the statement pair:

#ifndef _TIME_H_
#define _TIME_H_

adding more stuff to the end fixed our problem.

---

