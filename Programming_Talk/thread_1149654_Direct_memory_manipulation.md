---
title: "Direct memory manipulation"
date: 2009-05-05
forum: Programming Talk
---

### Post by CatsRninja on 2009-05-05
Hi there.

I am just wondering if direct memory manipulation its possible.
For example if i have a c program like in this pseudo code(somesort of pseudo:)) :
```

Start
Pause and wait for somesort of input
when input found:
print "STRING";
END

```

what i am wondering is if its possible to start the execution of the program,
Using a debugger sort like gdb know what is the memory adress of that string.
Alter it by accessing directly the memory.

what are your thoughts about this?is it possible?

btw, I read in someplace that you can overflow the memory instructions.
For example in c:
(might not be correct code, its just for example)
> 
#<string.h>

main( char *str[])  //accepts imput type char
{

char buffer[2]; //buffer can hold only 2 bytes
strcpy(buffer,str[1]); //copy the first argument to buffer
}

Ok this basicly does nothing usefull,the point is, if you input something more than 2chars (1byte each) it will leak to the next memory adresses.right?you can see it using gdb.

So i was thinking, this happens in c, python and java, doesnt have the the problem of expecifiing the string size.
> 
//python:
buffer="lalalalalskdjhdh" //no size input
//java:
String a= new String("çlkajdgjhadgkjaekbakdjhb") //i think this one is correct(not sure), so size input


So i was wondering, this type of error just heppens in compiled languages?(my bet is yes)

Thank you for your time.

---

### Post by CptPicard on 2009-05-05
> **CatsRninja said:**
> 
what i am wondering is if its possible to start the execution of the program,
Using a debugger sort like gdb know what is the memory adress of that string.
Alter it by accessing directly the memory.


Read about pointers.

Your string is nothing but an array of characters (bytes), and arrays are nothing but a pointer to the first item. The pointer itself is the memory address, and you can freely write to it (or the subsequent addresses in the array).

---

### Post by DoktorSeven on 2009-05-05
> **CatsRninja said:**
> 
So i was wondering, this type of error just heppens in compiled languages?(my bet is yes)


Well, it happens in C because C requires memory to be allocated for everything.  In languages such as Java (and it's not just non-compiled languages, some compiled languages have string handlers that will do that for you).  

You are simply not able to take over non-allocated memory in C without having issues.  You just aren't meant to change memory not given to you by the program since buffer overflow problems can happen and affect who knows what.  GNU/Linux will try to keep you from that by segfaulting misbehaving programs, but it won't catch everything.  This causes a lot of security problems in programs that accidentally overflow an allocated area since specifically formatted inputs in such programs can be used to do very bad things.

To give yourself more space, **malloc** enough space for you to use at the beginning, or at the very least use **realloc** to add more.  *Never* go outside the allocated memory space.

---

### Post by CatsRninja on 2009-05-05
mmm so i can write to any memory location in my system directly?
Thats my main doubt, say, 0x99999999 mem.
i want to put there the 01001001.I can do it without the OS complayning?
(off course i understand that in dooing that i can cause instability because that adreess might have something important).


> **DoktorSeven said:**
> 
You are simply not able to take over non-allocated memory in C without having issues.  You just aren't meant to change memory not given to you by the program since buffer overflow problems can happen and affect who knows what.  GNU/Linux will try to keep you from that by segfaulting misbehaving programs, but it won't catch everything.  This causes a lot of security problems in programs that accidentally overflow an allocated area since specifically formatted inputs in such programs can be used to do very bad things.


Ok, but if i want to cause that, just for experimenting.
Say i have a program( in a compiled language) and i execute it. Im not sure, but I believe that the OS will reserve memory to run it.Can i override the OS decision and put it in a place that i know that Xmemories above and bellow got nothing of interest and so i can tamper with it at my will.

how do i tamper with it?

I know i might be missing some core computer consepts, any mistakes i make please do correct, and if you know someplace where i can get good free indeapth info about it would be nice.
I know how to program well in python and java and i manage just fine in the workings and core concepts, but this lacking of "how does it realy works" info is a bit frustrating.

---

### Post by lloyd_b on 2009-05-05
Quick answer - you *don't* tamper with it.  Any attempt by a program to access memory that was not allocated by that program will result in the program being terminated with segfault (segmentation fault).

Because of the way memory is handled in Linux, the kernel, and only the kernel, has the ability to access all memory locations.  There is the special case of debuggers (like gdb) which can access the memory space of a program that they start, but other than that what you're trying to do is only possible by hacking the kernel itself.

Lloyd B.

---

### Post by CatsRninja on 2009-05-05
> **lloyd_b said:**
> 
Because of the way memory is handled in Linux, the kernel, and only the kernel, has the ability to access all memory locations.  There is the special case of debuggers (like gdb) which can access the memory space of a program that they start, but other than that what you're trying to do is only possible by hacking the kernel itself.
Lloyd B.

Well i guess thats more secure.
I thought that like debuggers could access the adress and see what was there, there was some way to access and write in it.
But i guess the Kernell is in charge of the addresses, you would have to bypass it to get somewhere(doable, but i guess not bye me then:)).

