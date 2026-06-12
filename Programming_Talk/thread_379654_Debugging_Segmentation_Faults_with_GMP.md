---
title: "Debugging Segmentation Faults with GMP"
date: 2007-03-08
forum: Programming Talk
---

### Post by prodonjs on 2007-03-08
A partner and I are spending this semester working on a development project to implement a faster algorithm for calculating the greatest common divisor of two arbitrary precision integers. We have spent many many hours thus far trying to get to the bottom of things and thus far, it appears like we have a correctly working version, that is until we try to add in one particular optimization.

Without going into too much detail, I tested the algorithm pretty thoroughly and it works correctly whenever I don't enable this optimization. In order to debug cleanly, I defined the following macro.

/* Used to enable or disable debugging lines of output */
#define JP_DEBUG 0

Then whenever I am going to use gmp_printf() statements to show me the status of variables, I put them within #ifdef statements as shown:

#if JP_DEBUG			
gmp_printf("U -> after n1V - d1U = %Nd\tusize = %zd\n", up, usize, usize);
gmp_printf("V -> after n2V - d2U = %Nd\tvsize = %zd\n", vp, vsize, vsize);
gmp_printf("---------- Finished with (kAry) loop iteration----------\n\n");
#endif

Therefore, whenever I want to debug I define JP_DEBUG as 1 and I get all my lines printed. Of course, this is really really time consuming whenever I'm running a test on 100,000 4096 bit integers to ensure the algorithm is correct so I usually have it turned off to make smaller files for 'diff' to compare.

Anyways, I turn this optimization on, and the thing immediately seg faults...but only when the macro is set to 0. As soon as I assert the macro, the program will run successfully (usually only up to a certain size), but still it runs where the deasserted version would crash. I checked into what the printf statements were doing and there is no way they could modify any of my data and there are no other statements inside the #ifdef blocks that could modify anything without my knowledge.

This is a very complex low-level C file, and it's extremely hard to pinpoint just one mistake that is causing this. Because the goal here is maximum calculation performance, I was declaring most of my functions as static and as inline, but I found that when I removed those two modifiers the segmentation faults were no longer apparent. The results are sometimes incorrect, but that is a problem due to improper mathematics rather than a program memory error.

I was just wondering if anyone here had ever encountered a situation where printf()'s were changing the outcome of their program, and whether or not it seg faulted. It seems to me like a simple debugging line should have absolutely no side effect on my program. If it crashes without printing those lines, there is no reason it shouldn't crash when it is printing them. But perhaps there is an issue of allocation whenever the compiler is providing space for the string constants that are defined in the gmp_printf() statements. That is my only theory.

Thanks for any help you guys can provide and if anyone is more interested and wants to see my code, let me know.

---

### Post by Mr. C. on 2007-03-08
While not terribly common (fortunately!), this problem does occur occasionally.  I've experienced this numerous times; most of them have been careless OBO errors, or pushing too large a structure into too small a space. 

You likely have a stack or overrun somwhere, where the insertion of diagnostic or instrumentation code may happen to shift the stack, string table, or other object data.  Sometimes, even a single addition/deletion of a local variable will mask the problem.  And using a debugger to step through the code (not likely in your situation) can also lead to such magically vanishing bugs.  Your printf's may themselves not be modifying anything, but they do affect the placement of other code, and they do affect speed of execution (which can hide signal or timing bugs).

Knowing what you are experiencing, you probably can imagine how difficult such a thing is to find when working on the kernel with asynchronous faults, interrupt handlers, and page table changes!

Not knowing how you allocate your memory, it is difficult to give aid.  I can suggest that if you are using malloc or friends, using instead a special, instrumented version that helps to catch such problems.  If you get lucky, runtime instrumentation might not mask the problem, but provide some insight.

I'm not sure this is much help to you; I hope you're able to find it!
MrC

---

