---
title: "Wanting to learn open source C/C++ programming fundamentals"
date: 2007-06-11
forum: Programming Talk
---

### Post by boz on 2007-06-11
Hi all,

I consider myself to be a good programmer.  Unfortunately, I haven't done much of it in the past couple of years.  I've been concentrating on my degree in Electronics Engineering which doesn't require much OOP knowledge and certainly not a lot of C++.  I've been interested in open source programming for quite a while, though, and now that I've graduated, I'd like to educate myself so that I might one day contribute to the awesome software that I've used throughout my college career (namely, the gEDA project and Ubuntu OS).

Does anyone know a good place to start reading up on open source programming fundamentals (program organization, modularity, techniques, makefiles, automake, autoconf, etc.).  I know some C++ - I'm certainly not fluent but I'm capable of using a desktop reference book to look stuff up.  I just want a broad overview.  I can work out the details myself or I can come here and ask if I have specific questions.  And, for now, I'm only interested in C/C++.

My programming background:  one course in C, one in C++, one in x86 assembly, one in Perl (for fun), one in VHDL, one in Verilog, and a couple requiring Matlab.  I've been reading up on C++ since I graduated in early May, so I'm feeling comfortable with the language again and I've written a couple of programs that require operator overloading, templating, and inheritance.  

I appreciate any comments.  Thanks.
Kelly

P.S. References don't necessarily have to be online.  I can check out a book or even buy one (if it's really, really worth it).

---

### Post by samjh on 2007-06-11
"Open source programming fundamentals"?

There is nothing so special about open source software development.  The same basic principles apply in software development in every industry.  Just learn the basics of C++, and do some small projects (writing a compression utility is a relatively simple and very educational).

After that you can read up on some software design and engineering theory, or just dive head-first into a larger FOSS project (look up Sourceforge, there are thousands of projects looking for coders).

The key is to do some small projects of your own so as to gain experience in actually putting your knowledge into practice.  Feel free to reinvent the wheel.  You can compare, contrast, and learn from existing FOSS programs.  In fact, re-doing a small FOSS project is probably one of the best ways to learn how to go about doing software projects and how they evolve over time.

For books, one of the set texts I used at university was *Software Engineering, a practioner's approach* by Pressman (latest edition: [http://www.rspa.com/about/sepa.html](http://www.rspa.com/about/sepa.html) ).  It's very heavy SE theory, so only recommended if you're really into the design aspect of software. :)

---

### Post by pmasiar on 2007-06-11
> **boz said:**
>  a good place to start reading up on open source programming fundamentals (program organization, modularity, techniques, makefiles, automake, autoconf, etc.). .

Use the source, Luke :-)

There is not such a thing as "open source programming" - there are many projects. Most code has good structure, some needs improvement. Pick a project you are interested to learn, and dive in. Ask developers on *that project* what you need to know and learn. Most projects are looking for "new blood" and welcome newbies, it they have good attitude and are willing to learn.

---

### Post by vialick on 2007-06-11
[http://sourceware.org/autobook/](http://sourceware.org/autobook/) the book on Autoconf, Automake and Libtool

Thinking in C++ seems pretty good

---

### Post by boz on 2007-06-11
samjh,

You're right - poor choice of words.  How about "large programming project development fundamentals?"  And, better yet, using GNU utilities such as gcc, g++, gdb, make, automake, etc.  I could always cheat and let Anjuta do it for me, but I'd much rather learn how to customize my Makefiles and manage large projects - for the experience.  I agree that starting small and working my way up is key, but I'd like to know what's going on when I execute stuff like ./configure && make && make install, too.

I've never written a compression utility, nor do I know where to start.  I"ll do a google search that describes the algorithms involved, but if you know of a good reference and explanation of the problem offhand, I would appreciate it if you would share it.

Thanks,
Kelly

---

### Post by loell on 2007-06-11
since you mentioned geda project as one of your interest,

you might like to look into gtk programming fundamentals. also a search on how to use autotools will yield numerous results , for those makes, and autoconf stuff.

for code referrences on opensource projects try looking into , google/codesearch and devhelp.


and oh, you won't have to worry about autotools that much, you can automate, by using IDE :P

ie(anjuta , Kdevelope)

---

### Post by samjh on 2007-06-11
> **boz said:**
> I've never written a compression utility, nor do I know where to start.  I"ll do a google search that describes the algorithms involved, but if you know of a good reference and explanation of the problem offhand, I would appreciate it if you would share it.

Thanks,
Kelly
There is a very simple algorithm for compressing standard ASCII text files.  All ASCII characters are 8 bits long, but they really only use 7 bits for encoding, and the 8th bit (the most significant bit or bit0) is not used.  So you can actually compress ASCII text files by shifting all the bits to fill up the unused bit0.

It's harder than it looks, but easy enough to solve in several hours of work.  It will exercise your ability to use loops and/or selections, file I/O, bit manipulation, and general ability to devise clean and efficient code.

There is another compression method called RLE.  Description is here: [http://en.wikipedia.org/wiki/Run-length_encoding](http://en.wikipedia.org/wiki/Run-length_encoding)
It's popular for image compression, but can be used for other things.

As for Autoconf and Automake, etc.  Look here: [http://sources.redhat.com/autobook/autobook/autobook_toc.html#SEC_Contents](http://sources.redhat.com/autobook/autobook/autobook_toc.html#SEC_Contents)

---

### Post by CptPicard on 2007-06-12
> **boz said:**
> I could always cheat and let Anjuta do it for me, but I'd much rather learn how to customize my Makefiles and manage large projects - for the experience.  I agree that starting small and working my way up is key, but I'd like to know what's going on when I execute stuff like ./configure && make && make install, too.


While your attitude is admirable, I disagree with the idea that getting all the help you can get from tools is "cheating". That's what the tools are there for. For example I absolutely love IDEs' code completion and automatic error-correction, as the point of programming is not to memorize the API 100% or be able to compile everything in your head but to get code actually written.

Certainly you need to read the autotools reference in order to be completely comfortable with them, but if I were you, I'd just use Anjuta for all it's worth and learn from the hand-holding it does for you. You get fully working examples you can then customize to your heart's content as you go along and learn more and actually need the extra functionality.

I, for one, prefer to do all my coding in Java for the one reason that the toolchain is simply so much cleaner... autotools is a horrible mess compared to Ant. Can't wait for Scons to become more widely accepted :)

---

### Post by the_unforgiven on 2007-06-12
There is also [cmake]("http://www.cmake.org") which can easily replace autotools.

---

### Post by boz on 2007-06-12
Thanks for all your advice, everyone.

---

