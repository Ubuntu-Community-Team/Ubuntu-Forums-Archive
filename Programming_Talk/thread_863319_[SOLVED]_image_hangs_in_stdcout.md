---
title: "[SOLVED] image hangs in std::cout"
date: 2008-07-18
forum: Programming Talk
---

### Post by glok_twen on 2008-07-18
this is deeply puzzling. i am really stuck on this one.

i have an image i run in multiple threads called from a java home-grown "grid controller". the image is written in c++ in linux. it's compiled with gcc of course, and i've done it with -O5 and also -g, getting the same erros. i've used it for years without a similar problem. after wrestling with find out where it hangs, i've seen that each copy of the image hangs, and always at a statement of the form:

```
					std::cout << "...blah..." << std::endl;
```

numerous searches have yielded only a similar case from 2002 in RH saying to make sure your dev images are patched. i am running ubuntu hardy server version.

here is the back trace common to all the images. they all get stuck in the "std::ostream::operator<<", as in frame 10 below:

```
#0  0xb7f28410 in __kernel_vsyscall ()
#1  0xb7d552f3 in write () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7cf35a4 in _IO_file_write () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7cf3255 in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0xb7cf354f in _IO_do_write () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7cf3d36 in _IO_file_sync () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7ce8860 in fflush () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7e94a10 in ?? () from /usr/lib/libstdc++.so.6
#8  0xb7e961d2 in std::ostream::flush () from /usr/lib/libstdc++.so.6
#9  0xb7e980a9 in std::endl<char, std::char_traits<char> > () from /usr/lib/libstdc++.so.6
#10 0xb7e956bf in std::ostream::operator<< () from /usr/lib/libstdc++.so.6
#11 0x0806b672 in Ctest01::Cgonow (this=0xbfa95fe8, testline=@0xbfa96400) at test01.cpp:3475
#12 0x0805583d in main (argc=543449410, argv=0xbfa97224) at bak_v06.cpp:859
```

it really looks like some sort of compiler or c++ library level problem. but no web searches have helped. 

any ideas?

---

### Post by Zugzwang on 2008-07-18
Would you mind telling what precisely you mean by "image"? I know the following definitions:
[LIST]
[*]Some kind of 1-1 copy of a data structure (like CD image)
[*]The graphical image (stored as PNG or JPG file, for example).
[/LIST]
The one you mean must be different since neither of them you can program in C++ in any reasonable way.

---

### Post by hod139 on 2008-07-18
I also don't know what you mean by image.  If you want a better backtrace you can turn off optimizations using the -O0 flag.  (Also, what's -O5?  I'm pretty sure it stops at -O3).

---