### Post by prodonjs on 2007-03-08
Yeah I can only imagine the difficulty that comes with kernel development. In my operating systems class, we had to do a few prototype models (in Java) that simulated OS tasks like page faults, swapping, virtual memory, process scheduling, and synchronization. Even those high-level simulations provided some challenges and that was in a nice, Java environment where it is typically much easier to diagnose exactly what is going on since the Java console tends to be very useful in backtracing your program and its data.

As I said, I spent some more time on this and I found that making three of the functions I had in question not inlined helped with some of the issues, but not all of them. I'm still getting segmentation faults and I am not very familar with using gdb, but when I have used it I have gotten the faults at various different locations. That's what is making things even more difficult, much like it would be with kernel programming, many of the faults seem to be asynchronous (which should not be the case in a static type program like this) which is essentially just an extended function built to work fast for any size number. My professor and advisor wrote the original code, but we're on spring break this week so rather than enjoy myself I've spent time debugging (although I suppose programming is still pretty enjoyable).

I'm hopeful that he can spot something I'm missing, but again if anyone is up to the challenge of seeing the code, let me know.

---

### Post by Wybiral on 2007-03-08
If you're trusting enough to PM the code to me I *may* be able to help. I'm even willing to sign a confidentiality agreement if need-be. I love low-level stuff and am only interested in helping solve the problem (most of my programming is graphics related and would not benefit much from your algorithm, and if it does, as I mentioned, I will sign an agreement to not use it... Ever. I just enjoy helping.)

---

### Post by Mr. C. on 2007-03-08
It sure sounds like a tough one.

Be sure those inlined functions are not being so overly aggressive, that pipelined operations are out of step.  I recall one case where I found an optimizer bug, that was just a cycle out of step.  Who knows - maybe you've found one too!

There's a contributer here who would probably love to spins some cycles looking through your assembler!  I'll drop him a PM - perhaps he's interested.

