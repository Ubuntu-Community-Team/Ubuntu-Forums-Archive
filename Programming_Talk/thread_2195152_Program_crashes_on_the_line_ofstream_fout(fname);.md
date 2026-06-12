---
title: "Program crashes on the line: ofstream fout(fname);"
date: 2013-12-22
forum: Programming Talk
---

### Post by EricDallal on 2013-12-22
This is just about the most inexplicable bug I have seen in over 10 years of programming. My program crashes on the line:
```
ofstream fout(fname);
```
with a segfault. I did include fstream. Note that I am compiling the program with -std=c++11. I'm not sure if that changes anything. Here is my makefile:

CFLAGS=-std=c++11 -c -Wall -Wextra -g

SimpCont.o : SimpCont.cpp Traffic.h
	g++ $(CFLAGS) SimpCont.cpp

Traffic.o : Traffic.cpp Traffic.h
	g++ $(CFLAGS) Traffic.cpp

traffic : Traffic.o SimpCont.o
	g++ Traffic.o SimpCont.o -o traffic

clean :
	rm -rf *o traffic

I have properly wrapped the Traffic.h file in

#ifndef TRAFFIC_H_
#define TRAFFIC_H_
...
#endif

Here is the output from gdb:

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff72848aa in ?? () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) bt
#0  0x00007ffff72848aa in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff7286f95 in malloc () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007ffff7b3536d in operator new(unsigned long) ()
   from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#3  0x00007ffff7b35469 in operator new[](unsigned long) ()
   from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#4  0x00007ffff7b89a4c in std::basic_filebuf<char, std::char_traits<char> >::_M_allocate_internal_buffer() () from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#5  0x00007ffff7b8a062 in std::basic_filebuf<char, std::char_traits<char> >::open(char const*, std::_Ios_Openmode) ()
   from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#6  0x00007ffff7b8b8d8 in std::basic_ofstream<char, std::char_traits<char> >::basic_ofstream(char const*, std::_Ios_Openmode) ()
   from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#7  0x00000000004052e5 in SimpCont::write (this=0x60e100, 
    fname=0x7fffffffe545 "TestOut1.txt") at SimpCont.cpp:218
#8  0x00000000004018ed in main (argc=4, argv=0x7fffffffe248) at Traffic.cpp:26

Using up a few times gives:

#7  0x00000000004052e5 in SimpCont::write (this=0x60e100, 
    fname=0x7fffffffe545 "TestOut1.txt") at SimpCont.cpp:218
218		ofstream fout(fname);

Does anyone have any ideas what could cause this?

---

### Post by spjackson on 2013-12-23
As you can see, it is crashing in malloc. This suggests that memory has been trampled before you get here. This tallies with crashing on the most innocuous looking line of code. I suggest you try valgrind to try to track it down.

If it's not that, then I guess it *could* be something to do with incompatibilities between link time and runtime libraries. However, I wouldn't consider that very likely.

---

### Post by EricDallal on 2013-12-23
> **spjackson said:**
> As you can see, it is crashing in malloc. This suggests that memory has been trampled before you get here. This tallies with crashing on the most innocuous looking line of code. I suggest you try valgrind to try to track it down.

You were right! Thank you immensely for your advice. I had been banging my head for hours trying to figure this out.

---

### Post by gaurav13 on 2014-07-28
Hi, I am facing the exact same problem. How did you go about solving it ?

---

### Post by dwhitney67 on 2014-07-30
> **gaurav13 said:**
> Hi, I am facing the exact same problem. How did you go about solving it ?

Undoubtedly the OP performed a detailed analysis of his code, trying to track down exactly where he had inadvertently added a bug to the code that was trampling over memory objects that he had allocated or had defined on the stack.

You should consider doing the same, perhaps, as suggested earlier, with the aid of valgrind.

---

