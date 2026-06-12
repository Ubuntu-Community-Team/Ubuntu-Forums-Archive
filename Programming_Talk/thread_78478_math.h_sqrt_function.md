---
title: "math.h sqrt function"
date: 2005-10-18
forum: Programming Talk
---

### Post by kalias on 2005-10-18
Hi!  I am just starting to do some C programming using gcc and I ran into a problem with the sqrt function.  I included math.h into my program but I get an error saying that sqrt is not found.  I checked the build-essential and that appears to be up to date.  Is there some place where the libraries for gcc are that I can check for this function?  Also, I was able to find the math.h header file in usr/ something or other but it did not have it.

Another question about gcc.  Is it by default ansi compliant or do I need to compile with the -ansi flag set to make it so?

thanks for any help :)

kalias :)

---

### Post by LordHunter317 on 2005-10-18
You'd need to compile -ansi.  Note that at least as of GCC 3.3, -ansi for C does C89, not C99.  

As for math, you did remembe to add '-lm' to link the math library, right?

---

### Post by SeanCallan on 2005-10-18
You could always just make your own function if you can't get it in the header.

LOL.  wow.  Today's been too long.

---

### Post by LordHunter317 on 2005-10-18
Except for the fact that's not a square root, sure...

---

### Post by kalias on 2005-10-18
Compile with -lm?  Um..no.   I have been doing the following from the command line:
gcc -o mathtest mathtest.c

I know this is probably very newbie ish so sorry for the dumb questions.

Sounds like there is more that I need to learn about gcc.
a) How do I make gcc C90 compliant? 
b) How to you setup the linker?  It currently appears to run automatically.

thanks for the help :)

kalias

---

### Post by toojays on 2005-10-18
Yep, there is certainly more for you to learn about gcc :)

A good start point would be to install gcc-doc and look at the info pages ("info gcc" at the command line, or "C-h i m gcc" in emacs).

The section "standards" in the emacs manual tells you what you need to know to turn on C90 compliance mode.

As for the linker, yes it will run automatically by default. If you just want to compile (and not link), use the '-c' flag. To link against the math library, use "-lm". You can find out more about these flags in the "invocation" section in the manual.

---

### Post by kalias on 2005-10-19
Thanks toojays :)  I gave it a try and it works great.  I installed all the documentation also.  There is really something to be said for linux.  Here I am using a free compiler and I get help within hours.  I also have microsoft visual .net which I paid money for and to get help with that takes days or weeks. Besides, I hate it! Gcc is much nicer especially for newbies like myself.  

Thanks alot for your help :)

kalias
btw: For development which ide do you think is better kdevelop or ajunta?

---

### Post by toojays on 2005-10-19
You're welcome.

Personally I prefer to work closer to my tools, so I use GNU Emacs and GNU Make, rather than a full blown IDE. I've not used kdevelop or ajunta, but they both have a fair following . . . I'm sure they're both good.

---

