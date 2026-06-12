---
title: "Random fact of the day (&quot;Hello _start!&quot;)"
date: 2007-04-04
forum: Programming Talk
---

### Post by Wybiral on 2007-04-04
GCC does not care if it compiles an object file without the "main" label. It also doesn't care if you use the "_start" label (which is where the linker designates as the program entry.

So I found an interesting trick to make combining C and assembly a little easier (and smaller)...

Save this as "mylib.asm":
```

section .text
   global print
   global exit

print:
   mov ecx, [esp+4]
   xor edx, edx
   dec edx
print_loop:
   inc edx
   cmp [ecx+edx], byte 0
   jne print_loop
   mov eax, 4
   mov ebx, 1
   int 0x80
ret

exit:
   mov eax, 1
   mov ebx, [esp+4]
   int 0x80
ret

```

Then assemble it using: nasm mylib.asm -f elf

Now save this as "mytest.c":
```

void print(char*);
void exit(long value);

void _start()
{
   print("Hello _start!\n");
   exit(1);
}

```

And compile that using: gcc mytest.c -c
You will now have two object files "mylib.o" and "mytest.o"
Simply link them with: ld mylib.o mytest.o -s
Now you have "a.out"... That's it!
Now look at the size of "a.out": 576 bytes!
The size of a regular "Hello _start!\n" in C: 3076 bytes

Take that C!

Anyway, that was my random fact of the day!

(this is 32 bit Intel assembly btw)

---

### Post by mardawi on 2007-04-04
interesting!

---

### Post by kpatz on 2007-04-04
Is your regular 3076-byte version using a main() function, or something other than your print() function to write the hello string?

Standard I/O adds some overhead, which you eliminated using your ASM print() routine.  main() has overhead for building argc and argv[], etc. which you eliminated by using _start().

---

### Post by Wybiral on 2007-04-04
> **kpatz said:**
> Is your regular 3076-byte version using a main() function, or something other than your print() function to write the hello string?

Standard I/O adds some overhead, which you eliminated using your ASM print() routine.  main() has overhead for building argc and argv[], etc. which you eliminated by using _start().

Yeah, I was comparing a normal C program that uses libc with my non-libc version that uses my assembly routines.

---

### Post by j_g on 2007-04-04
What worries me about this approach is that, directly overriding the entry point that the compiler would normally create, may also bypass some initialization that should be done. For example, who initializes any global instances of C++ objects or unitialized global C structs? Who initializes the _stdout variable, or other global variables, used by other C library functions that your app may call? (In particular, I'd be worried about any global variables associated with the malloc function). Unless you plan to totally forego all other calls to C library functions (which doesn't appear to be at all practical under Linux), and make sure you do all needed initialization (that otherwise would have been done by the default startup code), then this can have some dangerous implications. For example, calling the C library function exit() could result in that function attempting to do some cleanup based upon the assumption that the compiler's normal startup code allocated/initialized certain resources.

When I write DLLs for Windows, I do in fact deliberately bypass the startup code. But I also do not call any C lib functions unless I know that they're entirely safe, and I also provide my own initialization and cleanup code that work together appropriately. For example, I allocate memory using the API GlobalAlloc, rather than the C lib's malloc. I'm very careful about knowing all the implications of bypassing the compiler's defaults.

I'm not sure that the above approach has considered, and accounted for, those implications.

---

### Post by Wybiral on 2007-04-04
Yeah... But I know how C works and I don't need any startup code. It was for fun, nothing serious.

BTW, that's my exit function, not C's... It's just a system call.

I was just showing that you could compile C code as if it were assembly and bypass the need for main or libc.

And that code does "totally forego all other calls to C library functions"... Why is that hard in Linux?

I'm glad my code "worries" you... lol.

---

### Post by j_g on 2007-04-04
> It was for fun, nothing serious.

I see. Well, I do use this exact thing seriously on Windows. I was thinking of doing the same thing on Linux, but I decided against it because:

1). I don't think that it's practical for a C/C++ program to avoid using the C library on Linux.

2). Bypassing the compiler's startup code can have serious implications on use of the C library.

> that's my exit function, not C's... It's just a system call.

Ah right, I missed that. But is it doing all of the necessary termination that would otherwise be done by the C library exit() function on Linux? I have little doubt that the compiler's default cleanup code eventually calls that. (When I do the similiar thing on Windows, I do ensure that I account for such implications. For example, if you simply go with the default Windows compiler cleanup for an EXE, it eventually calls the API ExitProcess(). If you bypass the compiler's cleanup code, you _must_ make that call yourself).

