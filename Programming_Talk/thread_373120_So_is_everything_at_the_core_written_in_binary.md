---
title: "So is everything at the core written in binary??"
date: 2007-02-28
forum: Programming Talk
---

### Post by billdotson on 2007-02-28
so are all programs, OSes, etc. in computers at their core written in binary?  Like how was the first operating system created?  Did they set a certain standard for binary characters to equal certain things and go from there?

---

### Post by slayerboy on 2007-02-28
Every part of computers is broken down into Binary.  The very first program language was Binary.  Now there are compilers that convert programming to Binary.  So basically, yes when broken down computer programs are just basically binary.

---

### Post by Wybiral on 2007-02-28
You must mean machine code... Well, it varies from OS to OS and processor to processor.

Assuming you know that the processor does...

Machine code does in-fact talk directly to the processor and tell it what operations to apply to the data fed to it. Essentially everything on modern computers is fed to the processor via machine code.

But... Not everything is written in machine code. Take C for instance...

When you compile a C program, this happens:

C -> Assembly -> Machine code

When an interpreted program gets ran, it gets "translated" or virtual machined into that machine code on runtime.

Some vm's speak to the processor through conditional statements and aren't really "assembled"... This makes it easy on them because the same code can be ran on multiple platforms without significant rewrite of the vm. Some of them actually generate the assembly at runtime... When you see "JIT" or "Just In Time" compilers... That's what's being referred to.

But yes... Processors need fed a certain format, so essentially everything breaks down into a form of "machine code"

---

### Post by Arndt on 2007-03-01
> **slayerboy said:**
> Every part of computers is broken down into Binary.  The very first program language was Binary.  Now there are compilers that convert programming to Binary.  So basically, yes when broken down computer programs are just basically binary.

And before that, the programs were not even stored, they were wired physically.
(Electrons are physical too, but I mean cables that were moved around.)

---

### Post by slayerboy on 2007-03-01
> **Arndt said:**
> And before that, the programs were not even stored, they were wired physically.
(Electrons are physical too, but I mean cables that were moved around.)
Well true, but then again the abacus is the world's first computer.....

---

### Post by billdotson on 2007-03-01
so are there actually any people masochistic enough today to write a program in binary?

Also, the whole binary thing seems really interesting to me.  If I wanted to learn how exactly the binary talks to hardware and understand how programs work down at the core would I would need to learn a large amount of machine code and assembly langauge wouldn't I? 

It just blows my mind that when I type a letter on the keyboard the letter is actually seen by the computer at the bottom level as a string of 1's and 0's

---

### Post by pmasiar on 2007-03-01
> **billdotson said:**
> so are all programs, OSes, etc. in computers at their core written in binary?  Like how was the first operating system created?  Did they set a certain standard for binary characters to equal certain things and go from there?

CPU can execute only binary. But programs are written in many different languages, and then compiled to binaries. Most of Linux kernel is in C [http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux) says 71% of kernel's 2.4 million lines of code is in C, Debian 2.2 (in 2002) has 55 millions lines of code which would cost $1.9B (billion, not million) to develop.

Nowadays when you develop code for new processor, you write an emulator which will execute binaries of other processor (by calling procedure for every binary instruction - yes it is very slow), but you mostly need to port just C compiler, and after porting it to so many different architectures it is less hard work than it was before.

In old times, using high-level languages was controversial - "assembler only", exactly like people today are afraid to use dynamically typed languages and claiming "C/C++ only". Times change, people and arguments do not :-)

Old computers have ability to write directly to core and display binary content of selected memory cell, so it was possible to write binary program from panel and execute it. I've seen it myself once, when our guru was forced to write PDP dick driver program to read disk sectors to read admin password from disk. Being able to read I8080 binary instructions from paper tape was very usefull skill - many people did it in old times. Old school!

Legendary old hackers were able to do stuff like that. Lore says that first OS for CRAY supercomputer was entered from the panel. Or Paul Allen, the other Microsoft founder, once flew to Silicon valley to present his BASIC to investors and realized he forgot tape loader and so will not be able to present it. He wrote loader in binary from memory (he forgot his binary opcodes book too) in the plane and entered it from the panel while talking about the BASIC, and loaded BASIC, nobody noticed anything, it worked and Microsoft got founded. Yeah, those were real hackers! :-)

