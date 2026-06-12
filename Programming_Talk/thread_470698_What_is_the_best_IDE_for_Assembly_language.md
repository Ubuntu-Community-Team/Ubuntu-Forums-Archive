---
title: "What is the best IDE for Assembly language?"
date: 2007-06-11
forum: Programming Talk
---

### Post by willz06jw on 2007-06-11
Howdy,

My goal is to learn assembly for the Amd-64 before the end of summer.  Do you guys know a good IDE for Linux?

Will

---

### Post by ankursethi on 2007-06-11
Any text editor ought to work. I haven't really heard of people refactoring assembly code or creating large projects in it that need to be managed using an IDE. An IDE will be overkill for an asm project.

If you still want to go ahead, why don't you scour the web for an asm plugin for Eclipse? I'm sure someone out there must have had time to kill ...

---

### Post by boz on 2007-06-11
Honestly, I don't have oodles of experience in assembly but I was a teaching assistant for our assembly language class in the Electronics Engineering program in college.  I found that the best way to manage large assembly projects was to build your own libraries and document them well.  I only knew how to make static libraries in assembly, but it may be possible to make dynamic libraries as well.  It probably won't matter, though.  I actually made a functional text editor using MASM on the Windows platform (don't ask me why I did it on Windows...ugh - never again) and I need those libraries.  Otherwise, the code wouldn't have been manageable. within one document.

I've never heard of a good IDE on the Linux platform and it probably isn't necessary.  Just write libraries and document.  Of course, good software engineering (i.e. PLANNING) is always a plus.  Plan, write, document, and if necessary, refine.  I made libraries containing even the most simple stuff, like making a carriage return and line feed in DOS.  (Again, DOS...ugh.  Don't program in DOS.  It was required for us - you don't have an excuse.  Stick with Linux.)

---

### Post by loell on 2007-06-11
if you would just like, syntax highlights on assembly,  perhaps try 

```
scite
``` editor

---

### Post by the_unforgiven on 2007-06-12
Almost all programming specific text editors (like vim, emacs) have syntax highlighting support for ASM.
Also, if you are programming seriously in ASM, most of the build structure would be custom made, so any IDE will not be of great help. You'd need to write the Makefiles yourself.

HTH ;)

---

### Post by hockey97 on 2007-06-13
What is ASM good for?? becuse I got a book on it, and never really used it , I hear like it's too old, 

the book is about computer circuitry, and it talks about using ASM to program your boards ect.

but I hear on the fourms that ASM is old and C++ is more common to use, even for circuitry of computers,

meaning making an OS.

Is this true?? I wanted to learn ASM but after hearing that stuff I then stoped learning it thinking it's a waste of  time.

Could C++ do the same Work as ASM??

I know c++ and want to attempt on making an OS thiis summer since I have alot of time.

Thanks for your time.

---

### Post by Modred on 2007-06-13
For more general tasks, yes you would want to use a higher level language like C++.  Most ASM instructions have a 1-to-1 correspondence to machine instructions executed by the processor.  So if you need to optimize a particular piece of code, writing it in ASM and linking it to your C++ program could help a great deal.  Unless I'm mistaken, game developers still make use of ASM quite a bit when interfacing with graphics hardware, since every little bit of speed can make a difference in processor intensive stuff like games.

C++ can do the same things and more (at least out of the box) than ASM in userland, and is much quicker and simpler from a programmer's point of view.  Now if you're writing a complete OS, you'll have to do some ASM at some point.  When the computer boots, I believe at least some of your bootloader will need to be written in ASM so that you can get the computer far enough along to load the necessary libraries to run a C or C++ program.

---

### Post by willz06jw on 2007-08-02
Just a follow-up, I started using the Asm plugin to Eclipse