I'm not sure that such implications have been considered, and accounted for.

> And that code does "totally forego all other calls to C library functions"... Why is that hard in Linux?

Because your example does nothing useful. It is presumed that a programmer would want to otherwise do something useful, in which case, I don't think it practical for a C/C++ program to forego use of the C library on Linux.

---

### Post by Wybiral on 2007-04-04
Maybe you don't grasp this... The C library is not being used. There is nothing to initialize or cleanup.

Are you suggesting that Linux assembly is harder then Windows/DOS assembly?

The practical reason for something like this would be to organize your assembly programs. You can write all of the libraries in assembly (and link to other object files) and then use C code to manage everything since it's easier to manage then assembly code on it's own.

The point (yes, I will say it again) is that libC is not used, it's basically just using the C language without any of it's internals. As a means of organizing assembly functions.

The print/exit functions I wrote could easily be made useful if you added some other functions to the mix (like file or device IO). This was an *example*

---

### Post by j_g on 2007-04-04
> The C library is not being used.

Your example does nothing useful. My comments about use of the C library are in the context of typical C code, which obviously will want to do something more useful.

> Are you suggesting that Linux assembly is harder than Windows/DOS assembly?

I'm not talking about assembly at all. I am talking about bypassing the compiler's startup code, and the implications of that. The fact that you used assembly code to aid your effort to bypass the C startup code is irrelevant to this.

> The practical reason for something like this would be to organize your assembly programs. You can write all of the libraries in assembly (and link to other object files) and then use C code to manage everything since it's easier to manage then assembly code on it's own.

If you're going to use "C code to manage everything" in the above scenario, then you either need to make sure that you don't use the C library at all (which under Linux, I think places a pretty big practical limitation on what you can do in C -- if it's just to manage asm code, why not just code everything in asm as long as you have to defeat C advantages such as foregoing the C library?), or make sure you understand and account for the implications of using the C library while also bypassing the compiler's default startup and cleanup code.

> it's basically just using the C language without any of it's internals. As a means of organizing assembly functions.

I thought you were going for minimizing code size while still using C for the majority of the logic. Otherwise, I really don't see the point of mixing C and asm. In fact, placing limitations like "the C part can't use the C library" seems counterproductive. If you're going to write the majority of your logic in asm, why not just code the whole thing in asm? Then you don't have to deal with any compiler/C issues.

---

### Post by Wybiral on 2007-04-04
This isn't typical C code...

Did you even read my original post and code?

And why is not using libC useless in Linux in particular?

What startup code are you talking about?

Why use C to manage assembly? Because it's cleaner looking. Because you can use...

```

my_function(a, b, c);

```

Instead of...

```

sub esp, 12
mov [esp], eax
mov [esp+4], ebx
mov [esp+8], ecx
call my_function
add esp, 12

```

Why would you object to this?

What is your point?

---

### Post by j_g on 2007-04-04
> Why use C to manage assembly? Because it's cleaner looking.

Ok, well, it would have helped if you had told what was your intent with the example right from the start.

I had assumed that your initial intent was to minimize the code size of a C program. That wasn't your intent. (To be fair, you mentioned making a C compiled example "smaller", and you made a point to note that bypassing the C startup code made it smaller. So I think my interpretation was reasonable).

I responded with what I thought (and still do) were valid points about the problems of bypassing the C startup and cleanup code, especially on Linux where use of the C library is such a given for C programming.

_Now_ I find out that it wasn't about minimizing C code size at all. Apparently, your point is that asm code is not "clean looking", C code is "clean looking", so therefore it's a good idea to use C to "clean up" asm code.

In that case, my reply would be: Don't use asm code. Use C entirely. It will make your code look "cleaner".

---

### Post by slavik on 2007-04-04
I had a graphics prof that used to do gamedev and they wrote their game in pascal (I think) but all the graphics libraries were written in assembly :)

---

### Post by phossal on 2007-04-04
Wybiral, what resources did you use to learn assembly?

---

### Post by Wybiral on 2007-04-05
> **phossal said:**
> Wybiral, what resources did you use to learn assembly?

Most importantly the Intel manuals...
Various tutorials around the web...
And C compiler output.

j_g:
Still... What do you mean when you say:
> especially on Linux where use of the C library is such a given for C programming.
Why "especially one Linux"?

And what startup cleanup code are you talking about?
I've studied compiler output for a while now, AND the C library but I have no idea what you're talking about.

---

