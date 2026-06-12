---
title: "OK even hello world don't work!"
date: 2007-09-21
forum: Programming Talk
---

### Post by loza on 2007-09-21
hello there all!

I just started programming in gcc with unbuntu out of the box and it can't seem to find the stdio.h library!

I get file or directory not found when I try to compile.

Any ideas why my setup should be doing this please?

thanks in advance

---

### Post by frenchcr on 2007-09-21
cant remember exactly which packages you need, but build essentials is one of them...there have been many posts on this topic. please look again with different search terms.

---

### Post by loza on 2007-09-21
Thanks will do Frenchcr!

---

### Post by gnusci on 2007-09-21
Here we go, everyday task :)

[http://ubuntuforums.org/showthread.php?t=554070](http://ubuntuforums.org/showthread.php?t=554070)

---

### Post by loza on 2007-09-21
he-he! Thanks! 

I got it with 'sudo apt-get install build-essential'

interesting link... thanks for that gnusci !

I guess it must be a 'security thing' - I would have thought this would be part of a standard install.

---

### Post by LaRoza on 2007-09-21
> **loza said:**
> 
I guess it must be a 'security thing' - I would have thought this would be part of a standard install.


With most distros it is installed. There is a thread somewhere, not in this forum, on that topic.

build-essential will also install g++, for C++ programming. It works the same way as gcc, and can compile C programs.

---

### Post by Compyx on 2007-09-21
As I remember reading about it, the tool-chain wasn't installed by default because there simply wasn't anymore space on the install-CD.

Personally I feel any *nix system isn't complete without a tool-chain, the exception perhaps being servers where security could be compromised if a hacker gets access to a compiler.

Maybe someone should make a thread called something like 'stdio.h: no such file or directory', describe the solution (`sudo apt-get install build-essential`) and make it sticky?

---

### Post by LaRoza on 2007-09-21
> **Compyx said:**
> 

Maybe someone should make a thread called something like 'stdio.h: no such file or directory', describe the solution (`sudo apt-get install build-essential`) and make it sticky?

It is on the cd, so there is room.

It is in the sticky mentioned above. Although the title doesn't explicitly state that "stdio.h" is mentioned in it, it is, in bold.

---

### Post by tr333 on 2007-09-21
> **loza said:**
> I guess it must be a 'security thing' - I would have thought this would be part of a standard install.

The majority of Ubuntu users would probably not be software developers.  Why bother including something on the base install that most people wouldn't use, and could install easily if required?

As for the packages, you might also want to install "manpages-dev" to get sections 2 (linux system calls) and 3 (library calls) of the manual; and maybe "automake" and "autoconf" if you need them.

---

### Post by LaRoza on 2007-09-21
> **tr333 said:**
> The majority of Ubuntu users would probably not be software developers.  Why bother including something on the base install that most people wouldn't use, and could install easily if required?


Due to the number of software available that must be compiled, plust the large number of such questions indicates this package is used a lot, if not knowingly.

Some people, non-programmers, ask the question when they install from source.

---

### Post by speckman on 2007-09-21
Wow.  I guess that's a valid point that most ubuntu users won't need this, but I never thought I'd ever see an error when including stdio on a linux distro.

There is something very basically irritating about Ubuntu in this way.  Anything I want to do on it won't work out of the box, short of web surfing.  I have to do a google search everytime to figure out what Automatix is called and where it is, and now, to compile the most basic C program, I have to install a package.

---

### Post by LaRoza on 2007-09-21
> **speckman said:**
> 
There is something very basically irritating about Ubuntu in this way.  Anything I want to do on it won't work out of the box, short of web surfing.  I have to do a google search everytime to figure out what Automatix is called and where it is, and now, to compile the most basic C program, I have to install a package.

Yes, but many distros have it, and Ubuntu does have a target user, although anyone can use it.

Either way, it is better than Windows, to get a MS compiler, you have to jump through hoops, VS Express doesn't work without an internet connection and "validation", so I haven't used it.

---