---

### Post by pmasiar on 2007-03-01
> **slayerboy said:**
> Well true, but then again the abacus is the world's first computer.....

Not so. Most important part of computer magic, the secret sauce which enables everything else, is being able to treat data as program, and program as data. Loader loads data, and then executes them as program. Compiler reads data (source code) and creates binary code - executable program. 

Abakus displays only data - program is you. Without program, without your knowledge how to use it, abakus is just balls on wire.

---

### Post by slayerboy on 2007-03-01
> **pmasiar said:**
> Not so. Most important part of computer magic, the secret sauce which enables everything else, is being able to treat data as program, and program as data. Loader loads data, and then executes them as program. Compiler reads data (source code) and creates binary code - executable program. 

Abakus displays only data - program is you. Without program, without your knowledge how to use it, abakus is just balls on wire.
good point lol

---

### Post by billdotson on 2007-03-01
so if I wanted to be able to actually write a program in binary (so I can really understand the undercurrent of everything in a computer) what would I have to learn.  I am trying to familiarize myself with various concepts of programming, website development/design, hardware + software troublshooting, how computers "think" internally and networking before I have to choose a major in a couple years.  Right now I am learning Python.

---

### Post by Wybiral on 2007-03-01
> **billdotson said:**
> so are there actually any people masochistic enough today to write a program in binary?

Also, the whole binary thing seems really interesting to me.  If I wanted to learn how exactly the binary talks to hardware and understand how programs work down at the core would I would need to learn a large amount of machine code and assembly langauge wouldn't I? 

It just blows my mind that when I type a letter on the keyboard the letter is actually seen by the computer at the bottom level as a string of 1's and 0's

Some people do... It's not productive, but it is interesting. I've messed with machine code from time to time.

My advice... Learn assembly. Download NASM and get to studying. Assembly parallels almost literally to machine code where the opcodes in assembly represent a single byte in machine code.

If you want to edit a program in machine code, all you need is a hex editor. I use Ghex.

The only advantage I've found it to give you over regular assembly programming is that you can cut out all the crap that the assembler adds and squeeze codes into pieces of the program that you couldn't with assembly (like in the data segments or the executable header).