### Post by Wybiral on 2007-04-05
This is a simple itoa function added to the last library...
```

section .text
   global print
   global itoa
   global exit

print:
   mov ecx, [esp+4]
   xor edx, edx
   dec edx
print_loop:
   inc edx
   cmp [ecx+edx], byte 0
   jne print_loop
   mov eax, 4
   mov ebx, 1
   int 0x80
ret

itoa:
   mov ecx, [esp+4]
   mov eax, [esp+8]
   mov ebx, 10
   push ebx
   itoa_loop:
      cmp eax, ebx
      jl itoa_skip
      xor edx, edx
      div ebx
      push edx
   jmp itoa_loop
   itoa_skip:
      add al, byte 48
      mov [ecx], byte al
      inc ecx
      pop eax
      cmp eax, ebx
   jne itoa_skip
   mov [ecx], byte 0
ret

exit:
   xor eax, eax
   inc eax
   mov ebx, [esp+4]
   int 0x80
ret

```

And then a complimentary C program...

```

void print(char*);
void exit(long);
void itoa(char*, long);

void _start()
{
   long i;
   char buf[4];
   for(i=0; i<20; ++i)
   {
      itoa(buf, i);
      print("Iteration: ");
      print(buf);
      print("\n");
   }
   exit(1);
}

```

As far as size goes... If you assembly+compile+link as before, the size ends up being 1169 bytes. 

If you use a C program like this:
```

void print(char*);
void exit(long);
void itoa(char*, long);

int main()
{
   long i;
   char buf[4];
   for(i=0; i<20; ++i)
   {
      itoa(buf, i);
      print("Iteration: ");
      print(buf);
      print("\n");
   }
   exit(1);
}

```

Even with the assembly library being used, it's 6930 bytes.

Now, I know j_g, this program doesn't "do anything" by your standards. It's an example. It wouldn't be hard to extend it with more functions using assembly.

BTW: Yes I'm aware that that would overflow with larger then 3 digit numbers.

---

### Post by slavik on 2007-04-05
here's another "thing" ... #include simple tells the cpp to paste the file isntead of that line ... and gcc might also becompiling those functions even though they are not used (I haven't looked)... also, can you compare your atoi() versus the one in the library?

---

### Post by Wybiral on 2007-04-05
itoa isn't standard C actually.

Yes, "include" does add any code in it to the program during compile.

---

### Post by j_g on 2007-04-05
> What do you mean when you say: especially on Linux

Because use of the C library is ubiqitous in Linux C apps. Few C programmers do syscalls in their apps in lieu of using the C library. Even though I tend to eschew using the C library in my Win32 apps, I don't consider it very practical in Linux C apps.

---

### Post by j_g on 2007-04-05
> This is a simple itoa function added to the last library. The size ends up being 1169 bytes.

But what does it accomplish replacing the C library? I have absolute certainty that some app that is currently running on your system already has the C library loaded. I have rarely seen any significant C programs that eschew the C library, and a Linux system typically relies upon lots of C apps to get up and running.

Replacing the compiler startup/cleanup code may be useful (ie, directly reduces the size of the exe and can get rid of some unneeded init), if you know what the implications are and code around them. But I think that trying to bypass use of the C lib altogether is pointless on Linux.

I don't see any purpose to writing an asm itoa() function, to be called by C. Just use the C lib. It's undoubtably already loaded into memory, so your attempt to reduce the size of your exe on disk may very well be resulting in increasing your exe's footprint in memory.

---

### Post by Wybiral on 2007-04-06
> **j_g said:**
> But I think that trying to bypass use of the C lib altogether is pointless on Linux.

I don't see any purpose to writing an asm itoa() function, to be called by C. Just use the C lib.

Still... Why is it pointless in LINUX? Linux has very nice assembly support and very powerful syscalls. I don't find writing practical apps in Linux assembly difficult at all. No one uses Linux system calls? I use them almost daily.

Why not use the C itoa? Because it isn't standard! There's no guarantee that everyone will have it. But, if someone has Linux and a 386 processor, they can use that assembly.

Also, most of the C library was actually written in C and could use to lose the extra baggage that the compiler usually tosses in.

---

### Post by j_g on 2007-04-06
> Linux has very nice assembly support and very powerful syscalls. I don't find writing practical apps in Linux assembly difficult at all.

It's not about writing an app in assembly. It's about writing an app in C, while attempting to forego use of the C library. Use the C library if you're writing in C/C++. The C library is undoubtably already loaded in memory (as a shared lib), so it will reduce your exe's footprint in memory, and it's a lot easier and "clean-looking" than your hybrid approach. I don't see any advantage to the latter.

> Why not use the C itoa? Because it isn't standard!

