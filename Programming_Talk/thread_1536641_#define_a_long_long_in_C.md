---
title: "#define a long long in C"
date: 2010-07-22
forum: Programming Talk
---

### Post by nmaster on 2010-07-22
Some background:
I'm using [STREAM]("http://www.cs.virginia.edu/stream/") to take some benchmarks of some experimental swap configurations.  The machine has 24GB of RAM so I need to force the array size to be enormous so that the program takes about 48GB.

Problem:
The source code defines N like this:
```

#ifndef N
#   define N    2000000
#endif

```I need to store a much, much larger value for N ,something like this:
```

#ifndef N
#   define N    99999999999999999
#endif

```When I try this, I get the following error from gcc.  
```
$ gcc -o stream stream.c
/tmp/ccSMMs90.o: In function `main':
stream.c:(.text+0x103): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x114): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x2a9): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x312): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x323): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x3a1): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x3b1): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x422): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x42f): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x4b4): relocation truncated to fit: R_X86_64_32S against `.bss'
stream.c:(.text+0x4e8): additional relocation overflows omitted from the output
collect2: ld returned 1 exit status
```I've tried appending the number with LL, but that doesn't fix anything. 

I couldn't find the answer when googling stuff abotu C macros, but maybe  I was just searching for the wrong thing.  I'm not very experienced in C and haven't ever really needed to use such a large value for anything before.

How can I use the macro to store a long long int?  I could rewrite the source code to get around this, but (obviously) I'd rather not do that.  

Thanks for the help.

---

### Post by soltanis on 2010-07-22
Hi, if you need to just take up a lot of space, I suggest that you allocate it on a heap array rather than a stack array. If you try to cram a lot of stuff into the stack, you'll just overflow it.

You can do this (I hope I did my math right):
```

#define COUNTS 4800000
#define BLOCK 100000000
/* 4,800,000 allocations of 10,000,000 bytes = 48 GiB */

long i;
char *leak;
for (i = 0; i < COUNTS; i++) {
  leak = malloc(BLOCK);
  if (!leak) {
    perror("malloc");
  }
}

```

---

### Post by nmaster on 2010-07-22
> **soltanis said:**
> Hi, if you need to just take up a lot of space, I suggest that you allocate it on a heap array rather than a stack array....

Yeah, sorry if I wasn't clear in my original post, but I'm actually trying to run a benchmark.  You can find the source code [here]("http://www.cs.virginia.edu/stream/FTP/Code/stream.c").

