---
title: "So... what's the fastest lang?"
date: 2006-07-03
forum: Programming Talk
---

### Post by Lster on 2006-07-03
Speed is a real issue in my next project so I was wondering "What is the fastest language?". Probably G++ or GCC isn't it?

---

### Post by bieber on 2006-07-03
Assembly language.

---

### Post by dabear on 2006-07-03
[QUOTE=bieber]Assembly language.[/QUOTE]
If you know how to code in ASM that may be true, but C is so close and has a good standard library.

---

### Post by LordHunter317 on 2006-07-03
GCC and G++ aren't languages, they're compilers.  Incidentally, they're some of the slowest out there for their respective languages.

---

### Post by Horsman on 2006-07-03
If you are a great Assembly Coder, you'll find it the fastest but its absolutely unuseable in terms of GUI and project development.

C is easily the fastest near-full feature language, best as compiled with gcc.

---

### Post by Daverz on 2006-07-03
The ocaml people claim near C++ performance.  You might also check out sbcl.

---

### Post by LordHunter317 on 2006-07-03
[QUOTE=Horsman]C is easily the fastest near-full feature language, best as compiled with gcc.[/QUOTE]I'm not sure how one really define fully-featured, but I'm certain no matter how you define it, C isn't it.

---

### Post by IYY on 2006-07-03
C.

---

### Post by Horsman on 2006-07-03
I meant that its not a language that only applies to one thing, like say data conversion or database management. 

I too agree that C lacks in many things, but it's still a standard among many programmers.

---

### Post by Max Luebbe on 2006-07-03
Depends on how you're defining fastest!
If you're talking execution speed: 
ASM followed by C

If you're talking about fastest time to deployment/finished product:
Probably either Python, Java or another language with managed memory, that may not execute as fast, but will save you lots of time hunting and fixing memory bugs.

---

### Post by jtull89 on 2006-07-03
As I understand it, you can make usable programs in Perl with just a few lines. However, C and C++ run fast, if compiled and programmed well.

---

### Post by hod139 on 2006-07-04
I do believe fortran is faster than C, and the numerical libraries available for it are unbeatable.

---

### Post by LordHunter317 on 2006-07-04
Yes, for numerical stuff, FORTRAN is generally very hard to beat.

---

### Post by Max Luebbe on 2006-07-04
Fortran cannot be beat for floating point work.

All the hardcore numerical simulations are done in it, and all the faculty at my former school's engineering dept swear by it anytime theyre doing intensive stuff like Fluid Dynamics.

Can't say I like to write Fortran though.

---

### Post by pharcyde on 2006-07-05
What kind of work will this application be doing?  I think it really depends on what target system you are looking to write it for and readability of code v speed v size.  There are so many techniques when it comes to code performance it really depends on what you are tryign to do.  More efficient algorithms and programmign techniques usually speed up a program more than using a particular language.  Granted there are always exceptions to the rule.

---