What Linux distribution's C library _doesn't_ have itoa() (or sprintf, which can achieve the same result)?

> most of the C library was actually written in C and could use to lose the extra baggage that the compiler usually tosses in.

But if it's already loaded into memory (which is pretty much a given on most every Linux distro), then you've not really gaining anything. There may be some advantage to replacing the entire C library with one that is written entirely in asm (and frankly, I've seen plenty of C libraries that do indeed code often used functions in asm), but replacing parts of it within an exe is not very useful. I think this is one area where optimization is not really all that effective nor advised.

---

### Post by phossal on 2007-04-06
I have always been suspicious that Wybiral creates these other names just to have conversations with himself. ;) Stop it.

---

### Post by Wybiral on 2007-04-06
Yes phossal, 90% of the conversations I engage in on these forums do actually seem to be with myself :)

But j_g is still missing the point... I never said this as a serious approach. He's just arguing to argue... I said it as a "random fact" or just for fun.

BTW, sprintf receives the same results data-wise... But not performance wise.

So... Argue the point of this all you want... I quit.

---

### Post by mardawi on 2007-04-07
i've learned a lot out of this discussion... and i think others did too... so it wasn't useless!

---

### Post by pmasiar on 2007-04-07
> **Wybiral said:**
> I never said this as a serious approach. He's just arguing to argue... I said it as a "random fact" or just for fun.

I understand both points, you and j_g. You, Wybiral, program for fun, and trying to pull things apart and put them together to see how they work, to become skilled hacker. Hacker in old sense of course.

j_g is coming from Windows world, where things are done *proper way*  and not for fun. J_G things about preparing code to scale up -- Enterprise ready. If possible, using XML :-)

And occasionally j_g may be even right - seems to me that except of some very rare scaled-down Linux distro, proper library *will* be present, and even loaded in shared memory, so you don't save real memory. Of course you still have that learning experience. And as we remember J_G promoted idea of supporting only selected subset of distros (selected by some unknown authority - herding kernel hackers, LOL), so that possible obscure memory-starved distro is not even of the radar ATM. :-) and is not definitely "Enterprisey".

So it is cultural issue.

---

### Post by slavik on 2007-04-07
> **pmasiar said:**
> I understand both points, you and j_g. You, Wybiral, program for fun, and trying to pull things apart and put them together to see how they work, to become skilled hacker. Hacker in old sense of course.

j_g is coming from Windows world, where things are done *proper way*  and not for fun. J_G things about preparing code to scale up -- Enterprise ready. If possible, using XML :-)

And occasionally j_g may be even right - seems to me that except of some very rare scaled-down Linux distro, proper library *will* be present, and even loaded in shared memory, so you don't save real memory. Of course you still have that learning experience. And as we remember J_G promoted idea of supporting only selected subset of distros (selected by some unknown authority - herding kernel hackers, LOL), so that possible obscure memory-starved distro is not even of the radar ATM. :-) and is not definitely "Enterprisey".

So it is cultural issue.

Quoted for truth! :)

---

### Post by Wybiral on 2007-04-07
> **pmasiar said:**
> And occasionally j_g may be even right - seems to me that except of some very rare scaled-down Linux distro, proper library *will* be present, and even loaded in shared memory, so you don't save real memory. Of course you still have that learning experience.

Learning experience aside... If he suggests using itoa, then he's suggesting to use a non-c99 standard function, which isn't a good thing to promote in the C world at all.

I presents fact that you can make GCC act like an assembler.

He presents advice with using non-c99 standard function.

---

### Post by pmasiar on 2007-04-07
> **Wybiral said:**
> I presents fact that you can make GCC act like an assembler.

OK, Maybe even you are right, I cannot tell :-) I am not expert in low-level hacking like that - it is long time since I decided I will ignore assembly for now on. 

I am just amazed at the level you are playing - it is just fascinating that people still find it interesting to dig that deep and poke around... I just tried to hint about different goals, different approach, like different cultures: you are learning for fun, for hacking skills, for deep understanding how things work deep inside, not for enterprise appeal of your solution. 

I personally prefer to play at application level. But I also understand how small can be pretty: Once I created a very simple (but playable) text adventure game engine, one page of code (60 lines or so, of course Python :-) ). I should publish it somewhere...

---

### Post by Wybiral on 2007-04-07
> **pmasiar said:**
> I just tried to hint about different goals, different approach, like different cultures: you are learning for fun, for hacking skills, for deep understanding how things work deep inside, not for enterprise appeal of your solution. 

Well said pmasiar.

I'm not trying to promote some crazy new idea for serious applications, I was just playing around with things and presenting a fact of how GCC can create a "_start" object instead of main to bypass using libC.

