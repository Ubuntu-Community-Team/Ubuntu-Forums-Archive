---
title: "Problem using printf with getenv (C/Ubuntu 10.04)"
date: 2011-08-22
forum: Programming Talk
---

### Post by gnometorule on 2011-08-22
While reading a book, I copied in the following little program:

```

#include <stdio.h>
#include <stdlib.h>

int main(){

    const char *d = getenv("TEST");
    printf("%s at address %p\n", "TEST", d);

    return 0;
}

```I define a token environmental variable TEST. Here are the predictions of the book, which make sense to me (it is on Ubuntu 6.10). Let's assume, which is about right for my system, that the stack frame for main starts at 0xbffff333 (I realize it varies, this is not the issue). Then, a copy of the environmental variables will be stored around 0x200-0x300 bytes higher, let's simplify and say starting at 0xbffff666. Let's assume our TEST variable starts at 0xbffff777. Then the book predicts (as seems clear) that the program prints 0xbffff777. The addresses can change somewhat on the system for different runs run, but that's the logic.

Here is what happens on my system: the value printed is way before $esp even (say, around 0xbf399999), which seems random and strange.

I debugged as follows:

(1) gdb, print out memory region around 0xbfff666. I find the regular env variables, and the one I defined at, say, 0xbffff777. 
(2) I  disassemble. After a system call to getenv, eax holds the address 0xbffff777, and hands this value on to the printf system call 
(3) printf prints, say, 0xbf39999 (varies by run, but always way too low).

I compiled switching off anything that could interfere, and that I could think of (gcc -O0 -static - fno-stack-protector). I also created an alternative version in which I reserved space on the heap to store the address returned there, to make sure that (1) the pointer returned is not overwritten by further system calls, and (2) as a poor-man's attempt to check if it was related to preventing smash protection (as one could insert shellcode into the env variable) - despite compiling with -fno-stack-protector, just doubly sure; the malloc allocated storage is (unsigned*) of the pointer (just to mangle it around and decouple). No avail.

I am confused. If you do the same, same result? What is going on? I am sure I am missing something really stupid, and my apologies for that.

EDIT: The address returned does point to the string I put into the env variable I defined - apparently, to its location in memory when no program runs (???). However, as we determine the address while the program runs - why that location? It should return the 0xbffff777, as the book, too, predicted, shouldn't it? The question is mostly academic, but I would very much like to understand.

---

### Post by ofnuts on 2011-08-22
Well, since Ubuntu 6, things happened. Operating systems have become very security conscious, and a very frequent line of attack is playing with stack contents. So changes to make the stack layout a bit less predictable may have been done.

---

### Post by gnometorule on 2011-08-22
That was my first guess, a form of smash protection to make the location of env variables less predictable. If this is the case, any elaboration on what is going on, or a source where to read up on it, would be great.

---

### Post by Bachstelze on 2011-08-23
I think you are confusing the string and the pointer. When I run your program, the pointer is indeed in the stack frame (i.e. between %ebp and %esp). The string itself is not, but there is no reason why it should be. As you correctly noted, it is in a memory region where all the environment variables are stored. Actually you can access this memory area with envp:

```
firas@applejack ~ % cat test.c 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char **argv, char **envp)
{
        char *d = getenv("HOME");

        /* Look for HOME in envp */
        char **e = envp;
        while (e != NULL) {
                if (strncmp(*e, "HOME=", 5) == 0) {
                        break;
                }
                e++;
        }

        printf("%p %p\n", d, *e);
}
firas@applejack ~ % gcc -std=c99 -pedantic -Wall -Werror -m32 -o test test.c 
firas@applejack ~ % ./test 
0xffab9ea0 0xffab9e9b

```

It is the same string (with an offset because the first one points to "/home/firas", while the second one points to "HOME=/home/firas"). envp always exists, so when you call getenv, it just returns the location of the value in envp, it does not create a new string on the stack.

If that was not your problem, then please explain it a bit more clearly because your message is not very clear.

---

### Post by gnometorule on 2011-08-23
I figured it out. I was unfamiliar with ASLR stack protection. What I describe is due to ASLR scrambling the memory address space to protect prediction of the location of variables relative to it. ASLR has long been default switched on in LINUX kernels it appears.

To see what I meant, get su privilieges, then enter (the precise integer to send might vary based on your distro; on mine it is 0, and the default 2):

