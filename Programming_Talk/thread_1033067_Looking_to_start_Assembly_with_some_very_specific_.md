---
title: "Looking to start Assembly with some very specific issues"
date: 2009-01-07
forum: Programming Talk
---

### Post by JFASI on 2009-01-07
I've been looking to start using assembly for a long time now, and the only thing holding me back is the fact that all my computers are PPC based macs. I think I have a solution, and I know I have a problem: 

I can use Bochs to emulate an x86 machine and use this as my platform, but I will need an assembler! So I have two options. I can emulate Linux, which is excruciatingly slow, but would give me the advantage of being able to use the friendly GNU toolchain, or I could emulate DOS, which would be faster and less headache inducing, but would require me to get a DOS assembler. 

Personally, I prefer the second one, as I've once tried to emulate the Linux 2.6 kernel with Q, which failed spectacularly, and I have a pile of fallback options, more notably DOSBox. The only problem is I need an oldschool DOS assembler. Man this is a weird question to ask the Ubuntu forums, but yeah...

---

### Post by emmary on 2009-01-07
China Health Beauty Device Wholesale 
  
Nowadays people spend billions of dollars annually on health and beauty stuff. TRADESTEAD offers products for daily care. If you want inspiring performance in a compact package, our products are solid and satisfying choices. This kind of products on tradestead.com mainly falls into two categories, namely electrical massager and hair trimmer. 

Related Categories: USB Devices Bluetooth Device MP4 Players Car Monitors Pedometers Bluetooth Adapters
 
 
 


 Electrical Massagers 
 
 


 Hair Trimmers

---

### Post by Joeb454 on 2009-01-07
Moved to Programming Talk :)

---

### Post by Zugzwang on 2009-01-07
There's NASM, which is a free x86 assembler for a couple of platforms, including Linux, Windows and DOS.

---

### Post by JFASI on 2009-01-07
That's great. How would one go about linking that with C programs, though? Is it enough to compile a .o and let something like the venerable Turbo C compile it?

---

### Post by jimi_hendrix on 2009-01-07
mingw or cygwin ftw

then after you gcc'ed your C program use 
nasm -f win32 -o programName foo.asm
to compile you asm

link with ld

---

### Post by Zugzwang on 2009-01-07
> **jimi_hendrix said:**
> mingw or cygwin ftw

then after you gcc'ed your C program use 
nasm -f win32 -o programName foo.asm
to compile you asm

link with ld

Wouldn't run on DOS since cygwin or mingw is for win32 (except if you run Windows 3.1+win32 or Windows 95 in your dosbox. :-))

There's also that old DJGPP running in DOS, that might be working.

---

### Post by rplantz on 2009-01-08
> **JFASI said:**
> That's great. How would one go about linking that with C programs, though? Is it enough to compile a .o and let something like the venerable Turbo C compile it?

One of the many nice things about gcc is that you can easily mix C and assembly language functions. Place them in separate files and do:
```

gcc -o myProg myProg.c asmSub.s cSub.c

```
Probably better is to do:
[code}
as --gstabs -o asmSub.o asmSub.s
gcc -c -g -o myProg.o myProg.c
gcc -c -g -o cSub.o cSub.c
gcc -o myProg myProg.o asmSub.o cSub.o
[/code]
Another advantage of this is that it will automatically link in the C standard libraries. So you can use printf and scanf to do I/O from your asm functions. For example,
```

# echostring1.s
# Prompts user to enter a text string, then echoes it

        .data                  # the data segment
prompt:
        .string "Enter up to 100 characters: "
response:
        .space  101            # memory for user input string
format:
        .string "%s"

        .text                  # switch to text segment
        .globl  main

main:
        pushl   %ebp           # save caller's base pointer
        movl    %esp, %ebp     # establish our base pointer

        pushl   $prompt        # prompt user to enter string
        call    printf         # print the message
        addl    $4, %esp       # delete the argument

        pushl   $response      # place to store input
        pushl   $format        # "%s" format
        call    scanf          # get user input
        addl    $8, %esp       # delete the argument

        pushl   $response      # pass address to function
        pushl   $format        # "%s"
        call    printf         # echo the text string
        addl    $8, %esp       # delete the argument

        movl    $0, %eax       # return 0
        movl    %ebp, %esp     # restore stack pointer
        popl    %ebp           # restore caller's base pointer
        ret                    # back to calling function

```

---

### Post by wmcbrine on 2009-01-09
There's nothing wrong with learning PPC assembly instead of (or in addition to) x86. The basic principles are the same -- the key is to learn the *style* of asm programming, rather than a particular instruction set. Once you know one flavor of asm, you can pick up new instruction sets fairly easily.

Also, rumors of the PowerPC's death have been greatly exaggerated... it's not in new Macs, but it's in other places, like game consoles -- one of the areas where knowledge of asm may still be highly valued.

---

### Post by pmasiar on 2009-01-10
> **wmcbrine said:**
> There's nothing wrong with learning PPC assembly instead of (or in addition to) x86. The basic principles are the same -- the key is to learn the *style* of asm programming, rather than a particular instruction set. Once you know one flavor of asm, you can pick up new instruction sets fairly easily.

Exactly

> Also, rumors of the PowerPC's death have been greatly exaggerated... it's not in new Macs, but it's in other places,

another place is high-performance computing. IIRC, IBM's [http://en.wikipedia.org/wiki/Bluegene](http://en.wikipedia.org/wiki/Bluegene) is based on PowerPC

---

### Post by rplantz on 2009-01-11
> **wmcbrine said:**
> There's nothing wrong with learning PPC assembly instead of (or in addition to) x86. The basic principles are the same -- the key is to learn the *style* of asm programming, rather than a particular instruction set. Once you know one flavor of asm, you can pick up new instruction sets fairly easily.

Another "exactly" here. I've programmed in asm on a dozen architectures. I once had a software manager tell me that I wrote FORTRAN like an assembly language programmer. I was flattered. 

> **wmcbrine said:**
> Also, rumors of the PowerPC's death have been greatly exaggerated... it's not in new Macs, but it's in other places, like game consoles -- one of the areas where knowledge of asm may still be highly valued.
And, in my opinion, the PowerPC architecture is **MUCH** prettier than x86. But that's not hard to do. :-)

---

