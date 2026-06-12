---
title: "NOOB -  &quot;Hello World&quot; kinda question here"
date: 2007-05-21
forum: Programming Talk
---

### Post by timdoc1 on 2007-05-21
Tried to 'GCC' my program and I got compiler errors indicating stdlib.h and stdio.h etc are missing:

tim@bigguns:~$ gcc pthread.c
pthread.c:3:21: error: pthread.h: No such file or directory
pthread.c:4:20: error: stdlib.h: No such file or directory
pthread.c:5:19: error: stdio.h: No such file or directory
pthread.c: In function ‘main’:

How do I fix this?

---

### Post by bukwirm on 2007-05-21
Did you install the "build-essential" package?

---

### Post by timdoc1 on 2007-05-21
Can you tell me it's abbreviation in the Synaptic package manager????
Tim

---

### Post by timdoc1 on 2007-05-22
Found it, but doesn't look like the STDLIB.  Used for compiling DEBIAN !

---

### Post by WW on 2007-05-22
> **timdoc1 said:**
> Found it, but doesn't look like the STDLIB.  Used for compiling DEBIAN !
I don't understand what you mean.

**build-essential** is "meta-package"--it depends on the compilers gcc, g++, some standard libraries and a couple of tools.  If you install **build-essential**, either with Synaptic or with the command **sudo apt-get install build-essential**, you will be able to compile a "Hello, world" C program that uses stdio.h.

---

### Post by joe_bruin on 2007-05-22
> **timdoc1 said:**
> Tried to 'GCC' my program and I got compiler errors indicating stdlib.h and stdio.h etc are missing:

tim@bigguns:~$ gcc pthread.c
pthread.c:3:21: error: pthread.h: No such file or directory
pthread.c:4:20: error: stdlib.h: No such file or directory
pthread.c:5:19: error: stdio.h: No such file or directory
pthread.c: In function ‘main’:

How do I fix this?

What you need, among other things, is to install the libc6-dev package.  This will put pthread.h, stdlib.h, and stdio.h in /usr/include/

