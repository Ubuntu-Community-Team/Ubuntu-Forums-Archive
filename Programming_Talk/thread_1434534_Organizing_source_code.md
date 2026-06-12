---
title: "Organizing source code"
date: 2010-03-20
forum: Programming Talk
---

### Post by JDShu on 2010-03-20
So I'm trying to cross compile my program for Windows, and using Allegro and Glib, it seems to me that I need to learn how to use the Autotools to make it work easily. I guess a preliminary question is, is this correct?

My main question is that my current folder of files is a mess. I don't want to start figuring out Autotools before I have it organized into something workable. I'm writing a game that uses images, music files, plain text files for the user, source code, and header files. Can somebody tell me what the generally accepted way to organize the files in to folder or whatnot would be, or direct me to a tutorial? I can't google it because I don't know what exactly I should be looking for. Thanks in advance!

---

### Post by pholding on 2010-03-20
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]I'm interested to see what other developers come back with as still haven't settled on a directory structure for the project I'm working on and it sounds like I'm in a similar situation to yourself where I'm trying to move away from manually creating the Makefile.....anyway I found these two links which might be of some use.....[/FONT][/COLOR]
[/FONT][/COLOR]
[http://stackoverflow.com/questions/900240/c-project-source-code-layout](http://stackoverflow.com/questions/900240/c-project-source-code-layout)
 
[http://stackoverflow.com/questions/1398445/directory-structure-for-c-library](http://stackoverflow.com/questions/1398445/directory-structure-for-c-library)

---

### Post by JDShu on 2010-03-20
Thanks for replying, yeah moving from manually created makefiles is where I'm trying to move from, especially since the documentation on cross compiling glib seems to be quite lacking. Autotools is really daunting though haha.

---

### Post by soltanis on 2010-03-20
I'm not sure what Autotools is -- is that autoconf/automake? If so, I hate those tools. They're pretty much unnecessary and overly complicated.

A really common scheme I see in big projects is something like this:

bin/ (binaries)
docs/ (documentation)
src/
--> src/include/ (header files)
--> other src/ directories, which correspond to modular divisions in your program

For example, if I had two big modules, Client and Server, then I'd separate out their directories in the src/ tree.

Data files and such I would put in the bin/ directory under something like bin/resources, where your compiled program can get to it easily.

---

### Post by JDShu on 2010-03-20
Thanks, your way seems simple enough, I think I'll adopt it. And yeah, I meant autoconf/automake. I dunno if I should keep trying to learn it and if it solves my original problem which is cross compilation. I guess I'll make a new thread about that. Thanks everybody! :D

---

### Post by pholding on 2010-03-20
Slightly off topic but it might be worth having a look at CMake as an alternative to automake/autoconf. I haven't used either yet, so I can't really comment on the pros & cons but I believe that the Allegro project uses CMake.

---

### Post by Senesence on 2010-03-22
> **pholding said:**
> Slightly off topic but it might be worth having a look at CMake as an alternative to automake/autoconf. I haven't used either yet, so I can't really comment on the pros & cons but I believe that the Allegro project uses CMake.

I've used CMake, and it's been nothing but good news (at least for the kind of mid-sized projects I work on).

Everything is so simple: you list what libraries your code requires, you list your source files, and CMake keeps track of everything else.

You can then generate regular makefiles, or even full-fledged project files for popular development environments like visual studio on windows, or xcode on the mac.

I've never used automake/autoconf, but I don't hear good things about it (the term "Autohell" keeps popping up), so I'm probably going to stick with CMake for a long time.

I also used SCons for a while, and I think it's fairly easy to use, but it was a little too sluggish.

---

