---
title: "Error occurs when install Octave 3.4.0 on ubuntu_12.04 (32-bit)"
date: 2015-07-07
forum: Philippine Team
---

### Post by janis9 on 2015-07-07
Hi, 

I am trying to install Octave 3.4.0 on my laptop, and when I try to do the step "make', the following error always occurs. Anyone can help? Thank you.

[SUB]```
[/SUB]In file included from oct-alloc.cc:29:0:oct-alloc.h:32:28: error: expected ')' before 'item_sz'
oct-alloc.h:39:9: error: expected ';' at end of member declaration
oct-alloc.h:39:23: error: expected ')' before 'size'
oct-alloc.h:42:23: error: 'size_t' has not been declared
oct-alloc.h:57:3: error: 'size_t' does not name a type
oct-alloc.cc:32:26: error: 'void* octave_allocator::alloc' is not a static member of 'class octave_allocator'
oct-alloc.cc:32:26: error: 'size_t' was not declared in this scope
oct-alloc.cc:32:26: note: suggested alternative:
/usr/include/c++/4.6/i686-linux-gnu/./bits/c++config.h:155:26: note:   'std::size_t'
oct-alloc.cc:33:1: error: expected ',' or ';' before '{' token
make[3]: *** [liboctave_la-oct-alloc.lo] Error 1
make[3]: Leaving directory `/home/janis/TLD/octave-3.4.0/liboctave'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/janis/TLD/octave-3.4.0/liboctave'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/janis/TLD/octave-3.4.0'
make: *** [all] Error 2


[SUB]
```[/SUB]

---

### Post by slickymaster on 2015-07-07
Closed. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=2285650").

Please do not create duplicate threads, it dilutes the community’s efforts to provide support and causes confusion.

---