Just out of curiosity:
What about assembly?
I know its low level and all, and you program it with direct memory reference.
Althou i got a doubt here, i never worked with assembly so i dont know how you run it in a computer, for example, if you run it in your OS enviroment, it surely will work with it and so, the OS kernel has the control.......

mmm...just wondering.

---

### Post by soltanis on 2009-05-05
Just to give you the short answer on all your questions,

1) When you do an operation such as assigning a string buffer with code such as

```

fgets(str, BUFSIZE, stdin);

```

You are indeed directly modifying the memory starting where str points to, and continuing until the end of input, or until BUFSIZE characters (which in C correspond, usually, to one octet, 8 bits) have been read.

2) The second argument of fgets in this example, and similar parameters for the functions snprintf or strncpy, which specify the size of the buffer in memory, are intended to guard against buffer overflows, which you describe, which is when more data is written into a buffer than was originally allocated to that buffer.

Depending on the arrangement of memory and how the program is written, overflowing a buffer may do nothing, may trigger a memory access violation, may corrupt other parts of your program, or modify other variables that you have. For this reason you should never attempt to write to arbitrary memory without it having been allocated first.

The exploitation of programs that do not check how much data are being written into fixed-sized buffers is called a buffer overflow attack and is relatively common.

3) The operation of the Linux kernel operates on what is called a paged memory model; it is essentially where each program gets its own little address space to play around in. Instructions to write to a pointer at say 0xffffffff, first of all, even if they did succeed, would not actually be written to that location in memory (the address would actually be translated by the kernel while the program is executing to another address), and second of all, would probably go outside the programs address space and trigger a segmentation violation.

It is up to the kernel to enforce memory segmentation in circumstances such as these. There are some hobby-type microkernels not used on production systems which use a flat memory model (there is no "paging" of memory) or which enforce no such memory separation schemes at all, which would allow you to perform the operation you described. Needless to say, these systems have no security whatsoever, and hence, this model is not widely used.

Memory paging and address translation is often implemented at the hardware level, especially on Intel-based computers.

---

### Post by lloyd_b on 2009-05-06
> **CatsRninja said:**
> Well i guess thats more secure.
I thought that like debuggers could access the adress and see what was there, there was some way to access and write in it.
But i guess the Kernell is in charge of the addresses, you would have to bypass it to get somewhere(doable, but i guess not bye me then:)).

Just out of curiosity:
What about assembly?
I know its low level and all, and you program it with direct memory reference.
Althou i got a doubt here, i never worked with assembly so i dont know how you run it in a computer, for example, if you run it in your OS enviroment, it surely will work with it and so, the OS kernel has the control.......

mmm...just wondering.

C or C++ code can do pretty much anything that assembly can do.  Dropping to a lower-level language does *not* give you any greater control over the system (it just makes you do a lot more typing to accomplish things :)).

Regardless of if a program is written in C, Fortran, Assembly, or any other language, it can NOT access any memory except what the kernel has allocated to it.  Period.  

In Linux, when a program accesses an address (say 0x000000ff), it is NOT accessing that part of the physical memory.  It is accessing that address *within its allocated address space*.  Where that address space exists in physical RAM (or even *if* it exists in physical RAM at the moment) is strictly controlled by the kernel.

A program can easily mess up it's own address space - it happens regularly with buggy programs.  But it can't touch another program's address space.

In the case of gdb or other debuggers, the program being debugged is running inside of the debugger's address space, which is why the debugger can access that program's memory.

Lloyd B.

---

### Post by CatsRninja on 2009-05-06
Nooooo!!!Freadom is dead!!;)

I realy need to learn more.


Im am now clarrified.
Thanks for the repplies.

---

### Post by samjh on 2009-05-07
> **lloyd_b said:**
> C or C++ code can do pretty much anything that assembly can do.  Dropping to a lower-level language does *not* give you any greater control over the system (it just makes you do a lot more typing to accomplish things :)).

I'll point out that is not strictly true.  If assembly didn't give any greater control over the system, then operating systems could be written with no assembly code. ;)  However, all operating systems require some assembly, with the exception of those written for specialised processors with built-in compiler or interpreter.

However, for the purposes of application programming, you are right.  The days of writing applications with assembly have long passed. :)

---

### Post by Calmatory on 2009-05-07
> **samjh said:**
> The days of writing applications with assembly have long passed. :)


...which is a shame. Software gets slower faster than hardware gets faster. Especially during the times like we have now.

