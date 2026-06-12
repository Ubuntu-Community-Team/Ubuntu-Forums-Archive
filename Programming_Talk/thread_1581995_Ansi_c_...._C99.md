---
title: "Ansi c .... C99"
date: 2010-09-25
forum: Programming Talk
---

### Post by KdotJ on 2010-09-25
I've just started to have a look at C, my uni course will be using it in the up and coming semester to I decided to get a head start and read up and practise. I got a book from my uni library titled "C: How to program" (5th ed). 
I'm finding the book great so far, very well explained and I can easily skip a lot of general programming stuff (control statments etc) as I have experience in Java. 

The book however, is fairly old... it focuses on ANSI C and explains that a newer standard, C99, is now out but has not been widely adopted yet.

My question is, as the time has passed since the publication of this book, what is the *normal* standard now? Has C99 made it there? or is it still usually ANSI C that is worked with?


Thanks in advance

---

### Post by unknownPoster on 2010-09-25
ANSI C = C99

[http://en.wikipedia.org/wiki/ANSI_C](http://en.wikipedia.org/wiki/ANSI_C)

---

### Post by KdotJ on 2010-09-25
Thank you for the reply, I was just a bit confused, because when trying to compile a C program which had a for loop with the counter declaration in the for header, like so:

```

for (int i = 0; i < 10; i++) {
    //blah blah blah
}
```

.. when compiling with **gcc**, I get the following error:

```
error: ‘for’ loop initial declarations are only allowed in C99 mode
```

---

### Post by worksofcraft on 2010-09-25
I think C is mostly for old legacy code and new projects use C++.

Someone here told me of the new ANSI proposal standard [http://en.wikipedia.org/wiki/C%2B%2B0x](http://en.wikipedia.org/wiki/C%2B%2B0x) but personally I prefer it stays more as a kind of portable and object oriented assembler ;)

---

### Post by trent.josephsen on 2010-09-25
> **unknownPoster said:**
> ANSI C = C99

[http://en.wikipedia.org/wiki/ANSI_C](http://en.wikipedia.org/wiki/ANSI_C)
False, at least in the communities I frequent.  ANSI C is C89.  ISO is the standards organization responsible for all subsequent C standards, C99 included.  (ANSI adopted the C99 standard in 2000, but "ANSI C" is still used to refer to the earlier standard.)

@worksofcraft: The next C standard is in the works, often referred to as C1X, but it is in a very incomplete state.  Also, C++ is not a successor to C.  They hardly even compete in the same domains now-a-days, which is one reason I can see for many people thinking that C is dead (one of my pet peeves).  Know that the world is larger than your back yard.

@OP:  The book is still correct; C99 is out, but has not been widely adopted in many areas C dominates.  C89 is the lowest common denominator.  That said, there's nothing wrong with using C99 on systems that support it, which are pretty common in their own right.

---

### Post by unknownPoster on 2010-09-25
> **trent.josephsen said:**
> False, at least in the communities I frequent.  ANSI C is C89.  ISO is the standards organization responsible for all subsequent C standards, C99 included.  (ANSI adopted the C99 standard in 2000, but "ANSI C" is still used to refer to the earlier standard.)


It's not false, it's just a difference in semantics and we can argue that point all day to no end.

---

### Post by wmcbrine on 2010-09-25
> **unknownPoster said:**
> ANSI C = C99C99 is an ANSI standard, yes; but when people say "ANSI C", they usually mean C89.

Sadly, C99 is *still* not widely adopted. Gcc doesn't fully support it, even now.

[http://gcc.gnu.org/c99status.html](http://gcc.gnu.org/c99status.html)

---

### Post by Vox754 on 2010-09-25
> **worksofcraft said:**
> I think C is mostly for old legacy code and new projects use C++.

Someone here told me of the new ANSI proposal standard [http://en.wikipedia.org/wiki/C%2B%2B0x](http://en.wikipedia.org/wiki/C%2B%2B0x) but personally I prefer it stays more as a kind of portable and object oriented assembler ;)

It always irks me that you don't seem to realize that C and C++ are different languages.

Compile C code with gcc, and C++ with g++, understand this!

You definitely need to forget about assembler for a while, in order to understand higher-level concepts.

---

### Post by dwhitney67 on 2010-09-25
> **KdotJ said:**
> ...

.. when compiling with **gcc**, I get the following error:

```
error: ‘for’ loop initial declarations are only allowed in C99 mode
```

Compile your code with either the -std=c99 or -std=gnu99 options to successfully compile your code.

Personally, I use an alias for gcc; it is defined as follows:
```

alias gcc='gcc -Wall -pedantic -D_GNU_SOURCE -std=c99'

```

---

### Post by worksofcraft on 2010-09-26
> **Vox754 said:**
> It always irks me that you don't seem to realize that C and C++ are different languages.

Compile C code with gcc, and C++ with g++, understand this!

You definitely need to forget about assembler for a while, in order to understand higher-level concepts.

lol

IMO C++ is a super set of C. C is obsolete. They are both just portable assembler and I never use gcc. If I ever should want anything different...  well Python is quite a cute little interpreter I suppose :)

---

### Post by schauerlich on 2010-09-26
> **worksofcraft said:**
> IMO C++ is a super set of C. C is obsolete. They are both just portable assembler and I never use gcc. If I ever should want anything different...  well Python is quite a cute little interpreter I suppose :)

[No](http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B). Also, [no](http://james-iry.blogspot.com/2010/09/moron-why-c-is-not-assembly.html). Language != implementation. C and C++ can (and have) been implemented as [interpreted languages](http://en.wikipedia.org/wiki/Ch_interpreter). C's semantics are just convenient to implement on current machines (by design). And as for C being obsolete... well, i don't even really know where to start there.

---

### Post by worksofcraft on 2010-09-26
> **schauerlich said:**
> [No](http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B). Also, [no](http://james-iry.blogspot.com/2010/09/moron-why-c-is-not-assembly.html). Language != implementation. C and C++ can (and have) been implemented as [interpreted languages](http://en.wikipedia.org/wiki/Ch_interpreter). C's semantics are just convenient to implement on current machines (by design). And as for C being obsolete... well, i don't even really know where to start there.

lol yeah interpreted C/C++ is called PhP I think...
Anyway apart from the fact I'm not going to even look at that blog spot because it's title is insulting to it's audience,
joking aside, you have to look at what the language was **designed** for and it's pedigree:

Popularity of C stem from the way it could be used as a portable and structured language to drive hardware and write the unix kernel that was much more maintainable than dedicated assembler. 

When I stopped programming back in late 90's, C++ had already taken over as the the number one choice for real-time and embedded applications. IMO that is where it excels, that is it's primary and original intent and there are  plenty of other languages available for other things so trying to make C or C++ suitable for them is utterly futile.

---

### Post by KdotJ on 2010-09-26
Thank you all for the replies and clearing things up for me. For now I'm just going to use gcc as normal without the C99 flag as for uni I'm guessing I should go with the book, but it it's good to know. I'm going to continue C in my spare time and once I've finished the book I'll look into the features of C99. As for the C++ stuff, i have in the past considered taking to learn it but as I already practise an OO language, java, I'll skip it for now.

---

### Post by trent.josephsen on 2010-09-26
> **worksofcraft said:**
> lol yeah interpreted C/C++ is called PhP I think...
Ha ha!  Sorry, I thought you were just willfully ignorant.  I didn't know you were making a funny.

> When I stopped programming back in late 90's, C++ had already taken over as the the number one choice for real-time and embedded applications
Classic.  I ROFL'd.  Keep it coming.

---

### Post by worseisworser on 2010-09-26
> **worksofcraft said:**
> lol yeah interpreted C/C++ is called PhP I think...
Anyway apart from the fact I'm not going to even look at that blog spot because it's title is insulting to it's audience,
joking aside, you have to look at what the language was **designed** for and it's pedigree:

Popularity of C stem from the way it could be used as a portable and structured language to drive hardware and write the unix kernel that was much more maintainable than dedicated assembler. 

When I stopped programming back in late 90's, C++ had already taken over as the the number one choice for real-time and embedded applications. IMO that is where it excels, that is it's primary and original intent and there are  plenty of other languages available for other things so trying to make C or C++ suitable for them is utterly futile.

Oh shut up with the endless trolling and mischief already.


[quote=worksofcraft]
I think C is mostly for old legacy code and new projects use C++.
[/quote]

Here you say "projects" which is about as meaningless and vague as one can get. What are you talking about here?

The Linux kernel (as one kind of project) is very much used on embedded platforms (amongst others) and it is written in C, and the original author laughs at the very idea of using C++ in that context.

[http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918)
[http://www.realworldtech.com/forums/index.cfm?action=detail&id=110618&threadid=110549&roomid=2](http://www.realworldtech.com/forums/index.cfm?action=detail&id=110618&threadid=110549&roomid=2)

Still, regardless of what you mean by "projects" you know very well that C++ was *defined* in the late 90s (1998) so it could not have "taken over" *anything* at all by the end of that decade. You also very well know that it took *several years* before the various C++ implementations/compilers had somewhat proper support for the language.

edit:
As to being insulting to ones audience you've topped that several times already; the blog post is harmless ..

---

### Post by kahumba on 2010-09-26
Since gcc 4.4 to gcc 4.5 only 2 issues have been fixed towards having a full c99 implementation. At this pace we'll have to wait for like 5 years until we have full "C 1999" support (by like 2015). I know it's difficult to implement it but it shouldn't take that long either - it's ridiculous, not to mention that C is most likely the most important language that gcc supports (along with C++), so I think the gcc devs do need a "nudge" or some more help.

---

### Post by dwhitney67 on 2010-09-26
> **kahumba said:**
> Since gcc 4.4 to gcc 4.5 only 2 issues have been fixed towards having a full c99 implementation. At this pace we'll have to wait for like 5 years until we have full "C 1999" support (by like 2015). I know it's difficult to implement it but it shouldn't take that long either - it's ridiculous, not to mention that C is most likely the most important language that gcc supports (along with C++), so I think the gcc devs do need a "nudge" or some more help.

What are those 2 issues?  Do you require them?  Perhaps they are not that necessary.

The debate whether to use C99 or not is ridiculous.  Most people who develop code on a day-to-day basis don't have a clue as to what is missing, much less a complete picture of what is offered.

My thoughts -- write code in C++.  When the need to use C is necessary, which oftentimes it is not, then personally I would want to be able to write very similar style of code, without having to worry whether my declarations belong here or there, or whether I can get away with declaring a non-const pointer to a constant string literal, or whether I must use a certain style of comments.

Anyhow, my $0.02... which, with today's economy, is probably worth a mere $0.01.

---

### Post by The Cog on 2010-09-26
This thread is turning nasty instead of useful. I'm closing it.

---

