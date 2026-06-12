---
title: "Assembly vs. C++"
date: 2006-02-21
forum: Programming Talk
---

### Post by grim918 on 2006-02-21
I'm a beginner programmer, I mostly work with PHP, but now i want to learn something else. I want to learn Assembly but everyone that I know tells me that it will be a waste of time and that I should just learn C++. I would like to know what are some of the advantages of programming in assembly, if there is any, over programming in C++. My goal is to eventually learn how to program some useful applications like programming a cd burner. I know that I am far,far away from programming a project like that but my goal right now is to start learning a language that has the capability of doing something like that.

---

### Post by ignorance on 2006-02-21
i don't know what you can do with c++, but i can tell you if your going to learn assembly than i sugest you start learning how ram and such works. assembly mainly uses your registery's.

but here is a nice link towards assembly programming.
[http://la.kmv.ru/](http://la.kmv.ru/)

---

### Post by simon_is_learning on 2006-02-21
Well the advantages of C++ vs Assembly is for me the ease of starting.

I have no experience with C++, but where I am a trainee we program PIC's with assebmly. And the master in programing has his background in C++. 

So I think it's much more easy to start with C++ becouse all you need is a computer and a keyboard (and some brain). For assembly you have to get the code out of the box. You'll need a PIC (programmable integrated circuit) and electronical skills. 

If you want to learn that, maybe you'll better search up someone that already has it, maybe a company nearby.

---

### Post by Iandefor on 2006-02-21
Assembly is pretty dated and not all that applicable. I would suggest C++.

---

### Post by endersshadow on 2006-02-21
Try [Lisp](http://en.wikipedia.org/wiki/Lisp_programming_language)!!  Just kidding, of course.

You should figure out what you want to do...I would suggest C, or Python...but if it's between Assembly and C++, go C++ :-D

---

### Post by simon_is_learning on 2006-02-21
[QUOTE=Iandefor]Assembly is pretty dated and not all that applicable. I would suggest C++.[/QUOTE]

well.. depends on what you want. 
If you want to control the lights from your computer. 
Then assembly can come handy in place. 

i still recommend at first C++, then when you get the "thinking", start with assembly. But if you have some cash, then you can get proton IDE 
[http://www.picbasic.org/proton_ide.php](http://www.picbasic.org/proton_ide.php)
it's for windows and it's the only one I know. 

then you write in "basic" and it "translates" it to assembly/hex

so some "Basic" knowledge could be good to.

---

### Post by Spark* on 2006-02-21
Actually, PHP would probably be better suited to program a CD burner than assembly... I would suggest you to learn Python or C# if you are mainly interested in GUI programming and then get a grip of the most common GUI libraries. C and C++ are good choices for low level libraries or speed critical components. C probably more so than C++ because of the ease of creating language bindings for it.

---

### Post by LordHunter317 on 2006-02-21
[QUOTE=grim918]I'm a beginner programmer, I mostly work with PHP, but now i want to learn something else. I want to learn Assembly but everyone that I know tells me that it will be a waste of time[/quote]I wouldn't bother learning assembly unless you intend to do hardware work or have a need for it.  Then it's very useful, but it's a "niche" skill in the sense the carryover is almost zero.

When you need to know it, it's useful.  When you don't, it's useless.

> I would like to know what are some of the advantages of programming in assembly, if there is any, over programming in C++.You're closer to the hardware.

>  My goal is to eventually learn how to program some useful applications like programming a cd burner.If you mean like cdrecord, you don't need assembly to do that.  If you mean the kernel internals cdrecord uses, then you need to know C, not C++.

---

### Post by Swab on 2006-02-21
Learning assembly will help you understand what is really going on inside your computer...  There is a great free book called [Programming from the ground up]("http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf") (pdf) Check it out!

---

### Post by dtfinch on 2006-02-21
I think it's good to have programmed in assembly a bit, even if you never plan to use it again.

---

### Post by zkissane on 2006-02-21
[QUOTE=dtfinch]I think it's good to have programmed in assembly a bit, even if you never plan to use it again.[/QUOTE]

It is true, having some assembly knowledge (along with the co-requisite knowledge about memory allocation, registers, the run time stack and all that stuff) is helpful in making better C/C++/<insert language here> code.  In particular, knowing how assembly works helps you make more secure applications.

However, assembly as a first language would probably be overwhelming to all but the most dedicated learners.  I probably would have not gone into CS if assembly were my first exposure to programming.

---

### Post by celloandy on 2006-02-21
Assembly programming is so low-level that it's practically impossible to write any program of reasonable complexity (a GUI app, say) with it.  It would just take way too long, and would be almost impossible to debug.  Don't torture yourself by trying.  Nobody in industry uses it for entire large-scale, non-embedded apps, either.

That said, there *are* advantages to learning some assembly at some point, which is why most CS majors take assembly at some point (I'm taking an assembly class, now, actually), but again, no one expects us to write real programs in it.  We're not masochists.  Also, x86 assembly is hideously ugly, so as a learning language, consider using something like MIPS assembly, instead, over an emulator like spim.

Andrew

---

### Post by LordHunter317 on 2006-02-21
[QUOTE=zkissane]It is true, having some assembly knowledge (along with the co-requisite knowledge about memory allocation, registers, the run time stack and all that stuff) is helpful in making better C/C++/<insert language here> code. [/quote]There are far better ways to learn that than assembly.  In particular, most tasks assembly is used for on modern, protected-mode applications don't care about such things.

And in any other environment, the rules are different.

> In particular, knowing how assembly works helps you make more secure applications.Not especially.  It's likely a very poor path to this.

---

### Post by pharcyde on 2006-02-22
Since you are just beginning C++ is your best bet.  C++ offers most of the features of any high-level object oriented programming (OOP) language.  Learning these concepts is the most important if you are working on large scale projects that require generic libraries to be written and maintained.  If you learn the basic concepts of OOP you can basically translate that skillset to any of the high-level languages that exists today (i.e. C++, Java, Ruby, etc.).  I would start with focusing on basic uses for data structures and algorithms that utilize them.

As for assembly I find that it is also important because if you have a basic understanding of microarchitecture and ISA specifications it can help you significantly optimize your high-level C/C++ code.  Knowing how data structures are stored in memory, registers, and how the architecture stores/retrieves this data from caches is important in high-level code optimizations.  Another thing that is great about assembly is that you learn what instructions are available for your target ISA, and you can learn some really neat tricks used by compilers.

---

### Post by mips on 2006-02-22
Assembly is not that hard to learn if you understand the insides of computers, memory, registers etc.

It is very tedious to do things in assembly, you have to write pages of code to achieve something that can be done with one page of code when using a higher level language.

People still incorporate assemly code into C where it makes sense to do so. Lets just say you need to optimise a certain routine and in some instances to get the best performance you would use assembly to get the level of performance you want.

It is something that could be handy but for now I would say learn C++ first and just start reading up on assembly for now and try out a few little pieces of code.

I think Assembly is pretty much a compulsory subject if you are a electronic eng. student but not required for comp. science studies although offered. I learned assembly as a Electronic Eng student and we had to learn 8088, 8051 & PIC. Learned 680x0 on my own and havent used any of them in real life.

---

### Post by mmHg on 2006-02-23
I'm (finally) getting into programming and plan to progress as follows:

C++ >> python >> php/*SQL >> GORK. ;) 

I'm open to ideas, opinions, comments, jibes, laughs, etc.  Does this look like a (semi) logical progression?  I plan on doing some *nix-only development work as a hobby, and want to write apps for personal use as well.  Not a pro here (trying to be a doctor) but I'm 100% geek and want to write my own stuff.....

---

### Post by orlox on 2006-02-23
Don't know much about C++, but just began learning assembly, and it doesn't seem that impossible for me. Just figured out how to use the GTK library (to make GUIs), and it made feel truly capable of getting somewhere (actually, I just made a program that opened a window with nothing on it...)
I'm studying Astronomy right now, and I feel that assembly might become usefull to generate data analysing tools intended for some heavy use, with great performance speeds, since optimization can be increased quite a bit if you know how to handle it(or so I have read)...
Maybe i'm wrong, but even though, learning assembly is a good way to get to know what happens in your computer...

---

### Post by wmcbrine on 2006-02-25
Learn assembly. Then, don't use it.

I used asm extensively for a time (years ago), and I feel that I'm a much better programmer for it. It was my second language, after 8-bit BASIC. (At the time, those were pretty much the only choices.) Later, I moved to Pascal, but kept using bits of asm to get around Pascal's limitations. But once I learned C, I never looked back. C gives you most of the performance of asm along with most of the convenience of higher-level languages. (C++ is another level up, and you really shouldn't look at it as an either/or with asm.)

But without knowing asm, IMHO, you don't really understand computers.

---

### Post by sas on 2006-02-25
You don't need a PIC or anything to do assembly, you can just get nasm and the like out of the repos.

---

### Post by lcg on 2006-02-25
[QUOTE=grim918]I'm a beginner programmer, I mostly work with PHP, but now i want to learn something else. I want to learn Assembly but everyone that I know tells me that it will be a waste of time and that I should just learn C++.[/QUOTE]
Assembly is useful if you're interested in computer architecture and stuff like that. And if you want to learn about these things, I would **not** start with x86 assembly. Get "Computer Organisation" and "Computer Architecture -- A quantitative approach" by Hennessey and Patterson, a nice MIPS simulator and a month of free time and dig into it.

For everything else, I'd really recommend a decent high level language (and though a lot of people might disagree, I do not consider C++ decent, but that's a matter of opinion). Compilers take over the tedious and repetitive tasks a programmer has to face everyday. That's what they are built for.

HTH,
Lars

---

### Post by lcg on 2006-02-25
[QUOTE=endersshadow]Try [Lisp](http://en.wikipedia.org/wiki/Lisp_programming_language)!!  Just kidding, of course.[/QUOTE]
Actually, LISP (or Scheme) were and still are part of computer science at some universities. And the concepts and possibilities of functional programming are pretty cool, IMO. You probably don't use LISP or Scheme in the software engineering world, but the principles can be pretty useful (just like nobody speaks Latin nowadays, but the techniques you learn with it can be useful in a variety of fields).

Though both LISP and Scheme seem pretty strange at first, I can only recommend a class about functional programming (not for a beginner programmer, however).

Lars

---

### Post by narnian99 on 2006-02-25
I started out with BASIC and FORTRAN (hey I'm in my 40's now) and did a bit of Z80 and 6502 assembly, then on to C, Tcl, Perl.....

Assembly is nice, but I don't think it is really necessary for 99% of us.

What I think is much more useful - and which I never formerly trained in because I did  
Elec. Eng. and not Comp. Sci was things like structures and other formal constructs in computer programming. I'm thinking lists, and stacks, and trees, and things like that. And file organisation, and object-oriented abstractions.

As a hobbyist I eventually learned what these things are good for (mostly coding them myself in C). Then I learned to appreciate the things that higher level languages like Perl and the like had to offer.


And definitely learn to write little programs that talk to files and network sockets, and do timer alarms etc. You then appreciate what all the different bits that make up a running system need to do.

So yes they are techie things to learn - but I don't think assembly is necessary. (Much as you probably didn't need to know much about transistors when I started programming - though I did know quite a bit about them!!)

---