### Post by WW on 2008-07-18
It's not a term I use (and I don't recall when I last saw it), but "image" is basically the same as "binary executable"--perhaps specifically the copy in the computer memory where it was loaded to run.
 [The abstract here](http://portal.acm.org/citation.cfm?id=1017753.1017800&coll=GUIDE&dl=GUIDE) shows it used in context.

---

### Post by glok_twen on 2008-07-18
thanks for your responses and for considering this.

yes i meant the .bin file, one executing copy of the program. it is running separately in 12 different processes simultaneously. changed the posting title to make this more clear.

-O5 runs as an option, i think it gives the same level of optimization as -O3 and is left for legacy makefile support. to remove doubt, i get the same impact when i take out the -O flag completely, and replace it with -g.

can i get a better bt with -O0 even if i've used -g for the back trace above? 

in any case, i have been able to narrow it down to the exact line where it is hanging. it's hanging up in 12 sepate copies of the executable, and in each case on 1 of 2 different statements,each of the format 

std::cout << "blah" << std::endl;

and in each case in the bt it is on:

std::endl<char, std::char_traits<char> > () from /usr/lib/libstdc++.so.6

thanks for any help. really at a dead end.

---

### Post by hod139 on 2008-07-18
In my experience, having a program crash at a cout like this, usually indicates a memory error (array out of bounds access, etc).  I would suggest running the program using valgrind, and checking for illegal memory accesses.

---

### Post by |{urse on 2008-07-18
you'd really need to post your code if you want it proofed here.

---

### Post by dwhitney67 on 2008-07-18
The -O options are for optimization.  I guess one could say that the -g is the worst optimization parameter because it includes symbolic information in the linked application.  Personally, I think of the -O and -g as being similar to apples and oranges (err, oranges and grapefruit).

You stated that you are running a multi-threaded application.  Is this correct?  Are you aware that the output/input streams are not thread-safe?

---

### Post by glok_twen on 2008-07-18
i was not aware of that, no,  will check into it.

actually, i am running 12 copies of the program each in their own process space. (it's actually 12 separate java threads where each one of those java threads makes its own call to the c++ .bin file via ProcessBuilder - so the "threads" are truly separate processes with no shared memory,etc). do you know whether that set up would create risk to the input and output classes?

---

### Post by dwhitney67 on 2008-07-18
If the C++ programs are running in their own process space, which seems likely from what you have described, then no, this should not be the cause of your application's calamities.

My knowledge of Java is limited, but I would surmise that each ProcessBuilder is indeed a separate process.  But I could be wrong.  Google "reentrant code" to see if that concept applies to you.

---

### Post by glok_twen on 2008-07-19
indeed they are running in their own process space with distinct pid's.

---

### Post by Zugzwang on 2008-07-19
Ok, so when you write that you wrote your image in C++, then you can't expect that anyone will be able to guess what you mean since what you really meant is that you wrote your program using C++ and compile it to an image using GCC. :-)

Secondly, you didn't write what precisely happens when the given stack trace occurs. Does the program deadlock? Do you get a segmentation fault?

Now to the serious answer: I definitely second the tip of using valgrind. One possible cause of this problems could be a "wild pointer" which damages your "std::cout" object somehow. So keep an eye open for expressions like "&(std::void)" in your code! But this is just an example. I could also guess that you try to put a "(char)0" into the stream *in some earlier place* which might be impossible.

Since the problem occurs when flush is called, try putting "std::cout.flush()" after every writing to the stream in order the get the error as early as possible.

---

### Post by glok_twen on 2008-07-19
yes correct, i wrote the code in c++, compiled with gcc and produced an executable file (which using unclear lingo i referred to as an image while it was actually running.)

what happens when the execution freezes is, well, it just stops. at that instruction. doesn't move at all. they way i get to the backtrace was to have compiled it with -g, then wait for it to hang. then do an attach to it within gdb. then do a bt. and poof, out comes the bt i posted. in several copies of the executing c++ program, it stopped at different line numbers, even in different modules. in each case though, i attached gdb to the stopped process and sure enough it was just sitting on a line of code that looked like std::cout << "text" << std::endl;

in any case i will run with valgrind and see where that goes. thanks for the input.

other suggestions please advise.

---

### Post by dwhitney67 on 2008-07-19
If possible, I would suggest that you post your C++ code.  You probably have a simple bug, and with many more eyes (people) looking for it, it might get resolved sooner.

---

### Post by WW on 2008-07-19
You could also try replacing your C++ program with something simple (e.g. just print "Hello, world!", perhaps in a loop with some delays), and see if it exhibits the same behavior.  Or start taking code out of your C++ program, until it is so simple that it works.

And, as dwhitney76 and |{urse suggest, post your code, if you can; many eyes make light debugging.

---

### Post by glok_twen on 2008-07-20
thanks all for your help. i will admit that rather than solved i would have rather marked the post as "worked around". i changed the std::cout statements to instead write to files and simultaneously do an fprintf. for now anyhow it seems to be running ok again.

thanks again for considering it.

---

### Post by dwhitney67 on 2008-07-20
Sounds like a work-around, rather than a solution.  Also it seems your programming roots are in C, not C++, using the fprintf() function.

You should revisit your C++ code again to further analyse the issue.  I bet you still have a bug, and just because the program isn't crashing does not imply it is not there.

---

### Post by ajennings on 2008-10-21
I can recreate this with something as simple as:
```

#include <stdio.h>

int main(void) {
        unsigned long i=0;
        while (1) {
                printf("%ld\n", i);
                ++i;
        }
}
```
Everything is fine as long as the terminal window is visible, but if I cover it with another window or switch to another desktop, then it hangs.  I'd be curious to know if this happens to others.

It doesn't happen with xterm, so maybe it's just a "gnome-terminal" issue.

---

### Post by dwhitney67 on 2008-10-21
Do you really need me to test that program?  It looks fine, and if it so happens to work properly on my system, the output will probably be streaming by all day.

Can you test to see if the issue works (or fails) on your system with a smaller range of values for 'l'?

-------------------
Edited...

Actually, I recant my statement above... upon looking at the program again, it won't even iterate once through the loop.  'l' is initialized to zero, thus the while-loop conditional fails!

---

### Post by ajennings on 2008-10-22
That wasn't very smart of me to use a lowercase L as the variable name, was it?

The infinite loop is on purpose (that's a numeral "one" as the loop condition).

The point is that if gnome-terminal gets too much input, too quickly, when the window is not visible, then it hangs (on my system).  It happens within twenty seconds for me (about 80% of the time), so if doesn't happen for you within five minutes, then we can probably say it doesn't happen on your system.

Like I said, I'm pretty sure it's a gnome-terminal bug, but I'm kind of interested to see if it happens for others.

Multiple processes or threads are not required, so maybe this isn't the same thing that glok_twen was seeing.  But if I attach to the process with gdb, then I get the same stack trace:
```
#0  0xb7fc1410 in __kernel_vsyscall ()
#1  0xb7e052f3 in write () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7da35a4 in _IO_file_write () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7da3255 in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0xb7da354f in _IO_do_write () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7da3e59 in _IO_file_overflow () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7da340e in _IO_file_xsputn () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7d7c7cf in vfprintf () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7d85363 in printf () from /lib/tls/i686/cmov/libc.so.6
#9  0x0804847f in main ()

```

---

### Post by ajennings on 2008-10-22
I guess I should clarify that it doesn't hang immediately, it hangs after some random number of lines, anywhere from 50,000 to 1,000,000.

---

### Post by dwhitney67 on 2008-10-22
I ran your program, and it still seems to be working after a couple of minutes.

I am typing this response into Firefox which I am running on WinXP, which is running as a guest OS under VMware.  The short C program is running in an iconified state on my Ubuntu 8.04 system (the host OS for VMware)... let me check it again... yep, still running after more than 2 minutes.  The counter is past the 11,000,000 mark.

---

### Post by ajennings on 2008-10-22
Well, thanks for trying.

I guess I won't worry about it.

---

### Post by dribeas on 2008-10-22
So, what was the problem? (So others can see the solution if they encounter the same problem)

---

### Post by ajennings on 2008-10-22
I don't know.  It's still happening for me.

But I don't really have a desire to debug a gnome-terminal issue, especially if it's not a widespread problem.

My recommended workaround is to use xterm instead of gnome-terminal.

---

