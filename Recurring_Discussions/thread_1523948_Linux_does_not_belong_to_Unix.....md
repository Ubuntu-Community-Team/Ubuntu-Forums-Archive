---
title: "Linux does not belong to Unix....?"
date: 2010-07-04
forum: Recurring Discussions
---

### Post by gauravbutola on 2010-07-04
Please dont be mad at me as I am not asking an Ubuntu specific question.
What I had thought before was that Linux was made after the modification of Unix.
But i came across a guy who said that Linux has nothing to do with Unix.
Here is what he said--

> 1. Linux kernel was written from scratch.
2. Unix is proprietary and hence can not be modified to create and distribute freely.
3. Read about GPL license.
4. Linux is not based on UNIX [I guess you can find that in any good Linux book in the first chapter itself!]
5. Linux cloned unix's fundamental structure albeit being written from scratch and open source.
6. Read about Minix which inspired Linux.
7. Read about GNU [GNU is Not UNIX].

plz someone clarify this issue, as I thought Mac and Linux both are unix like operating systems and now I am in big doubt as someone has said me that "Linux has nothing to do with Unix".

---

### Post by mikewhatever on 2010-07-04
History of Linux
[http://en.wikipedia.org/wiki/History_of_Linux](http://en.wikipedia.org/wiki/History_of_Linux)

---

### Post by philinux on 2010-07-04
Moved to recurring discussions.

---

### Post by jrothwell97 on 2010-07-04
> **gauravbutola said:**
> plz someone clarify this issue, as I thought Mac and Linux both are unix like operating systems and now I am in big doubt as someone has said me that "Linux has nothing to do with Unix".

You've kind of answered your own question there.

Usage wise, a GNU/Linux system is very similar to "true" Unix. These days, to be called a "true" Unix, you have to meet certain criteria - Solaris and Mac OS X fall into this family.

Unfortunately, being "similar" or "a UNIX" does not mean interoperability. You can't run your Mac OS X apps on Ubuntu, for many reasons:

[list][*]The app is compiled for the Mac OS X kernel, Darwin, as opposed to Linux, which is Ubuntu's kernel.
[*]The app is linked against Mac OS X's "API" - that is, the set of default libraries, resources and functions that are built into the system. Ubuntu has no API, as such, and there's no direct compatibility layer.[/list]

I hope that cleared things up for you.

---

### Post by gauravbutola on 2010-07-04
please can u give your plane & simple answer...

---

### Post by oldfred on 2010-07-04
All your quotes look correct.

Unix is proprietary, but also has multiple versions. Linux software does not run directly in Unix and vice-vesa. Sometimes compatibily layers are added to run software from one in another.

Univ of California developed another version of Unix and even parts of it were included back into Unix. After a legal suit they were able to continue to distribute their Berkeley version BSD which is not GPL. Parts of the underlying Mac uses BSD.

This shows some of the versions
[http://en.wikipedia.org/wiki/File%3AUnix_history-simple.svg](http://en.wikipedia.org/wiki/File%3AUnix_history-simple.svg)

The system are Unix like in that they clone many of the commands so it may work in a similar fashion.

---

### Post by jrothwell97 on 2010-07-04
My plain and simple answer?

GNU/Linux is not Unix. It is Unix-like.

---

### Post by MCVenom on 2010-07-04
Simply put: your friend is right. I suggest you read more about the history of Linux, GNU, and other *nixes on Wikipedia; it's all very interesting. ;)

P.S.: Someone once approached me with a similar misunderstanding. I actually drew a chart of Linux's relationship to Unix and Mac OSX in response; I'll see if I can find it for you ;)

---

### Post by mickie.kext on 2010-07-04
Surviving UNIXes are AIX, Solaris and HP-UX. All else are clones of UNIX. GNU/Linux is UNIX rewrite without looking at the code, while BSD is UNIX rewrite with looking at the code. That is simplest I can put it.

But name UNIX doesn't mean much anymore.

---

### Post by gauravbutola on 2010-07-04
seriously, I did't expect this much fast replies.
thanks to you  guys..

---

### Post by Chame_Wizard on 2010-07-04
Unix rocks.:popcorn:

---

### Post by MCVenom on 2010-07-05
> **BlackOtaku said:**
> Simply put: your friend is right. I suggest  you read more about the history of Linux, GNU, and other *nixes on  Wikipedia; it's all very interesting. ;)

P.S.: Someone once approached me with a similar misunderstanding. I  actually drew a chart of Linux's relationship to Unix and Mac OSX in  response; I'll see if I can find it for you ;)

Here's that diagram I was talking about! :D

Keep in mind it's more of a relational diagram than anything else; it's by no means a complete or even precise history or diagram of how GNU/Linux developed compared to OSX, but you might find it helpful :P

P.S.: Yes, my handwriting is terrible. :lolflag:

---

### Post by Sporkman on 2010-07-05
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Unix_history-simple.en.svg/800px-Unix_history-simple.en.svg.png[/IMG]

---

### Post by mickie.kext on 2010-07-05
Here's more precise: [http://www.netneurotic.de/mac/unix/images/UNIX.png](http://www.netneurotic.de/mac/unix/images/UNIX.png)

---

### Post by MCVenom on 2010-07-05
> **mickie.kext said:**
> Wow, you bothered to draw and take a picture? Here is star to you:KS

No matter it is not very precise. 

Here's more precise: [http://www.netneurotic.de/mac/unix/images/UNIX.png](http://www.netneurotic.de/mac/unix/images/UNIX.png)
Actually, I dug up an old picture. It wasn't meant to be precise, it was meant to be a two minute read to hold a teenager's attention. :P

Please, the condescension is completely unneccessary. :|

EDIT: I feel I've feel I've done my part in this thread, so bye bye! ):P

---

### Post by mickie.kext on 2010-07-05
> **BlackOtaku said:**
> Actually, I dug up an old picture. It wasn't meant to be precise, it was meant to be a two minute read to hold a teenager's attention. :P

Please, the condescension is completely unneccessary. :|

EDIT: I feel I've feel I've done my part in this thread, so bye bye! ):P

Sorry, I really didn't mean to offend you. I will shut up now.

---

### Post by mojota on 2010-07-05
By the looks of them pics it seems Linux is a world away from anything else (Mac, BSD,Solaris)
I did'nt think Mac was so close to free bsd, the problem is to get a working enviroment in free bsd don't you have to virtually install linux inside bsd which then does'nt make it genuine free bsd?

---

### Post by RiceMonster on 2010-07-05
> **mojota said:**
> I did'nt think Mac was so close to free bsd, the problem is to get a working enviroment in free bsd don't you have to virtually install linux inside bsd which then does'nt make it genuine free bsd?

No. There is linux emulation that you may want for a few things like flash, but other than that you don't even need it. The majority of Linux apps have FreeBSD ports.

---

### Post by Bachstelze on 2010-07-05
> **RiceMonster said:**
> No. There is linux emulation that you may want for a few things like flash, but other than that you don't even need it. The majority of Linux apps have FreeBSD ports.

Also useful for Linux natuve games (UT, Quake, NWN, etc.).

---