---

### Post by j_g on 2007-04-07
> coming from Windows world, where things are done *proper way*  and not for fun.

There are plenty of Windows programmers who don't do things the "proper way". I've seen their code. And also, plenty of Windows programmers who program for fun, myself included.

In fact, I started out writing applications entirely in assembly. I'm very, very big on reducing code size (in memory, not so much on disk because hard drive space isn't really a problem). That's why, I had _already_ thought about the possibility of bypassing the gcc startup and cleanup code in Linux apps and foregoing all use of the C library, just like how I routinely do in my Windows apps with MSVC's compiler. But I decided against it because it's pretty much a given that a C/C++ app is going to use the C library on Linux. The C library is a major component of the Linux OS (and I seem to recall reading that gcc even handles the linking to it in a different way than other shared libs, in order to optimize use of it).

Sometimes, in an effort to reduce code size, you reach the point of diminishing returns, and in the case of attempting to forego use of the C library in a Linux C/C++ app, that's true. As I point out, the C lib is undoubtably already loaded into memory, so you _don't_ decrease the footprint of your running app. (You actually increase it). Also, a hybrid C/asm approach is not "easy" nor "clean-looking". These were reasons that Wy previously gave for taking the approach he did. Now, he has switched to citing merely the reason "I did it for fun, but it has no practical use.". Fine. Yes, it has no practical use. (Well, the part of foregoing the C lib altogether is impractical. I think that the act of bypassing gcc's default startup/cleanup code _could_ be useful. But the experiment needs to gauge what impact that has on the C library -- such as what C lib funcs are then not safe to call. I'd like to see a serious experiment with this. Obviously, Wy's experiment is not that).

> J_G promoted idea of supporting only selected subset of distros

Yes, and I still do. Being that GNU's C library has itoa(), and I suspect that a distro which doesn't use it is a very obscure one, I would therefore recommend that a Linux programmer not worry about supporting a Linux distro that doesn't support itoa(). Leave that support to people who have time to waste.

And it's up to each individual programmer to determine what's worth supporting. I simply urge Linux programmers to be more discerning in how they expend their time and effort, focussing upon the major distros to improve and advance them, and to do their part to stem the plague of Linux forking by not supporting everything released by Tom, Dick, Harry, and their pet poodles.

P.S. There's no need to employ Wy's approach for the purpose of "making gcc act like an assembler". GCC already supports inline assembly. If you need it, use that.

---

### Post by Wybiral on 2007-04-07
> **j_g said:**
> P.S. There's no need to employ Wy's approach for the purpose of "making gcc act like an assembler". GCC already supports inline assembly. If you need it, use that.

I will say this once again... It was a random fun-fact... Not some crazy new "approach" as you're calling it.

I don't understand why you insist on trying to make your way the only way... Here's an idea... Let people enjoy programming and experiment with new things instead of just randomly ridiculing everything that isn't done your way. :)

---

### Post by j_g on 2007-04-07
:: rolls eyes ::

You originally billed this a way of making a C example "smaller" and "easier". I posted some things that I thought were important as further consideration, also noting how and why your example was neither smaller nor easier. You then changed your mind, and decided this was about using C to glue together some asm routines to make code "clean-looking". I reiterated that there is still an issue about foregoing the C library in any practical use of C, and suggested that there is nothing "clean-looking" about hybrid C/asm code. You then changed your mind, and decided this was all about fun with no practical use at all. As I said earlier, it would really help if you made up your mind what you're saying _before_ you post. Then you wouldn't have to get so defensive when someone has to point out how each one of your shifting theories is not really true, up until the point where you finally all but admit that those theories weren't valid to begin with.

---

### Post by Wybiral on 2007-04-07
"Random fact of the day"

---

### Post by j_g on 2007-04-07
With the emphasis upon "random" apparently, and de-emphasis upon "facts".

---

### Post by pmasiar on 2007-04-07
EXACTLY - with no enterprise-level XML in sight - pure fun. :-)

---

### Post by Wybiral on 2007-04-07
> **j_g said:**
> With the emphasis upon "random" apparently, and de-emphasis upon "facts".

There was a fact, it just wasn't good enough for you :)

Sorry.

---

### Post by phossal on 2007-04-08
Everyone hates a know-it-all who doesn't. I'm not sure you weren't clear enough about your intentions in your first post, Wybiral. I'm sure the new guy will mellow out once he gets the hang of things, or has to deal with a few dozen people like himself.

---

### Post by weldan on 2007-04-09
:lolflag:

---

