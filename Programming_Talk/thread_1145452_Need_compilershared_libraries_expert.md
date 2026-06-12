---
title: "Need compiler/shared libraries expert"
date: 2009-05-01
forum: Programming Talk
---

### Post by uffish2 on 2009-05-01
Hi guys,

Here is my problem: I have a program that I wrote in the past and used to work. It uses libplot. I took this program to ubunutu, compiled it and tried to run it. It crashed immediately with a segmentation fault. Opening it in the gdb, it just said that the program crashed in "main(argc, argv)" so it somehow must have crashed when initializing libplot or something.

Does anyone have any idea how to proceed? Should I post the program?

Thx,

---

### Post by dwhitney67 on 2009-05-01
> **uffish2 said:**
> ...
Should I post the program?

Thx,

That would help; we are not psychic.  A segfault is generally caused by accessing an uninitialized pointer (i.e. one that is zero, or possibly pointing to an address outside the program space).

---

### Post by uffish2 on 2009-05-01
There you go. I had to add a ".bz2" to be able to upload it but it isn't zipped. Just remove the extension.

Run it without any parameters (in which case it SHOULD just print a usage message and exit), and it will crash.


Thx.

---

### Post by uffish2 on 2009-05-01
On a second thought, here is the Makefile too. Again, remove the ".bz2"

---

### Post by dwhitney67 on 2009-05-02
Your code looks more like C than C++; I would recommend that if you are interested in using C++, that in lieu of using arrays, that you use the STL vector.

Also, in lieu of passing objects by pointer, pass by reference.

I was unable to build your application because my system lacks plot.h and libplot.a (or .so).

I also was unable to deduce what parameters you passed to the application when you ran it.  Once again, I am not psychic.

If you are able to build the app on your system, I suggest you load the executable into the 'gdb' debugger, and see where it crashes.

```

make percol
gdb percol
(gdb) run <your parameters>

```

---

### Post by uffish2 on 2009-05-03
Hi,
 
The whole point is libplot. It's a standard ubuntu package called IIRC plotutils.
 
As for the parameters, as I said, run it without any parameters.
 
As for the debugger, as I said, I tried it and it said the program crashed in the line that says 
 
"main(int argc, char **argv)"
 
which makes no sense - unless it somehow crashed when loading or initializing libplot.
 
Thanks,

---

### Post by dwhitney67 on 2009-05-03
> **uffish2 said:**
> ...
 
As for the parameters, as I said, run it without any parameters.
 
...

It has been a few days since I looked at your code; if I recall correctly, you need to pass it command-line args.  By not passing the args, and with the app assuming you did... boom!

Please recheck your main() function, and search for where 'argv' is being used.

argv[0] = program name
argv[1] = first command-line parameter
argv[2] = second ...
argv[3] = third  ...
...

---

### Post by Furat on 2009-05-03
Can tou post the backtrace after the crash

---

### Post by stroyan on 2009-05-04
The percol program is crashing when trying to initialize local variables.
The problem is that the very large arrays are exceeding the limit on stack size.
You could correct that in any of several different ways.
[LIST]
[*]Increase the stack size limit ```
$ ulimit -s 40960
```

[*]Change the locals in main to be on the heap instead of the stack.
Either declare them outside of the main function, or add a "static" classifier to their declaration.

[*]Use malloc() or new() for allocating those big arrays.

[*]Make them not quite so big.
[/LIST]

---

### Post by uffish2 on 2009-05-05
Thanks stroyan, that seems a very reasonable explanation to the behavior I'm seeing. I'm now travelling, I'll check if it solves the problem when I get back home in a week or so.
 
BTW, why didn't I get a "stack overflow error"? Do I have to enable something to get this error message?
 
Best,

---

### Post by stroyan on 2009-05-05
I don't expect linux to report 'stack overflow' as different from other segmentation violations.  Perhaps you are accustomed to that from experience with some other OS.

---

### Post by uffish2 on 2009-05-06
I converted the program to allocate memory with malloc, and now it works! Thanks everybody.
 
(man, I'm rusty, it took me 4 attempts to remember how to cast into array pointers...)

---

