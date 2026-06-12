---
title: "Writing Drivers"
date: 2007-09-01
forum: Programming Talk
---

### Post by Uncle_Grombor on 2007-09-01
Hi all.  I've had some limited programing experience, and I'm fed up with Lexmark.  I cannot find any drivers for there 1200 series All in One printers for Linux.  Not even an rpm, so, I have decided to venture into the realm of driver writing and pray to Allah, Elohim, Zeus, etc... that I don't crash and burn.  I did get the printer aspect of the 1200 to work, using the z600 driver, but I would like to be able to scan and copy also.  I would be forever indebted to be directed where to begin such an undertaking.  One that is actually like trying to play Mozart and only knowing how to play chopsticks!!!  Thanks and have a great holiday weekend all.

---

### Post by pmasiar on 2007-09-01
You obviously know it will not be trivial, that is good. Don't worry, Linux community is friendly to people who desire to learn: if you persist, someone will help you to get there. When student is ready, guru will come. :-)

What exactly is your programming experience? In terms of languages used, lines written, weeks/years spent digging deeper? Do you prefer direct way ("drivers or bust!"), or you want to become passable programmer before you dive into deep waters of driver programming? What are your other goals in programming area?

Because many roads can go to your goal... and to keep with the allegory, they may have different sceneries :-)

---

### Post by jpkotta on 2007-09-01
IIRC, Lexmark has a driver framework that makes it simpler to write drivers for (some) of their printers.  I might be totally wrong about this.

There is a framework for scanners in Linux called SANE.  I have never bothered to get it to work.  I use the web interface built in to my printer (HP Photosmart 3200) to scan things.

---

### Post by Uncle_Grombor on 2007-09-01
> **pmasiar said:**
> 
What exactly is your programming experience? In terms of languages used, lines written, weeks/years spent digging deeper? Do you prefer direct way ("drivers or bust!"), or you want to become passable programmer before you dive into deep waters of driver programming? What are your other goals in programming area?

I've had limited experience in Unix on a RS9000 at my local community college.  I've tasted Assembler for the IBM 360 Mainframe.  Some Pascal.  No C/C++ (That may be where I need to start).  HTML is simple, just don't remember the codes.  Beating myself with a cat o' nine would be more fun then taking COBOL again (God, that's why they invented the spreadsheet!!!!)  But to be honest most of my computer skills were learned in High School and some college.  The problem with the college part is I found out I liked booze better then school.  Until then I didn't think I liked anything better then school.  Finally got my head out of my rear a few years ago and now most of my programing experience is in CNC's (gag, I hate the things, so dry, but a lot better then having to type a companies income reports in COBOL!!!)

---

### Post by pmasiar on 2007-09-01
My first "personal computer" was IBM/360 with 1MB RAM :-) I was programming with one astronomy student in night shifts :-) .... not many people here seen it! Lots of fun.

OK so if you are not in a hurry and better learn it stet by step this time.

I would recommend you to start with Python. Either use "Dive into Python" (it expect you to remember variables, loops, functions, arguments etc), or start from  beginner level, using any online book from wiki in my sig. You need to buy at least one book: Pocket Python reference, $10.

After refresher, go for C. Sticky in this forum has many links. Ask for help if needed.

Even as hardcore C hacker, you can still use Python for utility programming: generate test data, compare results, parse logs, move files around.

Better start late than never! :-)

---

### Post by slavik on 2007-09-02
I would recommend the K&R book (The C Programming Language 2nd Ed. by Kernighan and Ritchie).

Sorry, pmasiar, but in this situation Python only seems to be a detour.

---

### Post by Mathiasdm on 2007-09-02
> **slavik said:**
> I would recommend the K&R book (The C Programming Language 2nd Ed. by Kernighan and Ritchie).

Sorry, pmasiar, but in this situation Python only seems to be a detour.

I have to agree here. We're talking about someone who knows things like Pascal and Assembly (though perhaps a bit vague).
I'll follow slavik and advise C.

Next after that: [Linux Device Drivers](http://lwn.net/Kernel/LDD3/).

---

### Post by public_void on 2007-09-02
Agreed with others C is the language to use.
>  		I would recommend the K&R book (The C Programming Language 2nd Ed. by Kernighan and Ritchie).
Great book, a must for any C/C++ programmer.

---

### Post by pmasiar on 2007-09-02
> **slavik said:**
> 
Sorry, pmasiar, but in this situation Python only seems to be a detour.

Well, no: teachers teaching programming have experience that teaching Python before more complicated languages lets then teach programming basics separately and faster than teaching them in "hard" language.

And everyone needs "scripting" language for small task, and I posted. Even if you do drivers for living :-) Do you use C to shuffle files around, or parse logs? You really do?