Furthermore, the original author says this ([http://www.cs.virginia.edu/stream/ref.html):](http://www.cs.virginia.edu/stream/ref.html):)
> For an automatically parallelized run on (for example) 16 cpus, each with 8 MB L2 caches, the problem size must be increased to at least  N=64,000,000.   This will require a lot of memory!  (about 1.5 GB).   If you get much  bigger than this, you will need to compile with 64-bit addressing, and once N  exceeds 2 billion, you will need to be sure to use 64-bit integers.  (Yes, I  have run lots of cases bigger than this -- not on peecees, of course!) 

is there a way to compile with gcc to set the default integer size to by 64-bit? I know that I can edit the gcc source code and recompile it to do this, but once again, I'd rather not!

---

### Post by nmaster on 2010-07-22
i ended up just re-writing the benchmark.  if anyone knows how to do what i needed with the directive, the information would still be appreciated!

---

### Post by endotherm on 2010-07-22
this may help. 
[http://stackoverflow.com/questions/1458923/long-long-in-c-c](http://stackoverflow.com/questions/1458923/long-long-in-c-c)

---

### Post by Can+~ on 2010-07-22
> **neal.m.master said:**
> How can I use the macro to store a long long int? I could rewrite the source code to get around this, but (obviously) I'd rather not do that.

Macros and constant definitions don't really have a type, they're replaced directly on the code on the preprocessing stage, for example:

original code.c:
[PHP]#define X 1234
#define MACRO(Y) Y+2
...
printf("This is %d", MACRO(X));[/PHP]

pre-compiled code.c (this is how it "would look like"):
[PHP]...
printf("This is %d", 1234+2);[/PHP]

> **neal.m.master said:**
> is there a way to compile with gcc to set the default integer size to by 64-bit? I know that I can edit the gcc source code and recompile it to do this, but once again, I'd rather not!

ints are always 32-bit. longs may support 64-bit (platform dependant), and long longs guarantee 64-bit length.

From the manpages:
```
       -m32
       -m64
           Generate code for a 32-bit or 64-bit environment.  The 32-bit environment sets int, long and pointer to
           32 bits and generates code that runs on any i386 system.  The 64-bit environment sets int to 32 bits
           and long and pointer to 64 bits and generates code for AMD's x86-64 architecture. For darwin only the
           -m64 option turns off the -fno-pic and -mdynamic-no-pic options.
```

---

### Post by dwhitney67 on 2010-07-22
I have no trouble compiling the following on an x86_64 system:
```

unsigned long long BIG_VAL = 9999999999999999999ULL;

int main(void) {}

```

---

### Post by MadCow108 on 2010-07-22
> **Can+~ said:**
> Macros and constant definitions don't really have a type, they're replaced directly on the code on the preprocessing stage, for example:


constants do have a type.
numbers default to int but you can change that by suffixes (case insensitive):
u makes it unsigned, l makes it long ll makes it long long (can be combined with u)

similar decimals default to double. but you can make it float with the suffix f.

strings have the type const char * and may be reference counted by the compiler

if you have added LL and it still does not work the problem is elsewhere (maybe an implicit conversion back to int?)

please show some code, I have never encountered this particular error message so I can only guess whats happening
but you somehow seem to overflow the data section of your executable.
This may be related to using static or stack arrays as soltanis already mentioned.

---

### Post by nmaster on 2010-07-22
> **MadCow108 said:**
> constants do have a type.
numbers default to int but you can change that by suffixes (case insensitive):
u makes it unsigned, l makes it long ll makes it long long (can be combined with u)

similar decimals default to double. but you can make it float with the suffix f.

strings have the type const char * and may be reference counted by the compiler

if you have added LL and it still does not work the problem is elsewhere (maybe an implicit conversion back to int?)

please show some code, I have never encountered this particular error message so I can only guess whats happening
but you somehow seem to overflow the data section of your executable.
This may be related to using static or stack arrays as soltanis already mentioned.

the code was posted above in a link.  i agree that the .text section is overflowing. that's exactly what the error message from gcc says.

---

### Post by nmaster on 2010-07-22
> **Can+~ said:**
> Macros and constant definitions don't really have a type, they're replaced directly on the code on the preprocessing stage, for example:

original code.c:
[PHP]#define X 1234
#define MACRO(Y) Y+2
...
printf("This is %d", MACRO(X));[/PHP]pre-compiled code.c (this is how it "would look like"):
[PHP]...
printf("This is %d", 1234+2);[/PHP]

ints are always 32-bit. longs may support 64-bit (platform dependant), and long longs guarantee 64-bit length.

From the manpages:
```
       -m32
       -m64
           Generate code for a 32-bit or 64-bit environment.  The 32-bit environment sets int, long and pointer to
           32 bits and generates code that runs on any i386 system.  The 64-bit environment sets int to 32 bits
           and long and pointer to 64 bits and generates code for AMD's x86-64 architecture. For darwin only the
           -m64 option turns off the -fno-pic and -mdynamic-no-pic options.
```

thanks for the explanation or macros, i kind of already knew the basics though... and also, there are types.  32.0 can be used as a double, whereas 32 would be used as an int.

i had read that in the man page for gcc, but i'm saying you can change the size of an integer in the *source code* for gcc. [http://www.delorie.com/gnu/docs/gcc/gccint_112.html](http://www.delorie.com/gnu/docs/gcc/gccint_112.html) you just need to edit the code before you compile *gcc*.

anyway, my code works now (as i said earlier) so i'm not looking for suggestions on how to write the program.  i just want to know how to put a long long in the text section of the code.  i could always edit the assembly by hand before the compilation/linking/etc. but i feel like there should be an easier way of doing this.

---

### Post by Can+~ on 2010-07-22
> **MadCow108 said:**
> constants do have a type.

Yes, constants do have a type (i.e 20LLU). Constant definitions (i.e #define X 20) don't, as they haven't yet interpreted by the compiler itself, just the preprocessor.

But I understand the ambiguity of my original statement.

(OP) Also, here's how to look at the preprocessor output:
[FONT="Courier New"]gcc -E filename.c[/FONT]

---

### Post by DotNate on 2010-07-23
[PHP]
#ifndef N
    #define N 0x016345785d89ffff    //99999999999999999
#endif
[/PHP]

The above compiles fine for me on x86_64.

---

### Post by nmaster on 2010-07-25
> **DotNate said:**
> [PHP]
#ifndef N
    #define N 0x016345785d89ffff    //99999999999999999
#endif
[/PHP]The above compiles fine for me on x86_64.

it doesn't for me though... not on my personal (ubuntu) laptop, not on the macbook from work, not on the RHEL at work either... did you use any special options with gcc?

---

### Post by slooksterpsv on 2010-07-25
Works fine for me too, here's my source as well as what I typed to compile:
[php]
#ifndef N
	#define N 0x016345785d89ffff
		//99999999999999999  
#endif
#include <stdio.h>

int main()
{
	printf("%lld\n", N);
	printf("99999999999999999\n");
	return 0;
}
[/php]
[php]
shawn@shawn-ubuntu-laptop:~$ pico test.c
shawn@shawn-ubuntu-laptop:~$ gcc test.c
test.c: In function &#8216;main&#8217;:
test.c:9: warning: format &#8216;%lld&#8217; expects type &#8216;long long int&#8217;, but argument 2 has type &#8216;long int&#8217;
shawn@shawn-ubuntu-laptop:~$ ./a.out
99999999999999999
99999999999999999
shawn@shawn-ubuntu-laptop:~$
[/php]

EDIT:
My gcc is version 4.4.3 if that makes any difference.

---

### Post by DotNate on 2010-07-26
I'm using gcc 4.4.3, no special options.

Using it in printf does generate a warning, but simply appending the constant with the LL suffix fixes that:

[PHP]
#ifndef N
    #define N 0x016345785d89ffffLL  //99999999999999999
#endif

#include <stdio.h>

int main()
{
    printf("%lld\n", N);
    return 0;
}

[/PHP]

---