[http://sourceforge.net/projects/asmplugin/](http://sourceforge.net/projects/asmplugin/)

Thanks Team,
William
:guitar:

---

### Post by hasanbacioglu on 2011-10-11
> **hockey97 said:**
> What is ASM good for?? becuse I got a book on it, and never really used it , I hear like it's too old, 

the book is about computer circuitry, and it talks about using ASM to program your boards ect.

but I hear on the fourms that ASM is old and C++ is more common to use, even for circuitry of computers,

meaning making an OS.

Is this true?? I wanted to learn ASM but after hearing that stuff I then stoped learning it thinking it's a waste of  time.

Could C++ do the same Work as ASM??

I know c++ and want to attempt on making an OS thiis summer since I have alot of time.

Thanks for your time.

:) After reading your post and laughing a lot in front of my Liquid Crystal Display, (which is very awkward kind of interaction between an electronics engineer and substance), I just wanna say that you'll need more than "a summer, and a lot of time" for making or writing (or whatever you call it) your own operating system. Why don't you simply try  writing a driver for your own mouse or better try to print mouse's coordinates on your console just using assembly, c or c++ ? It should be much more easier than writing an non-operational operating system and also you may make better use of your "a lot of time, and the heat of summer", and dedicate all your skills to much more achievable goal.
  If you ever make any progress, just let me know so that your next assignment would be more hardware oriented. More explicitely, related with FPGA's. 
  Anyway good, luck have fun :)

---

### Post by 11jmb on 2011-10-11
> **hockey97 said:**
> What is ASM good for?? becuse I got a book on it, and never really used it , I hear like it's too old, 

the book is about computer circuitry, and it talks about using ASM to program your boards ect.

but I hear on the fourms that ASM is old and C++ is more common to use, even for circuitry of computers,

meaning making an OS.

Is this true?? I wanted to learn ASM but after hearing that stuff I then stoped learning it thinking it's a waste of  time.

Could C++ do the same Work as ASM??

I know c++ and want to attempt on making an OS thiis summer since I have alot of time.

Thanks for your time.

assembly is not used much for large software projects to my knowledge (most high-level programs are c and c++ dominant), but it is HUGE for programming embedded systems.

assembly allows you to completely control the structure and flow of your program, so you can make critical parts of your program extremely fast. Just as one example, it allows you to control which variables are stored in registers (which are faster read/writes) for a boost in speed

---

### Post by 11jmb on 2011-10-11
> **hasanbacioglu said:**
> :) After reading your post and laughing a lot in front of my Liquid Crystal Display, (which is very awkward kind of interaction between an electronics engineer and substance), I just wanna say that you'll need more than "a summer, and a lot of time" for making or writing (or whatever you call it) your own operating system. Why don't you simply try  writing a driver for your own mouse or better try to print mouse's coordinates on your console just using assembly, c or c++ ? It should be much more easier than writing an non-operational operating system and also you may make better use of your "a lot of time, and the heat of summer", and dedicate all your skills to much more achievable goal.
  If you ever make any progress, just let me know so that your next assignment would be more hardware oriented. More explicitely, related with FPGA's. 
  Anyway good, luck have fun :)

another great assembly assignment: write a simple function in c and assembly (sorting a long array, for example) compile the c code into 4 object files, compiled with -O0, -O1, -O2, -O3

write an executable that links against the 5 objects and tests the runtime for each

that may help you to understand why assembly is still very useful

another fun exercise: look at the output of an assembler compared to a hand-coded asm file. you may be surprised how sloppy even a good assembler can be

---

### Post by trent.josephsen on 2011-10-11
Ugh.  Check post dates, guys.  OP's long summer was four years ago.

---

### Post by SciBerC on 2011-12-21
Most of you guys are rather impolite and rude, so what if he want's to make a OS? Does the duration of time really matter? Imagine the criticism Steve Jobs or Bill Gates would have gotten when they made Mac and Windows or even Dannis Ritchies and Brian whatever his last name is that made C but does guys successfully made C, Windows and Mac. C was made in assembly, C++ is a extension off C, I would make a OS in Assembly, than I would write most of the apps in C and C++. :D I would love to see your OS so far :)

---

### Post by trent.josephsen on 2011-12-21
This thread is over 4 years old.  Thought I should mention it.

---

### Post by sffvba[e0rt on 2012-05-11
*Back to sleep **old** thread.*


404

---

