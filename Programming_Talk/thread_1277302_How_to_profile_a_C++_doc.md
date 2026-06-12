---
title: "How to profile a C++ doc"
date: 2009-09-28
forum: Programming Talk
---

### Post by titolorient on 2009-09-28
Hi,
I have a C++ program and I want to profile it.
How to do it ?
I install gcc and g++ but I don't know how to do.
Thanks a lot for your help

---

### Post by Zugzwang on 2009-09-28
Here's some simple solution. Compile your program using the "-g" switch. If you don't know how to compile a program, look into the stickies and/or read [this post]("http://ubuntuforums.org/showthread.php?t=1258665").

Then install "valgrind" and run your program from the terminal using "valgrind --tool=callgrind ./insert_the_name_of_your_executable_here". A file with a name starting with "callgrind." will be created. Run "kcachegrind" on the file (install it beforehand) after your program has finished to see the results.

---

### Post by titolorient on 2009-09-28
Thanks,
I've tested it and that does'nt work when I've used your steps.
My prog is named 3DCHAP5.CPP and is on desktop.
So how to do to compil it and profile it.
Thanks again

---

### Post by A_Fiachra on 2009-09-28
Why is your code on the desktop???

That's sorta stupid.

Do you even know what a compiler is?

```

man gcc

```

---

### Post by dwhitney67 on 2009-09-28
> **A_Fiachra said:**
> Why is your code on the desktop???

That's sorta stupid.

Do you even know what a compiler is?

```

man gcc

```

What difference does it make where the source file is located?  Re-read your post and then ask yourself who is stupid.

---

### Post by dwhitney67 on 2009-09-28
> **titolorient said:**
> Thanks,
I've tested it and that does'nt work when I've used your steps.
My prog is named 3DCHAP5.CPP and is on desktop.
So how to do to compil it and profile it.
Thanks again

Install the development tools, if you haven't already done it:
```

sudo apt-get install build-essential

```
To build/run your application (using a terminal):
```

cd ~/Desktop
g++ -g 3DCHAP5.CPP
./a.out

```
If the compiler spews out errors during the compilation phase, then forget about running the application until you correct those errors.

---

### Post by titolorient on 2009-09-29
Thanks a lot

---

### Post by A_Fiachra on 2009-09-29
> **dwhitney67 said:**
> What difference does it make where the source file is located?  Re-read your post and then ask yourself who is stupid.


gcc -c -Wall -g -I<path-to-includes> source.cpp -o source.o
gcc -g -L<path-to-libs> source.o -o source

is going to leave a source.o file on your desktop.

That practice makes the desktop cluttered.

I believe the practice is stupid.  I never said you were stupid.

---

### Post by titolorient on 2009-09-29
Thanks a lot but what about profiling ??

---

### Post by Zugzwang on 2009-09-29
> **titolorient said:**
> Thanks a lot but what about profiling ??

I've written a way how to do it in the second post. If there's something wrong with it, feel free to post us the corresponding error messages/problem description to get to know how to solve the problem.

---

### Post by dwhitney67 on 2009-09-29
> **titolorient said:**
> Thanks a lot but what about profiling ??

[http://www.cs.utah.edu/dept/old/texinfo/as/gprof.html](http://www.cs.utah.edu/dept/old/texinfo/as/gprof.html)

Happy reading.  :-)

---

### Post by titolorient on 2009-09-30
Bonjour,
I've tried, it seems to be ok.
How to find the PID in kcachegrind callgrind.pit.[PID]
How to find it which command to use.
[FONT=monospace]There is what I have after using valgrind --tool=callgrind  ./3DCHAP5modifie.CPP

