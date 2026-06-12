---
title: "C++ - multiple definition of nspace::foo"
date: 2006-12-12
forum: Programming Talk
---

### Post by me1on on 2006-12-12
I'm taking some SDL tutorials and everything is going great (at the moment I'm learning how to make a dot move around the screen :)) but I don't really like the way the code is designed. All the code is crammed into one file making it difficult to navigate, so I had the brilliant idea of spreading the code into separate files and putting all the custom SDL-related functions in it's own namespace. Problem is, I've been staring at my new code for about 3 hours and I can't figure out what's wrong with it. I managed to reproduce the error with a much smaller program, so here it is (this is C++ code by the way):

test.cpp
```
// test program
#include "nspace.h"

int main()
{
	nspace::display();
	
	return 0;
}

```

nspace.h
```
#ifndef NSPACE_H_
#define NSPACE_H_

#include <string>

namespace nspace
{
	std::string foo = "testing";
	
	void display();
}

#endif // NSPACE_H_

```

nspace.cpp
```
#include <iostream>
#include "nspace.h"

namespace nspace
{
	void display()
	{
		std::cout << foo << std::endl;
	}
}

```

Here is the compiler output:
```
cd '/home/john/Projects/test/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
make all-recursive
Making all in src
compiling test.cpp (g++)
compiling nspace.cpp (g++)
linking test (g++)
linking test (g++)
nspace.o: In function `__tcf_1':
/home/john/Projects/test/src/nspace.h:8: multiple definition of `nspace::foo'
test.o:/home/john/Projects/test/src/nspace.h:8: first defined here
collect2: ld returned 1 exit status
make[2]: *** [test] Error 1
make[2]: Target `all' not remade because of errors.
make[2]: Nothing to be done for `all-am'.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

```

It seems like simple enough code, but I've been trying to figure out how to fix the problem (without having to combine everything into one file) for about 3 hours now and it's really starting to annoy me. It's probably a stupid mistake, but could anyone please help me out?

Edit: Thanks Thumper, using extern solved the problem!

---

### Post by thumper on 2006-12-12
Your problem lies in nspace.h.

You are going to have multiple definitions of the string foo.  If you really want this in the header file then declare it extern and define it in the cpp.

Header...
```

namespace foo {
  extern std::string bar;
}
```

Source...
```

namespace foo {
  std::string bar="bzr";
}
```

---

### Post by po0f on 2006-12-12
me1on,

I haven't tried thumper's solution, but I got it working by declaring nspace::foo as [FONT="Courier New"]const[/FONT] (in the header file).  [FONT="Courier New"]extern[/FONT] might work as well, I don't know the specifics as to why they both work.

---

### Post by surfingpenguin on 2007-03-31
I just ran into this problem myself, thank you thumper for that solution.
Just wondering, why does this happen and what exactly does extern do? The multiple definition thing doesn't happen if instead of using a namespace you make a wrapper class (I tried).
I'm still making my way through all of the nuances of C++, so shedding some light on anything would be quite helpful.

---

### Post by Jmccaffrey on 2007-03-31
> **surfingpenguin said:**
> I just ran into this problem myself, thank you thumper for that solution.
Just wondering, why does this happen and what exactly does extern do? The multiple definition thing doesn't happen if instead of using a namespace you make a wrapper class (I tried).
I'm still making my way through all of the nuances of C++, so shedding some light on anything would be quite helpful.

When programming in C++ you need to consider how and why a header file works in the first place, when putting something in that file.  When a .cpp or .c file includes a header file, the pre-processor actually reads the header file and in effect pastes it into the including file.  You would achieve the same effect if you copy and pasted your header file into your source file each time it was included.  The problem with this is that your variable declaration in your header file is being "pasted" into multiple places after pre-processing.  In C++, data cannot be stored in a header file, because when the code is compiled headers are included in .c and .cpp files which are translated into .o files where code and data(static) are actually declared.  To fix this common problem, the extern keyword was devised, this keyword will in effect allow you to say that a variable is declared elsewhere in the body of code, and it is now the job of the linker to resolve its location after compilation.   This will let you "store" your data variable in the .c file (which will become a .o file), and have other .o files link to and access that data.

---

### Post by surfingpenguin on 2007-03-31
Ah, thanks a lot.

---

