---
title: "To loop or not to loop?"
date: 2007-03-27
forum: Programming Talk
---

### Post by ibanezix on 2007-03-27
In a very simple program that prints the same character many times, and the amount of times is not selected by the user, but decided by the programmer, is it better to create a** loop **to print the character e.g. 100 times, or to manually** print **it?

I mean, programming-wise is it more efficient to have something like:

```
for i=0 to 100 print *
```

or to have:

```
print ********************........*****   (100 times)
```

assuming that it is not a matter of saving the programmer some time of having to type * one hundred times in the second case?

Maybe another option is to have a separate function to print that character and call it with parameter the amount of times? Like:

```
function print_many (times) { for i=0 to times print *}
```

Which is the best way?

---

### Post by Tomosaur on 2007-03-27
A loop would be better. Computers are pretty much designed to loop through instructions anyway. There is also the consideration that a string of 100 *s would take up more memory than a pointer to the beginning of the print procedure (which is what is happening at the machine level in a loop).

If you had a really clever compiler, it may recognise that your string of 100 *s is less efficient than a loop, and simply convert it into the loop approach at machine level anyway.

Your procedure approach is no different than using:
```

for i to 100:
  print "*"

```

Where i is an integer passed to the program via the command line.

---

### Post by Poisson_Pilote on 2007-03-27
If it is set by the programmer, it is best to do a loop. In C, you can even do it with a constant so it'll be easier to change in the future:

#define CST_LOOP 5

[...Code...]

for(i=0;i<CST_LOOP;i++)
{
  printf("*");
}

---

### Post by lnostdal on 2007-03-27
Best way is to generate the constant at compile-time:

```
(defparameter *str* (make-string 100 :initial-element #\*)) 
```

.. *str* now contains a string of hundred * characters. No need to compromise.

---

### Post by Poisson_Pilote on 2007-03-27
Ugh, just a personal opinion, but isn't that unoptimized ? (besides from being very ugly code :))

---

### Post by lnostdal on 2007-03-27
As opposed to what? Calling print 100 times each time you want a string with 100 *'s? No.

edit: Oh, and it is compiled to native optimized machine code.

---

### Post by ibanezix on 2007-03-27
Where t1 is the time that you guys responded and t2 is the time I take to finish a simple function:

t1 < t2 // by far!

I am going with the loop, and I suppose that when my knowledge of programming is deaper I will try the compile-time definition.

Thank you.

---

### Post by lnostdal on 2007-03-27
..or like this:

```

(defmacro genStr (char num)
  (make-string num :initial-element char))

```

Now any form similar to `(genStr x y)' in your code will be replaced by a string literal at compile time. So when you see..

```

