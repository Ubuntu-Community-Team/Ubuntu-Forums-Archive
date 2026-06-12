---
title: "Assembly Language - int $0x80"
date: 2006-03-17
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2006-03-17
I am learning assembly language programming.  Here is the first program which does nothing but exits and returns 0.  

```

.section .data
.section .text
.globl _start
_start:
movl $1, %eax # this is the linux kernel command
                    # number (system call) for exiting
                    # a program
movl $0, %ebx # this is the status number we will
                    # return to the operating system.
                    # Change this around and it will
                    # return different things to
                    # echo $?
int $0x80        # this wakes up the kernel to run 
                    # the exit command

```

What is the significance of $0x80.  I mean why is only 0x80 is used as the interrupt number and why not any other number?

I am using the book Programming from the Ground Up which can be freely downloaded from here [http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf]("http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf")

---

### Post by PhairOh on 2006-03-17
Read page 27 of the book you posted (page 33 of the pdf).  It has your explanation.

---

### Post by rplantz on 2006-03-17
Or, as I've said in the book I'm writing: > 
    Calling a function that is embedded in the operating system is accomplished through a
special type of instruction sometimes called a &#8220;software interrupt.&#8221; The instruction itself
will be discussed in Section 15.3 (page 291), but it is easy to understand its use at this
point. The technique involves moving the arguments to speci&#64257;c registers, placing a special
code in the eax register, and then using the int $0x80 instruction to &#8220;call&#8221; a function in
the operating system. The operating system will perform the action speci&#64257;ed by the code
in the eax register, using the arguments passed in the other registers. The values required
for reading from and writing to &#64257;les are given in Table 7.2.
```

Table 7.2: Register set up for system calls to read or write.
      system call   eax   ebx             ecx                edx
      -----------   ---   ---             ---                ---
      read          3     &#64257;le descriptor  pointer to place   number of bytes
                                          to store bytes     to read
      write         4     &#64257;le descriptor  pointer to &#64257;rst    number of bytes
                                          byte to write      to write

```


---

### Post by vijayanand_sodadasi on 2006-03-18
Thanks for your replies.  
So the interrupt number 0x80 is linux specific right.  I mean if I were to write an assembly language program in DOS or some other OS for that matter, I must use the interrupt number specific to that operating system.  Am I correct?

Thanks again for your replies.
vijay

---

### Post by rplantz on 2006-03-18
[QUOTE=vijayanand_sodadasi]Thanks for your replies.  
So the interrupt number 0x80 is linux specific right.  I mean if I were to write an assembly language program in DOS or some other OS for that matter, I must use the interrupt number specific to that operating system.  Am I correct?

Thanks again for your replies.
vijay[/QUOTE]

Correct. When the OS is starting up is loads the interrupt vector table. You have to know which interrupt number to use for the particular OS. I've never programmed under DOS (by choice), but according to one of my assembly language books the vector number for output to the screen is 0x21.

---

### Post by LordHunter317 on 2006-03-19
Rather, the main DOS interrupt vector is 0x21.

---

### Post by runcoder_en on 2010-07-10
yes.
each os have different os soft interrupt.
especially assembly can't port easily!

---

### Post by texaswriter on 2010-07-10
> **runcoder_en said:**
> yes.
each os have different os soft interrupt.
especially assembly can't port easily!

I always wondered about the imagination of people when they speak of assembly like its a spent [insert spent item here]. 

Well, $OS_interrupt_vector would be a stand-in. OS portability solved. Took me a microsecond to think up and a few seconds to type up. 

The text editor could even have several $[ stand-ins]... so when you pushed $, a little menu popped up with the most used [followed by all the rest].... oooh!!!! dreamy!!! 

Not that I'm saying people should all go jump into assembly, but arbitrarily saying assembly can't port is just plain unimaginative. Any problem is itself its own solution, just in a different form. Even something as complicated as a rubics cube is its own solution. Just have to puzzle it out. 

:popcorn:

---

### Post by schauerlich on 2010-07-10
> **texaswriter said:**
> I always wondered about the imagination of people when they speak of assembly like its a spent [insert spent item here]. 

Well, $OS_interrupt_vector would be a stand-in. OS portability solved. Took me a microsecond to think up and a few seconds to type up. 

The text editor could even have several $[ stand-ins]... so when you pushed $, a little menu popped up with the most used [followed by all the rest].... oooh!!!! dreamy!!! 

Not that I'm saying people should all go jump into assembly, but arbitrarily saying assembly can't port is just plain unimaginative. Any problem is itself its own solution, just in a different form. Even something as complicated as a rubics cube is its own solution. Just have to puzzle it out. 

:popcorn:

That said, it's much easier to port a python program than an assembly program. Especially if you need it on your G5 Mac. :)

---

### Post by texaswriter on 2010-07-10
> **schauerlich said:**
> That said, it's much easier to port a python program than an assembly program. Especially if you need it on your G5 Mac. :)

I wouldn't doubt it. My intention was not so much to compare the portability of one language to another, but to say that assembly can be just as portable as any language. 

For example, you could even create an assembly language that used generic opcodes and then at compile time the compiler would insert actual registry names and use "macros" when a certain opcode wasn't supported, even allowing complex code to be ported to simpler platforms. The vast majority of computers going back [many many decades] all have the same families of basic opcodes [also called mnemonics]. Abstracting specific registers and implementations [memory registers, memory to register, register to memory, register to register, memory to memory, etc] could allow someone to use their own arbitrary set of registers. You could have an add this, that where this was a memory location and that was something else. If the intended platform didn't support adding memory locations, it would be translated to: ld register, memory address; ld register2, memory address; add register1, register2; and then another ld to put it in a memory address. NOTE: ld = mov; 

Not saying this is *how* it should be implemented, but it is one easy method that allows assembly code to be robust and platform independent.

---

### Post by schauerlich on 2010-07-10
Well then that's hardly assembly, more like meta-assembly. And it would be inefficient if you were moving between a many-registers machine and a limited registers machine. You'd have to be constantly swapping registers off the stack to keep up, to the point where you might as well just use C.

---

### Post by texaswriter on 2010-07-10
> **schauerlich said:**
> Well then that's hardly assembly, more like meta-assembly. And it would be inefficient if you were moving between a many-registers machine and a limited registers machine. You'd have to be constantly swapping registers off the stack to keep up, to the point where you might as well just use C.

Well, not really inefficient. You wouldn't set out to create it inefficient. BUT, if you took a program that relied on 20 registers and ported it to one with 6, yes you would be doing that [as the programmer]. And, no, this isn't any better than C. C would have the same machine limitations as any other language. 

This is not intended to make someone start programming in assembly or not in c... That is a red herring that I would ask you leave out of replies to my post. I am *not* trying to get people to program in assembly. 

I am simply responding to a post that someone had that essentially said that assembly isn't portable between OS [which would be even less portable by machines]... 

What this swapping would do is allow a program that otherwise doesn't have the register / mnemonic support on this process to run perfect, supposing someone a) made the "meta-language" as you say [which wouldn't actually have to be a meta language since the programmer could use the same set of registers he always uses, i.e. x86 or amd64,  or any combination thereof], b) make configuration files with the specific set of registers and mnemonics on specific platforms / os's, c) combine existing mnemonics on platforms with deficiencies to account for those in the regular platforms.

a) yes to have the compiler that did this you would have to actually write it. 

b) This would really be the meat of it and wouldn't be that hard to make per platform. 

c) Since this is assembly, most of the deficiency programming would be very easy. For example, for the add function that we did there, that is more or less code that would work fine. 

A note: OBVIOUSLY, it would be better to write specific code for a platform, but it wouldn't be too bad to arbitrarily assume [at the assembly level] that a program could run on any platform / os. When you load lots of external libraries, this can complicate things, but once again, if the makers of that library had, from the outset, assumed they were writing multi-platform code, these libraries would have been platform independent [or at least had specific optimizations per each platform].  

Examples of platform independent can be witnessed by what Wine has done to enable very large, complex applications to run seamlessly on any platform [essentially] that Linux / MacOS X runs. 


Anyways, my suggestions here does not amount to any comprehensive in a way that you would use it to resolve that such an idea is good or bad. If you are going to undertake a project, a very comprehensive and thorough evaluation would have to be made, carefully weighing all possibilities.

---

### Post by texaswriter on 2010-07-10
As an addendum, although this idea may not be *the best*, imagine if all libraries and programs **by default** ran on ANY platform imaginable because we used a robust architecture like this [REGARDLESS of the language you programmed in]. Or in other words, if all languages derived from C[just using my imagination], than anything derived from C would hypothetically run [or be easily portable to] any platform, supposing C was written in a way to be consistently cross-platform. It would take some doing to have all libraries and programming languages this way, but once done it would be effortless. 

THEN, let's say the default for a platform was less efficient, it would be a simple matter to tune certain libraries or implementations. [That's not to say it would be a simple matter...]

I think the JIT method of .net framework does this, but it's hard to say that MS would really try to support multiple platforms, especially ones that didn't run its current OS. 

It would be a better step for the community at large to take this stance to ensure its inclusion.

---

### Post by joshebosh on 2010-07-15
texaswriter,

     Do you code assembly? You strike me with a solid understanding of software. I've been trying off and on for a while to get a solid understanding of programming... I'm tired of scripting junk, and have recently connected the dots on compiling... Can do the helloworld trash but am trying desperately to plot a single pixel on the screen... I've searched the internet back and forth for an easy follow me instruction, but everbody either missing important steps, or overbloated books, or just snippets assuming you already know what they know that should've been coded before and after the snippet...

would you be able to provide a small simple .asm file that access the VGA and plot a single color pixel so i can study/manipulate the code?

I've got two books and 15 web pages i'm sifting through to try and put together this very steep assembly learning curve. And all i get is Segmentation Fault which i gdb to SIGSEGV, where i get lost... and some one out there knows how to sum this up for me in sentences unlike the others who spout encyclopedias... i'm looking for small working code to study concerning simple graphics in assembly... have you any pointers? 

Honestly i'm looking for a gray haired man whos ready to retire and data dump his life assembly experience on some young guy like me, eager and ready to help carry him into retirement... know of anyone?

---

### Post by slavik on 2010-07-15
> **joshebosh said:**
> texaswriter,

     Do you code assembly? You strike me with a solid understanding of software. I've been trying off and on for a while to get a solid understanding of programming... I'm tired of scripting junk, and have recently connected the dots on compiling... Can do the helloworld trash but am trying desperately to plot a single pixel on the screen... I've searched the internet back and forth for an easy follow me instruction, but everbody either missing important steps, or overbloated books, or just snippets assuming you already know what they know that should've been coded before and after the snippet...

would you be able to provide a small simple .asm file that access the VGA and plot a single color pixel so i can study/manipulate the code?

I've got two books and 15 web pages i'm sifting through to try and put together this very steep assembly learning curve. And all i get is Segmentation Fault which i gdb to SIGSEGV, where i get lost... and some one out there knows how to sum this up for me in sentences unlike the others who spout encyclopedias... i'm looking for small working code to study concerning simple graphics in assembly... have you any pointers? 

