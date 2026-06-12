---
title: "Another question about the c language."
date: 2008-07-10
forum: Programming Talk
---

### Post by Gorgonkernel on 2008-07-10
I know that in the DOS operating system you can use the Ansi driver to writte in colors or position the mouse cursor in the way you want. But how can you do it now on windows xp and linux?

Thanks!

---

### Post by pmasiar on 2008-07-10
Exactly the same (in terminal mode). There are sequences to write in colors and position the cursor (curses/ncurses), i am not sure about the mouse but mc does it so it is possible.

BTW you should read in my sig 'how to ask questions' and get better title next time

---

### Post by Gorgonkernel on 2008-07-10
```
#include <stdio.h>
int main (void)
{
printf("\033[44m");
 
 printf("This is a simple test ");
 
}

```
This is the code. I added printf("\033[44m");,like you do it in the dos but it doesnt`t work. Sorry for the stupid post and question but i`m in a hurry.

---

### Post by mali2297 on 2008-07-10
> **Gorgonkernel said:**
> ```
#include <stdio.h>
int main (void)
{
printf("\033[44m");
 
 printf("This is a simple test ");
 
}

```
This is the code. I added printf("\033[44m");,like you do it in the dos but it doesnt`t work. Sorry for the stupid post and question but i`m in a hurry.

It works fine for me, black text on blue background. Where do you execute the program? (Which terminal emulator?)

---

### Post by nvteighen on 2008-07-10
> **Gorgonkernel said:**
> 
This is the code. I added printf("\033[44m");,like you do it in the dos but it doesnt`t work. Sorry for the stupid post and question but i`m in a hurry.

It works for me: I get blue text background (foreground unchanged). Though you should add printf("\033[0m"); to reset the terminal.

---