[ EDIT: I see he's already responded! ]

MrC

---

### Post by Mr. C. on 2007-03-08
prodonjs,

I just assumed that you had allowed your program to core dump, and then run gdb against it ?

Would I be correct in that assumption?

MrC

---

### Post by prodonjs on 2007-03-08
Yeah, I had a feeling that inlining a few those functions could result in some problems. In fact, in the existing code there was already a macro saying to specifically not inline a particular function on the x86 architecture (which is naturally what I am using to build).

I guess another big thing for me is that C is not my most comfortable language either. I learned programming in the O-O style of Java and I guess I grew accustomed to it (for better or worse). I don't know if it is the security I feel in Java and VB that makes me like them so much, but I know that is part of the reason. I guess coming from Java where you need to be explicit about everything that you are doing to please the compiler, and moving to C where you can do crazy things (in my mind) like accidentally assigning instead of comparing two variables inside an if clause, or using pointer arithmetic to treat essentially any memory location as a particular type with no real boundaries, it just gets scary and a segmentation fault can mean virtually anything when it appears. Oh well I'll keep plodding away on it.

---

### Post by Mr. C. on 2007-03-09
Make sense.  C gives one a lot of power and control.

Sorry, I'm still not sure if my question was answered.  Have you let your program core dump and then debug the core with :

   gdb myprog code

In addition, has this been done with symbols compiled into your code (cc -g and ld -g) ?

You can see exactly where it faulted, stack trace, etc.  If you've done this, sorry to be so presumptuous.

MrC

---

### Post by hod139 on 2007-03-09
In addition to debugging with gdb, you can try the tool valgrind which is made to find memory issues.

---

### Post by prodonjs on 2007-03-09
Mr. C,

I'm not really familiar with gdb so you're going to have to elaborate a little more on what a core dump is. Basically, all I have done with gdb so far is execute the program, which then segfaults and then I do a backtrace to see what function I am in and since all of the methods are static, the space allocated to them should all be done prior to run-time. In all of the methods, I'm only accessing data via pointers to the heap, so on the stack itself there shouldn't be any data overflow, the pointers and simple long integer types cannot grow in size at all.

The other complication that makes gdb a little more confusing is that, because I'm testing out the functionality of a library file and I am making numerous changes, I don't do a make install after each update of the library. I simply do a make and then I use libtool to link the library to my testing program as such.

./libtool --mode=link gcc -o testGCD testGCD.c libgmp.la

And then when I do that, the libtool actually makes a wrapper script around the actual testGCD program that gets things initialized before running. That could potentially be a problem, but as I said, when I use the original gcd.c file that is unchanged, there are no problems.

So when I use gdb, I need to say something like this... ./libtool --mode=execute gdb testGCD

I'm not sure how that is going to affect doing a core dump, but it definitely sounds like that would help me out. I would appreciate hearing some more information back from you.

---

### Post by Mr. C. on 2007-03-09
Ah, good; since a very important tool lays at your disposal, there might be a quick find after all.

Libtool is simply helping build the executable (this tool was developed to create a cross-platform solution to the numerous variants of shared-library creation).  Once your executable has been re-linked, it's just an executable.

Run your program as you desire, without GDB, and use whatever wrapper script you need.

When it seg faults, the OS will want to dump a core file.  You run:

    gdb myprog core

and then start examining the stack, data, etc.  Then it is just a matter of tracing backwards in the data and time to see what happened.

If you have not noticed any core files, then your system / environment has been configured to not dump them.  You simply need to configure it to allow them to be dumped.

man core

and here's a thread where another user asked about why his system wasn't producing core files.

[http://www.ubuntuforums.org/showthread.php?t=379168&highlight=core+file](http://www.ubuntuforums.org/showthread.php?t=379168&highlight=core+file)

MrC

---

### Post by prodonjs on 2007-03-09
Ok, I was curious to see what using the core dump would do for me and I am not surprised to be having complications. My system doesn't have a man page entry for core or for valgrind actually and when I read that thread about someone's machine not generating core files, mine doesn't even say core dumped after it seg faults. It just seg faults and that is that.

Any ideas of why I don't have this? By the way I'm using Kubuntu if that matters any.

---

### Post by prodonjs on 2007-03-09
When I use gdb and do a backtrace, this is what I get. 

Program received signal SIGSEGV, Segmentation fault.
0xb7f94d7c in __gmpn_addmul_1 () from /home/jason/gmp-4.2.1/.libs/libgmp.so.3
(gdb) bt
#0  0xb7f94d7c in __gmpn_addmul_1 () from /home/jason/gmp-4.2.1/.libs/libgmp.so.3
#1  0x258392f5 in ?? ()
#2  0xbf8bf850 in ?? ()
#3  0xb7faa2e0 in ?? () from /home/jason/gmp-4.2.1/.libs/libgmp.so.3
#4  0xb7fa0943 in __gmpn_gcd () from /home/jason/gmp-4.2.1/.libs/libgmp.so.3
Previous frame inner to this frame (corrupt stack?)

I'm not sure what the problem is below the top level of the stack. the addmul_1 function should be called within a function called kAryReduce and that should be called within the mpn_gcd function. Somewhere along the line there is some extra stuff getting onto the stack. I'm not sure where to go from here. I supose I should do some more reading about how to use gdb. I'm befuddled though as to why I don't have the capability to do core dumps.

---

### Post by Mr. C. on 2007-03-10
Core dumps have become consider more nuisance than aid, so many systems default to configure user's accounts to not produce core files.

There are several methods:

1) ulimit
2) a 0 byte core file, that is read-only
3) directory read-only permissions
4) kernel configuration

Stack backtracing, especially with inlined functions can be a challenge.  You will have to examine the instructions at those locations to determine their validity.  Since you experienced abberant behavior with your program, it is not-uncommon to see stack corruption, or broken return frames.

This is where you need to get your hands dirty, and start walking through the code.

What is around memory location: 0x258392f5?  Look at a hex dump of the stack all around the stack backtrace.  Verify that the frame pointers in both directions.  Sometimes clues are left.

MrC

---