Honestly i'm looking for a gray haired man whos ready to retire and data dump his life assembly experience on some young guy like me, eager and ready to help carry him into retirement... know of anyone?
Have you looked at OpenGL?

[http://nehe.gamedev.net/lesson.asp?index=01](http://nehe.gamedev.net/lesson.asp?index=01)

---

### Post by joshebosh on 2010-07-16
thanks slavik for the recommendation, but i want assembly knowledge. I intend to eventually get into mobile OpenGL and other mobile 3D programming, but i need a solid understanding of assembly... but first, a little help to at least get me started in assembly graphics...

---

### Post by slavik on 2010-07-16
> **joshebosh said:**
> thanks slavik for the recommendation, but i want assembly knowledge. I intend to eventually get into mobile OpenGL and other mobile 3D programming, but i need a solid understanding of assembly... but first, a little help to at least get me started in assembly graphics...
mobile opengl is still opengl.

not sure what "other 3d programming" is meant by, but I don't think anyone wrote any graphics routines in assembly since 2000.

---

### Post by xb12x on 2010-07-16
> **texaswriter said:**
> 
For example, you could even create an assembly language that used generic opcodes and then at compile time the compiler would ...

Assembly language is NOT compiled. It's ASSEMBLED by an ASSEMBLER. That might be why it's called ASSEMBLY LANGUAGE.

> **texaswriter said:**
>  ... If the intended platform didn't support adding memory locations, it would be translated to: ld register, memory address; ld register2, memory address; add register1, register2; and then another ld to put it in a memory ...address

That already EXISTS. They're called COMPILERS.

---

### Post by joshebosh on 2010-07-17
> **slavik said:**
> mobile opengl is still opengl.

not sure what "other 3d programming" is meant by, but I don't think anyone wrote any graphics routines in assembly since 2000.


one comes to mind is the Java Micro Edition stuff... but who wrote those routines? where do i find them? google produce alot of stuff, but nothing solid... who knows anything about the int $0x80 and video B800 or 0A00 video access areas?

---

### Post by slavik on 2010-07-17
> **joshebosh said:**
> one comes to mind is the Java Micro Edition stuff... but who wrote those routines? where do i find them? google produce alot of stuff, but nothing solid... who knows anything about the int $0x80 and video B800 or 0A00 video access areas?
Well, if you want to write J2ME stuff, then write it, but if you actually want to go into assembly for ARM CPUs (as your post kind of implies) to figure out how J2ME works, that's a different story.

I suggest looking into the Android code repositories. :)

---

### Post by texaswriter on 2010-07-19
> **xb12x said:**
> Assembly language is NOT compiled. It's ASSEMBLED by an ASSEMBLER. That might be why it's called ASSEMBLY LANGUAGE.



That already EXISTS. They're called COMPILERS.

Quit being a troll. Read for content. The assembly language is a series of mnemonics that are stand ins for the actual codes sent off to the machine. In other words, they are the stand-ins for the binary executable code, containing opcodes and data. If you are trying to put semantics into the conversation, this is not necessary. Capital letters are also, generally speaking, not necessary. A compiler of any type can be said to translate human-readable [by some] code and translate it into some kind of object code or executable code. Beyond that, we can abstract any technical details. Assembled.... hrrm... Let's just call them compilers and be done with it... 

Joshebosh> Please understand I am talking that hypothetically such a compiler could exist. Because any higher level language is essentially just a method of using "stand-in" words to represent what will actually take place on the machine level, assembly code can be said to be a stand-in too. How much abstraction is all relative and besides the point. Needless to say, the actual assembly mnemonics haven't changed much in ages<<<<ages>>>.... So, although there will be varying degrees of extra sets of registers here or there, more or less, all platforms are going to be very similar. The differences of course will be when going to a smaller platform, say a mobile platform. Needless to say, the whole POINT of building your lowest level libraries to be arbitrarily multi-platform is that you can arbitrarily port any program / operating system to *any* platform. Perhaps the default port [which will *always* exist under such a system] may be less efficient than it can be, but it is far preferable to have a slightly slower but fully functional port than none at all. It is much easier to go into the base libraries and tweak this on the code level... really you wouldn't even need to do that. Just go into the compile options and register / mnemonic list / details file and make the necessary changes. Then, if inefficiency still abounds, you can play around with the libraries and higher level programs based on them... That is the real benefit to this. 

If you have read up on C# and what Mono and the .net framework does, this is essentially what I am talking about. .net is by no means multi-platform, but its structure is designed around jit and other compile options to take into consideration maximum performance and compatibility with a wide array of factors, including, but not limited to: os, hardware, library changes, patches,... etc Really, there isn't a limit. 

Abstracting this idea is where I get the idea for this universal assembly. At some level, you have to decide to build your basic libraries and operating systems on a relatively low level language, either assembly, C, or some combination of these and/or others. Because of this, base all your low level languages and the supporting libraries on universal code [even if it is NOT assembly], this way your everything is automagically multi-platform without regard to anything. Or in other words, if you invented a photon computer [just saying], and it performed operations like add, subtract, etc... move memory, pop push... you would instantly have all your programs on this computer the instant you created an assembly compiler for that architecture... You would layer your higher level assembly compiler on top of that OR your other higher level language compilers / libraries. Because those libraries would be based in your universal language [i.e. not coded to assembly in a specific architecture, just a generic assembly if you will], all that would be left to do is optimize this for the specific architecture. 

Voila really... All the trouble people are having porting this framework, this operating system, etc,... relates to failure to realize the abstraction model. Even if C is meant to be your lowest level high level language, abstract it.. Abstract the assembly its based on... Abstract everything, even if its a one to one relationship for most architectures... It's a virtual abstraction there, but the abstraction serves a purpose elsewhere. 

Anyways, this really gets long in the tooth... but that should help you see. Some companies and corporations will have short-term goals that would not benefit at all from this sort of abstraction, but, actually, in the long run it would benefit EVERYBODY related to computers, programming, etc... That includes mobile phone, pda, etc platforms as well. Now that the computing age has migrated to the mobile platform era, it will be a major benefit to developers to have a solid base of compatibility. 

I mean, look at how Apple basically cursed developers with the release of the ipad... They don't want ANY current programming language / interface but theirs to be used... plain and simple... Although highly ridiculous to developers, there is actually some good reason behind this: some of the programming platforms are highly inefficient and buggy... This implementation problem would not exist if all languages / libraries were based on a truly modular and abstracted universal platform that I described. The amount of resources out there would easily be able to handle any sort of streamlining of these libraries to the individual platform, instead of basically starting from scratch everytime one of "the big corporations" decides to reinvent the whole world of computing. 

Haha, but I used to program in assembly, but a long long time ago. I'm not a CS major, so I just program as a hobby... I was really attracted to C and have done most recent programming in this language. I've moved on to C#, especially C# and MonoDevelop [Mono obviously] as it allows me to make programs [even gui ones] fast and efficiently. This works well in my limited time. It will get to the point where I need to make a GUI program on a dime... Doing this otherwise entails alot [imo] and I would rather not mess with unnecessary details to accomplish the same task. 

If you want to get into assembly, find the communities. MASM has a great community... Try googling around for forums for all the different famous assembly compilers.. GASM, MASM, ...etc. Find the forums, even if its a windows platform... You might be surprised how much the MASM community might benefit you, even on Linux for example. 

So: 
1) Google the top 3-10 assemblers / compilers for ASM...

2) Google the top 5-10 forums / websites / communities for each one of the above assemblers

3) Peruse them and get a feel for the communities

4) Immerse yourself in the world of assembly. 

If you really want to do something like graphics in assembly, you are going to need to be a master at assembly of all kinds. I'd go on a serious assembly splurge, implement a few programs that represent a wide array of programming repertoire... I'm sure at one of the above websites you find you'll find the graphics programming resources you are after... 

Good luck... In another life I'd have chosen to be a CS major, and in that case I'd really pioneer the idea of assembly and an assembly language with extensive macro and library support. Actually if you really get good with MASM, you'd be surprised how macros can be used to program almost as fast as a higher level language... 

TBH, actually making an assembly compiler that would translate a program to virtually any platform isn't hard to come by... Some platforms would not support advanced graphics features or math features [etc] and would need extensive libraries written to support these missing opcodes [etc]... Other barriers would be proprietary hardware that may have incomplete documentation. This would be a major hindrance [especially for graphics programming]. To abstract this on the assembly level would be extremely difficult [eh, hehe, it would just be stand-in macros really that pointed to the real code for a specific graphics card]... Needless to say, higher level libraries for proprietary hardware [especially involved tasks like graphics processing] is much preferable in this regard... 

Really, my knowledge is quite general, so I will leave it to you to actually discover the specifics of all this on your own. If I had the time and chosen that as my major, it would be my passion, believe me. 

Keep me up to date of what you find and decide... pm, thread, etc...

---

### Post by texaswriter on 2010-07-19
Haha, I apologize for my long post... also, please consider these points in generall... I know, if taken too specifically, some things I say may not be exact... The general geist is my point.. Anything general has to be applied specifically, and it is at that point that these specifics should be worked out... I put enough details to make my general ideas concrete enough to realize, but not specific enough to be anywhere near the final realization... If that makes any sense to anybody at all. 

TIA

---

### Post by CptPicard on 2010-07-19
Umm... texaswriter, it seems to me like you're essentially talking about compilers and JIT-compiled languages, claiming the beginner should start with assembly anyway and then telling him to figure out the details... 

If one needs to work on a low-level, portable language, that is certainly C. The only real reason for hand-written assembly these days is either special hardware access or the rare case where you're actually getting a performance increase. You seem to voluntarily blow the efficiency argument out of the water; the C compiler will always be able to compile, in a general case, a more efficient cross-platform object from the C-level abstraction than a fixed asm-based object would be.

Mind you, your idea that higher-level languages are just collections of stand-in words for machine code blocks seems to be a typical misconception of low-level language programmers. Yes, the underlying stuff is deterministic so you get the execution of a specific set of instructions for some given piece of code, but higher-level language primitives really have a semantic meaning that is quite detached from the instructions that get run...

But anyway, have you looked at Forth? It probably comes closest to what you have in mind.

---

### Post by texaswriter on 2010-07-21
CptPicard> Okay, it seems you don't understand the premise of my post. If a software producer merely had to tell somebody in their company to compile their program for Linux and it was done just like that, any given piece of software would run JUST as efficiently on Linux, Mac, etc, as Windows because they are built on the same architecture. 

Since this scenario does not exist, therefore this is the premise [the starting point] of my post. Being that you cannot just say, compile it for any os, any platform, any architecture, is saying you do not have the existing infrastructure to do so. 

Therefore, to point to existing infrastructure is the incorrect way of going about it. 

