---
title: "Scripting/programming?"
date: 2009-10-20
forum: Programming Talk
---

### Post by nothingman02 on 2009-10-20
HI everybody,
Im new to this field and am right now introducing myself to all concepts. Iam touching on programming right now and have some very basic doubts..

1) What actually is scripting and how is it different from programming?

2) What actually is shell scripting and how is it different from any other scripting or programming languages.

thanks for the help. I have been receiving a lot of help here in this forum and thanks again for taking the time.

---

### Post by Bachstelze on 2009-10-20
1) The difference is very vague. Usually, "scripting" refers to programming in interpreted languages, but it's really still programming.

2) Shell scripting is making scripts that are to be interpreted by a shell (Bash, ash, ksh, etc.). It is just another language.

---

### Post by nothingman02 on 2009-10-20
HI and thanks for the reply.

1) So could I assume that there isnt really a whole lot of difference?
That is, I could substitute a scripting language with a programming language or vice versa to accomplish THE SAME TASK?
I could substitute say C++ with Python for developing applications? And can I use C++ to develop scripts that are embedded in applications?

---

### Post by Bachstelze on 2009-10-20
> **nothingman02 said:**
> 
That is, I could substitute a scripting language with a programming language or vice versa to accomplish THE SAME TASK?

Yes. However, a given task might be easier to accomplish in one language than in another. That's why we have different languages. :)

---

### Post by martrn on 2009-10-20
> **nothingman02 said:**
> What actually is scripting and how is it different from programming?

Programming the writing, debugging and testing of instructions that are written for a computer, where a computer can take the instructions and interpret and following them performing a set of actions.

Scripting is a subset of programming whereby a script which is executed on a computer would be a like a computer program but would be written with particular limitations in mind.  The limitations of vbscripts could be that it can only control databases or spreadsheets, javascript could be java that can only perform actions within a browser, or php, (was) a scripting language that could on be excuted while running a web server.

> **nothingman02 said:**
> 2) What actually is shell scripting and how is it different from any other scripting or programming languages.

Shell scripting is a job control language.  Its limitations are that it can only perform actions and take control of programs that have already been written.  The idea of shell scripting is the automation of computer tasks.

The best programming language is c or c++ because it runs at the lowest level of the computer language, just before you reach the machine code level which is language of the computer.

Usually scripting languages are the highest levels, and hence the restraints.

---

### Post by H4F on 2009-10-20
> **nothingman02 said:**
> HI and thanks for the reply.

1) So could I assume that there isnt really a whole lot of difference?
That is, I could substitute a scripting language with a programming language or vice versa to accomplish THE SAME TASK?
I could substitute say C++ with Python for developing applications? And can I use C++ to develop scripts that are embedded in applications?

yeap you can  nearly always substitute.  It just a matter of how easy is to implement particular task in particular language.

scripting . its a text file with program which can be interpreted
compiled . compiler compiles file to byte code which runs directly and faster

---

### Post by nothingman02 on 2009-10-20
Hi and thanks everybody for the replies. 

I am clear..:)

So I am thinking Id stick to learning C++ and Shell scripting. I am looking to a career of a system admin and am under the impression that i wouldnt need anything else. Or so I hope. I am learning too many things and theres only so much I can take.
-----------------------------------------------------------------------
Off topic, I have joined Unitek's Red Hat (RHCT) training for classes 033 and 133 starting on November 9th through 21st and on the last day i will have the exam. 

Theres just under 20 days left for the training to start and I am trying to prepare as much as I can. I am new and from a different background and am learning everyday. So far I have learned a little bit (just basics) of OS, H/W, N/W and Linux file structures and its (Linux's) different layers and stuff. I am now touching on the shell scripting a bit and then am planning to study 'linux internals' and its operations in a little detail. 

Could someone let me know if I would be ready for the RHCT training? Im spending around $4500 (loan/investment) for the training and exam and do not want to take it up if I need to have some prior knowledge and experiance for the RHCT training and exam. 

I am obviously looking to start off as a support tech and work my way up to admin but am also wondering what all goes into being a sys admin. Would one need to know networking and programming as well or just managing the Linux filesystem and its processes and users, installations etc will sufffice?
Thanks again for the help.

---

### Post by t0p on 2009-10-20
> **martrn said:**
> The best programming language is c or c++ because it runs at the lowest level of the computer language, just before you reach the machine code level which is language of the computer.


I hate to be a pedant.  But here goes anyway.  Under C/C++ you have assembly.  Then there's the machine's language of 0s and 1s.

---

### Post by Flimm on 2009-10-20
A script is read and run from top to bottom. Syntax errors and the like are detected once it reaches them.
A program is compiled first, and then executed. Syntax errors are detected before any code is executed.
That's the simplest difference between a script and a program that I can think of.

---

### Post by anewguy on 2009-10-20
> **nothingman02 said:**
> Hi and thanks everybody for the replies. 

I am clear..:)

So I am thinking Id stick to learning C++ and Shell scripting. I am looking to a career of a system admin and am under the impression that i wouldnt need anything else. Or so I hope. I am learning too many things and theres only so much I can take.
-----------------------------------------------------------------------
Off topic, I have joined Unitek's Red Hat (RHCT) training for classes 033 and 133 starting on November 9th through 21st and on the last day i will have the exam. 

