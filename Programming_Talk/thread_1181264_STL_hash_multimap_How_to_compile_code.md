---
title: "STL hash_multimap: How to compile code?"
date: 2009-06-07
forum: Programming Talk
---

### Post by Rij on 2009-06-07
Hello,

I am writing a C++ application in which I intend to use the STL hash_multimap  associative container. I am not sure what to include, what packages to download so that the code compiles.

Can someone provide an insight please?

Thanks ..

---

### Post by Rij on 2009-06-07
Well, I found a solution.

Use:
#include <ext/hash_map>
using namespace __gnu_cxx;

Although it compiles and works fine, it shows a warning message that a depracated header is used. It suggests that I visit backward_warning.h to find the correct headers.

I consulted that file and there is suggests that I use:
 <unordered_map>, unordered_multimap  instead of <ext/hash_map>, hash_multimap

When I do that, the compiler spews out lines of error starting with the following:
/usr/include/c++/4.3/c++0x_warning.h:36:2: error: #error This file requires compiler and library support for the upcoming ISO C++ standard, C++0x. This support is currently experimental, and must be enabled with the -std=c++0x or -std=gnu++0x compiler options.

Can someone please help?

---

### Post by MadCow108 on 2009-06-07
you probably want the unordered multimap of the TR1 (Technical report 1 for the upcoming standard c++0x)
for that you need to include:
#include <tr1/unordered_map>

example of usage:
std::tr1::unordered_multimap<int, double> mymap;
(you can skip the tr1 in include and namespace if you compile with the flag you mentioned)

TR1 hash container tutorial:
[http://www.codeguru.com/cpp/cpp/cpp_mfc/stl/article.php/c15303__2/](http://www.codeguru.com/cpp/cpp/cpp_mfc/stl/article.php/c15303__2/)

but be aware that you are not coding standard c++ when using this.
The specifications of the elements of TR1 may change in the final standard (or even TR2).
Your search for hash_multimap is probably related to such a change from an earlier proposal.

---

### Post by Rij on 2009-06-07
So long story short: using either one in my code could cause my code to fail int the future?

So is the solution that I use either one and keep my eye out until the final standard has come out and then make the changes accordingly?

---

### Post by MadCow108 on 2009-06-07
it won't fail once compiled it just could get difficult to compile it again in a few years when the tr1 libraries slowly disappear (as they are experimental).
But I have no experience in what happens when standard change occurs (the last was ten years ago :/)

a pretty safe method would probably be using the boost libraries. Most of TR1 is anyway from boost.

---

### Post by Rij on 2009-06-07
Thanks MadCow. Appreciate your help.

---