Here's a "Hello world!" program I wrote in NASM, then manually optimized in a hex editor. The result is a 92 byte program... 
[http://p13.wikispaces.com/space/showimage/tinyHello](http://p13.wikispaces.com/space/showimage/tinyHello)
(the actual assembly doesn't start until byte 0x42, the rest is all executable header info... Which is where I stashed the data)

Hello world compiled...
C++ = 4072 bytes
C = 3076 bytes
GAS Assembly = 604 bytes

So... If you're in the business of making tiny programs, you might want to look into it. Otherwise it's entirely too time consuming and hard to manage.

---

### Post by pmasiar on 2007-03-01
> **billdotson said:**
> so if I wanted to be able to actually write a program in binary (so I can really understand the undercurrent of everything in a computer) what would I have to learn. 

Closest to how CPU works is Assembler. To get a glimpse: [http://en.wikiversity.org/wiki/Introduction_to_Programming/About_Programming](http://en.wikiversity.org/wiki/Introduction_to_Programming/About_Programming)

CPU is much more complicated now than it was in old days - CPU for [http://en.wikipedia.org/wiki/PDP-11](http://en.wikipedia.org/wiki/PDP-11) (wikipedia: "The archetypal minicomputer; a 16-bit machine, widely regarded as the best 16-bit instruction set ever created") was "huge", size of 2 pages of paper with many many circuits (it was way before CPU on a microchip) and still had only 8 registers. Intel processor have much less regular architecture: [http://en.wikipedia.org/wiki/X86](http://en.wikipedia.org/wiki/X86) - links also to assmble language and instruction set. After learning PDP, I never liked irregular I86 architecture, decided (wisely) to stay with C and higher. :-)

Not many people dive *that* deep into the hardvare these times - CPU become faster and we need to burn the cycles: read more about evolution of programming languages, and which direction languages might evolve: [http://www.paulgraham.com/hundred.html](http://www.paulgraham.com/hundred.html)

You can learn a lot from wikipedia, just follow the links - and don't fry your mind! :-)

---

### Post by esaym on 2007-03-01
I have found that in my limited knowledge that it is very hard to learn programing by just reading.  It really helps to have someone explaining it all.  I am sure a simple programming class at your local community college would only cost about $400 total to take, then you can claim it on your income tax and get it back:KS

---

### Post by billdotson on 2007-03-01
wow I read that essay about the evolution of languages and my mind just blew about 10 capacitors.. I obviously do not know enough about programming to read that sort of work.  

I have only been reading a simple Python book for a couple days (a PDF book from greenteapress.com) so I don't know much of anything about programming.

---

### Post by yaaarrrgg on 2007-03-01
> **billdotson said:**
> wow I read that essay about the evolution of languages and my mind just blew about 10 capacitors.. I obviously do not know enough about programming to read that sort of work.  

As a quick summary, it's just saying that Python is slow, but in a hundred years, it won't matter :)

You might find HLA a bit easier to understand than other flavors of assembly languages... it was really a teaching tool for a book "The Art of Assembly Language" (Randall Hyde) which is not bad ...

---

### Post by Wybiral on 2007-03-01
> **yaaarrrgg said:**
> As a quick summary, it's just saying that Python is slow, but in a hundred years, it won't matter ...

Python isn't always slow... The interpreter is compiled and does some things very quickly (it was well written).

But one thing that disappoints me these days is that people seem to not care about efficiency, they just say "oh... it wont matter how fast or small it is because soon computers will be like lightning with infinite amounts of space"

That doesn't make any sense to me... Even if they do get faster and with more memory (and they inevitably will) why use that as an excuse to write inefficient code?

My philosophy is to write code as efficient as possible, that way when computers do get better, my software will just seem that much faster and smaller. I just think we should take the advancement of computer's as a way to further increase the efficiency of our programs, not as an excuse to write less efficient programs. If we strive to create faster and smaller programs, and the hardware industry strives to create faster and more memory efficient hardware then it will double the efficiency of computers from both ends.

Naturally this philosophy won't work in the industry these days because time is money and a company is more apt to want to pay their programmers less even at the cost of the efficiency of they're product. Sad, but true...

However, as open source and Linux programmers... We should focus on efficiency, I believe it will give us an edge. I believe Linux is better than Windows because it wasn't written as a "product", it was written as an efficient OS. That's why I moved to Linux, it is less memory intensive and takes up less space on my hard drive.

Btw, none of this is directed towards anyone in this post, I just seen the topic brought up and have wanted to type something along these lines for a while now.

---

### Post by lnostdal on 2007-03-01
i recommend this book: [http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf](http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf)

it will answer any question you have about these things .. it's a very good book

a critical difference between humans and machines is that the computer does not _understand_ binary; it only does certain _predefined_ tasks based on what the binary is

it also happens to be easy to use binary to represent things .. you probably already know that binary can represent numbers .. but numbers can easily represent or _map to_ characters

characters in turn can represent words .. and you can use words to represent each of the predefined tasks a computer can do .. so while getting a computer to calculate the sum of two numbers might be "010010010" it is easy to map this to a more human word like "sum"

you can further combine words to create new words .. if one word, or predefined task of a computer is "sum-of" and another word or predefined task of a computer is "multiple-of" you can easily create a new word and have that word represent the task of first getting the sum of two numbers then multiplying the result by 2:

```

cl-user> (defun sum-of (a b)  ;; well, this represents a word the computer already can do
           (+ a b))
sum-of
cl-user> (defun multiple-of (a b) ;; this too
           (* a b))
multiple-of
cl-user> (defun sum-and-multiple-of-2 (a b)  ;; and we create a new word - thus a new language, based on the already existing words
           (multiple-of 2 (sum-of a b)))
sum-and-multiple-of-2
cl-user> (sum-and-multiple-of-2 3 2)
10

```

..and this is how we create new words and ultimately new languages; we build on the fundamental tasks the computer can do already and thus creat new words and languages the computer can understand

the computer now understands the new word `sum-and-multiple-of-2' because it is based on words it already know: `sum-of' and `multiple-of' ..   these are in turn based on `+' and `*' .. and so on and so on .. until in the end you get to the fundamental words (binary) at the core

---

### Post by pmasiar on 2007-03-01
Just for fun, same thing in [Forth]("http://en.wikipedia.org/wiki/Forth_%28programming_language%29") it  uses argument stack directly.

```

>: sum-of + ;
>: multiple-by * ;
>: sum-of-and-multiple-by-2 sum-of 2 multiple-by ;

```

To test, use word . (dot) - it prints top value from the stack as number

```

> 2 3 sum-of .
5
>2 4 multiple-by .
8
>2 5 sum-of-and-multiple-by-2 .
14

```

---

### Post by Arndt on 2007-03-02
> **billdotson said:**
> so if I wanted to be able to actually write a program in binary (so I can really understand the undercurrent of everything in a computer) what would I have to learn.  I am trying to familiarize myself with various concepts of programming, website development/design, hardware + software troublshooting, how computers "think" internally and networking before I have to choose a major in a couple years.  Right now I am learning Python.

You can start by writing a small program in C (prog.C), then compile it using the -S option. That gives you assembler code (in prog.s). Understand the assembler code. For that, you need a manual for the processor of your machine. In that manual will also be the actual binary values for the various instructions, so you could enter it all in binary, if you wanted (no one wants that).

The processor manual will not explain how a stack is used, for example, only which register houses the stack pointer, and which instructions affect the stack. You need to read about calling conventions, stack, registers, types of memory, linking, etc. I don't know a good book about this. I've picked it up as I've gone through the years.

With the assembler file (prog.s), assemble it using the assembler (the assembler is called "as"). Now you have prog.o.

To learn about the linking step, compile and link the original prog.C with some option that shows you exactly what gcc is doing (I don't remember the name of the option). Then read up on the linker 'ld'.

Now you can put the program together without the C compiler: First "as", then "ld".

There used to be a tool 'adb' with which you could inspect an executable file (and run it) on the machine code level. Perhaps 'gdb' works for the purpose. So you can take 'gdb', tell it to show you machine code, and single step the program.

And so on.

Then there is how the program interacts with the environment. That's usually done with system calls (special machine instructions), which pass control to the Unix kernel, and which code you don't normally see. There's a lot to learn if you really want to see the _whole_ picture in binary. Take it one step at a time.

---

### Post by Wybiral on 2007-03-02
> **Arndt said:**
> You can start by writing a small program in C (prog.C), then compile it using the -S option. That gives you assembler code (in prog.s). Understand the assembler code. For that, you need a manual for the processor of your machine. In that manual will also be the actual binary values for the various instructions, so you could enter it all in binary, if you wanted (no one wants that).

The processor manual will not explain how a stack is used, for example, only which register houses the stack pointer, and which instructions affect the stack. You need to read about calling conventions, stack, registers, types of memory, linking, etc. I don't know a good book about this. I've picked it up as I've gone through the years.

With the assembler file (prog.s), assemble it using the assembler (the assembler is called "as"). Now you have prog.o.

To learn about the linking step, compile and link the original prog.C with some option that shows you exactly what gcc is doing (I don't remember the name of the option). Then read up on the linker 'ld'.

Now you can put the program together without the C compiler: First "as", then "ld".

There used to be a tool 'adb' with which you could inspect an executable file (and run it) on the machine code level. Perhaps 'gdb' works for the purpose. So you can take 'gdb', tell it to show you machine code, and single step the program.

And so on.

Then there is how the program interacts with the environment. That's usually done with system calls (special machine instructions), which pass control to the Unix kernel, and which code you don't normally see. There's a lot to learn if you really want to see the _whole_ picture in binary. Take it one step at a time.

You may also use "gcc prog.s" to do the assembling and linking.

---

### Post by billdotson on 2007-03-02
so I guess I need to finsih learning more Python, then move on to C or C++ and then I can finally look at the assembly code and understand some binary instructions.. interesting.

I find computer technology incredibly interesting.. too bad you have to take expensive classes often to learn these sorts of things.

---