Theres just under 20 days left for the training to start and I am trying to prepare as much as I can. I am new and from a different background and am learning everyday. So far I have learned a little bit (just basics) of OS, H/W, N/W and Linux file structures and its (Linux's) different layers and stuff. I am now touching on the shell scripting a bit and then am planning to study 'linux internals' and its operations in a little detail. 

Could someone let me know if I would be ready for the RHCT training? Im spending around $4500 (loan/investment) for the training and exam and do not want to take it up if I need to have some prior knowledge and experiance for the RHCT training and exam. 

I am obviously looking to start off as a support tech and work my way up to admin but am also wondering what all goes into being a sys admin. Would one need to know networking and programming as well or just managing the Linux filesystem and its processes and users, installations etc will sufffice?
Thanks again for the help.

I have no idea what the requirements are for the Redhat stuff you are looking at.  I can, however, give you an idea of the things you need to know to function effectively as a systems administrator and a systems programmer.  I hate to say it, but basically you need to know it all.  Maybe not as much detail in some things, but you need an in-depth knowledge of:

- the operating system, no matter what it is.  This can't be learned in just a couple of weeks of looking at things - it takes times, a lot of reading, a lot of trial and error (and the assoicated mistakes you learn from)

- at least 1 programming language such as C++ or C, as most operating systems are written in those languages, and a good understanding of the language teaches you not only how to approach problems (is it a programming problem, an OS problem, a hardware problem, a user error?), but also the underlying logic skills needed

- networking, including setting up networks, IP address schemas, setting up, debugging and managing servers, firewalls and security systems

- a scripting language of choice for the OS you are concentrating in

- hardware, at least to the point of being able to build systems and debug problems with the assembly, installing additional hardware, configuring the OS to use the hardware, etc.

This is just an extremely basic outline and list.  I admire you ambitions, but also be aware there just aren't any shortcuts.  It takes time, and a combination of schooling and real world experience starting at the bottom to get there.

In my younger days I was a system administrator and systems programmer on large mainframes, then minis when they came out, and finally on micros when they came out (what the vast majority of people think of as a computer now days).  Worked with different types of networks and servers.  Unfortunately things have changed a great deal, I my thirst for needing to know everything diminished after I stopped working.  While there are times I really want to know something and therefore will dig, ask questions, try things, ask more questions, etc., for the most part I'm down to just wanting things to work now.  A lot of that drive, which you seem to have now, is past for me.  For me at least, it just took time and a lot of just doing things to learn everything needed for the job.

Just my 2-cents worth!

Dave :)

---

### Post by Arndt on 2009-10-21
> **martrn said:**
> 

Usually scripting languages are the highest levels, and hence the restraints.

The only connection in my mind between the meaning of "scripting" and "high level" is that the programmer doesn't have to deal with low-level details of memory allocation.

Scripting languages start out as enabling just a series of commands, then enhanced by introducing variables and loops, and if the language continues growing, functions, etc. High-level languages start out with some particular semantic concepts in mind. Once they have developed a bit, calling them one thing or the other may be only a difference in aspect.

(Viewed historically, "high level" was no higher than freeing the programmer from having to deal with in which register each value was kept, and handling the stack explicitly, etc., as you have to when using assembler. But nowadays, C is not seen as very high level.)

---

### Post by CptPicard on 2009-10-21
> **martrn said:**
> The best programming language is c or c++ because it runs at the lowest level of the computer language, just before you reach the machine code level which is language of the computer.

Usually scripting languages are the highest levels, and hence the restraints.

This just comes up over and over and over again :) Well, ok, read the [HLL vs. LLL megathread]("http://ubuntuforums.org/showthread.php?t=851794"). Really, the machine level is not special in any other way except that it is practically necessary because you must physically run stuff at some point. As a language, machine code is remarkably boring. For all I care it could be a Turing-complete magic abacus down there, or a Lisp machine even :)

High-level languages typically introduce more abstract, higher-level concepts to the language that can allow for quite a different take of your problem than an implementation in a lower-level language would allow or suggest. I find it hard to imagine that, say, asm would be so "unrestricted" that a programmer would know how to just hack up something like higher-order functions or a closure mechanism from scratch. Or that conversely a higher-level language programmer wouldn't *know* how to manipulate state using a sequence of operations, because his language is supposedly very "restricted".

For those who are very concerned about native-compilation (it really is not an issue), check out SBCL which actually compiles Lisp, a rather high-level language, down to mahine code. From the programmer's perspective, it is rather meaningless.

And for an idea of what is meant by a different "model" adopted by a high-level language, take a look at Prolog. It's a Turing-complete language (that is, as theoretically equivalent to the rest of them as any other), but the core idea of specifying the program as a set of satisfiable predicates is something quite different. I would be loathe to say that there are "limitations" in Prolog simply because it doesn't behave as asm/C does... it's just very different.

As the OP is looking to going into sysadmining, I really feel that he would benefit from a good scripting language along the lines of Python or maybe Perl. A sysadmin very rarely, if ever, needs to touch C++.

---

### Post by VertexPusher on 2009-10-21
> **nothingman02 said:**
> What actually is scripting and how is it different from programming?
Programs control hardware. Scripts control programs.

> What actually is shell scripting and how is it different from any other scripting or programming languages.
Shell scripts control a program called shell.

---