So there is no possibility to read from or write to certain process memory addresses? As in, no equivalents for ReadProcessMemory and WriteProcessMemory which are found in Win32?

---

### Post by Jiraiya_sama on 2009-05-07
> **Calmatory said:**
> ...which is a shame. Software gets slower faster than hardware gets faster. Especially during the times like we have now.


From what I've heard, GCC is better at generating optimized binaries than many assembly programmers.

---

### Post by lloyd_b on 2009-05-07
> **Calmatory said:**
> ...which is a shame. Software gets slower faster than hardware gets faster. Especially during the times like we have now.

So there is no possibility to read from or write to certain process memory addresses? As in, no equivalents for ReadProcessMemory and WriteProcessMemory which are found in Win32?

AFAIK, there're no system calls equivalent to those Win32 functions.  I suspect someone who knows what s/he's doing could write a kernel module to create this functionality, but I doubt such a module would ever make into the mainline kernel, since the only use for it would be to compromise the inherent stability that comes from having each process secure in its own memory space.

As for software getting slower - well, maybe, but consider the other side of the equation.  It takes a lot of time/effort to accomplish anything using assembly code.  Using more assembly *might* get you more efficient code, but the price would be that it would take longer to get it.  So which would you prefer - a much smaller amount of super efficient code, or a large ecosystem of somewhat less efficient code?

Lloyd B.

---

### Post by doas777 on 2009-05-07
> **samjh said:**
> I'll point out that is not strictly true.  If assembly didn't give any greater control over the system, then operating systems could be written with no assembly code. ;)  However, all operating systems require some assembly, with the exception of those written for specialised processors with built-in compiler or interpreter.

However, for the purposes of application programming, you are right.  The days of writing applications with assembly have long passed. :)

Interesting. i have always focused on abstraction (of hardware, kernel, and middleware) as the key reason assembly is avoided in middle and upper-layer code. the less assembler, the less you have to alter to port it to another hardware platform. all you need to write is the bottom of the kernel, and the C compiler to be machine specific. everything else just compiles up (in theory at least).

---

### Post by samjh on 2009-05-07
> **doas777 said:**
> Interesting. i have always focused on abstraction (of hardware, kernel, and middleware) as the key reason assembly is avoided in middle and upper-layer code. the less assembler, the less you have to alter to port it to another hardware platform. all you need to write is the bottom of the kernel, and the C compiler to be machine specific. everything else just compiles up (in theory at least).

The assembly code on most modern, mainstream operating systems is reduced pretty much down to basic I/O.  And if there is no C (or other, eg. Ada, Forth, Pascal) compiler for the processor architecture, then the compiler.

You're right in saying abstraction is why assembly is avoided in anywhere but the deepest foundations of kernels.  However, if the performance benefit of using assembly exceeds the disadvantages of lack of portability and maintainability, then assembly will be used at developers' discretion.  Pertinent examples include graphics drivers.  Performance is still a big factor in OS design, especially in embedded and real-time systems.  And if the system is a one-off for a specific architecture, who cares about portability?

---

### Post by CatsRninja on 2009-05-07
> **samjh said:**
> The assembly code on most modern, mainstream operating systems is reduced pretty much down to basic I/O.  And if there is no C (or other, eg. Ada, Forth, Pascal) compiler for the processor architecture, then the compiler.

You're right in saying abstraction is why assembly is avoided in anywhere but the deepest foundations of kernels.  However, if the performance benefit of using assembly exceeds the disadvantages of lack of portability and maintainability, then assembly will be used at developers' discretion.  Pertinent examples include graphics drivers.  Performance is still a big factor in OS design, especially in embedded and real-time systems.  And if the system is a one-off for a specific architecture, who cares about portability?

I guess writing in assembly is conterproductive if you got something to deliver in a short time, even if it was a long time, it might take longer that that.Assembly is quind of cryptic(in my view) and one function call in anylanguage witch you just write once, could lead to an enourmous amont in assembly.

But isnt assembly the machine?
In terms of total control isnt assembly the major?
I mean, as pointed out, you still need a compiler and some kernell is written in assembly.

---

### Post by doas777 on 2009-05-07
> **CatsRninja said:**
> I guess writing in assembly is conterproductive if you got something to deliver in a short time, even if it was a long time, it might take longer that that.Assembly is quind of cryptic(in my view) and one function call in anylanguage witch you just write once, could lead to an enourmous amont in assembly.

But isnt assembly the machine?
In terms of total control isnt assembly the major?
I mean, as pointed out, you still need a compiler and some kernell is written in assembly.

