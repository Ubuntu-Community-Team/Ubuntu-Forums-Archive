---
title: "DIfference between manpages-dev and libstdc++ manpage"
date: 2009-03-18
forum: Programming Talk
---

### Post by flylehe on 2009-03-18
Hi,
I was wondering what is the difference between manpages-dev and libstdc++ manpage? 
Is there a manpage used in terminal to show the basic syntax for C and C++ like for class, virtual function, while, for and etc...?
Thanks!

---

### Post by snova on 2009-03-18
> **flylehe said:**
> I was wondering what is the difference between manpages-dev and libstdc++ manpage?

I've never heard of libstdc++ manpages, what/where are they?

> Is there a manpage used in terminal to show the basic syntax for C and C++ like for class, virtual function, while, for and etc...?

Not to my knowledge.

[http://www.cplusplus.com/](http://www.cplusplus.com/)

---

### Post by flylehe on 2009-03-18
libstdc++ is GNU standard C++ library and has its own manpage.
So do you know the part of manpages-dev for C and C++? What does it cover?

---

### Post by snova on 2009-03-18
> **flylehe said:**
> libstdc++ is GNU standard C++ library and has its own manpage.

I've never seen it. What package is it in?

> So do you know the part of manpages-dev for C and C++? What does it cover?

I think it's mostly C, but most (if not all) of the standard C library, and Linux system calls. There are over 1,600 manpages in it.

---

### Post by flylehe on 2009-03-18
If you type: apt-cache search libstdc++, you will get a bunch of packages.

---

### Post by snova on 2009-03-18
> **flylehe said:**
> If you type: apt-cache search libstdc++, you will get a bunch of packages.

Interesting; wish I'd discovered libstdc++6-4.3-doc earlier. There's about four hundred manpages in it, but the bulk appears to be HTML (about ten times as many files).

As an overall answer, then, manpages-dev covers the C library; libstdc++ the C++ one.

---

### Post by flylehe on 2009-03-18
A new question:
I have such an impression that the info about which file to include is not always clearly specified or even unavailable on manpage. For example, by man std::vector, I am not able to find such info as to add "#include<vector>" in my code if I would like to use std::vector. Or am I missing something?

---

### Post by WitchCraft on 2009-03-18
> **flylehe said:**
> 
Or am I missing something?


> 
Constructor & Destructor Documentation
   template<typename _Tp, typename _Alloc = std::allocator<_Tp>> std::vector<
       _Tp, _Alloc >::vector () [inline]
       Default constructor creates no elements.

       Definition at line 213 of file stl_vector.h.
stl_vector.h --> #include <vector>

general:
stl_something.h --> #include <something>

[http://www.google.com/codesearch](http://www.google.com/codesearch)
[http://code.google.com](http://code.google.com)

---

### Post by geirha on 2009-03-19
> **flylehe said:**
> A new question:
I have such an impression that the info about which file to include is not always clearly specified or even unavailable on manpage. For example, by man std::vector, I am not able to find such info as to add "#include<vector>" in my code if I would like to use std::vector. Or am I missing something?

It's written in the first line of the synopsis ...
```

std::vector(3)                                                  std::vector(3)

NAME
       std::vector - A standard container which offers fixed time access to
       individual elements in any order.

SYNOPSIS
       #include <vector>

       Inherits std::Vector_base< Type, Alloc >.

...

```

---

### Post by flylehe on 2009-03-19
To WitchCraft: thanks!

To geirha: mine is different:
> std::vector(3)                                                  std::vector(3)

NAME
       std::vector -

SYNOPSIS
       Inherits std::_Vector_base< _Tp, _Alloc >.

       Inherited by std::match_results< _Bi_iter > [private].

Detailed Description
   template<typename _Tp, typename _Alloc = std::allocator<_Tp>> class
       std::vector< _Tp, _Alloc >
       A standard container which offers fixed time access to individual
       elements in any order.

       Meets the requirements of a container, a reversible container, and a
       sequence, including the optional sequence requirements with the
       exception of push_front and pop_front.


I installed libstdc++6-4.3-doc through synaptic package manager. What did you install, geirha?

---

### Post by geirha on 2009-03-19
> **flylehe said:**
> 
I installed libstdc++6-4.3-doc through synaptic package manager. What did you install, geirha?

libstdc++-doc on Hardy

---

### Post by geirha on 2009-03-19
> **geirha said:**
> libstdc++-doc on Hardy

Err, how did I manage to get that wrong?. I meant [libstdc++6-doc](apt:libstdc++6-doc)

---

### Post by flylehe on 2009-03-19
I can't find libstdc++6-doc for installation. Maybe the name is not correct?

---

### Post by snova on 2009-03-19
> **flylehe said:**
> I can't find libstdc++6-doc for installation. Maybe the name is not correct?

geirha is running Hardy, so if you are running Intrepid, it doesn't exist.

---

### Post by geirha on 2009-03-19
Yeah, according to this, its been around since dapper, and the last release to have that package is Hardy; [http://packages.ubuntu.com/search?keywords=libstdc%2B%2B+-doc&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libstdc%2B%2B+-doc&searchon=names&suite=all&section=all). Looking more closely at it, it seems to be documentation for g++-3.4 (which is an ancient version by now), so the version you have installed is probably the preferred one. I wonder why they removed such useful information from the docs though. Doesn't make sense to me.

---

