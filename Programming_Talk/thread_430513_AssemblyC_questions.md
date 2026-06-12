---
title: "Assembly/C questions"
date: 2007-05-02
forum: Programming Talk
---

### Post by quark_77 on 2007-05-02
Hi All,

Have been teaching myself C for a while now. It appears that the best way to optimise some routines is to dive right in and write assembly code (I'm talking mathematical routines here) so I've had a look at assemblers and what not to see whats there. My question is this: which assembler does everyone use? I'm not interested in writing huge programs in assembly -- i have better things to do, but a small number of routines need optimising. At the risk of starting a war, do people use Intel or AT&T syntax? When you write assembly routines, do you stick them in .S files and compile those or do you prefer in-line c/c++ source?

Finally, where can I begin learning this arcane art? I have a feeling whichever route I choose it's going to be difficult...

Thanks in advance for any advice you have!

Quark_77

---

### Post by engineer on 2007-05-02
i guess the easiest way would be to write inline assembly code.
gcc understands assembly code. 

[Inline assembly howto]("http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html#s3")

as far as i remember, there are also pagma switches to turn assembly syntax on/off

---

### Post by phossal on 2007-05-02
If you're truly optimizing mathematical routines using assembly, you're probably tied to a specific architecture. The compilers for the various platforms are better than *efficient*. If that's the case, most of your decisions will probably be made for you in advance. If you don't already know an asm language, what makes you think you *could* optimize any routines?

---

### Post by yaaarrrgg on 2007-05-02
if you're using gnu's compiler, it might make the most sense to use gas.  other than that, not everyone is crazy about the syntax.  nasm is also another assembler that is fairly popular ... you might try both.

for books, you might look at "Professional Assembly Language, by Richard Blum"  It's fairly comprehensive, although I'm sure there are better books.

generally, the same principles apply to assembly programming as in c programming, but it gives you more control over accessing the specifics properties of the cpu.

but, using all the bells and whistles of the cpu means it won't be very portable ... you'd have to rewrite portions for every cpu family you want to use.  speed is not always the best thing.  

also, it's hard to write assembly code that will be more effiicient than what the compiler will generate.  the biggest speed increases are by optimizing code at a large scale level... choosing the best algorithms, data formats, inline functions, etc.  assembly will more than likely only be useful in micro-optimizatoin, like very a tight loop, and might not even be worth bothering with in terms of speed differences.

for gcc, also, you might also compare when comipiled with some flags ...
-O3   ... general optimization
-march=your cpu
-mcpu=your cpu
-mtune=your cpu

or you can even trade some c saftey for speed :
-funsafe-math-optimizations

-S  .... dumps the c generated assembly so you can inspect/edit

EDIT: Note, even if assembly code *looks* more optimized, being faster is a different thing.  The best way to really know what is faster is to test each block of code.  Some things that seem intuitive are sometimes backwards.  For example, it might seem faster to precompute a value and store it in memory, but the reverse may be the case if the cpu has to look it up in memory rather than fetching the all the other values in the l1 cache and computing the result.  At that level micro-optimization it really depends entirely on the hardware.  One technique might speed up the program on one machine, but actually slow it down on another.  Knowledge of assembly is not as necesary as knowldge of the machine architecture.

---

### Post by Wybiral on 2007-05-02
> **phossal said:**
> If you're truly optimizing mathematical routines using assembly, you're probably tied to a specific architecture. The compilers for the various platforms are better than *efficient*. If that's the case, most of your decisions will probably be made for you in advance. If you don't already know an asm language, what makes you think you *could* optimize any routines?

It's not really a matter of compiler efficiency, compilers are programs and they don't fully understand your code, every now and then they plop out a less than efficient chunk of assembly.

You can write object files in assembly using basically any assembler. The only two I ever use are NASM and GAS (which is the backend assembler for GCC).

You need to learn how GCCs function calls work, then you can write an object file in assembly and a header (just like it were a C program), then you can link it to your program like a normal object file.

As far as inline assembly goes... It's an option, IMO an ugly option. But using external assembly is much cleaner and if you need to port it to another platform you can just change the assembly file (you don't even have to mess with the header file that goes with it most of the time).