You also may not have read a previous post in this thread where I said the starting ground did not have to be in assembly, it could be in any language you so chose, though one of the lower level HLA's would be preferable. C, assembly, Cpp, C#, Java... Any one of those would be idea because they rely on libraries, libraries which could be made platform independent. C#, to a great extent, makes writing GUI applications very similar cross-platform do to abstraction. If not as similar as one might hope, it abstracts alot of the details [especially with GTK] that get in the way. 

So, while I can appreciate your suggestions and opinion on the matter, because the problem that exists, a current implementation can not be said to be the end solution. 

A current implementation may be used as part of the solution, a tool in creating the solution, but it must be realized that a problem exists and that it needs to be transformed into a solution. 

Joshebosh> Have you taken any of those suggestions, looking for communities. It's a bag of worms to open, really, but if you are interested, you will definitely want to have a community(ies) to back up on.

---

### Post by texaswriter on 2010-07-21
> **CptPicard said:**
> Umm... texaswriter, it seems to me like you're essentially talking about compilers and JIT-compiled languages, claiming the beginner should start with assembly anyway and then telling him to figure out the details... 

If one needs to work on a low-level, portable language, that is certainly C. The only real reason for hand-written assembly these days is either special hardware access or the rare case where you're actually getting a performance increase. You seem to voluntarily blow the efficiency argument out of the water; the C compiler will always be able to compile, in a general case, a more efficient cross-platform object from the C-level abstraction than a fixed asm-based object would be.

Mind you, your idea that higher-level languages are just collections of stand-in words for machine code blocks seems to be a typical misconception of low-level language programmers. Yes, the underlying stuff is deterministic so you get the execution of a specific set of instructions for some given piece of code, but higher-level language primitives really have a semantic meaning that is quite detached from the instructions that get run...

But anyway, have you looked at Forth? It probably comes closest to what you have in mind.

Yes, you are correct here with higher level languages. The re-implementation of them is always going to be harder. But, these languages are typically written in C? I would have to imagine all the libraries are either rewritten in C# or in C... [or whatever the respective language we are talking about]. So, some work would be in order to actually port a high level language, but the world shouldn't be churning HLA that aren't getting used.. C, Cpp, C#, Java,... these are the most commonly used computer programming languages these days. If the world migrates to one more, that's fine... It probably means one of the old ones disappeared... Certainly, C# is probably the hardest language to port ever because it is based on the .NET framework, others are alot easier [imo]. I imagine C# was in fact easy to port, just as any other language, but the translation of the .NET framework by MONO has been the tedious process [still is]. 

It's kind of hard to imagine, simply because the makers of the operating systems have significant differences at the basic levels, but if one actually tried to make everything compatible, it would be a system... Like any complex and well-developed system, it would work like a beauty, constantly surprising you. 

When you try to do the opposite, it seems like a nightmare integrating anything. This is artificial however. 

That said, I'm comfortable writing programs in C and C# for Linux... These were just food for thought for people... Haha, rantings of a mad computer man!!!! Mwuhahahaha..... :D:KS:popcorn::p;):o

I'll look into Forth too... other languages are fun!! I'm currently in the process of getting as familiar in C# as I am in C... Rewriting one of my programs for a beginner challenge in C#...

---

### Post by trent.josephsen on 2010-07-21
> **texaswriter said:**
> If a software producer merely had to tell somebody in their company to compile their program for Linux and it was done just like that, any given piece of software would run JUST as efficiently on Linux, Mac, etc, as Windows because they are built on the same architecture.

