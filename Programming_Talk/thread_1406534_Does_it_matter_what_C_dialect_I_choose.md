---
title: "Does it matter what C dialect I choose?"
date: 2010-02-14
forum: Programming Talk
---

### Post by Wokzombie on 2010-02-14
After looking around I have found two information sources that look like a good point to start learning C with.

The first is K&R's [**C Programming Language (2nd Edition)**](http://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628) teaching 'ANSI C' which I assume is what people call C89/C90.
The second one that calls itself the [**The GNU C Programming Tutorial**](http://www.crasseux.com/books/ctutorial/) which I assume is either C89/C90 or C99 with a few GNU adjustments.
(I also noticed both of these information sources are mentioned [**here**](http://ubuntuforums.org/showpost.php?p=2045086) as well)

The thing is I will most likely program in GNU/Linux so I would guess the GNU C tutorial would be most fit for me, but the K&R book looks really good, and maybe even more important, complete.

Would I be able to mix-and-match information from both sources or would that become confusing?
And how important is it to focus on 'GNU C' in a GNU environment?

---

### Post by howlingmadhowie on 2010-02-14
As an inexperienced C programmer i would say that ANSI C is the way to go. You can be pretty sure that everything will compile well on lots of different compilers. Also i can't remember the differences being that large, so i don't think mixing literature will be confusing. 

Good luck with C :) It's a fun, powerful, if sometimes frustrating, language.

---

### Post by MadCow108 on 2010-02-14
Luckily there is not too much difference between the standards in C. The syntax is mostly the same.

Go with the newest one (C99) and if you really need the 20 years old C89 learn the differences when needed.
The most important differences I recall are that you need to place statements after declarations, you can't declare variables in for loop line (for(int i=0,;i++)) and you have no designated initializers.
I think you also don't have variable sized arrays, but all compilers I know add this as extension.

gcc provides a few warning flags which warn about code which is not C89 compatible.
Also gcc provides many of C99 features as extensions even for C89 code (then called gnu89)

gnu99 does not really add much stuff you really need often. But it does not harm to have a look at them when you only write for gcc.

here's a list
[http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/C-Extensions.html#C-Extensions](http://gcc.gnu.org/onlinedocs/gcc-4.4.3/gcc/C-Extensions.html#C-Extensions)
looks like much but most are C99 extensions for C89 and stuff only needed in specialized code.

---

### Post by gil_johnson on 2010-02-14
Does it matter? Probably not. As others have noted, there is not much difference.

C99, with or without gnu extensions, enforces some good practices, so I would compile the code with the C99 option, then recompile for ANSI C. You will probably not have to change anything, and if you do, you would have the "opportunity" to learn about C89.
Gil

---

### Post by Wokzombie on 2010-02-15
Thanks for the replies.

Seeing that C99 is preferred but that next to that the differences are somewhat ignorable I just went out and looked for a book that fit my learning style.

I found and bought [**C for Dummies**](http://www.amazon.com/C-Dummies-2nd-Dan-Gookin/dp/0764570684/ref=sr_1_1?ie=UTF8&s=books&qid=1266247380&sr=8-1). (Pause for laughter)

But really, I'm halfway though the third chapter and even though it's basic and a bit slow (which I prefer) it is a really good book that takes learning the C language seriously. (What you wouldn't expect with the 'for Dummies' title)
One thing I really like about it is that it pretty much starts out with debugging.

Thanks again =)

---