---

### Post by nss0000 on 2007-09-02
Yes, K&R is a most valuable outline, reference and "task_master". But K&R is NOT always adequate as a tutorial source for self-teaching. It's good fotune that -- for the less obvious C-language elements --  you may find DETAILED examples and discussions at various websites:

Some I have found useful are:

[http://www.space.unibe.ch/comp_doc/c_manual/C/SYNTAX/syntax.html](http://www.space.unibe.ch/comp_doc/c_manual/C/SYNTAX/syntax.html)
[http://www.imada.sdu.dk/~svalle/courses/dm14-2005/mirror/c/](http://www.imada.sdu.dk/~svalle/courses/dm14-2005/mirror/c/) 
[http://einstein.drexel.edu/courses/CompPhys/General/C_basics/](http://einstein.drexel.edu/courses/CompPhys/General/C_basics/)

IMHO it's best to patently work-thru both examples, and your own varients of each task. And combine tasks as you build skills. A couple months hour-or-two a day will get you going.

---

### Post by jnorthr on 2007-09-02
Go here: [http://safari.oreilly.com/](http://safari.oreilly.com/)
under 'search' column put 'device drivers' click 'go'
click on book: linux device drivers by johnathan corbet to start your research. prepare to spend 6 months or so with the examples of character, block and network device drivers. 

This is exactly what i've done as i have an old iomega zip100 parallel port disk drive. it does not work under recent versions of ubuntu and none of the howto's are relevant any more, so i set myself a small challenge to try to make/kludge a device driver for it. It's a long job, but the satisfaction alone is worth every bit of blood\\:D/,sweat and tears.

---

### Post by shawnhcorey on 2007-09-02
You should check out [SANE]("http://www.sane-project.org/").  They may already have a driver you can use.

Most device drivers are written in C since it's a high-level language that's universally available.  A good IDE is recommended.  Otherwise you should learn make(1).

---

### Post by slavik on 2007-09-02
personally, I use perl and cat|grep

Another thing for the OP to check out: [http://www.amazon.com/Linux-Device-Drivers-Jonathan-Corbet/dp/0596005903/ref=pd_bbs_sr_1/103-2780105-4647805?ie=UTF8&s=books&qid=1188745002&sr=1-1](http://www.amazon.com/Linux-Device-Drivers-Jonathan-Corbet/dp/0596005903/ref=pd_bbs_sr_1/103-2780105-4647805?ie=UTF8&s=books&qid=1188745002&sr=1-1)

---

### Post by the_unforgiven on 2007-09-02
Here, you can download the entire 3rd edition of LDD for free in PDF form - thanks to Jonathan Corbet:
[http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

But, as everybody has already said, first check out if the work is already done in the SANE project - it's no point to reinvent the wheel - except probably if you want to LEARN ;)

HTH ;)

---

### Post by Uncle_Grombor on 2007-09-03
Thanks everyone.  I greatly appreciate the information and help.  I started by downloading LDD 3rd ed. and I have a text book on C++.  "Starting out With C++ 3rd Edition" by Tony Gaddis.  Is it any good? If I'm not mistaken C++ is only different from C in that it has high level capabilities.  I'm really racking my brain hear, but if I remember right, I can somehow use (sh ? csh ?  Unix shell scripts I think, but don't know yet if they carried over to linux in the same fashion that they are used in Unix) to write and compile C code.  I have used sh to compile code I have downloaded.  Maybe I can code in pico? gedit?  then compile it with sh?  I'll continue to search through all the links and information everyone has so generously given.  Thanks again.  Oh, and a side note.  I fixed my printer problem by returning it and buying an HP Photosmart (better quality printer anyway)! :lolflag:  I sure miss the days of text based internet with gopher, archie, and ftp, sigh.

---

### Post by fct on 2007-09-03
If you are programming modules, it's better to use C. You'll probably run into many difficulties mixing C++ code (that can be quite different) with the C source code of the kernel.

About editing, any C editor is fine. Vim, Emacs, whatever. Don't worry about the scripts part, the LDD book will probably guide you through the build system, but yes, you can customize your builds in many ways, including shell scripts.

---

### Post by samjh on 2007-09-03
> **Uncle_Grombor said:**
> I have used sh to compile code I have downloaded.  Maybe I can code in pico? gedit?  then compile it with sh? 

Both Gedit (in Ubuntu) and Kate (in Kubuntu) are adequate editors.  They have syntax highlighting, scripting, and advanced code editing features.  I would use those if were you (I use them myself), and not worry too much about the choice of editor.

The standard method for compiling C/C++ programs in UNIX/Linux is by using the compiler directly or by using Makefiles.  To use Makefiles, you need to know how to use the compiler from the command-line anyway.

For C programs, to compile hello.c into a hello executable binary, just type this in the directory where your source code file is:
```
gcc hello.c -o hello
```
Likewise for C++ programs:
```
g++ hello.cpp -o hello
```

Makefiles can help to automate compile procedures so you are not having to type out all those commands every time you want to compile something.

This is a **very simple** example of a Makefile for compiling hello.c to a hello exectuable:
```
hello: hello.c
        gcc hello.c -o hello
```As I said, it is an extremely simple example.  To run it, just type "make" (without quotes) into your terminal in the same directory as your Makefile.  Alternatively you can type "make hello", which is compile your hello program.

If you add this to the above example:
```
bye: bye.c
        gcc bye.c -o bye
```...you can choose whether to compile hello or bye.  To compile hello, just type "make hello"; to compile bye, just type "make bye".  But if you type just "make", it will compile hello only, because that is the first target in your makefile.

Makefiles can be very complex and powerful.  The two examples given are extremely simple uses of Makefiles, which should suffice for small programs.

---

### Post by j_g on 2007-09-03
Oh good lord. :: rolls eyes ::

Do _not_ use Python to write a device driver. You may very well need to call certain APIs within a kernel (as opposed to user mode) context, and I have no doubt that the Python interpreter has no facilities for marking code to be run in kernel mode, let alone be launched in kernel mode.

---

### Post by tgbrowning on 2007-09-03
Begging everybody's pardon, here, but I'm on a similar quest -- only I'm looking to write a device driver for a USB DVD/CD carousel. 

Experience:  About twenty years of programming. My best work was in Turbo Pascal and Assembly language for DOS, which is where I learned to program. I've written drivers for embedded 80xx chips in C, though and have a fair amount of C programming experience. I'm currently working as a Traffic Engineer writing Excel VB code for traffic analysis (but, thank deities unnamed, in 10 months I'm retiring and then, no more VB and no more bloody Microsoft. <loud chorus in background singing hosannas>) 

Most of what I know was with the benefit of a good IDE (Borland put out some very nice ones that did Pascal or  C, C++ and Assembler) and frankly, I'm not impressed with Eclipse so far. I don't like Java, to be honest). 

I stumbled on references to Anjuta and have spent a very frustrating time trying to get that IDE built. Every time I turn around I seem to be lacking something. I'm about ready to give that a complete miss and go to using make alone along with emacs. 
 
Is it worthwhile to continue trying to get Anjuta to compile or should I just forget it and go back to basics?

Browning>>>
Browning>>>

---

### Post by slavik on 2007-09-03
IMO, for drivers anjuta may be overkill.

anjuta is great if you have something large like a small game where you may easily have 5-10 files of source code.

along with emacs, may I suggest looking into geany?

---

### Post by kvorion on 2007-09-03
Hi All,

I was getting my hands wet, trying to write my first hello world kernel module (reading the book LDD):

```
#define MODULE
#include <linux/module.h>
int init_module(void) { printk("<1>Hello, world\n"); return 0; }
void cleanup_module(void) { printk("<1>Goodbye cruel world\n"); }

```

 Apparently I need to #include the <linux/module.h> file. When I tried to compile my code, I got an error saying 

```
error: linux/module.h: No such file or directory
```

I went into the /usr/include/linux folder and I found that the module.h file was not present in it. I also could not find some other files like config.h and init.h in this folder. I located the init.h and more importantly the module.h file in the 

```
/usr/src/linux-headers-2.6.20-15/include/linux
``` folder. How can I include the file from this folder in my program?

I tried doing ```
#include</usr/src/linux-headers-2.6.20-15/include/linux/module.h>
```

but that threw a lot of errors on me saying that the files included inside module.h are not found.

Am I doing something wrong here? How do I go ahead and compile my sample program?

---

### Post by tgbrowning on 2007-09-03
Slavik,

You can indeed and I just took a look -- I expect it will do pretty much exactly what I want. Not too big, fairly straightforward and configurable.  Thanks for the tip!

Browning>>>

---

### Post by samjh on 2007-09-03
> **kvorion said:**
> I went into the /usr/include/linux folder and I found that the module.h file was not present in it. I also could not find some other files like config.h and init.h in this folder. I located the init.h and more importantly the module.h file in the 

```
/usr/src/linux-headers-2.6.20-15/include/linux
``` folder. How can I include the file from this folder in my program?

Use this switch when you compile using gcc:

```
-I/usr/src/linux-headers-2.6.20-15/include/linux
```

so something like this:
```
gcc mymodule.c -I/usr/src/linux-headers-2.6.20-15/include/linux
```

---

### Post by slavik on 2007-09-04
> **pmasiar said:**
> Well, no: teachers teaching programming have experience that teaching Python before more complicated languages lets then teach programming basics separately and faster than teaching them in "hard" language.

And everyone needs "scripting" language for small task, and I posted. Even if you do drivers for living :-) Do you use C to shuffle files around, or parse logs? You really do?
I'm sorry to the OP if I am hijacking this thread, but how does teaching print in Python help get away from the preprocessor when it will have to be there? I guess this is going to become a battle of preference, but I think it is best to keep reminding someone who is new with C that there are things he will have to learn.

I also know some professors who would rather teach Java after C++ because then you gain efficient programming skills (memory is cheapER, not free and not infinite) and you also gain appreciation for garbage collection.

Also, if someone's goal is to write device drivers for the linux kernel which I am sure we are going to agree is going to be done in C, how much Python should a person learn before moving on to C?

As for moving things around, people have used make to do this. Make has what are called phony targets (where a file is not actually created, so, install, clean, uninstall are actually phony targets).

---

### Post by the_unforgiven on 2007-09-04
> **kvorion said:**
> Hi All,

I was getting my hands wet, trying to write my first hello world kernel module (reading the book LDD):

```
#define MODULE
#include <linux/module.h>
int init_module(void) { printk("<1>Hello, world\n"); return 0; }
void cleanup_module(void) { printk("<1>Goodbye cruel world\n"); }

```

 Apparently I need to #include the <linux/module.h> file. When I tried to compile my code, I got an error saying 

```
error: linux/module.h: No such file or directory
```

I went into the /usr/include/linux folder and I found that the module.h file was not present in it. I also could not find some other files like config.h and init.h in this folder. I located the init.h and more importantly the module.h file in the 

```
/usr/src/linux-headers-2.6.20-15/include/linux
``` folder. How can I include the file from this folder in my program?

I tried doing ```
#include</usr/src/linux-headers-2.6.20-15/include/linux/module.h>
```

but that threw a lot of errors on me saying that the files included inside module.h are not found.

Am I doing something wrong here? How do I go ahead and compile my sample program?
Kernel modules are to be built using the kernel build system - which has changed drastically for the 2.6.x series of kernels.

Take a look at:
[http://en.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN119](http://en.tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN119)
especially, section 2.2.

---

### Post by Uncle_Grombor on 2007-09-04
Another question, If I may.  Is the Linux kernel written in c?  I was informed that I can go in and remove unnecessary drivers and the like.  Kinda' like trimming the fat so it runs faster and more efficient.

---

### Post by samjh on 2007-09-04
The Linux kernel is written in C.

In fact, later versions of Unix were/are written in C.  Originally it was written in Assembly, but C was developed to make developing and porting Unix easier, thus its fame and popularity among operating system developers and Unix/Linux fans.

---

### Post by kvorion on 2007-09-04
I was wondering if I need anything additional to be installed before I can build this program. Does the build-essential package suffice for this task?

---

### Post by lisati on 2007-09-04
> **Uncle_Grombor said:**
> I've had limited experience in Unix on a RS9000 at my local community college.  I've tasted Assembler for the IBM 360 Mainframe.  Some Pascal.  No C/C++ (That may be where I need to start).  HTML is simple, just don't remember the codes.  Beating myself with a cat o' nine would be more fun then taking COBOL again (God, that's why they invented the spreadsheet!!!!)  But to be honest most of my computer skills were learned in High School and some college.  The problem with the college part is I found out I liked booze better then school.  Until then I didn't think I liked anything better then school.  Finally got my head out of my rear a few years ago and now most of my programing experience is in CNC's (gag, I hate the things, so dry, but a lot better then having to type a companies income reports in COBOL!!!)

IBM 360? That goes back a few years. The nearest I can manage in my experience is for IBM 370 - and the last coding I did for that was about 20 years ago! But I digress.....

---

### Post by fct on 2007-09-04
> **Uncle_Grombor said:**
> Another question, If I may.  Is the Linux kernel written in c?  I was informed that I can go in and remove unnecessary drivers and the like.  Kinda' like trimming the fat so it runs faster and more efficient.

You can do that. That's recompiling the kernel. Caveat: you must know what you are doing and know your hardware well enough in order no to end up with an unusable kernel.

And yes, the kernel is mostly written in C, with some hardware dependant parts written in assembler.

---