This is not true.  Windows executables are constrained to work within the Windows operating system.  This means running on top of the Windows virtual machine, which may impose restrictions not native to the underlying architecture.  Similarly, Linux and other Unix-likes implement their own virtual machines, which impose restrictions of their own.  The sets of instructions available to Windows executables and those available to Linux x86 executables are necessarily different.  (I'm sure you know all this; please bear with me.)

What's more, the efficiency of most operations depend on their implementation within the OS and not only on the underlying architecture.  Memory models, for example, vary not only between Windows and Linux, but between different builds of the Linux kernel.  Furthermore, different operating systems impose security checks that may influence the efficiency of operations one way or another.  Finally, the number of processes running simultaneously and the amount of memory available also have impacts on program efficiency.  Your assumption that identical performance would be possible with the appropriate infrastructure would be true only if compiled programs contained pure machine opcodes (which mandates doing away with the OS entirely, and eliminates cross-architecture portability) or all operating systems were the same, in which case the argument becomes meaningless.

> Since this scenario does not exist, therefore this is the premise [the starting point] of my post. Being that you cannot just say, compile it for any os, any platform, any architecture, is saying you do not have the existing infrastructure to do so.

With the "equal efficiency" requirement, such an infrastructure cannot exist; it is logically self-contradictory.  Without the assumption that such an infrastructure is possible, your "solution" to what you consider a "problem" (assembly language being unportable) falls in ruins.

It is certainly possible to write a "pseudo-assembly" that operates on a virtual machine the way "real" assembly operates on a physical machine.  But because the virtual machine must be emulated (at compile time or runtime, it doesn't matter) on each platform, you will still get varying degrees of performance.

If you rescind the constraint of equal efficiency, then it's easy enough to construct a "portable assembly language" with a set of opcodes (bytecode) to match.  But that's been done, with the JVM and with Python and MIX and probably dozens of others; none of them have achieved use by more than a handful of HLLs.  How would what you propose be different from what has already been done?

---

### Post by texaswriter on 2010-07-22
Okay, bear with me. I have to pick this post apart a bit... 

> **trent.josephsen said:**
> This is not true.  Windows executables are constrained to work within the Windows operating system.  This means running on top of the Windows virtual machine, which may impose restrictions not native to the underlying architecture.  Similarly, Linux and other Unix-likes implement their own virtual machines, which impose restrictions of their own.  The sets of instructions available to Windows executables and those available to Linux x86 executables are necessarily different.  (I'm sure you know all this; please bear with me.)


If you really want to simplify it down, as in taking away all operating system calls, an executable is a block of memory loaded with assembly with an entry point and hopefully an exit point... With the most basic operating system, a program would simply be loaded into memory and jumped to the initial default starting position. The return position would return control to the os. 

This is the default.. This sort of executable would work and should work on any operating system on the same architecture. 

However, if this program makes operating system calls, *then* we reach a stage where you have to emulate *or* abstract this to get the program to run on another operating system. 

Also, most operating systems do more complicated things with memory and task routing [in a gui] environment. 

But at least understand that by default, an executable, barring external libraries and operating system calls [which would be in virtually all programs fwiw], is just a block of memory with a chunk of assembly with an entry point and exit point. 

The reason why i say this, if you abstract or emulate the operating system calls and the necessary libraries, you can have the program run anywhere you want it to. This is essentially what wine does... It runs the necessary processes [*.exe] to allow a windows executable to function, routing, emulating [etc] the necessary system calls to Linux ones. Because of how they do this, alot of programs actually run faster/better on Linux because you don't have the overhead that Windows has. That's besides the point, but it does show how easily a Windows program can be ran on top of the Linux os without having the whole Windows overhead. 

> **trent.josephsen said:**
> 
What's more, the efficiency of most operations depend on their implementation within the OS and not only on the underlying architecture.  Memory models, for example, vary not only between Windows and Linux, but between different builds of the Linux kernel.  Furthermore, different operating systems impose security checks that may influence the efficiency of operations one way or another.  Finally, the number of processes running simultaneously and the amount of memory available also have impacts on program efficiency.  Your assumption that identical performance would be possible with the appropriate infrastructure would be true only if compiled programs contained pure machine opcodes (which mandates doing away with the OS entirely, and eliminates cross-architecture portability) or all operating systems were the same, in which case the argument becomes meaningless.


Well, this is a bag of worms argument... no really way to agree one way or another. The best thing I can say is that programmers are really lazy. For example, it is possible to have a Linux gui that is more or less fully capable, but perhaps less snazzy, that can run *very fast* on a Pentium 2/3. A normal browser can run and you can install alot of software from even modern ubuntu repositories [and tons others]... Puppy Linux of course... However, throw Ubuntu on it or Debian [the latest version] and it runs fairly sluggish [pretty damn slow]... Can't even install the latest version of Windows. You can definitely install XP [almost 10 year old OS], but it will be as slow or slower than the latest version of Ubuntu/Debian. Now, these operating systems are basically performing the same function. 

Now I want to be clear about one thing... A window that encapsulates a program in a GUI environment is essentially doing the same things since Windows 95 [that's 15 years ago at least]. So, why is the basic environment requiring the latest processor to run just okay? Lazy programmers. 

So, yes, your implementations argument is true, but because of why? Are you going to blame a generality that I am making or the specific reason [that it is] of programmers and programming companies being lazy and / or just not giving a **** about performance. 

I mean, everytime I have *ever* talked to programmers [and programming instructors] about performance, I get a very stern look and : you shouldn't be concerned about performance.... haha, lolwut. oh... that explains a lot of things actually. 

> **trent.josephsen said:**
> 
With the "equal efficiency" requirement, such an infrastructure cannot exist; it is logically self-contradictory.  Without the assumption that such an infrastructure is possible, your "solution" to what you consider a "problem" (assembly language being unportable) falls in ruins.

It is certainly possible to write a "pseudo-assembly" that operates on a virtual machine the way "real" assembly operates on a physical machine.  But because the virtual machine must be emulated (at compile time or runtime, it doesn't matter) on each platform, you will still get varying degrees of performance.

If you rescind the constraint of equal efficiency, then it's easy enough to construct a "portable assembly language" with a set of opcodes (bytecode) to match.  But that's been done, with the JVM and with Python and MIX and probably dozens of others; none of them have achieved use by more than a handful of HLLs.  How would what you propose be different from what has already been done?

I can't really respond to the rest of the argument because it is based on faulty premises. 

I think I warned earlier about taking specific points with the argument.. I am speaking about general outlines... It would be like going into WWII... We are going to go to war in Europe... We are going to go to war in France... But the moment we decided to goto war in Europe or to goto war in France, we hadn't decided every bunker to take. That was something that was decided and resolved closer to the operation taking place. 

So, basically, to resummarize what I am saying to avoid unnecessary confusion: 

Problem: programs and libraries and frameworks are essentially not portable by default. Solution: Make programs, libraries, and frameworks portable by default. 

How do you do this? You lay the foundation for the solution, since different tracts of the problem need to be solved in different ways. This is going to be a multilateral solution for a multilateral problem. 

We are building a house. Lay a foundation, build the frame... put skin on it, windows, all the trimmings, then move the family in. Don't try to move the family in before you are done though. 

Ok, what's the foundation: whatever the programmers who make your core operating system, core libraries, core languages, core frameworks are programming in needs to be the starting point of your solution. If you say, this operating system, library, language, framework, *absolutely needs* to be on any and all architectures [even future ones], you write in a pseudo-language that can be identical to the most commonly used one [identical or very similar]. This pseudo-language would have such generics as $system_call <<--- the code for performing any os system call, varies per operating system. Instead of loading a specific value, a stand-in that would be replaced at compile time. 

Let's say you decide your basic language is C: You would abstract all OS specific features to code to the same things per operating system [which more or less works fine with say I/O]. This is the true purpose of abstraction. 

Either way, you choose some arbitrary point to be the point of abstraction [of OS/platform] and build that language, libraries, frameworks around it. 

It is easier starting at pseudo assembly because you can write everything, even the language libraries in it. 

Needless to say, there is nothing you can say one way or another about efficiency... It's goal is not for efficiency. It's goal is for portability of programs, the abstract view of a program, where programs represent programming: of os, libraries, frameworks, or just programs. Efficiency, even when a program is native, is something that has to be coded in. Haha, how efficient are FB apps... running such simple graphics that you could run it fine on computers so old you couldn't run modern os on it... yet these FB apps can lag modern processors. This is true!!! Efficiency: the flash plugin is made specifically for that operating system [and architecture] and the hardware is all modern... efficiency doesn't exist for this native program. You could go in C and still code the wrong way and have a program an order of magnitude or more slower than a better implementation.

Magic doesn't happen with programming, you have to work hard to get what you want... All this does is guarantee some ease of portability. For example, to get Windows applications running on Linux you have to emulate whatever .dll they depend on, etc. Had these .dll been written with the goal of being portable, it would be a much simpler fact to get them run natively. Perhaps you wouldn't even need WINE to run Windows applications, and vice versa. 

It is a logical fallacy to assume that because a program is written for a specific architecture and operating system that it is efficient. To furthermore assume that moving a program that is arbitrarily efficient on its native operating system is arbitrarily inefficient on any others is just as fallacious. By default, assembly code runs the same on any platform of the same architecture... How you translate the operating specific elements will always be an issue. How the programmer used or failed to use PADCV to program is always an issue [Planning, Analysis, Design, Coding, Verification]. These are points to be taken care of in a specific way. In a general way, we would not base our thinking on a specific point when we can not possibly have any idea about it. 

You would do this with the assumption that something would be done specifically [that was good] wherever specific issues existed. 

HTH

---

### Post by CptPicard on 2010-07-22
Hmm... I really don't know where to get a hold of your argument as your point seems very elusive and vague, but let's at least comment on a few specifics...

> **texaswriter said:**
> If a software producer merely had to tell somebody in their company to compile their program for Linux and it was done just like that, any given piece of software would run JUST as efficiently on Linux, Mac, etc, as Windows because they are built on the same architecture. 

Of course it doesn't work just like that, but library/OS incompatibilities nonwithstanding, after you've built some piece of software from source, one of the more important benefits you can derive is targeting the specific CPU architecture... here a language like C is useful, as register allocation etc is not fixed beforehand. The remaining incompatibility issues just need to be coded for, I see no way to get around those short of making use of a VM solution or alternatively this magical portability system you're talking of, which would require reimplementation of everything ;)

> 
Therefore, to point to existing infrastructure is the incorrect way of going about it. 

Reimplementing everything in a rather unclear way to achieve this does not sound feasible. I'd rather make use of the existing infrastructure to get the portability I can.

> C, assembly, Cpp, C#, Java... Any one of those would be idea because they rely on libraries, libraries which could be made platform independent.

Very broad range there. Hard to see how they could all ideal, especially considering that this was about portability of assembly to begin with.

> 
A current implementation may be used as part of the solution, a tool in creating the solution, but it must be realized that a problem exists and that it needs to be transformed into a solution.

IMO if a problem is ill-defined, over-broad ("not everything is completely portable") or does not have feasible possible solutions, it's not much of an interesting problem.


> **texaswriter said:**
> Yes, you are correct here with higher level languages. The re-implementation of them is always going to be harder. But, these languages are typically written in C?

That part does not really matter. For some reason I come across this idea every now and then that high-level language implementations are somehow reliant on C as a "host" language; of course the connection between language and implementation language is much more tenuous than people seem to imagine. As long as the toolkit is compiled somehow or runs on something, it does not really matter what it is.

> 
This is the default.. This sort of executable would work and should work on any operating system on the same architecture. 

I still don't quite understand why this would be so desirable. Portable binaries lose architecture-specificity and after all, the OS calls are there because we want to make use of the OS. And we use different OSes because, you know, horses for courses.

> That's besides the point, but it does show how easily a Windows program can be ran on top of the Linux os without having the whole Windows overhead. 

It's hardly "easy" -- Wine is a reimplementation of a lot of the Windows API, and it's still missing a lot of stuff. The Windows "overhead" is just the parts that are missing.

> 
Now I want to be clear about one thing... A window that encapsulates a program in a GUI environment is essentially doing the same things since Windows 95 [that's 15 years ago at least]. So, why is the basic environment requiring the latest processor to run just okay? Lazy programmers. 

Perhaps we should consider, though, the possibility that there's just more stuff running, instead of assuming that programmers got lazier and started being sloppy with the codebase? How are they lazy anyway?

> 
I mean, everytime I have *ever* talked to programmers [and programming instructors] about performance, I get a very stern look and : you shouldn't be concerned about performance.... haha, lolwut. oh... that explains a lot of things actually. 


Considering that you're a self-confessed hobbyist -- could you give me an idea of what you consider to be "performance"? I'm asking this because most of the time it turns out especially beginners assume that performance comes from hand-tuning assembly anywhere and everywhere so that they're not being "lazy".

It might be of use to consider why these programmers and instructors say what they do about this matter. It is probably not so much that performance does not matter, but that "premature optimization is the root of all evil". Correctness is the most important virtue in software, and good architecture is one, as well. The great majority of performance comes from correct algorithm selection and consistently avoiding the creation of major performance bottlenecks. When it comes to the low-level tuning, compilers pretty much always beat humans because of their consistency in applying the most beneficial transformations.

> 
If you say, this operating system, library, language, framework, *absolutely needs* to be on any and all architectures [even future ones], you write in a pseudo-language that can be identical to the most commonly used one [identical or very similar].

Or, alternatively, in a generally very portable language such as C, and write for portability. Or, use a language like Java that has a portable bytecode representation and a "machine" that is virtual in the sense of what you mostly seem to be talking about...

>  This pseudo-language would have such generics as $system_call <<--- the code for performing any os system call, varies per operating system. Instead of loading a specific value, a stand-in that would be replaced at compile time. 

This really is not doable; you're assuming this to be simpler than it is. It's not just the call's "name", but also its behaviour...

> 
Either way, you choose some arbitrary point to be the point of abstraction [of OS/platform] and build that language, libraries, frameworks around it. 

Sounds like you're just advocating a portable programming style in general.

> 
It is easier starting at pseudo assembly because you can write everything, even the language libraries in it. 

Why? Sounds like it would be harder to start with, and the reasons have been mentioned in this thread before. I can write the language libraries (depending on what you mean by them) in a lot of languages; most standard libraries of most languages are written in the language itself. Some languages can write their own compilers (not just C; any native-code generating language can do this, like Haskell).

> Efficiency, even when a program is native, is something that has to be coded in.

Well, there we're agreed. Efficiency begins with the algorithm selection.

> By default, assembly code runs the same on any platform of the same architecture...

Last time I checked, computation is deterministic, so under the same circumstances, any code runs the same under the same conditions...

---

### Post by trent.josephsen on 2010-07-22
At this point I'd like to repeat my earlier question:
> **trent.josephsen said:**
> How would what you propose be different from what has already been done?

Specifically, how would "portable assembly" be different from (for instance) assembly for the JVM?

> **texaswriter said:**
> Problem: programs and libraries and frameworks are essentially not portable by default. Solution: Make programs, libraries, and frameworks portable by default.

So... use a higher level language, and code portably, using cross-platform libraries.  Problem solved.

You seem to be advocating a solution to a problem that doesn't exist.  When people write portable code, their code will be portable "by default".  The "problem", if it can be called such, is lazy programmers -- not in the sense of performance, but in the sense of portability.  To use Python as an example, why use os.pathsep when / will do?

---

### Post by nvteighen on 2010-07-22
@texaswriter

I've been reading your posts and all I can conclude is that you don't know the history of programming. What you finally want is to recreate C... C was developed by Ritchie and folks because they needed the most portable language that could be translated to Assembly in a trivial way and losing the least possible amount of efficiency. The idea: make UNIX be as portable as possible at that time.

C is the perfect meta-Assembly or portable Assembly you want. It has been done and it works. C is non-portable when you add non-standard stuff to it, so it's not the language's "fault", but the coder's. Ok, you'll tell me that in order to have C be a portable you have to implement different assemblers and compilers for each platform. Yes, but that's the implementation, not the language.

What I want you to see is that programming languages are, principally, languages: symbolic systems that one can use to create some message encoding some cognitive content and communicate it (to the computer or to a fellow programmer). The C language is defined by its specs and you surely can write a C compiler in Java to compile C programs for the JVM... as long as the language is the same, no matter how it is implemented, it is C. Write C code on a paper, isn't that also C code?

My point is: while there can be non-portable C code, the C language is portable... but Assembly is non-portable in its own because it relies on something else in its very own definition: you define what Assembly is according to what platform you have. Write Assembly on a piece of paper? You'll have some Assembly code that no matter how much you avoid to use platform-specific stuff, it still will be bound to some platform.

Of course, you could write a higher-level programming language that looks like Assembly... but I hardly would call it Assembly. And even if you would call it like that, the concept will be completely different and still not equal to the other real Assembly languages there are.

---

### Post by texaswriter on 2010-07-23
Haha, people seem to be missing the point. 

It's just basically one standard, although implemented differently on different systems, would basically be the same all over... like .NET framework ~ Mono... Not that it has to be that specific... Something similar, whereby, hypothetically, everything was inter-operable.. On top of the libraries and other things that would be overarching, sufficient abstraction would take place to completely bury any system differences [for most programmers]... And, no, it doesn't matter what language you used... When abstracting, you would use a higher level language, but the actual coding to make the abstraction possible should be done with a lower level language [if that makes sense]. 

But anyways, this thread has gone too long... so, besides the above point, I'll return it to the original post I made: Shouldn't judge a language because of a [false] perception. Assembly is just as portable as any other... this fact is masquerade simply because not a lot of people program in it and are ignorant of what exists. Most people don't know assembly coders can use macros that can make their coding just as fast as any other language.

But this is, in general, true of any language...

---

### Post by JwB Zoofware on 2010-07-23
> **joshebosh said:**
> one comes to mind is the Java Micro Edition stuff... but who wrote those routines? where do i find them? google produce alot of stuff, but nothing solid... who knows anything about the int $0x80 and video B800 or 0A00 video access areas?

Basically those addresses are mapped directly into VGA memory; 0xb8000 is for text mode and the other is for 256 colour. 

To print a character to the screen in text mode you'd do something like:

```

unsigned char * p = (unsigned char *) 0xb8000;
*p++ = 'H';
*p++ = 0x7f;

```

which would put a H in the top left corner, however, as far as I know you can't do this from a user land program (hence the seg fault), and is only useful if you're writing an OS or doing some funky real mode DOS program.

"int 0x80" causes a CPU interrupt, which is a way for your program to request the kernel to do something. You can't call functions in the kernel directly as a running program is in userspace (ring 3 I think) and the kernel is running in kernel space (ring 0).

[http://en.wikipedia.org/wiki/System_call](http://en.wikipedia.org/wiki/System_call)

---

### Post by CptPicard on 2010-07-23
> **texaswriter said:**
> sufficient abstraction would take place to completely bury any system differences [for most programmers]...

Yes, it's been done, especially with Java/CLR. Nothing new in this idea.

> 
but the actual coding to make the abstraction possible should be done with a lower level language [if that makes sense].

Abstractions aren't really "made possible" by lower level languages; it's just that some languages are closer to the hardware in their abstraction than others, so in that sense, at some point, one will have to use one of them. But even their use isn't absolutely necessary; see the GHC Haskell compiler having been written in Haskell. Binary generation is a practical requirement, not a language abstraction-level issue.

> Shouldn't judge a language because of a [false] perception. Assembly is just as portable as any other... this fact is masquerade simply because not a lot of people program in it and are ignorant of what exists.

Such as? What does exist?

I'm sorry but I'm not really sure if you truly are in a position to judge other people's knowledgeability on this matter considering that this "asm is just as portable as any other" claim has been repeatedly countered here, as I see it.

>  Most people don't know assembly coders can use macros that can make their coding just as fast as any other language.

I thought this was about portability, not speed?

> But this is, in general, true of any language...

Macro systems are actually an interesting subject; it's not really true of all languages. Lisp's macros are a full language transformation system, for example, unlike anything else in any other language...

---

### Post by nvteighen on 2010-07-23
> **texaswriter said:**
> 
It's just basically one standard, although implemented differently on different systems, would basically be the same all over... like .NET framework ~ Mono... Not that it has to be that specific... Something similar, whereby, hypothetically, everything was inter-operable.. On top of the libraries and other things that would be overarching, sufficient abstraction would take place to completely bury any system differences [for most programmers]... And, no, it doesn't matter what language you used... When abstracting, you would use a higher level language, but the actual coding to make the abstraction possible should be done with a lower level language [if that makes sense].

But anyways, this thread has gone too long... so, besides the above point, I'll return it to the original post I made: Shouldn't judge a language because of a [false] perception. Assembly is just as portable as any other... this fact is masquerade simply because not a lot of people program in it and are ignorant of what exists. Most people don't know assembly coders can use macros that can make their coding just as fast as any other language.

But this is, in general, true of any language...

If you want a programming language that's totally interoperable, without any constraints of platform and that meanwhile can "completely bury" any system differences... there you have it: use portable code... Portable C or C++ code, Java or whatever... Of course I know that C isn't what you mean because you need to recompile the code for each platform, but the code will stay the same if you haven't use anything that's dependent on the platform... Ok, then take e.g. Lisp and try not to interface with the OS, which is the way non-portable stuff could "infect" your otherwise portable abstract program.

What I want you to know is that even the lowest level programming languages like C or C++ have a major difference with Assembly: Assembly is not quite a language... because it lacks symbolicity... Look, languages themselves are already abstractions (static ones, if you want) of reality... words are signs for some reality. Ok, what is Assembly? Just a mnemonic version of the CPU instruction set... its own definition makes it impossible to think of a "true" Assembly language without think in a certain platform. If x **is** absolutely equivalent to y, then x is not a sign for y, but y itself. Meanwhile, Perl, C, C++, Java, Forth (the lowest-level thing I know...), Lisp, Python, etc. can be understood and learned independently of the platform they run... any keyword or construct in C is a sign for an idea rather than a mnemonic for a specific CPU instruction.

Why? Again, you can implement something that runs C on the JVM... or on the SBCL Common Lisp VM... I know C is usually "translated" into Assembly, but that's not part of the definition of what C is. Ok, in the concrete case, C is usually implemented in the mnemonic code of Assembly which is far away from being symbolic.

Java/CLR is something of a different nature: what it achieves is nothing about portability (although they are portable), but about VM technology that avoids you to recompile stuff... because they had to recompile their VM for each platform. If that's what you want and not about the language-issue, what you are referring to is about JIT compilers, as someone already pointed out.

The thing is: always distinguish language and its implementation. The first one is what makes you code. The second is just the way the content of the code in some language happens to be executed by a computer... But again, you always can write your muffins recipe in Smalltalk-80 :P

And about perceptions... well, I agree, but you should show why the perception of Assembly being non-portable is false. You haven't. I have given a quite good reason in favor of the opposite idea, basing myself on the very definition of the language.

---

### Post by CptPicard on 2010-07-23
> **nvteighen said:**
> Ok, in the concrete case, C is usually implemented in the mnemonic code of Assembly which is far away from being symbolic

Well, actually, C as in the compiler is usually implemented in C :p

---

### Post by nvteighen on 2010-07-23
> **CptPicard said:**
> Well, actually, C as in the compiler is usually implemented in C :p

Hm... yeah... supress that sentence from my post. It's redundant.

---

### Post by worseisworser on 2010-07-23
I'm not sure I'm interested in this discussion (edit: too vague etc.), but on my daily browsing of the web I came about this; [http://www.coyotos.org/pipermail/bitc-dev/2010-March/001863.html](http://www.coyotos.org/pipermail/bitc-dev/2010-March/001863.html) .. and thought about this thread.

---

### Post by texaswriter on 2010-07-24
> **worseisworser said:**
> I'm not sure I'm interested in this discussion (edit: too vague etc.), but on my daily browsing of the web I came about this; [http://www.coyotos.org/pipermail/bitc-dev/2010-March/001863.html](http://www.coyotos.org/pipermail/bitc-dev/2010-March/001863.html) .. and thought about this thread.

hooray, an exact copy of this thread!!! 

now my work is done!!!:KS:popcorn::p;):D

---

### Post by CptPicard on 2010-07-24
As I see it, in that thread they are writing a compiler and discussing whether it outputs C or asm, and the outcome seems to be that they're going to write machine-dependent asm (not surprising, it being a compiler).

As much as compilers internally may use some sort of general asm solutions in the low-level code optimization and generation phase, I'm not sure what it has to do with the point of our thread... if there is a point, I'm not sure of that either :)

---

### Post by texaswriter on 2010-07-24
> **CptPicard said:**
> As I see it, in that thread they are writing a compiler and discussing whether it outputs C or asm, and the outcome seems to be that they're going to write machine-dependent asm (not surprising, it being a compiler).

As much as compilers internally may use some sort of general asm solutions in the low-level code optimization and generation phase, I'm not sure what it has to do with the point of our thread... if there is a point, I'm not sure of that either :)

Ok, this is where the  imagination comes in... 

Right, so they are saying: have an abstracted language like C, or above [C is abstracted btw, otherwise it would be as easy to learn as assembly, which is like building real-sized buildings out of lego pieces... can't get any easier]. 

Now, if you truly believe in abstraction, you abstract everything... That's just the way it is... If you believe in God, you don't just believe he can make wine from water... you believe everything... That's exactly how people should embrace abstraction. 

So, THEN, this abstract language gets translated to guess what: either another pseudo [read: abstracted] language OR goes to machine-dependent assembly. WHY? Why you say? BECAUSE: that's the point of pseudo-code: to eventually become actual code... That's the whole point. 

That *is* the point of it all. 

But yes, that was what I was kind of saying, but I'm just a lot more long-winded in doing so... 

See, C is mostly multi-platform/multiarchitecture, but try writing GUI... input output?... more abstraction please!!! What, C isn't the language to abstract you say: okay, jump to the next up language... abstract that to oblivion.... 

And *yes*, I do realize that all that abstraction has to be coded in, by someone, but what it means is people on one platform don't even have to think about coding for another platform... it *just works*. <<<--- NOTE: The corollary to life is that nothing ever just works until you have officially ripped all your hair out of your head.... but still!!!

AND, just because I know someone is going to say it: you can't say: "this is what already happens", because if you read for content here you understand that we mean ANY machine-dependent assembly.... not just a machine-dependent assembly. So, if you can't write *any* C language program [read omg any, seriously any] and compile it willy-nilly for any platform/os/architecture [that is commonly supported] without modifications, then you reallly can't say "this is what already  happens" and have truly read for content here...

---

### Post by nvteighen on 2010-07-24
> **texaswriter said:**
> Ok, this is where the  imagination comes in... 

Right, so they are saying: have an abstracted language like C, or above [C is abstracted btw, otherwise it would be as easy to learn as assembly, which is like building real-sized buildings out of lego pieces... can't get any easier]. 

Now, if you truly believe in abstraction, you abstract everything... That's just the way it is... If you believe in God, you don't just believe he can make wine from water... you believe everything... That's exactly how people should embrace abstraction. 

So, THEN, this abstract language gets translated to guess what: either another pseudo [read: abstracted] language OR goes to machine-dependent assembly. WHY? Why you say? BECAUSE: that's the point of pseudo-code: to eventually become actual code... That's the whole point. 

That *is* the point of it all. 

But yes, that was what I was kind of saying, but I'm just a lot more long-winded in doing so... 

See, C is mostly multi-platform/multiarchitecture, but try writing GUI... input output?... more abstraction please!!! What, C isn't the language to abstract you say: okay, jump to the next up language... abstract that to oblivion.... 

And *yes*, I do realize that all that abstraction has to be coded in, by someone, but what it means is people on one platform don't even have to think about coding for another platform... it *just works*. <<<--- NOTE: The corollary to life is that nothing ever just works until you have officially ripped all your hair out of your head.... but still!!!

AND, just because I know someone is going to say it: you can't say: "this is what already happens", because if you read for content here you understand that we mean ANY machine-dependent assembly.... not just a machine-dependent assembly. So, if you can't write *any* C language program [read omg any, seriously any] and compile it willy-nilly for any platform/os/architecture [that is commonly supported] without modifications, then you reallly can't say "this is what already  happens" and have truly read for content here...

I've had to read your post several time to understand what you meant. Really.

So, ok, from what I could get, it seems that to you, everything boils down to Assembly and that Assembly is the only real code there is. And that the rest is just pseudo-code or something that's abstracted but isn't quite what in your programming is real code. Also, you claim that kind of programming to be easier than C.

Well, it's a respectable opinion, but such an approach is completely impractical to be applied in the real world. First, Assembly may be simple, composed of exactly as much instructions as the platform's CPU has (ok, sometimes some Assembler macros...), but its built-in data structures (none... just byte lengths), means of combination (none, actually... you just play with contiguous memory chunks) and means of abstraction (labels...) are so poor that if you want to write something complex on it, you'll find yourself first implementing, say, struct's and procedures in order to have a mantainable construct.

It's not about real vs. "pseudo" code. In real world programming, what you need is stuff that allows you to do some task. And people just care about what the chosen language allows you to do and consider that language to be real code, because it is, of course. Yes, everything boils down to some native binary that sometimes you don't even see (e.g. Java, Python... what you see is a bytecode-compiled file...), but that's just an implementation detail. The concept of your code is written in whatever language you've chosen and all your work is going to happen there... that seems quite real to me (a hobbyist as you, IIRC) and I'm sure it's even more real for the guys who code for money. 

And why? Because those "abstracted" languages are the ones who give us building blocks much more suitable for projects in which, for example, we don't need/want to reimplement a resizable doubly-linked list or a garbage collector. Of course, sometimes one needs access to less abstracted stuff while also not wanting to reimplement really trivial but time-consuming things. There you might use languages like C (+ some powerful high-level library such as GLib), C++ or Objective-C... You know, one shouldn't write GUIs in C, but sometimes the conditions need you to have, for example, access to some library and you have to cope with C... Of course, if possible, you'll try to combine different languages and have multi-language projects combining C and Python or Tcl/Tk or whatever.

You seem to get CptPicard's, schauerlich's and my point on abstraction, but partially. Abstraction shouldn't be embraced. It's about how human mind works: we work with concepts and seek out ways to understand reality. In code we do the same, we just don't abstract and abstract blindly just because you can, you abstract as much as you need. And be aware that overabstraction is also a flaw the same as underabstraction... you can easily make some vital component inaccessible just because of the beautiful "black box" which you decided to throw it into.

What you want already exists: you want a language that you can compile into some sort of universal Assembly that works without any kind of modification nor recompilation in all platforms. The thing is that to have such a system working, you'd need to somehow declare a hardware and software standard that all vendors should be forced to use for all their products. That's the only way to have your idea working... Because having an "Universal Assembly" interpreter in all different platforms so that any binary could be used in any of them, would render your "Universal Assembly" to be a redundant layer over each platform's own Assembly/CPU opcodes... And having a unique software and hardware platform for absolutely *everything* apart from curtailing several personal freedoms, is highly impractical: can you expect a mobile phone be programmed exactly the same as a web server?

Just an advice: whenever you believe to have the ultimate evolution of programming history in mind, chances are 90% that you are wrong and that it somehow has already been tried (succesfully or unsuccesfully). This is why I always recommend people to learn not only how to program, but also the history of this craft.

---

### Post by texaswriter on 2010-07-25
Hehe, once again, bear with me... 

> **nvteighen said:**
> I've had to read your post several time to understand what you meant. Really.

Just as a comment to the above, I do think people should read and think about something more than once... Alot of people, esp. in this thread haven't taken the time [it seems] to read a post once... Don't get me wrong, all the opinions given here by all are worthy and show experience... definitely a valid angle from which to base an opinion. But still, if I try to render opinion on something, I try to give it as much thought as time allows. 

> **nvteighen said:**
> So, ok, from what I could get, it seems that to you, everything boils down to Assembly and that Assembly is the only real code there is. And that the rest is just pseudo-code or something that's abstracted but isn't quite what in your programming is real code. Also, you claim that kind of programming to be easier than C.

Well, what's the actuality [hrrm, reality] of it: everything does inevitably boil down to the assembly. But, as I keep saying, my whole idea does not pivot on the assembly... but understand that any abstraction *would*, by the very definition of how CPU's operate, hinge on assembly code... 

So, that's not so much *my* thing as just the reality of it... 

But yes, at some point, no matter what level, to make a truly multi-platform/architecture, you would have to account for the differences in those somehow and that would mean looking at the mnemonics/registers [and the associated deficiencies/strengths, speeds, etc]. 

> **nvteighen said:**
> Well, it's a respectable opinion, but such an approach is completely impractical to be applied in the real world. First, Assembly may be simple, composed of exactly as much instructions as the platform's CPU has (ok, sometimes some Assembler macros...), but its built-in data structures (none... just byte lengths), means of combination (none, actually... you just play with contiguous memory chunks) and means of abstraction (labels...) are so poor that if you want to write something complex on it, you'll find yourself first implementing, say, struct's and procedures in order to have a mantainable construct.

Well, ok, in the real world people don't mostly program in C... right? Going forward this is going to be even moreso true... If you look at the world of assembly, even *less* people program in that. So, the impracticality of this has little weight... Programmers already live in an abstracted world... So we aren't forcing anybody to go back a bit... 

Anything that is done is done by a few for the many...

> **nvteighen said:**
> It's not about real vs. "pseudo" code. In real world programming, what you need is stuff that allows you to do some task. And people just care about what the chosen language allows you to do and consider that language to be real code, because it is, of course. Yes, everything boils down to some native binary that sometimes you don't even see (e.g. Java, Python... what you see is a bytecode-compiled file...), but that's just an implementation detail. The concept of your code is written in whatever language you've chosen and all your work is going to happen there... that seems quite real to me (a hobbyist as you, IIRC) and I'm sure it's even more real for the guys who code for money. 

Well, ok, pseudo code was a bit of a general term...prolly not specific in what I meant... What I meant to say was, thinking of how much you abstract things, you can look at it as pseudo code compared to what is actually taking place [ala macro] by your language... E.g., making a list that accepts more members and allows you to search: your language *should* be implementing a hash routine... which means using some prime number scheme... which means making a hash table,... which means redoing the hash table everytime its resized [or sometimes at least]... which would mean rehashing your table... So, even when this is called abstraction, it can be thought of as pseudo code... People don't think of it anymore... but that used to be something you had to program in...

As far as I am concerned, it is both an abstraction and pseudo code: basically in your outline it would say: make searchable / resizable array named holdThis... so yeah, the lines of code [in some languages] aren't much bigger than that, depends on what language you look at... 

Tell me that isn't pseudo code. 

But I do want to point out, I *do* see what everybody is saying about alot of languages already being there... And what I keep trying to point out is: despite this, the system still needs more of this... And it's not much one or two programmers can do... the whole world has to get the idea of this... Software and standards can't stay in a state of proprietary... Needs will always be shifting enough for plenty of programmers to be in business... Nobody has to think their software and companies aren't going to be needed. 

I mean, look how many Linux distro's exist... popular opinion will still exist that MS Windows or Mac OS X are worth paying money for... 

> **nvteighen said:**
> And why? Because those "abstracted" languages are the ones who give us building blocks much more suitable for projects in which, for example, we don't need/want to reimplement a resizable doubly-linked list or a garbage collector. Of course, sometimes one needs access to less abstracted stuff while also not wanting to reimplement really trivial but time-consuming things. There you might use languages like C (+ some powerful high-level library such as GLib), C++ or Objective-C... You know, one shouldn't write GUIs in C, but sometimes the conditions need you to have, for example, access to some library and you have to cope with C... Of course, if possible, you'll try to combine different languages and have multi-language projects combining C and Python or Tcl/Tk or whatever.

I think this is a misunderstanding... Abstraction means the HLA's stay the same... nothing changes... Remember this: the few work hard for the many... [or so the many don't have to]... 

BTW: I like ellipsis' --->>> ... 

So, yes, some libraries would have to be ported individually... *but*, if you really did a good job in an organization that managed and maintained this stuff, it would be in a format whereby you didn't... At some point you could use modularity to your advantage to shuffle to one section of code such highly machine dependent parts of something like memory management, that the other modules still would apply to virtually any memory... Just needs clever imagination and thought. 

Or in other words... if instead of compiling C programs, you wrote them to a pseudo-assembly: you make machine dependent versions of these... you can choose the parameters of any conversions... and if need be play around with the code for custom optimizations... <<<--- but don't say this isn't possible or practical... Since all C programs, which is virtually all your basic things [in Linux anyways], can be sent to assembly, this is easy to be made to convert this to pseudo-assembly... 

You would just arbitrarily declare *standard*, current, practised assembly [on either 32-bit or 64bit platform] to be the standard, define your flavors, per any and all CPU combinations, platform combinations, etc... and set your configuration files to reflect the mnemonics and registers of these... 

It really isn't that hard of a concept to get... I completely don't understand the resistance to this idea... It's so easy, I could do it even... Seriously, it's just a command line option to GCC to output the assembly... how hard is it going to be to make a program to parse those and compare registers / mnemonics to ones in a pre-formatted configuration file... Generate a report of differences, calculate [from pre-tabulated data] the likely performance change of a port + any deficiencies... For example, if you translated a program that used floating point math, i.e. depended on hardware-supported fp math, you could code [or have pre-built] code that did this and returned the appropriate format number... 

You would scale the performance of the origin machine to the destination.. for example if a function in the program was calculated to be x amount of clock cycles on origin machine, and y amount of clock cycles on destination machine, through looking at many aspects / functions of the program, it could be said that the program, on average, would become y times slower/faster by porting... So, you would then weight any performance changes by necessary code substitution [etc] with these figures... 

This way, if you were porting something time-specific, you would know instantly, by looking at this data whether the program's performance would be acceptable. If not: fail [if the program cannot be made to run acceptably], retry [scaling back the program's requirements], or continue anyways [knowing the facts and just deciding to accept the performance hit]. 

So once again, the very basic levels of this, given time, I could do... but really, the whole community of programmers would need to adopt and implement.  

> **nvteighen said:**
> You seem to get CptPicard's, schauerlich's and my point on abstraction, but partially. Abstraction shouldn't be embraced. It's about how human mind works: we work with concepts and seek out ways to understand reality. In code we do the same, we just don't abstract and abstract blindly just because you can, you abstract as much as you need. And be aware that overabstraction is also a flaw the same as underabstraction... you can easily make some vital component inaccessible just because of the beautiful "black box" which you decided to throw it into.

Yes, abstraction is nice.. C# and Java have these beautiful things called classes... I don't know how well C# supports overloading operators [if at all]... but, if I am not mistaken, overloading an operator is when you don't give it enough information... or give it the wrong type... I really haven't used this... but essentially, defaulting to certain "common" or "default" values for variables or basic tasks can be used, and members of classes can be called or more information/variables passed to perform more complex tasks. 

But, otherwise, yes, anything can be done over or under... I agree with this... 

See, I believe in giving people enough rope for them to be able to hang themselves in.. why? it teaches people restraint... get burnt by this enough and sooner or later you learn to restrain yourself... 

What do I mean: I would really like to be able to go into an open format type of object browser and put together a window.. now any gui that I have ever seen as all the same type of elements... plain and simple.. this is true... Which means, if I make a window with six buttons and some text boxes... that open format should be just as valid to be programmed into on Windows as on Linux as on Mac... <<<--- there is no contradiction to this... this is my wish... 

Is this so much to ask for? Visual Studio probably has the best version of a window editor... you drag and drop.. double click on stuff to write code for it... all the options are there... simple... 

Other platforms have things similar, but not nearly this simple... [that i have seen]

Right, well that's just one example of abstraction. I don't care about the actuality resulting in that.. like i've said before, programming in GTK in C is a ridiculous mess.. I get that it's probably got a lot of power, but still: I gave up on C once I saw how hard it was going to be... too much... plain and simple. 

You should be able to do something like that... but, yes, there might be a time when you want to do something more specific, even something specific to one architecture or os [etc]... There shouldn't be total barriers to this sort of thing. This can be accounted for down the line as is necessary. 

> **nvteighen said:**
>  What you want already exists: you want a language that you can compile into some sort of universal Assembly that works without any kind of modification nor recompilation in all platforms. The thing is that to have such a system working, you'd need to somehow declare a hardware and software standard that all vendors should be forced to use for all their products. That's the only way to have your idea working... Because having an "Universal Assembly" interpreter in all different platforms so that any binary could be used in any of them, would render your "Universal Assembly" to be a redundant layer over each platform's own Assembly/CPU opcodes... And having a unique software and hardware platform for absolutely *everything* apart from curtailing several personal freedoms, is highly impractical: can you expect a mobile phone be programmed exactly the same as a web server?

Hrrm, I kind of handled osme of this stuff later... but I don't really like your web server analogy.. 

First off, going from a web server to a mobile phone platform would be done with great caution, as the performance difference between the two are significant [extreme]... That would be the exception... still, the abstraction model works... Abstract [on some level] enough functions to account for these differences. 

Maybe on one level you use pseudo-assembly [which, btw, wouldn't have to be any different from regular assembly on the defacto platform], another you rewrite entire libraries specific for an architecture/platform [but understand that higher level languages wouldn't {or shouldn't} notice much difference...], on another level you account for irreconcilable diferences by outlining "crucial platform differences"... For example, don't expect the most modern FPS game to run on an ipad unless you drastically tune down the graphics requirements... To do that, perhaps, you might have to change the graphics rendering model... So, some things can't be ported to certain platforms. 

What about graphics: should programmers really be programming in a way to account for specific proprietary hardware: should they have to... the answer is no... that is ridiculous to expect game programmers to account for all the hardware... <<<love them ellipsis'>>>> 

Something open format, like DirectX, or OpenGl [haha at DirectX = open format, yeah right] needs to account for anything that most programmers need to account for... The rest: let hardware manufacturers account for... Since an Nvidia xfx isn't made for an ipad... you could write opengl apps, and so long as opengl existed on an ipad, you could expect your program to translate reasonably well... <<<<understand that the normal glut of Murphy and Murphy-like laws still apply>>> 

> **nvteighen said:**
> Just an advice: whenever you believe to have the ultimate evolution of programming history in mind, chances are 90% that you are wrong and that it somehow has already been tried (succesfully or unsuccesfully). This is why I always recommend people to learn not only how to program, but also the history of this craft.

Well, it might be a logical fallacy [or two] to automatically assume that, but I do agree that even well intentioned plans can end badly. 

I really don't mean this thread to keep going on like this... 

But, I do like my ideas to be clear to others when they are clear in my head... 

It really isn't a hard idea, even simpler to start to implement... To actually test and perfect, and inevitably convert the whole world: that's the hard part. 

But seriously, if a bunch of programmers can't see the benefit of it,... this idea doesn't stand a chance in hell. teehee!!!!:tongue:

---

### Post by slavik on 2010-07-25
I think your argument boils down to understanding the layer below which you program. That and C is one such assembly standard. As soon as you leave pure assembly, your language will need to be compiled (since your standard has to be translated to the target architecture).

---

### Post by worseisworser on 2010-07-25
> **texaswriter said:**
> hooray, an exact copy of this thread!!! 

now my work is done!!!:KS:popcorn::p;):D

Well, not quite; I actually understand what's being said in that thread. :?

Ok, I do not see how this generic idea you talk about is different from what several other portable VMs out there do or can do.

The portable assembly is Java bytecodes for the JVM, CIL for .Net/Mono(#1) or the IR for the LLVM -- and one can translate Java bytecodes to CIL using IKVM, for instance. Also see VMKIT.

I think what nvteigen says at the end about looking at what's out there already, and history, is a good idea. You might not be "wrong" though, but you're probably talking (vaguely) about things that already exist; perhaps for a long time (even 1960s perhaps); and/or things people already are working on and perhaps even have been for a long time.


[INDENT]#1: One might argue how portable .Net/Mono really is being *based on* a closed implementation, but ok.[/INDENT]

---

### Post by StephenF on 2010-07-25
Far better to have a fully programmable instruction set around a RISC core. Sort of how CPUs are architected today only more so. If this could be fully context switched for each process so much the better.

I would take your idea to a chip designer as the software implementation would be horribly slow on account of the concrete nature of assembly language being somehow reworked for a different instruction set. There are too many registers to keep account for in my opinion so the chances are the stack will be used heavily making a mockery of register allocation. Note how the register keyword in C is heavily discouraged? Well if you are coding pseudo assembly you'll be effectively doing that virtually all of the time.

---

### Post by schauerlich on 2010-07-25
> **worseisworser said:**
> Ok, I do not see how this generic idea you talk about is different from what several other portable VMs out there do or can do.

The portable assembly is Java bytecodes for the JVM, CIL for .Net/Mono(#1) or the IR for the LLVM -- and one can translate Java bytecodes to CIL using IKVM, for instance.

+1. What he's talking about already exists, it's called a virtual machine. [http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)

---

### Post by nvteighen on 2010-07-25
Ok, I'll try to reply just to what I consider to be the key issues involved in this discussion... in an attempt to reduce the post's length :P

> **texaswriter said:**
> 
Well, ok, pseudo code was a bit of a general term...prolly not specific in what I meant... What I meant to say was, thinking of how much you abstract things, you can look at it as pseudo code compared to what is actually taking place [ala macro] by your language... E.g., making a list that accepts more members and allows you to search: your language *should* be implementing a hash routine... which means using some prime number scheme... which means making a hash table,... which means redoing the hash table everytime its resized [or sometimes at least]... which would mean rehashing your table... So, even when this is called abstraction, it can be thought of as pseudo code... People don't think of it anymore... but that used to be something you had to program in...

As far as I am concerned, it is both an abstraction and pseudo code: basically in your outline it would say: make searchable / resizable array named holdThis... so yeah, the lines of code [in some languages] aren't much bigger than that, depends on what language you look at... 

Tell me that isn't pseudo code. 

But I do want to point out, I *do* see what everybody is saying about alot of languages already being there... And what I keep trying to point out is: despite this, the system still needs more of this... And it's not much one or two programmers can do... the whole world has to get the idea of this... Software and standards can't stay in a state of proprietary... Needs will always be shifting enough for plenty of programmers to be in business... Nobody has to think their software and companies aren't going to be needed. 

I mean, look how many Linux distro's exist... popular opinion will still exist that MS Windows or Mac OS X are worth paying money for... 


Ok, we both agree in that good programming means to abstract stuff. Perfect: for example, if I coded a player in some RPG using several of separate global variables instead of using a "Player" class, you'd be right if you told me that I'm a bad programmer.

What I don't get is why you consider abstraction to be worthy and, simultaneously, something "less real" (to avoid the "pseudocode" name and concentrate on the concept) than Assembly. I sense you consider abstraction more or less "a necessary evil" that somehow "obscures" what really is going on. You recognize it's necessary for practical reasons, but you still seem to operate on the base that the implementation is what really is.

But really, the point of abstracting things is exactly the opposite: is to focus on the specifics of your specific problem without caring of stuff that's already been solved for you.  Why bother about how a 3D rendering library draws a cube when all you want is to code a game... if the library does it well, you just go and write what your game is about and not how to draw cubes... Do you get my point?

> 
So, yes, some libraries would have to be ported individually... *but*, if you really did a good job in an organization that managed and maintained this stuff, it would be in a format whereby you didn't... At some point you could use modularity to your advantage to shuffle to one section of code such highly machine dependent parts of something like memory management, that the other modules still would apply to virtually any memory... Just needs clever imagination and thought. 

Or in other words... if instead of compiling C programs, you wrote them to a pseudo-assembly: you make machine dependent versions of these... you can choose the parameters of any conversions... and if need be play around with the code for custom optimizations... <<<--- but don't say this isn't possible or practical... Since all C programs, which is virtually all your basic things [in Linux anyways], can be sent to assembly, this is easy to be made to convert this to pseudo-assembly... 

You would just arbitrarily declare *standard*, current, practised assembly [on either 32-bit or 64bit platform] to be the standard, define your flavors, per any and all CPU combinations, platform combinations, etc... and set your configuration files to reflect the mnemonics and registers of these... 

It really isn't that hard of a concept to get... I completely don't understand the resistance to this idea... It's so easy, I could do it even... Seriously, it's just a command line option to GCC to output the assembly... how hard is it going to be to make a program to parse those and compare registers / mnemonics to ones in a pre-formatted configuration file... Generate a report of differences, calculate [from pre-tabulated data] the likely performance change of a port + any deficiencies... For example, if you translated a program that used floating point math, i.e. depended on hardware-supported fp math, you could code [or have pre-built] code that did this and returned the appropriate format number... 

You would scale the performance of the origin machine to the destination.. for example if a function in the program was calculated to be x amount of clock cycles on origin machine, and y amount of clock cycles on destination machine, through looking at many aspects / functions of the program, it could be said that the program, on average, would become y times slower/faster by porting... So, you would then weight any performance changes by necessary code substitution [etc] with these figures... 

This way, if you were porting something time-specific, you would know instantly, by looking at this data whether the program's performance would be acceptable. If not: fail [if the program cannot be made to run acceptably], retry [scaling back the program's requirements], or continue anyways [knowing the facts and just deciding to accept the performance hit]. 

So once again, the very basic levels of this, given time, I could do... but really, the whole community of programmers would need to adopt and implement.  


First. I'm sorry to tell you that there's no standard Assembly... actually, there's not even a formal definition for it. And as Linus said that we should show code instead of just talking, look at this:

```

;; Linux x86 NASM Assembly

section .data
        hello db "hello!", 10
        hello_len equ $ - hello

section .text
        global _start

_start:  
        mov eax, 4
        mov ebx, 1
        mov ecx, hello
        mov edx, hello_len
        int 0x80

        mov eax, 1
        mov ebx, 0
        int 0x80

```

This program is written in NASM (first "issue": you know in GNU/Linux you have two main Assembly languages... both with radically different syntax... but ok, syntax is not what makes a language). But it's specifically: **Linux x86 32-bit NASM Assembly**... Try to assemble this in Windows, even with NASM (not sure if ported) and you'll get issues with **int 0x80**... Why? Because while in DOS/Windows Assembly (btw, IIRC, DOS/Windows Assembly now runs under a kind of emulation system...) uses various BIOS interrupts to call the syscalls, Linux just uses a centralized interrupt to do the job... IIRC, in DOS you'd have used **int 0x21** for output... and of course, using registers in a completely different way...

But wait... not even Linux x86 32-bit Assembly is a uniform thing... We've got GAS Assembly, which has some differences with NASM:
```

;; Linux x86 32-bit GAS Assembly

.section .data
hello:
        .ascii "hello!\n"

hello_len:
        .set HELLO_SIZE, hello_len - hello
        
.section .text
        .globl _start
        
_start:
        mov $4, %eax
        mov $1, %ebx
        mov $hello, %ecx
        mov $HELLO_SIZE, %edx
        int $0x80

        mov $1, %eax
        mov $0, %ebx
        int $0x80

```

Yes, both versions assemble to the same binary code... but... ok, this is something to take account of.

And then, you've got embedded devices, where even the amount of registers is different... different kernels (or none)... etc...

So, ok, let's choose a standard... what should you choose? That's why I told you my web server vs. mobile phone analogy... Ok, you may have a Universal Assembly (ok, let it be with Lisp syntax), but in the end, as soon as you want to access the platform, you'll need a platform-specific language, thus rendering your Universal Assembly to be like  either some sort of C with different syntax and therefore something completely redundant or just a redundant layer of abstraction that adds nothing in between platform-specific Assembly and whatever language is being used for the system-specific stuff (in GNU/Linux, it's C... in OS X, Objective-C... in a Lisp machine, Lisp).

Ok, you could always force people to stick one single platform... but... uh... you'd need to be some kind of dictator or something to achieve that.

> 
Yes, abstraction is nice.. C# and Java have these beautiful things called classes... I don't know how well C# supports overloading operators [if at all]... but, if I am not mistaken, overloading an operator is when you don't give it enough information... or give it the wrong type... I really haven't used this... but essentially, defaulting to certain "common" or "default" values for variables or basic tasks can be used, and members of classes can be called or more information/variables passed to perform more complex tasks. 

But, otherwise, yes, anything can be done over or under... I agree with this...
 

I talked about "overabstraction", not "operator overloading". What I meant with that is for example, this:

```

def vector_dot_product_and_print(vector1, vector2):
    # Assume vector1 and vector2 are two instances of a class Vector that has
    # two attributes x and y.

    result = vector1.x * vector2.x + vector1.y * vector2.y

    print("Result is: %d" % result)

```

That code is overabstracted because it assumes too much... and therefore it also hides too much: it assumes that there's a single conceptual object consisting in taking the dot-product of exactly two 2D vectors and then printing it to standard output exactly as "Result is: ...". But, if later you happen to just want to take the dot-product of two vectors without printing them, this function is useless and you'd have to reimplement that operation even though it's already implemented here... but, as it has been placed in a "black box", you just can't take it out from there... A correctly abstracted piece of code might have been:

```

def vector_dot_product(vector1, vector2):
    # Assume vector1 and vector2 are two instances of a class Vector that has
    # two attributes x and y.

    return vector1.x * vector2.x + vector1.y * vector2.y

def vector_print_result(message, result):
    # Taking message also as an argument may be a bit extreme.

    print(message % result)

# How these are combined is up to the developer... but now nothing prevents you
# to use ncurses to show the message... without reimplementing
# vector_do_product... just not use vector_print_result, for example.

```

My point with this is that abstraction is just about abstracting everything. The mistake in the first snippet is exactly assuming that your abstraction level is higher than you might really need.

Your Universal Assembly, IMO, suffers from that same mistake: if you consider it as a replacement for Assembly... you may get into hiding vital components and prevent people to do smart things. The only way to avoid that is to *add* that Universal ASM to the system without eliminating ASM... for no benefit, because you already have other languages doing that very same thing.

Unless of course you're talking about a Virtual Machine... then, you'd need something like that. But creating a Universal VM on which every platform in the world should be run seems to be a really bad idea... you know: needs are completely different in different platforms.
 
> 
What do I mean: I would really like to be able to go into an open format type of object browser and put together a window.. now any gui that I have ever seen as all the same type of elements... plain and simple.. this is true... Which means, if I make a window with six buttons and some text boxes... that open format should be just as valid to be programmed into on Windows as on Linux as on Mac... <<<--- there is no contradiction to this... this is my wish... 

Is this so much to ask for? Visual Studio probably has the best version of a window editor... you drag and drop.. double click on stuff to write code for it... all the options are there... simple... 

Other platforms have things similar, but not nearly this simple... [that i have seen]

Right, well that's just one example of abstraction. I don't care about the actuality resulting in that.. like i've said before, programming in GTK in C is a ridiculous mess.. I get that it's probably got a lot of power, but still: I gave up on C once I saw how hard it was going to be... too much... plain and simple. 

You should be able to do something like that... but, yes, there might be a time when you want to do something more specific, even something specific to one architecture or os [etc]... There shouldn't be total barriers to this sort of thing. This can be accounted for down the line as is necessary. 


Well... there's a GUI library that works in several platforms and is called Nokia/Trolltech's Qt.

Anyway, as far as I understand your idea, the arguments of above apply to your GUI example as well.

(btw: C GTK+ can be done orderly if you stick to some techniques... but it's quite hard to do, I agree... Well, C itself is hard to use, exactly for the same reasons as Assembly: it's a language with very sparse built-in resources).

> 
Hrrm, I kind of handled osme of this stuff later... but I don't really like your web server analogy.. 

First off, going from a web server to a mobile phone platform would be done with great caution, as the performance difference between the two are significant [extreme]... That would be the exception... still, the abstraction model works... Abstract [on some level] enough functions to account for these differences. 

Maybe on one level you use pseudo-assembly [which, btw, wouldn't have to be any different from regular assembly on the defacto platform], another you rewrite entire libraries specific for an architecture/platform [but understand that higher level languages wouldn't {or shouldn't} notice much difference...], on another level you account for irreconcilable diferences by outlining "crucial platform differences"... For example, don't expect the most modern FPS game to run on an ipad unless you drastically tune down the graphics requirements... To do that, perhaps, you might have to change the graphics rendering model... So, some things can't be ported to certain platforms. 

What about graphics: should programmers really be programming in a way to account for specific proprietary hardware: should they have to... the answer is no... that is ridiculous to expect game programmers to account for all the hardware... <<<love them ellipsis'>>>> 

Something open format, like DirectX, or OpenGl [haha at DirectX = open format, yeah right] needs to account for anything that most programmers need to account for... The rest: let hardware manufacturers account for... Since an Nvidia xfx isn't made for an ipad... you could write opengl apps, and so long as opengl existed on an ipad, you could expect your program to translate reasonably well... <<<<understand that the normal glut of Murphy and Murphy-like laws still apply>>> 


Well, then you get my point. Platform-differences can be/are impossible to abstract into a common base... and how would you do that? Again, you'd face the issue by leaving the real platform-specific Assembly there and have a redundant Universal Assembly on top of it... because what that hypothetical Universal Assembly will be used for will be exactly what C and C++ already do in modern OSes.


> 
It really isn't a hard idea, even simpler to start to implement... To actually test and perfect, and inevitably convert the whole world: that's the hard part. 


Ok, then do it. No, don't take this offensively, I'm being quite serious: if you're sure that you're right, at the end, the best way to show us we're wrong is to actually do it and shut our mouths up with facts. But I can assure that it's nothing simple to accomplish.

---

### Post by CptPicard on 2010-07-25
It should also be noted that compilers often use a kind of "pseudo-assembly" internally:

[http://en.wikipedia.org/wiki/Three_address_code](http://en.wikipedia.org/wiki/Three_address_code)

That is then optimized further and finally serialized into actual asm by use of the back-end architecture selector switch :)

---

### Post by howlingmadhowie on 2010-07-25
> **CptPicard said:**
> It should also be noted that compilers often use a kind of "pseudo-assembly" internally:

[http://en.wikipedia.org/wiki/Three_address_code](http://en.wikipedia.org/wiki/Three_address_code)

That is then optimized further and finally serialized into actual asm by use of the back-end architecture selector switch :)

just to complicate matters further i think i should point out that one school of thought says that a compiler like the gnu compiler collection takes an input in various formats (c, c++, fortran etc.), abstracts out of that a tree view of the program in something called p-code and then translates this p-code into a version of assembly for the target architecture/operating system. 

someone did however once tell me that no compiler is actually that pure, and a compiler tends to use information about the target to generate better p-code for the target.

this sort of makes sense. consider one of the differences between risc and cisc machines, namely that on a risc machine, arithmetic operations on fixed-point numbers are guaranteed to take a certain amount of time exactly. this allows the compiler in some cases to plan what can be done while waiting for the result. or there are the unused jump slots which can be filled with other stuff. 

computers at the level of the hardware are very different beasts. even register machines (amd64, ia64, sparc v9, mips 9k etc.) are difficult to consider together, stack based machines (for example microjava) are totally different and require very different compilation methods.

another thing that strikes me is the supposition that "assembly is what's really going on".  as mentioned elsewhere, "what's really going on" in a program depends a lot upon who you ask. the physicist will say "some p-type semiconductors are changing state", the engineer will say "some locks and nand gates are being set", the opcode designer will say "some assembly commands are being performed", the programmer will say "my for loop is running", the computer scientist will say "an algorithm with time complexity of O(nlog(n)) is running" and the computer user will say "my window's not responding".  i can't see any innate reason to say that one person's summation of the situation is necessarily more intrinsically right than any other person's view.

just my 2 cents.

---

### Post by worseisworser on 2010-07-25
> **howlingmadhowie said:**
> 
another thing that strikes me is the supposition that "assembly is what's really going on".  as mentioned elsewhere, "what's really going on" in a program depends a lot upon who you ask. the physicist will say "some p-type semiconductors are changing state", the engineer will say "some locks and nand gates are being set", the opcode designer will say "some assembly commands are being performed", the programmer will say "my for loop is running", the computer scientist will say "an algorithm with time complexity of O(nlog(n)) is running" and the computer user will say "my window's not responding".  i can't see any innate reason to say that one person's summation of the situation is necessarily more intrinsically right than any other person's view.

Nice, and there seem to be no end to it; atoms are made up of further even smaller parts still.

What people sometimes miss is that abstraction can actually *add* to what one in a very real sense *can* do at some current level of interest -- in addition to only(#1) "increasing what one can think and reason about as dumb, weak humans".

E.g., think of digital as an abstraction of the analog; digital *adds* precision and predictability at the cost of speed and detail; this is very worthwhile and "real" in the non-social/human but still, at this level, machine sense of it all.

Adding new, often more abstract(#2) words to a language does not actually remove or change reality at its own level, but it enables us to control it or move away from it, describe things for it to do; the machine, in *new* ways when working or focusing on a *different* (another reality), often higher, level. It is not always about "nicer so we humans can deal with it", but actually about the possible vs. the impossible.

I like the fight depicted on the front cover of the dragon book(#3); pick your arena, but every level is just as important and real as the other; there are turtles all the way down. :)


[INDENT]#1: This is the normal argument; "we humans are weak and dumb so we must dumb things down", but this is not true; we are in a very real sense *adding* to what is actually possible![/INDENT]

[INDENT]#2: Closer to us or our problem; our *current* level of interest or focus.[/INDENT]

[INDENT]#3: [http://en.wikipedia.org/wiki/Dragon_Book_(computer_science)](http://en.wikipedia.org/wiki/Dragon_Book_(computer_science))[/INDENT]

---