### Post by Gorgonkernel on 2008-07-10
I`m currently on windows and i use an antique compiler Turbo c++Lite

---

### Post by nvteighen on 2008-07-10
Check [http://en.wikipedia.org/wiki/Conio.h](http://en.wikipedia.org/wiki/Conio.h):

"But the library supplied with Turbo C++ and Borland C++ did not use the DOS API but instead accessed video RAM directly for output and used BIOS interrupt calls."

---

### Post by supirman on 2008-07-10
ncurses is useful for writing 'gui' command line apps.  There is also a library called CDK (curses development kit) that implements a number of useful widgets on top of ncurses.  CDK has it's quirks, but all in all I've enjoyed using it.

---

### Post by tornado89 on 2008-07-12
I'm using ncurses on Linux for Mouse, Menus & Colors Effects

---

### Post by GoS_ on 2008-07-12
I find this very interesting.  Does anyone know how this, or ncurses, work?  Am I correct that it is impossible to use hardware interrupts in Linux or versions of Windows after Me?  So it must go through the operating system somehow?  Is it the OS that makes the hardware interrupt, or does some even less efficient software related thing go on?  Finally, does anyone know which is more efficient, ncurses, or these escape sequences. My guess would be the escape sequences since they don't call any functions (or do they?).

Obviously I'm not the most intelligent person when it comes to programming, but I tried googling this and couldn't find any answers.

---

### Post by nvteighen on 2008-07-12
> **GoS_ said:**
> I find this very interesting.  Does anyone know how this, or ncurses, work?  Am I correct that it is impossible to use hardware interrupts in Linux or versions of Windows after Me?  So it must go through the operating system somehow?  Is it the OS that makes the hardware interrupt, or does some even less efficient software related thing go on?  Finally, does anyone know which is more efficient, ncurses, or these escape sequences. My guess would be the escape sequences since they don't call any functions (or do they?).

All executables pass through the OS somehow, to read the binary format, set up virtual memory, load dynamic libraries, etc. There's no "absolute standalone" program, unless it is a bootable operating system.

Yes, you probably could pass hardware interrupts from a C code (using inline Assembly?), but why bother if you can take advantage of the underlying kernel? What I mean, C is low-level enough... do you want it even lower? C is that flexible that you might be able to do it as an experiment, though completely unpractical.

On ncurses vs. escape sequences. In theory, you should be able to rewrite all ncurses functionality with escape sequences, but again, there's a reason why ncurses exists and it's used: it makes you focus on the actual program instead of creating a whole new UI toolkit. It gives you coding efficiency by the cost of losing a ridiculous fraction of time in indirection (a fraction that small that you'd probably won't be able to measure exactly with average tools).

Don't worry, with CPUs running at several GHz, some function calls won't harm you... :)

---

### Post by GoS_ on 2008-07-12
Thanks for the answers nvteighen.  Ever since I read *Assembly Language Step-by-Step*, by Jeff Duntemann, I can't stop worrying about speed.  The book was written in 1992 and assumes the reader is using a 80486 processor at best. :)  There is slight difference between 25MHz single core, and a 3.0GHz dual-core with all the new superscalar/pipelining features, I assume.

---

### Post by LaRoza on 2008-07-12
> **GoS_ said:**
> Thanks for the answers nvteighen.  Ever since I read *Assembly Language Step-by-Step*, by Jeff Duntemann, I can't stop worrying about speed.

Assembly isn't automatically faster. A C compiler's output can be faster than handwritten assembly for the same purpose and the C version would take less time. Also, the C version might take longer to write than say a Perl version with no noticable loss in speed.

Think about this forum. It uses PHP on the server. PHP is extremely high level (like Perl). So a collection of PHP scripts are execuated from multiple files on a server (Apache) on Linux (Ubuntu Server) and has to connect to MySQL every query, plus all the Ajax. In all of that, the most time spent it waiting for pages to load over a network.

Don't pay attention to speed until you have to. It will cripple you for nothing. (For driver programmers, device programmers, and those on super computer clusters, ignore this)

---

### Post by GoS_ on 2008-07-12
> **LaRoza said:**
> Assembly isn't automatically faster.   

Sorry if that's what it sounded like I meant.  I was referring to the fact that the book was written in 1992 and the author makes points about staying away from the RAM and describing the speed disadvantages of calling functions.  Which, yes, I understand aren't very relevant with 3.0+Ghz processors.  I also understand that I shouldn't worry about speed very much, but since I read the book, silly things like the time it takes to call the OS or a function pop into my head.  Don't worry I'm trying to not let it cripple me.

---

### Post by nvteighen on 2008-07-12
Yes, there's a theoric speed disadvantage when calling a function. But consider the advantages of functions:

1. Structured programming: one task = one function. Whenever you have to check something, you'll know that there's only one place to look at.
2. You can reuse code as many times you want just calling the function!
3. 1 + 2: your program is likely to be more mantainable and also more extensible in future.

In two words: Development efficiency.

And how are we supposed to stay away from RAM, according to that author? Limiting ourselves to processor registers?? Is he crazy?

---

### Post by GoS_ on 2008-07-12
Again I may have been a bit unclear.  Duntemann explains that RAM is slower than the CPU (obviously), and so you should avoid using it when you can.  Not that you shouldn't use it at all.  That really would be horrible.  And to make myself clear, I agree with those statements about functions.  Functions make programming a lot easier, and their benefits far out weigh their very few flaws.  When I asked if escape sequences were faster than ncurses, it was out of curiosity.  One would have to be crazy to use escape sequences instead.

---

### Post by LaRoza on 2008-07-12
> **GoS_ said:**
> Sorry if that's what it sounded like I meant.  I was referring to the fact that the book was written in 1992 and the author makes points about staying away from the RAM and describing the speed disadvantages of calling functions.

Yeah, you have to forget about that for this type of programming :-)

If you are programming a device,  such things would make sense.

> **GoS_ said:**
> Duntemann explains that RAM is slower than the CPU (obviously), and so you should avoid using it when you can.
There is more to it. There is the clock speed, the CPU's multiplier, the front side bus, and the RAM speed. All of this is meaningless when coupled with IO or a network or database. 

> 
When I asked if escape sequences were faster than ncurses, it was out of curiosity.  One would have to be crazy to use escape sequences instead.

In terms of simple speed, probably, however, it would have absolutely no impact on the program (unless it is being run on bare hardware). It has to go through the kernel anyway, and the kernel is a busy piece of software and any speed you'd gain (it would be small to begin with) would be meaningless because the kernel can be handling a lot at once.

---

### Post by gnusci on 2008-07-12
You can use ANSI codes, but (maybe only) work on Unix systems, like Linux or Mac. I am not sure works Win. Here a list of the codes:

> 
Text attributes
       0    All attributes off
       1    Bold on
       4    Underscore (on monochrome display adapter only)
       5    Blink on
       7    Reverse video on
       8    Concealed on

    Foreground colors
       30    Black
       31    Red
       32    Green
       33    Yellow
       34    Blue
       35    Magenta
       36    Cyan
       37    White

    Background colors
       40    Black
       41    Red
       42    Green
       43    Yellow
       44    Blue
       45    Magenta
       46    Cyan
       47    White
 

You can use with **printf** like in this example

[PHP]
#define BRIGHT 1
#define RED 31
#define BG_BLACK 40
printf("%c[%d;%d;%dmHello World", 0x1B, BRIGHT,RED,BG_BLACK);
[/PHP]

The result is a printed string with bright red but the color setting will remain, to reset back the default colors use:

[PHP]printf("%c[%dm", 0x1B, 0);[/PHP]

On another hand, you better use ncurses, even if you will run you program on Linux. if you want to run the program on different systems like Linux, Mac or Win, ncurses is the best option, if not you may need to recode for every system.

---

### Post by pmasiar on 2008-07-12
> **GoS_ said:**
>  Ever since I read *Assembly Language Step-by-Step*, by Jeff Duntemann, I can't stop worrying about speed. 

Good compiler can often optimize code better than your limited bag of tricks in optimization. Ie. JIT runtime compiler/optimizer can inline function calls and do other cool tricks ASM hacker cannot, because they rely on runtime info.

---

