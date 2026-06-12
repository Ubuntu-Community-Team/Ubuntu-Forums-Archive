---
title: "Lambda expressions for C"
date: 2009-05-21
forum: Programming Talk
---

### Post by soltanis on 2009-05-21
My two favorite concepts in programming are C and lambda expressions (anonymous functions).

Now the biggest obstacle to having functions that write functions in C is the fact that C is compiled directly to machine-specific binary. With the ability to load shared libraries dynamically, on demand, and with modern C compilers, perhaps one could eventually realize the dream of such proposed languages as `C (which is C with more or less one extension, a backtick operator, which marks a block of code to be compiled at run-time).

What I'm saying is this; ostensibly, one could write a C compiler that did something like this:

1) Recognizes a certain section of code as being marked for run-time compilation; or allows arbitrary, run-time determined data to be compiled into machine code, then executed on demand;

2) Compiles the rest of the executable, and links to it a fast C compiler or C compiler library (ex. tcc).

3) At run-time, compiles code on demand by running the compiler through it, writing it into a shared library and loading the library into memory, mapping things like function pointers to functions in that library;

4) On-demand code can now be executed by use of function pointers.

The first versions of tcc didn't even write executable code to disk; they loaded the binary straight into memory. Those familiar with tcc also know that it can be used as a "scripting" language, whereby a C "script" is compiled and immediately executed by tcc. Which is pretty damn cool.

C, extended with the ability to have code that writes code, would be (in my opinion) one hell of an ultimate language.

---

### Post by nvteighen on 2009-05-21
gcc allows nested functions, so that may be a place to look for implementing some sort of lambda closure in C. If you can combine that with function pointers and some heavy preprocessor macros I imagine you can use that... The problem: it's non-standard C code.

An alternative is to use GLib's closure facilities... but I don't how they perform or work...

The issue is the following; does C need something like that? Remember it is a low-level language... if you want a C with closures, maybe you are looking into Perl... (or Python?)

```

use strict;
use warnings;

my $blah = sub {print "a";};
$blah->();

```

Closures are powerful in a context where your model is abstract enough to have them... In Lisp, closures are natural. In Python, even when you have lambdas available, they just don't feel quite right... as they were something strange in the language (maybe because of the OOP-ness, which makes you capture data in a class instead of an environment...)

But it could be nice to see something like this, even if just for academic reasons and see how nice/nasty it works :)

---

### Post by soltanis on 2009-05-21
gcc only allows functions to be nested downwards (like, closures not possible).

What I mean is not necessarily a closure (although those are cool), I mean functions capable of writing functions. The only way to do that would be...well...write a compiler (that's what they do).

Tcc is a very fast compiler, unfortunately, it is x86 only. If one were to implement this idea, it would be very much limited to one platform only, not ideal.

---

### Post by CptPicard on 2009-05-21
Lambdas can be compiled fine, it is the environment that essentially requires gc. Hello Greenspun's tenth rule!

---

### Post by hod139 on 2009-05-21
Lambda expressions are coming to C++: [http://www.boost.org/doc/libs/1_39_0/doc/html/lambda.html](http://www.boost.org/doc/libs/1_39_0/doc/html/lambda.html)
[http://en.wikipedia.org/wiki/C%2B%2B0x#Lambda_functions_and_expressions](http://en.wikipedia.org/wiki/C%2B%2B0x#Lambda_functions_and_expressions)

---