Now your program will compile, but it will not link.  It will tell you that ld (the linker) cannot find the pthread functions ("undefined reference to `pthread_create'").  To link properly, you will have to tell gcc to use the pthread library using -l (that's a lower-case L).

$ gcc yourprogram.c -lpthread

Note that the -l argument must be the *last* thing on your command line.

---

### Post by timdoc1 on 2007-05-22
OK. Thanks so much, unfortunately, I need a follow-up so sorry for the hand-holding here.

My output is wrong, in VI it looks like this:
^?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@<80><84>^D^H4^@^@^@T^O^@^@^@^@^@^@4^@ ^@^G^@(^@$^@!^@^F^@^@^@4^@^@^@4<80>^D^H4<80>^D^Hà^@^@^@à^@^@^@^E^@^@^@^D^@^@^@^C^@

Just a bit longer.  It should only be "a"'s and "b"'s in the output (it's a very small program.

Question is :  Could this be possible becasue I installed 32 bit C libraries on my 64 bit Fiesty install?  Who can one tell what the install was? (32 vs. 64bit)?

Thanks,
Tim

---

### Post by Mirrorball on 2007-05-22
You should have just installed **build-essential**. Go and install it. :)

---

### Post by j_g on 2007-05-23
It's imperative that the package maintainers rename/repackage "Build-essentials" into something that is _much_ more obvious that it contains the bare minimum C/C++ headers and libraries needed to do any C/C++ development.

The frequency at which new developers report not getting something to compile because stdio.h is missing underscores that the current package name is just not working.

---

### Post by pmasiar on 2007-05-23
> **j_g said:**
> It's imperative that the package maintainers rename/repackage "Build-essentials" into something that is _much_ more obvious that it contains the bare minimum C/C++ headers and libraries needed to do any C/C++ development.

The frequency at which new developers report not getting something to compile because stdio.h is missing underscores that the current package name is just not working.

What name will be better?

If "build-essentials" does not suggest that package is essential, what about "package-essential-to-build-anything" ? :-)

Obviously this FAQ question is coming up again and again, but IMHO it is issue of ppl not doing homework before trying to dive into developing. 

If you search for [stdio.h is missing ubuntu](http://www.google.com/search?q=stdio.h+is+missing+ubuntu) you get same advice. If people cannot RTFM and cannot google they will keep asking FAQ - no amount of renaming can solve that, IMHO.

---

### Post by Soybean on 2007-05-23
> **timdoc1 said:**
> My output is wrong, in VI it looks like this:
^?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@<80><84>^D^H4^@^@^@T^O^@^@^@^@^@^@4^@ ^@^G^@(^@$^@!^@^F^@^@^@4^@^@^@4<80>^D^H4<80>^D^Hà^@^@^@à^@^@^@^E^@^@^@^D^@^@^@^C^@

Just a bit longer.  It should only be "a"'s and "b"'s in the output (it's a very small program.

That's a compiled program. It's like an .exe file in Windows. Are you sure that opening it in VI and looking at the ASCII conversion is what you wanted to do here? 

If you actually wanted to run your program... it's probably called "a.out", if you used the command-line suggested above. So, from the directory where you compiled it, type ```
./a.out
```

I think that if you were actually getting conflicts between 32-bit and 64-bit things, there would be more obvious errors.

---

### Post by timdoc1 on 2007-05-24
I think** I searched for stdio.h** and didn't find it quickly... so asked.  I had also looked through the PM and didn't find anything obvious to me.  How about **C/C++ build/essentials**?  Sorry if that sounds a bit redundant.

---

### Post by pmasiar on 2007-05-24
> **timdoc1 said:**
> I think** I searched for stdio.h** and didn't find it quickly... so asked.  I had also looked through the PM and didn't find anything obvious to me.  How about **C/C++ build/essentials**?  Sorry if that sounds a bit redundant.

No worry, nothing personal. Trival questions are sometimes hard to google.

We had heated discussions with j_g before, him whining how Linux sux and Windows is better, so... you are innocent bystander.

I checked build-essential description, and it is not obvious either :-( And it is not obvious you need to read build-essential description :-( But I don't think renaming package will solve that.

I am not sure what would be the best place to mention to anyone that build-essential are essential. Looks like package name cannot contain "C/C++". You may want to petition maintainers to change description, but I don't see that happening. When people start thinking about programming in C/C++, where they look for info? Where you looked?

---

### Post by fyo on 2007-05-24
> **pmasiar said:**
> What name will be better?

If "build-essentials" does not suggest that package is essential, what about "package-essential-to-build-anything" ? :-)

Obviously this FAQ question is coming up again and again, but IMHO it is issue of ppl not doing homework before trying to dive into developing. 

If people cannot RTFM and cannot google they will keep asking FAQ - no amount of renaming can solve that, IMHO.

I had the same problem. I fixed it by googling (which eventually brought me to this page), but it took much longer than it needed to and I can certainly understand why others would be tempted to just ask.

"build-essential" is a PATHETIC name. I'm sorry, but it is. The name itself doesn't say anything about what kind of "builds" this refers to and the description makes it even worse:

"If you do not plan to build Debian packages, you don't need this
package.  Moreover this package is not required for building Debian
packages."

Uhmm... hello... that's just not a very good description, regardless of content.

The simple truth is that (some) people ask questions if they can't figure it out themselves *quickly*. Nowhere in the description or the name is "gcc" or "header" or any of the file names people would ask about (like stdlib.h) mentioned.

I may just be an idiot, but if I want GCC to actually work on my Ubuntu box (including the necessary header files to do pretty much ANYTHING), I expect to be able to find it in Synaptic using a search for GCC. Not random-***-crap like "build-essential". Sorry for the coarse language, I realize it makes for an easy attack vector on my arguments, but so be it.

This is just about as user-unfriendly as something can get and the fix would be EASY. Better name or, at the very least, a MUCH better description.

"gcc-build-essential" as a name for example. Judging by the description and all the packages actually being installed by the "build-essential" meta-package would seem to indicate that much more is contained than just what is useful for gcc - that may or may not be the case, I don't know - but if that is in fact the case, the package should probably be split up or a new sub-package created. I.e. a new meta-package called, e.g., "gcc-build-essential" (with a PROPER description), containing just the packages related to gcc builds (and you could argue that libx11-dev should be included in that list).

---

### Post by pmasiar on 2007-05-24
OK, if enough beginners will present this case to MOTU, they might change description. Sorry I do not see a change to change package name, but you can try.

Maybe some highly positioned wiki page for ubuntu gcc development will do. What docs/whatever you read when you decided to start developing?

When people want to dive into coding, they better be prepared to solve complex problems. "build-essentials" is a simple one, IMHO.

I found 2 places where you may want to add "build-essentials"
[https://help.ubuntu.com/community/Programming](https://help.ubuntu.com/community/Programming)
[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions) - why page is not called FAQ?

But did you used any of them to search for answer? Would you find them?

---