Where-as inline requires you to hunt down all of the chunks of assembly.

As far as your main question "which assembler does everyone use?":
If I can get away with it, then NASM. It's really clean and faster to write.
If I'm editing assembly that the compiler spat at me, then I have to use GAS.

---

### Post by quark_77 on 2007-05-02
Hi Wybiral,

My plan was always to separate assembly files from c source, but I've seen a number of inline programs, the one that caught my eye being Dr Brian Gladman's Serpent implementation, which is actually a cpp file but there's no C++ in it save a bunch of __asm directives and the wrapping code.

NASM and GAS sound good, even though they're different syntaxes. I couldn't get to grip with MASM at all (then there's the small issue that it only works on Windows!) and FASM doesn't seem to like producing object files.

phossal - Wybiral is right. Although I don't have much experience at all with assembly I do know that compilers spit out a lot more assembly code than assemblers do, thereby reducing the efficiency of anything I write. This is noticeable even with hello world programs.

As for my platform, i386 until I have the money / time to invest in anything better.

Thanks for all your ideas everyone.

---

### Post by phossal on 2007-05-02
> **"quark_77 said:**
> ...I couldn't get to grip with MASM at all...phossal - Wybiral is right. Although I don't have much experience at all with assembly...

Well, you know what you know. Good luck with that.

[EDIT] For the record, my infraction for sarcasm was reversed. ;)

---

### Post by quark_77 on 2007-05-09
Back again to demonstrate my inexperience, I have two files, one a C one including stdio.h and two externs for functions in an assembly file, written in AT&T (I also changed it to NASM). Linking them together results in gcc spitting the dummy out, here goes:

```
$ gcc -c asm.S
$ gcc -c testasm.c
$ gcc -o test asm.o testasm.o
```

after the last step I get this:

```
arithtest3.o: In function `main':
testasm.c:(.text+0x5d): undefined reference to `Add'
testasm.c:(.text+0x72): undefined reference to `Sub'
collect2: ld returned 1 exit status

```

My assembly file contains two labels, one _Add, the other _Sub which are defined beforehand as .globl (AT&T). I have the same problem using the nasm source... it doesn't want to link!!

Just in case, here's the asm:
```
.globl _Add
.globl _Sub

/* Code */

/* int Add(a, b) */
_Add:
        pushl	%ebp                 /* create stack frame         */
        movl	%esp, %ebp			 
        movl	8(%ebp),%eax         /* grab the first argument    */
        movl    12(%ebp),%ecx        /* grab the second argument   */
        addl    %ecx, %eax           /* sum the arguments          */
        popl    %ebp                 /* restore the base pointer   */
        retl
        
/* int Sub(a, b) */
_Sub:
        pushl   %ebp                 /* create stack frame         */
        movl    %esp, %ebp			 
        movl    8(%ebp),%eax         /* grab the first argument    */
        movl    12(%ebp),%ecx        /* grab the second argument   */
        subl    %ecx, %eax           /* sum the arguments          */
        popl    %ebp                 /* restore the base pointer   */
        retl

/* End of File */

```

and here's the C:
```
#include <stdio.h>

extern int Add(int a, int b);
extern int Sub(int a, int b);
           
int main(int argc, char* argv[])
{
	int a1, a2, x, y;	  
	a1 = 2;
	a2 = 3;
	x = Add(a1, a2);
	y = Sub(a1, a2);
	printf("%d + %d = %d\n", a1, a2, x);
	printf("%d - %d = %d\n", a1, a2, y);

	return 0;
}

```
Using gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4) on an i386 for now. Bizarrely enough, gcc 3.4.2 (mingw32) WILL compile & link this without argument and even Microsoft's link will link the gnu as .o file with it's .obj file to produce an exe...

Thanks for all your help, even Phossal, who now has a chance to put me in my place! (Joking aside, all help/criticism/assistance is welcome... it has taken some work to produce the above...)

Quark_77

PS I know it doesn't DO anything remotely useful!

---

