---
title: "C++ via g++ iostream errors"
date: 2009-07-02
forum: Programming Talk
---

### Post by wbest on 2009-07-02
Hey, I have some windows C++ code I need to port to Linux (Really wbest?  You do?  I wouldn't have guessed based off the other dozen threads you started on the subject)

Anyway, I'm trying to compile a program, but keep getting the following error output

In file included from include/rw/rstream.h:46,
                 from include/rw/cstring.h:33,
                 from include/core/typedef.h:35,
                 from include/core/property.h:25,
                 from include/core/core.h:32,
                 from include/core/string_helper.h:16,
                 from include/core/trans.h:14,
                 from include/tw_precomp.h:108,
                 from SMsgGroup.cpp:1:
/usr/include/c++/4.2/backward/iostream.h:35: error: ‘ostream’ is already declared in this scope
/usr/include/c++/4.2/backward/iostream.h:36: error: ‘istream’ is already declared in this scope
/usr/include/c++/4.2/backward/iostream.h:37: error: ‘ios’ is already declared in this scope

*rstream.h only calls #include <iostream> once 
    (I changed the code to make it only call once, originally it had several setup in if/thens such that          only one could be called)

*tpyedef.h calls #include <iostream> (as well as strstream) in
#ifdef NOT_STL_STRING 
  #include <iostream> 
  #include <strstream> 
 
  #define RWAV_STRING 
#endif 
 
#ifdef USE_COMPAT 
  #include <rw/cstring.h>

*property does not call it

*core does not call it

*string helper does not call it

*trans does not call it

*tw_precomp calls it, as well as <io>
    (io is a windows only header file, near as I can tell, right now I have an empty file standing in for          it, under suggestion in another thread)

*SMsgGroup does not call it


I can't give out too much code, because this is for work and there's non-disclosure and copyright laws and stuff I need to worry about; I'm already a bit uneasy putting out what i put out.

---

### Post by dwhitney67 on 2009-07-02
How are you trying to compile the code?  In other words, what pre-processor information are you passing g++?

Also, it would be helpful if you did post some code, because we are unable to harness our psychic powers to peer through your company's walls and see the contents of such files as /usr/include/rw/rstream.h.

---

### Post by wbest on 2009-07-02
I'm using:
g++ -I include -w SMsgGroup.cpp

I'm not sure how much code to post, I obviously can't post all of, because there's just too much.  What files do you want code from?  I posted some snipets that I believed pertinent above, but if you want more, I can add some lines

As for rstream, I'll post some more, and yes it gets past that original ifndef preprocessor call (I put in a fake #include call and it couldn't find the fake file):
#ifndef __RWRSTREAM_H__ 
#define __RWRSTREAM_H__ 
 
/* 
RANDOM COMMENTS/COPYRIGHT INFO/ETC
 */ 
 
#include "rw/defs.h" 
#include <iostream>
/* 
#  ifdef __GLOCK__ 
#    include <iostream.hxx> 
#  else 
#    if !defined(RW_NO_IOSTD) 
#      include <iostream> 
#    else 
#      include <iostream.h> 
// RSL 
#                if defined(_MSC_VER) && _MSC_VER >= 1300 
#                    include <iostream> 
#                else 
#                    include <iostream.h> 
#                endif
#    endif 
#  endif
*/

PROGRAM BODY

#endif /*__RWRSTREAM_H_*/



It is hard to find a happy median between adding all the info needed to solve a problem and the limits of both copyright and space when adding code to get help on a forum.  I had hoped I gave enough of the first time, but evidently you needed more, sorry.

---

### Post by dwhitney67 on 2009-07-02
EDIT:  Forget what I stated just moments ago; I got my if-else-endif's mixed up and the section of code that caused me grief is commented out.

Check the other /usr/include/rw header files to ensure that <iostream.h> is not being included.

---

### Post by MadCow108 on 2009-07-02
should'nt it be
#include <sstream>
?

if I use strstream I get deprecated warnings

---

### Post by dwhitney67 on 2009-07-02
> **MadCow108 said:**
> should'nt it be
#include <sstream>
?

if I use strstream I get deprecated warnings

Good call!  ... but still, the OP is getting errors, not warnings.

---

### Post by MadCow108 on 2009-07-02
/usr/include/c++/4.2/backward/iostream.h
doesn't the backward mean it tries to read backward compatible header files?
Maybe he tries to include once a deprecated one and once a recent one.
If the have different include guard defines this could result in the error.

Is there maybe a #include <iostream.h> somewhere?

---

### Post by dwhitney67 on 2009-07-02
> **MadCow108 said:**
> /usr/include/c++/4.2/backward/iostream.h
doesn't the backward mean it tries to read backward compatible header files?
Maybe he tries to include once a deprecated one and once a recent one.
If the have different include guard defines this could result in the error.

Is there maybe a #include <iostream.h> somewhere?

You are probably correct, but without the privilege of seeing the other header files, it is anyone's guess right now.

I think the OP should fix each of the /usr/include/rw files to be compatible with Linux, while also supporting the M$ platform.  Something like:

```

#ifndef _MSC_VER
#include <iostream>

#elif _MSC_VER >= 1300
#include <iostream>

#else
#include <iostream.h>

#endif

```

---

### Post by wbest on 2009-07-07
Sorry this is late, I was away from work over the weekend, so I wasn't checking my threads.  Hopefully this still finds answers...
 
Anyway, I'm pretty sure I already went through and checked to make sure by going down the line that only one iostream.h was included.  I'll check again and get back to you all.
 
And the header files and stuff in /rw should all be platform independent.  My company bought it from a third party, and my boss told me they should work on both PC and *NIX systems.  I've had no problems with them at any other time, no compiler errors or anything, other than this.  So I'm not conviced they are the problem.
 
I'm not expecting you guys to work miracles or anything...I don't want to come off sounding ungrateful or making the problem sound ridculous (does it sound ridiculous and unsolvable?  I fear it may) or anything.  
 
So yeah, I'll check again on what you guys have been saying and try to get back to you.

---