```

cd /proc/sys/kernel
export OLD=$(less randomize_va_space) // save old value to restore after
echo 0 >  randomize_va_space  // 0 == turn off ASLR

```
Then run my little program again: it will report back the address I expected (around 0xbffffiii). After, obviously, restore old protection using
```

echo $OLD > randomize_va_space

```

Many thanks everyone as usual! Closing this now.

---

### Post by Bachstelze on 2011-08-23
After reading your message twice I still can't figure out what you expected or why, but okay. :p

---

### Post by gnometorule on 2011-08-23
:)
 
Prior to ASLR scrambling (when I say 'prior to', don't zoom into the way I express this as I don't know how the architecture is implememnted), env variables on the x86 are in the 0xfffffiii region, always. When running the simple program, in gdb you find references to those regions when checking the registers (gdb does not print ASLR generated memory regions - again, pls don't zoom into my formulations; I assume you understand what I mean). Hence, you have a pretty good idea where all your env variables are. After, they are all over the place. My goal was to print addresses in the regions that are generated prior to scrambling, or on systems with ASLR disabled (as in the distant past). 
 
Additionally, as gdb operates w/o ASLR, but ASLR is by default enabled, you see address differences between the printed value from the program output, and the one from machine code when single stepping through the gdb disassembly and looking at the gdb memory regions, which seemed completely unexplained  - the differences persisting even when I parked the gdb-generated address on the heap. And now it makes sense.

---

### Post by Bachstelze on 2011-08-23
> **gnometorule said:**
> 
Additionally, as gdb operates w/o ASLR, but ASLR is by default enabled, you see address differences between the printed value from the program output, and the one from machine code when single stepping through the gdb disassembly and looking at the gdb memory regions, which seemed completely unexplained  - the differences persisting even when I parked the gdb-generated address on the heap. And now it makes sense.

That's where I stop following you. For me, everything is consistent: the address stored in eax after getenv has returned is the same address that is stored in d, and printed, and if I run examine in gdb on this address, I will find my variable. The only difference ASLR makes is that the address will be different at each call. Also why are you mentioning machine code? Unless I missed something, the machine code says nothing about the location of the environment variables.

---

### Post by gnometorule on 2011-08-23
On my system, the system call to getenv returns its value into eax. In a variant of the code above, I store the returned pointer address on the heap (not in the code shown), to make sure nothing is due to the pointer simply being overwritten. I single step through. The value assigned to the heap variable is the one returned from eax  (in the 0xbffffiii region). I then print the value stored on the heap even before printing the original pointer. The value printed is not the one that I see put in the respective register before handing it on to the printf system call, instead at consistently lower, but variable locations. 

You are considerably more knowledgeable than me, and maybe this is what I should have expected. But w/o factoring in that gdb debugs "w/o ASLR", but printf operates in an ASLR enabled environment, this made no sense to me.

---

### Post by Bachstelze on 2011-08-23
This is interesting. Could you please post the problematic code? No offense, but I think you might be doing something wrong.

---

### Post by gnometorule on 2011-08-23
Certainly no offense taken. Your interest, level of knowledge, and readiness to help are most welcome. While I assembler hacked in the 80s, I've only recently come back to serious coding.

I did not have the file I referred to anymore, but this is what it should have been. I realize that the hacky storage of the pointer by miscasting it is weird, but I meant to decouple it as much as possible from what it really is. This is not related to the issue I'm getting at for sure.

```

#include <stdio.h>
#include <stdlib.h>

int main(){

    const char* d = getenv("TEST");
    unsigned* i = (unsigned*) malloc(sizeof(unsigned));
    i = (unsigned*) d;

    printf("heap address: 0x%8x\n", i);
    printf("stack address: %p", d);

return 0;
}

```

Run this per se, stepping, then after setting randomize... to 0, and you should see (assuming your system behaves like mine).

Incidentally, how do you copy from emacs into firefox etx.?

---

### Post by Bachstelze on 2011-08-23
Well...

```
firas@itsuki ~ % lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty
firas@itsuki ~ % cat /proc/sys/kernel/randomize_va_space
2
firas@itsuki ~ % cat test.c 
#include <stdio.h>
#include <stdlib.h>

int main(){

    const char* d = getenv("TEST");
    unsigned* i = (unsigned*) malloc(sizeof(unsigned));
    i = (unsigned*) d;

    printf("heap address: 0x%8x\n", i);
    printf("stack address: %p", d);

return 0;
}
firas@itsuki ~ % gcc -o test test.c            
test.c: In function &#8216;main&#8217;:
test.c:10:5: warning: format &#8216;%8x&#8217; expects type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;unsigned int *&#8217;
firas@itsuki ~ % ./test
heap address: 0xbffc8ff0
stack address: 0xbffc8ff0%  
```

> Incidentally, how do you copy from emacs into firefox etx.?

I'm a vim guy. ;)

---

### Post by gnometorule on 2011-08-23
True. I get what you get, when entering this. But that was not the point I was trying to make. 

When you single step through the disassembly while keeping track of the values in the registers that are handed on to the system calls. the value handed on is not the value printed. Again, maybe that is to be expected...but I found that most weird not knowing about ASLR (and gdb not 'using' it).

Edit: and this stops when you change the randomize flag.

---

### Post by Bachstelze on 2011-08-23
> **gnometorule said:**
> 
When you single step through the disassembly while keeping track of the values in the registers that are handed on to the system calls. the value handed on is not the value printed. Again, maybe that is to be expected...but I found that most weird not knowing about ASLR (and gdb not 'using' it).


You mean you're single-stepping through the machine code of getchar and all the calls it makes? It wouldn't surprise me if it did some weird things with the registers, but that's mostly irrelevant. What's relevant is what getchar returns (i.e. the value stored in eax after it returns), and this value is always the one that will be ultimately printed.

---

### Post by gnometorule on 2011-08-23
If I understood what you said correctly, it just doesn't (on setting '2' in randomize_va_space, the default). The value handed on ultimately to printf in its registers was, for me, not the value printed.

Edit: to be more precise, the value handed on **as shown by gdb**.

---

### Post by Bachstelze on 2011-08-23
> **gnometorule said:**
> If I understood what you said correctly, it just doesn't (on setting '2' in randomize_va_space, the default). The value handed on ultimately to printf in its registers was, for me, not the value printed.

The value is not handed to printf in a register in x86, it is passed on the stack like in any procedure call. And the value stored in eax after getenv returns is indeed the value printed:

```
(gdb) start
Temporary breakpoint 2 at 0x804842d: file test.c, line 6.
Starting program: /home/firas/test 

Temporary breakpoint 2, main () at test.c:6
6           const char* d = getenv("TEST");
(gdb) next
7           unsigned* i = (unsigned*) malloc(sizeof(unsigned));
(gdb) info register
eax            0xbfffffd1       -1073741871
ecx            0x54     84
edx            0x2      2
ebx            0x28bff4 2670580
esp            0xbffffae0       0xbffffae0
ebp            0xbffffb08       0xbffffb08
esi            0x0      0
edi            0x0      0
eip            0x804843d        0x804843d <main+25>
eflags         0x286    [ PF SF IF ]
cs             0x73     115
ss             0x7b     123
ds             0x7b     123
es             0x7b     123
fs             0x0      0
gs             0x33     51
(gdb) print d
$1 = 0xbfffffd1 "test"
(gdb) next
8           i = (unsigned*) d;
(gdb) 
10          printf("heap address: 0x%8x\n", i);
(gdb) print i
$2 = (unsigned int *) 0xbfffffd1
(gdb) cont
Continuing.
heap address: 0xbfffffd1
stack address: 0xbfffffd1
Program exited normally.

```

If you are using step or stepi, I would hazard a guess that you are reading the value of the registers at the wrong time.

---

### Post by gnometorule on 2011-08-23
You are obviously right, as I confirmed on my computer. I don't know how I could have misread the values as much. I also confirmed not only the p/o of 'd', but the values handed on in the registers as consistent with those printed.

What you do notice is that, when running through gdb, you get the 0xbfffffiii region addresses, when not, lower ones. It probably means that gdb disables scrambling during its runs. This is consistent across tries, and probably started my confusion as I could not reconcile the addresses returned with those from gdb. However, what you said is correct, and what I claimed wrong. Sorry for wasting time. I need to test even more thoroughly before making claims.

---

### Post by Bachstelze on 2011-08-23
> **gnometorule said:**
> You are obviously right, as I confirmed on my computer. I don't know how I could have misread the values as much. I also confirmed not only the p/o of 'd', but the values handed on in the registers as consistent with those printed.

What you do notice is that, when running through gdb, you get the 0xbfffffiii region addresses, when not, lower ones. It probably means that gdb disables scrambling during its runs. This is consistent across tries, and probably started my confusion as I could not reconcile the addresses returned with those from gdb. However, what you said is correct, and what I claimed wrong. Sorry for wasting time. I need to test even more thoroughly before making claims.

No prob, it was interesting. ;) And yes, I get the same thing as you when runnin in gdb vs. not: higher and consistent memory adresses.

---