not unless you hack the bios ROM. when you run your program, it still uses it's run environment to execute. no program can run just by itself, unless it is tied to hardware, as the bottom of the kernel is (via the boot process). some kind of environment always has to run your program or its just useless bits. thus all the kernel security features are still in place. you could bypass some API calls by writing your own methods, but you still need to play by the resource allocation rules that the kernel sets.  thats why people made rootkits; to gain the kind of control your thinking about, and in that case it doesn't matter what langague your working in.

---

### Post by samjh on 2009-05-08
> **CatsRninja said:**
> But isn't assembly the machine?Not really.  Assembly is just a tool to control the machine, but there are many layers.
> In terms of total control isn't assembly the major?Well, that depends on the context.  If you're programming a small microcontroller, you're quite free to do whatever you want on it using assembly.  But a general-purpose operating system like Windows or Linux has numerous layers between machine and the end-user, and numerous "machines" in the hardware layer.  Something needs to tie it all together.  That is what the operating system kernel does: provide the lowest level of abstraction to control the input and outputs to and from the hardware and software, and coordinate all the information that flows through it.

When you write an assembly program to run in Linux, you're writing an assembly program to run according to the rules that the Linux kernel imposes on it.  Otherwise, you might as well write your own kernel.  This is the same on Windows, BSD, Solaris, and whatever else.  No operating system worth using will allow the user to run wild just because a program is written in assembly.

You cannot write a program in assembly for Linux, and expect it to run on Windows just because the language is assembly and the target CPU is Intel x86.  That's because Linux and Windows expects programs that run on top of their kernel to behave in a particular way, using the system calls and other facilities that are provided by the kernel.

The level of control you are asking for can only be attained if you basically write your own operating system kernel. or "hack the BIOS" as the previous poster put it.

---

### Post by Calmatory on 2009-05-08
> **Jiraiya_sama said:**
> From what I've heard, GCC is better at generating optimized binaries than many assembly programmers.

Off topic I know. :| 

Claiming that C with GCC is faster than pure assembly? :P

..if it was such that people used assembly/c/c++.. No. They use Python! For everything!

People shouldn't learn high-level(Ruby, Pyhton, Perl) languages first. They will just stick to them and never learn assembly or even C, never know how to strip the executables down, never know how to optimize them and never know what exactly happens inside the CPU. Programming blindfold is not good. :P

---

### Post by Zugzwang on 2009-05-08
> **Calmatory said:**
> People shouldn't learn high-level(Ruby, Pyhton, Perl) languages first. They will just stick to them and never learn assembly or even C, never know how to strip the executables down, never know how to optimize them and never know what exactly happens inside the CPU. Programming blindfold is not good. :P

As mentioned probably a million times in this forum before, there are two approaches to programming:
[LIST]
[*]Doing it bottom-up (what you propose), i.e. learning low-level langauges first in order to "understand" what is happening in the computer.
[*]The top-down approach, i.e. learning "programming logic", typical problem solving solutions, etc. first, using high-level langauges.
[/LIST]
Both methods are perfectly valid, i.e. the first one is often preferred by technicians, the second one is more the "mathematical" view onto the problem. 

However, you are claiming that "programming blindfold" is no good. However, high level programming is far from being programming blindfold. I'll explain that using your examples:
[LIST]
[*]They will just stick to them and never learn assembly or even C,
[*]never know how to strip the executables down, 
[*]never know how to optimize them and never know what exactly happens inside the CPU.
[/LIST]
Comments:
[LIST]
[*]So they will never learn assembly or C -- Ok, but where's the problem with this? This is like saying that one shouldn't drive a car without driving a motorcycle first, because otherwise one will never learn the latter. So where is the problem here? Also, people will go back and start the stuff when they will actually need it.
[*]Why should a Python programmer know how to strip executables. He/She is not dealing with executables. That's like saying that one shouldn't start with driving cars before knowing how to put on a motorcycle helmet.
[*]The same for optimizing executables -- As far as the algorithmic side of the program is concerned, high-level languages make no difference to low-level ones -- in both, you start optimizing when your program is too slow. Also, you don't know exactly what happens in your computer, either. You can fill books just with how the CPU computes absolute memory addresses! So you just program at a lower level of abstraction.
[/LIST]

Summary: The problem you mention aren't there for high-level programmers. In fact, abstraction is a nice and necessary concept and the right level of abstraction depends on the problem you are tackling. For most people, a high abstraction level should be fine. And when talking about learning the basics, one can also argue what actually are the basics. One might say understanding the concepts of algorithms is most important, which can be perfectly done in high level languages without hassle (such as memory management, etc.). You can always go deeper in the abstraction chain **if needed**.

---

### Post by doas777 on 2009-05-08
+1 Zugzwang.

we as a society need programmers of all levels of skill, for different jobs. most folks that write drivers in assembly, don't usually do POS distributed database frontends. your right, in IS lower level skills are very important, but there are far more jobs in IT, where your better off with .net/java/python.

---