(genStr #\a 10)

```

..in your code, you can mentally replace it with..

```

"aaaaaaaaaa"

```

..because that is what the compiler sees.

---

### Post by Wybiral on 2007-03-27
I like lnostdals solution, building it once and saving it as a string to use whenever.

In C, something like:
```

   int i;
   char some_array[101];
   for(i=0; i<100; ++i)
   {
      some_array[i] = '*';
   }
   some_array[100] = '\0';

```

I put the "\0" at the end of the array so it can be used as a string.

Only using one loop would certainly be the best way to go... This way you don't have to manually type out the string, which would bloat your source, but you get the speed increase of not using loops, the memory address can just be sent to "printf" instead of character-by-character calling the function and having to initialize the loop iterator and perform the conditional checks on the loop.

This, of course, is assuming you plan to use the string more then once... If this is a one time thing, then a simple loop in place will do.

---

### Post by slavik on 2007-03-27
well, this is an argument of whether you want to optimise for code size vs. code speed.

having the loop makes a very short piece of code, but not having a loop, makes the code long yet fater to run (since there is no increment and check).

also, if you optimise a for loop for speed, gcc will actually expand that loop, so you do end up calling printf so many times. printf, while not very expensive is still a system call ...

I say print the string in one pass, unless you need the space for other things.

it also depends on the size of the loop you want to do ...

---

### Post by Wybiral on 2007-03-27
Well, whether it unrolls the loop or not, you'd still be making the function call for each character if you do it in place.

But he can put it all in one string with a loop, then only have to make one call to the print function (for whatever language he's using). This seams like the best way...

It's only a *tiny* bit larger in source then just using the loop in place, but you can reuse the string AND you don't have to call the print function for every character. I'd say it's a winner.

---

### Post by hod139 on 2007-03-27
This is more than an argument about code size versus code speed. lnostdal's solution is a form of metaprogramming, he is making the preprocessor do work that is normally done at runtime.  In this case, he is unrolling the loop and generating a string literal. 

You can do the same thing in C++ without having to use the horrible C macro system though by using template metaprogramming.  Here is one way to do it using functors and template metaprogramming:

```

#include <iostream>

template< int i >
class PRINT_MANY{
  public:
    const void operator()(void) const
    { 
      std::cout << "*";
      PRINT_MANY<i-1>()(); 
    }
};

template <>
class PRINT_MANY< 1 >{
  public:
      const void operator()(void) const
      { std::cout << "*\n"; }
};


int main(void)
{
  PRINT_MANY< 100 >()();
  return 0;
}

```The templated function  PRINT_MANY recursively calls itself during compilation, and the compiler continually makes these classes until PRINT_MANY< 1 > is reached.  All the recursion is done by the compiler.  If you were to look at the assembly produced by this, there would be no loop.  Instead, there would be 100 cout statements.

---

### Post by Wybiral on 2007-03-27
Functors... *shivers*

lol.

But if it generates 100 cout calls, wont that bloat your executable and the performance (lots of function calls)?

---

### Post by hod139 on 2007-03-27
> **Wybiral said:**
> 
But if it generates 100 cout calls, wont that bloat your executable and the performance (lots of function calls)?
For this example, probably.  I guess I got caught up in the metaprogramming, and felt like writing a C++ example.  You can, however, do much more powerful stuff with template metaprogramming, one common example is computing factorial. 

I could alter the above example to produce a string literal similar to lnostdal's macro example (maybe I will). The point of my example is to show how you can shift work normally done at runtime to be done at compile time using templates.

---

### Post by lnostdal on 2007-03-27
Yes, performance-wise it is probably worse than calling printf 100 times.  

Space-wise it is probably not too good either; it generates at compile-time 100 different functions each containing a copy of the same code (cout'ing the same character).

---

### Post by hod139 on 2007-03-27
Here's an example that creates a string literal

```

#include <iostream>
#include <string>

template< int i >
class PRINT_MANY{
  public:
    const void operator()(std::string &result) const
    { 
      result.push_back('*');
      PRINT_MANY<i-1>()(result); 
    }
};

template <>
class PRINT_MANY< 1 >{
  public:
      const void operator()(std::string &result) const
      { 
        result.push_back('*');  
        result.push_back('\n');
      }
};


int main(void)
{
  std::string j;
  PRINT_MANY< 100 >()(j);
  std::cout << j;
  return 0;
}

```

Now, at runtime j will be a string containing 100 "*"s.  The compiler recursively built it.  I could have probably made the classes contain the string and not pass it in, but this was fastest.

---

### Post by silas_irl on 2007-03-27
[quote=Inostdal]Yes, performance-wise it is probably worse than calling printf 100 times. [/quote]Yeah it definitely is, the templated code generated in general tends to be very bloated and in this case would add significant overhead to the solution.

It depends on how the compiler is optimised.  If it's for speed then the compiler will be limiting the number of function calls it has to make. So the most intuitive solution would be to create a block of memory that can hold the 100 '*'s and issue a printf call with this block.

Below is an example of unrolling the simple loop, you don't need to do it, any half decent compiler will see the loop can be easily unrolled and will do it for you.

```
char *mem = malloc(101 * sizeof(char));
for (int i = 0; i < 100; i += 5)
{
   mem[i] = '*';
   mem[i+1] = '*';
   mem[i+2] = '*';
   mem[i+3] = '*';
   mem[i+4] = '*';
}

mem[i+1] = '\0';
printf(mem);
free(mem);

```

Someone described printf() as a system call, it is not one, it's an ansi c system library call.  A system call is a function that is normally belonging to the OS.  Such as open, close, write, dup, stat.  Generally its a low-level function.

---

### Post by hod139 on 2007-03-27
Ok, my last post.  Here is the example such that you do not have pass in the string, but a literal is instead returned.

```

#include <iostream>
#include <string>

template< int i >
class PRINT_MANY{
  public:
    std::string operator()() const
    { 
      return std::string("*" + PRINT_MANY<i-1>()());
    }
};

template <>
class PRINT_MANY< 1 >{
  public:
      std::string operator()(void) const
      { 
        return std::string("*\n");
      }
};


int main(void)
{
  std::cout << PRINT_MANY< 100 >()();
  return 0;

}

```

It might be neat to compare this binary code with a macro based or compiler unrolled loop binary.

---

### Post by lnostdal on 2007-03-27
got things like memset btw.

```

char* mem = malloc(101);
memset(mem, '*', 100); mem[101] = '\0';

```

---

### Post by hod139 on 2007-03-27
> **lnostdal said:**
> got things like memset btw.

```

char* mem = malloc(101);
memset(mem, '*', 100); mem[101] = '\0';

```

You can do that with std::strings as well, but I didn't think that was the point of this :)

```

std::string foo(100, '*');

```

---

### Post by Wybiral on 2007-03-27
memset... Why didn't I think of that! It's really fast too. Nice call lnostdal.

---

### Post by pmasiar on 2007-03-27
You are wasting your time guys. Python has **obviously** :-) superior way to print 'a' 100 times is:

print 'a' * 100

And in case it is not obvious, it was joke. It depends what you want optimize for. Python is optimized for obviousness - hence Python way is obviously better :-)

Long live language nitpicking wars! :-)

---

### Post by hod139 on 2007-03-27
> **pmasiar said:**
> You are wasting your time guys. Python has **obviously** :-) superior way to print 'a' 100 times is:

print 'a' * 100

And in case it is not obvious, it was joke. It depends what you want optimize for. Python is optimized for obviousness - hence Python way is obviously better :-)

Long live language nitpicking wars! :-)

In C++ you can do
```

cout << string(100, '*');

```

Not too difficult in C++ either :). 

 I, admittedly, got hooked on the template metaprogramming solution when there are obviously easier ways.  Guess that's the power and downside of C++

---

### Post by gus sett on 2007-03-27
this one is flexible, though high on I/O.  so you can #define a string of, for example,
20 to 32 asterisks, vary CST_LOOP from 5 to 3 accordingly...but in the latter instance
you'd have to tack on 4 more * to get 100 :wink: 
> **Poisson_Pilote said:**
> If it is set by the programmer, it is best to do a loop. In C, you can even do it with a constant so it'll be easier to change in the future:

#define CST_LOOP 5

[...Code...]

for(i=0;i<CST_LOOP;i++)
{
  printf("*");
}

---

### Post by Mr. C. on 2007-03-27
This is a text-book example of very smart people proposing solutions *before* clarifying the requirements and goals.

The initial question has no universal right or wrong answer.

MrC

---

### Post by gus sett on 2007-03-27
Aha, but you didn't ask for additional clarification before responding
either :mrgreen:

---

### Post by Mr. C. on 2007-03-27
> **gus sett said:**
> Aha, but you didn't ask for additional clarification before responding
either

This makes no sense at all.  Where is the solution I proposed ?  You're not going to cut it in programming with such illogical conclusions.

MrC

---

### Post by gus sett on 2007-03-27
exactly, a bystander commenting on respondents.  I drew no conclusion,
but your last assessment is erroneous by many yrs.
> **Mr. C. said:**
> This makes no sense at all.  Where is the solution I proposed ?  You're not going to cut it in programming with such illogical conclusions.

MrC

---

### Post by rplantz on 2007-03-27
Here are two solutions, looping and not looping, in assembly language. The code could be tightened up a bit at the expense of maintainability (IMHO).
```

# lineLoop.s
# Prints a line of '*'

        .equ    stdout,0
        .equ    length,70
        .data
theString:
        .byte   '*'
newLine:
        .byte   '\n'
        .text
        .globl  main

main:
        pushl   %ebp        # save base pointer
        movl    %esp, %ebp  # set new base pointer
        pushl   %ebx        # save for counter variable
        movl    $length, %ebx
loop:   pushl   $1          # write one char at a time
        pushl   $theString  # address of the character
        pushl   $stdout     # write to standard out
        call	write
        addl    $12, %esp   # remove arguments from stack
        decl    %ebx        # decrement counter
        ja      loop        # go back if > 0
        
        pushl   $newLine    # do a newline
        pushl   $stdout     # write to standard out
        call	write
        addl    $12, %esp   # remove arguments from stack

        movl    $0, %eax    # return 0;
        movl    %ebp, %esp  # restore stack pointer
        popl    %ebp        # restore base pointer
        ret
```
```

# line.s
# Prints a line of '*'

        .equ    stdout,0
        .equ    length,70
        .data
theString:
        .fill   length,1,'*'
        .byte   '\n'
        .text
        .globl  main

main:
        pushl   %ebp        # save base pointer
        movl    %esp, %ebp  # set new base pointer

        pushl   $length+1   # number of bytes to write
        pushl   $theString  # address of string
        pushl   $stdout     # write to standard out
        call	write
        addl    $12, %esp    # remove arguments from stack
        
        movl    $0, %eax    # return 0;
        movl    %ebp, %esp  # restore stack pointer
        popl    %ebp        # restore base pointer
        ret

```
Looking at the sizes:
```

bob@ubuntu:~/programing$ ls -l line
-rwxr-xr-x 1 bob bob 6112 2007-03-27 13:52 line
bob@ubuntu:~/programing$ ls -l lineLoop
-rwxr-xr-x 1 bob bob 6109 2007-03-27 13:59 lineLoop
bob@ubuntu:~/programing$ 

```
shows they are very close.

They both run so fast, coming up with good timing numbers would take some time. :)

---

### Post by Wybiral on 2007-03-27
Oh yeah? Take this...

```

BITS 32
  
org 0x08048000

ehdr:
   db 0x7F, "ELF", 1, 1, 1, 0
   dw 0000, 00000, 0, 0, 2, 3
   dd 1, _start, phdr-$$, 0, 0
   dw ehdrsz, phdrsz
ehdrsz equ $-ehdr

phdr:
   dd 1, 0, $$, $$, filesz, filesz, 5, 0x1000
phdrsz equ $-phdr

  _start:
  
   mov al, 'd'
   for:
      push byte '*'
      dec al
   ja for

   mov  al, 4
   mov  bl, 1
   mov ecx, esp
   mov edx, 400
   int 80h

   mov eax, 1
   int 80h
  
filesz equ $-$$

```

Read 'em and weep... **104** bytes! :)

That's NASM assembly BTW, compiled with...

```

nasm -f bin -o a.out program_name.asm
chmod +x a.out

```

---

### Post by rplantz on 2007-03-27
I've never used nasm. I taught assembly language to students who already knew C/C++. My approach was to teach what was "going on under the hood" rather than writing in assembly language. So one of the teaching tools I used is the -S gcc option. Also, it made sense (to me) in my teaching methodology to use a main function and link with all the C standard libraries.

The assembly language I posted was intended to show approximately what the C compiler would do, and that both approaches are about the same size.

Anyway, if I wanted to ignore C and write in "pure" assembly language, I would probably do something like:
```

# line.s
# Prints a line of '*'
        .equ    stdout,0
        .equ    sys_write,4
        .equ    length,70
        .data
theString:
        .fill   length,1,'*'
        .byte   '\n'
        .text
        .globl  _start

_start:
        movl    $length+1, %edx   # number of bytes to write
        movl    $theString, %ecx  # address of string
        movl    $stdout, %ebx     # screen
        movl    $sys_write, %eax  # write
        int     $0x80             # system call

        movl    $1, %eax          # back to kernel
        int     $0x80

```
which takes .... **100** bytes. :) I don't know offhand if the system looks at the high-order parts of eax and ebx. If not, I could save a few bytes by storing the stdout and sys_write codes in al and bl.

---

### Post by rplantz on 2007-03-27
By the way, does nasm produce a listing where you can see the machine code. Here's the gas (gnu assembler) listing, which shows the machine code:
```

   1              	# line.s
   2              	# Prints a line of '*'
   3              	        .equ    stdout,0
   4              	        .equ    sys_write,4
   5              	        .equ    length,70
   6              	        .data
   7              	theString:
   8 0000 2A2A2A2A 	        .fill   length,1,'*'
   8      2A2A2A2A 
   8      2A2A2A2A 
   8      2A2A2A2A 
   8      2A2A2A2A 
   9 0046 0A       	        .byte   '\n'
  10              	        .text
  11              	        .globl  _start
  12              	
  13              	_start:
  14 0000 BA470000 	        movl    $length+1, %edx   # number of bytes to write
  14      00
  15 0005 B9000000 	        movl    $theString, %ecx  # address of string
  15      00
  16 000a BB000000 	        movl    $stdout, %ebx     # screen
  16      00
  17 000f B8040000 	        movl    $sys_write, %eax  # write
  17      00
  18 0014 CD80     	        int     $0x80             # system call
  19              	
  20 0016 B8010000 	        movl    $1, %eax          # back to kernel
  20      00
  21 001b CD80     	        int     $0x80

```

---

### Post by Wybiral on 2007-03-28
lol, it's like an assembly showdown!

I've got 404 bytes after stripping yours. Did you use any special assemble technique?

As far as NASM disassembly goes, I usually just use a hex editor (I'm starting to memorize the bytes for the 386's)

The source I posted was cheating as far as size goes because I built the elf executable header and program header manually by just saving the right bytes in place.

Yours inlines the bytes of the star in the executable, right? Wouldn't that mean it could never be less then the number of bytes (plus the executable header)?

OK, this time I REALLY cheated because I stole some of the bytes from the elf header (why are there so many 0 bytes after the elf ID?) to put five of the stars so I could write them by fives...

```

; Save as:
;    stars.asm
;
; Assemble:
;    nasm -f bin -o a.out stars.asm
;
; Set permission:
;    chmod +x a.out

BITS 32
  
org 0x08048000

ehdr:
   db 127, 69, 76, 70,  1, 1, 1

star:
   db  42, 42, 42,  42, 42
   dw   0,  0,  2,   3,  1, 0
   dd  _start, phdr-$$,  0, 0
   dw  ehdrsz, phdrsz
ehdrsz equ $-ehdr

phdr:
   dd 1, 0, $$, $$, filesz, filesz, 5, 0x1000
phdrsz equ $-phdr

_start:
   mov di, 20
   for:
      mov  al, 4
      mov ecx, star
      mov  dl, 5
      int 80h
      dec di
   ja for

   mov al, 1
   int 80h
filesz equ $-$$

```

Executable size after assembled: 99 bytes :)
Size after being stripped... 99 bytes, lol (strip is no match for me)

I'm not sure how much further we can take this, lol, I'm out of ideas.

We should assembly dual more often...

Optimizing is like a puzzle, I actually enjoy the challenge.
The solution eventually ends up being a hacky mess like my code above ^ but it's still fun to see how much you can compress something... It certainly isn't something you would want to present in a serious project, but you can learn some practical optimization techniques along the way in case one ever does serve a practical purpose!

EDIT:

BTW, this is the OP's fault for not saying what language he needed the solution in, lol.

---

### Post by ibanezix on 2007-03-28
> **Wybiral said:**
> BTW, this is the OP's fault for not saying what language he needed the solution in, lol.

I realised that after two or three answers, but by then the talk had already become so interesting...

---

### Post by jvc26 on 2007-03-28
That was such a fascinating conversation guys! Very interesting to see the method get stripped down and down. Anyhew, thought I'd drop the line it was pretty fascinating lol,
Il

---

### Post by Wybiral on 2007-03-28
Alright... This is the smallest I could hack it and still have a working program...

```

; Save as:
;    stars.asm
;
; Assemble:
;    nasm -f bin -o a.out stars.asm
;
; Set permission:
;    chmod +x a.out

BITS 32
  
org 0x08048000

ehdr:
   db 127, 69, 76, 70, 0

_start:
   mov di, 100
   push byte '*'
   jmp begin
   dw 2, 3, 1, 0
   dd  _start, phdr-$$

next:
   int 80h
   dec di
   ja  for
   mov al, 1
   int 80h
   dw  32

phdr:
   dd 1, 0, $$, $$
   dd filesz, filesz

begin:
   mov ecx, esp
   for:
      mov  al, 4
      mov  dl, 1
   jmp next

filesz equ $-$$

```

Final size? 76 bytes!!!

Naturally, it's a tangled mess of slipping in code where header information should be... BUT, it assembles and it works. 100 stars, 76 bytes.

I wonder if there's enough assembly programmers around here to have a weekly assembly programming contest!!! That would be both fun and educational. I haven't seen a lot of assembly posted though, so probably not.

Anyway...

xor eax, eax
inc eax
int 0x80

---

### Post by rplantz on 2007-03-28
> **ibanezix said:**
> I realised that after two or three answers, but by then the talk had already become so interesting...

Thank you for saying that, ibanezix. I was feeling sorta guilty for "hijacking" your thread.

---

### Post by gus sett on 2007-03-29
Glad you chipped in, too.  it was fascinating, not 
too much of a stretch, & done really well to boot. 
glad also the OP left it open. 
> **rplantz said:**
> Thank you for saying that, ibanezix. I was feeling sorta guilty for "hijacking" your thread.

---

### Post by samjh on 2007-03-30
I profiled the two methods in Java:

Execution time: 3.29ms (average of three runs)
Heap memory used: 947.408 bytes
```
for (int i=0; i<100; i++) {
    System.out.print("*");
}
```

Execution time: 0.396ms (average of three runs)
Heap memory used: 886,208 bytes
```
System.out.println("*******************************************************" + 
    "*********************************************");
```

So in Java, the straight print is clearly faster (more than 8 times), and uses slightly less heap memory.

Interestingly, the execution times for the two code fragments differed wildly between runs.  The for-loop had much smaller variance, with the fastest being around 1.9ms, and slowest around 3.6ms.  The straight print had huge variance, being fastest at around 0.2ms, and slowest around 0.85ms.

Heap sizes were constant for every run.

---

### Post by slavik on 2007-03-30
I think that with something like a print loop, it is possible for a scripting language (perl, python, etc) to actually become faster faster than a compiled language (if not optimised).

printing to a terminal is a system call and the interpreter can be spmart enough to realise that it can simply accumulate the printing into it's own buffer and print it in one shot. but then, the compiler can be that smart, too ...

we need to test something on the order of millions of characters to be printed, anything below 1000 will not be 'slow enough' to measure ...

---

### Post by Wybiral on 2007-03-30
> **slavik said:**
> I think that with something like a print loop, it is possible for a scripting language (perl, python, etc) to actually become faster faster than a compiled language (if not optimised).

printing to a terminal is a system call and the interpreter can be spmart enough to realise that it can simply accumulate the printing into it's own buffer and print it in one shot. but then, the compiler can be that smart, too ...

we need to test something on the order of millions of characters to be printed, anything below 1000 will not be 'slow enough' to measure ...

I don't know... I doubt you're going to get any faster then mine and rplantz assembly... It's raw system calls and direct register manipulation. No middle man. With as interpreted language, there's really no telling how it's going to do it, unless you study the languages source code or have a VERY VERY detailed manual on it's workings (down to it's compile process and VM) but how many here can raise they're hands for that one?

It would be cool to find a way to time it though and see just how far out of the water the machine code blows the interpreted ones, lol.

---

### Post by samjh on 2007-03-30
> **slavik said:**
> we need to test something on the order of millions of characters to be printed, anything below 1000 will not be 'slow enough' to measure ...

Well, you asked for a million, so here are the results using Java:

Compiled using Sun JDK 1.5.0_8
Running on Sun JRE 1.6.0 Server VM

Profiler: Netbeans 5.5 Profiler

Code for looped method (profiled code fragment in **bond** font):
```
[b]for (int i=0; i<1000000; i++) {
    System.out.print("*");[/b]
}
```

Code for straight printing (profiled code fragment in **bold** font):
```
String theString = "";
    
for (long i=0;i<1000000;i++) {
    theString.concat("*");
}
        
**System.out.print(theString);**
```

Results from 5 consecutive runs for each algorithm (shown in order with first run at the top, last run at the bottom).  Netbeans was started up three times - first to get the JVM running, second time to profile the loop code, third time to profile the straight printing code.

**Loop**

Execution time (ms) | Maximum heap memory usage (bytes)

3349 | 2920752
3619 | 2763184
3393 | 2253408
3617 | 3109816
3576 | 2742864

**Straight printing**


Execution time (ms) | Maximum heap memory usage (bytes)

0.120 | 4003480
0.067 | 4001448
0.070 | 4001296
0.056 | 4001448
0.069 | 4003480

--------------------------------------

The disparity becomes clearer with this test.  Straight printing still wins hands down.  There doesn't seem to be any effort on the part of the VM to optimise the loop.  Complexity of the looped algorithm remains linear - as can be expected.  On the other hand, the straight printing method remains extremely fast (56 microseconds!), although with heavier toll on memory.

Code review is also welcome.  It was a quick 30-second throw-out of code, so it could do with improvements, I'm sure. :)

(Also interestingly, do you notice the symmetry in heap memory usage for the straight printing implementation?  I'm sure it's just coincidence, but it's weird.)

---

### Post by lnostdal on 2007-03-30
yeah, without buffering the asm might be slower (edit: but not beceause it is "compiled" ofc.) .. but if the asm either implements buffering or calls something that will buffer the output it will be the same or faster

---

### Post by Wybiral on 2007-03-30
You can buffer it on the stack with ASM pretty easily, that's actually how C and C++ allocate function scope variables (by subtracting the bytes from the ESP register)

If the number of stars is predetermined you can even use the .bss or even constant bytes in the file itself.

---

### Post by Wybiral on 2007-03-30
This is incredibly generic, non-optimized NASM assembly. It's actually called from a C function...

```

; Save as:
;    atest.asm
; Assemble with:
;    nasm -f elf atest.asm

global  asmFunc

asmFunc:
   mov  edx, [esp+4]
   mov  ebx, edx
   FORLOOP:
   push 544043841
   dec  ebx
   ja   FORLOOP
   mov  eax, 4
   mov  ebx, 1
   mov  ecx, esp
   int  0x80
   mov  eax, edx
   mov  edx, 4
   mul  edx
   add  esp, eax
   ret

```

It can then be initiated with this C code...

```

// Save as:
//    ctest.c
// Compile with
//    gcc atest.o ctest.c

void asmFunc(long count);

int main()
{
   asmFunc(1000000);
}

```

It easily prints out 1000000 characters. I haven't been able to profile it (I don't have any profilers that work with NASM assembly, if anyone knows of any, let me know).

It could also be written as pure assembly (without being called from C) but I thought it was more interesting this way :)

---