==5776== Callgrind, a call-graph generating cache profiler.
==5776== Copyright (C) 2002-2008, and GNU GPL'd, by Josef Weidendorfer et al.
==5776== Using LibVEX rev 1884, a library for dynamic binary translation.
==5776== Copyright (C) 2004-2008, and GNU GPL'd, by OpenWorks LLP.
==5776== Using valgrind-3.4.1-Debian, a dynamic binary instrumentation framework.
==5776== Copyright (C) 2000-2008, and GNU GPL'd, by Julian Seward et al.
==5776== For more details, rerun with: -v
==5776== 
==5776== For interactive control, run 'callgrind_control -h'.
: not founddifie.CPP: 1: //////////////////////////////////////////////////////////////////////////
==5777== 
==5777== Events    : Ir
==5777== Collected : 262282
==5777== 
==5777== I   refs:      262,282
./3DCHAP5modifie.CPP: 2: //: Permission denied
==5778== 
==5778== Events    : Ir
==5778== Collected : 275635
==5778== 
==5778== I   refs:      275,635
./3DCHAP5modifie.CPP: 3: //: Permission denied
==5779== 
==5779== Events    : Ir
==5779== Collected : 283303
==5779== 
==5779== I   refs:      283,303
./3DCHAP5modifie.CPP: 4: //: Permission denied
==5780== 
==5780== Events    : Ir
==5780== Collected : 292169
==5780== 
==5780== I   refs:      292,169
./3DCHAP5modifie.CPP: 5: //: Permission denied
==5781== 
==5781== Events    : Ir
==5781== Collected : 303965
==5781== 
==5781== I   refs:      303,965
./3DCHAP5modifie.CPP: 6: //: Permission denied
==5782== 
==5782== Events    : Ir
==5782== Collected : 315341
==5782== 
==5782== I   refs:      315,341
: not founddifie.CPP: 7: //////////////////////////////////////////////////////////////////////////
==5783== 
==5783== Events    : Ir
==5783== Collected : 319998
==5783== 
==5783== I   refs:      319,998
: not founddifie.CPP: 8: 
./3DCHAP5modifie.CPP: 9: //: Permission denied
==5784== 
==5784== Events    : Ir
==5784== Collected : 342120
==5784== 
==5784== I   refs:      342,120
: not founddifie.CPP: 10: 
./3DCHAP5modifie.CPP: 11: //: Permission denied
==5785== 
==5785== Events    : Ir
==5785== Collected : 355983
==5785== 
==5785== I   refs:      355,983
./3DCHAP5modifie.CPP: 14: cannot open ncurses.h: No such file
./3DCHAP5modifie.CPP: 15: //: Permission denied
==5786== 
==5786== Events    : Ir
==5786== Collected : 373993
==5786== 
==5786== I   refs:      373,993
: not founddifie.CPP: 19: 
./3DCHAP5modifie.CPP: 20: //: Permission denied
==5787== 
./3DCHAP5modifie.CPP: 20: MACROS: not found
: not founddifie.CPP: 21: 
: not founddifie.CPP: 32: 
==5787== Events    : Ir
==5787== Collected : 396224
==5787== 
==5787== I   refs:      396,224
./3DCHAP5modifie.CPP: 33: //: Permission denied
==5788== 
==5788== Events    : Ir
==5788== Collected : 455908
==5788== 
==5788== I   refs:      455,908
: not founddifie.CPP: 34: 
./3DCHAP5modifie.CPP: 35: //structurte: not found
==5789== 
==5789== Events    : Ir
==5789== Collected : 469795
==5789== 
==5789== I   refs:      469,795
./3DCHAP5modifie.CPP: 37: typedef: not found
: not founddifie.CPP: 54: 
./3DCHAP5modifie.CPP: 54: unsigned: not found
: not founddifie.CPP: 54: 
./3DCHAP5modifie.CPP: 54: }_palette: not found
: not founddifie.CPP: 54: 
: not founddifie.CPP: 54: 
: not founddifie.CPP: 54: 
./3DCHAP5modifie.CPP: 54: //: Permission denied
==5790== 
==5790== Events    : Ir
==5790== Collected : 593013
==5790== 
==5790== I   refs:      593,013
./3DCHAP5modifie.CPP: 54: typedef: not found
: not founddifie.CPP: 54: 
: not founddifie.CPP: 54: 
./3DCHAP5modifie.CPP: 54: //: Permission denied
==5791== 
==5791== Events    : Ir
==5791== Collected : 658981
==5791== 
==5791== I   refs:      658,981
./3DCHAP5modifie.CPP: 54: typedef: not found
: not founddifie.CPP: 54: {
./3DCHAP5modifie.CPP: 54: int: not found
: not founddifie.CPP: 54: 
./3DCHAP5modifie.CPP: 54: unsigned: not found
: not founddifie.CPP: 54: 
: not founddifie.CPP: 54: 
: not founddifie.CPP: 55: 
./3DCHAP5modifie.CPP: 56: //: Permission denied
==5792== 
==5792== Events    : Ir
==5792== Collected : 751024
==5792== 
==5792== I   refs:      751,024
./3DCHAP5modifie.CPP: 57: typedef: not found
: not founddifie.CPP: 58: {
./3DCHAP5modifie.CPP: 59: float: not found
: not founddifie.CPP: 59: 
./3DCHAP5modifie.CPP: 60: Syntax error: "}" unexpected
==5776== 
==5776== Events    : Ir
==5776== Collected : 794269
==5776== 
==5776== I   refs:      794,269


Thanks
[/FONT]

---

### Post by Zugzwang on 2009-09-30
> **titolorient said:**
> There is what I have after using valgrind --tool=callgrind  ./3DCHAP5modifie.CPP


Sorry, but you are not applying "valgrind" on your compiled program but you rather try to apply it to your sourcecode.

First of all, rename your source code to have a lower-case file extension:
```

mv 3DCHAP5modifie.CPP 3DCHAP5modifie.cpp

```

Then compile it
```

g++ -g 3DCHAP5modifie.cpp -o 3dchaps

```

and then apply valgrind on the compiled program:
```

valgrind --tool=callgrind  ./3dchaps

```

---

### Post by titolorient on 2009-09-30
Thanks a lot [COLOR=Black][Zugzwang]("http://ubuntuforums.org/member.php?u=403348")
Is it possible to know how exactely use as command to obtain the same result with gprof or/ and gconv.
Thanks
[/COLOR]

---

### Post by Zugzwang on 2009-09-30
> **titolorient said:**
> Thanks a lot [COLOR=Black][Zugzwang]("http://ubuntuforums.org/member.php?u=403348")
Is it possible to know how exactely use as command to obtain the same result with gprof or/ and gconv.
Thanks
[/COLOR]

Please rephrase your question. It is hard to understand. Are you asking for a way to make valgrind producing precisely the same output as gprof? It is unlikely that such a feature exists, as it is unncessary. 

If you want to know how to use gprof for profiling, then have a look at the page that dwhitney67 referred to. If you have problems understanding it, come back with precise questions.

---

### Post by titolorient on 2009-10-01
Hi
This is the steps done in the terminal and the messages obtained.
gcc -Wall -c -pg 3DCHAP5modifie1.cpp
3DCHAP5modifie1.cpp:54: warning: ‘typedef’ was ignored in this declaration
3DCHAP5modifie1.cpp:60: warning: ‘typedef’ was ignored in this declaration
3DCHAP5modifie1.cpp:69: warning: ‘typedef’ was ignored in this declaration
3DCHAP5modifie1.cpp:78: warning: ‘typedef’ was ignored in this declaration
3DCHAP5modifie1.cpp:86: warning: ‘typedef’ was ignored in this declaration
3DCHAP5modifie1.cpp:92: warning: ‘typedef’ was ignored in this declaration
3DCHAP5modifie1.cpp: In function ‘int main()’:
3DCHAP5modifie1.cpp:672: warning: deprecated conversion from string constant to ‘char*’
3DCHAP5modifie1.cpp:650: warning: unused variable ‘choix’
tarek@tarek-laptop:~/Bureau$ gcc -Wall -pg 3DCHAP5modifie1.o
3DCHAP5modifie1.o: In function `normalise(_3D*)':
3DCHAP5modifie1.cpp:(.text+0x165d): undefined reference to `sqrt'
3DCHAP5modifie1.o: In function `precalc()':
3DCHAP5modifie1.cpp:(.text+0x1b53): undefined reference to `sin'
3DCHAP5modifie1.cpp:(.text+0x1b7e): undefined reference to `cos'
3DCHAP5modifie1.o: In function `main':
3DCHAP5modifie1.cpp:(.text+0x1ce6): undefined reference to `operator delete[](void*)'
3DCHAP5modifie1.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
Now I don't know how to have a table who give me the results of profiling.
Thanks a lot.

---

### Post by MadCow108 on 2009-10-01
you're missing a few objects or libraries to link against.
here are a few tips how to solve compiling problems.
[http://ubuntuforums.org/showthread.php?t=691451](http://ubuntuforums.org/showthread.php?t=691451)

but why do you want to profile a program which you can't even compile yourself?
the information will probably be pretty useless for you

---

### Post by Zugzwang on 2009-10-01
> **titolorient said:**
> Hi
This is the steps done in the terminal and the messages obtained.
gcc -Wall -c -pg 3DCHAP5modifie1.cpp


titolorient, please use the command for compiling&linking (plus adding "-pg" for gprof-profiling) that I've provided in post #13. You have to use "g++" instead of "gcc" for C++-programs as "gcc" does not link against the standard C++ libraries.

---

### Post by jespdj on 2009-10-01
> **A_Fiachra said:**
> gcc -c -Wall -g -I<path-to-includes> source.cpp -o source.o
gcc -g -L<path-to-libs> source.o -o source

is going to leave a source.o file on your desktop.
To compile C++ programs, you must use g++, not gcc, otherwise you'll get lots of error messages. So try this instead:
```
g++ -c -Wall -g source.cpp -o source.o
g++ -g source.o -o source
```

---

### Post by titolorient on 2009-10-02
Thanks a lot.
Just a small problem.
How to go after this prob on my program
warning: ‘typedef’ was ignored in this declaration
Thanks

---

### Post by MadCow108 on 2009-10-02
its just a warning so it does not have to be a problem.
just check the code and see whats the reason for the warning and fix it (or not)

but I ask again: why do you want to profile something what you seemingly don't really understand?

---

