---
title: "I need a little help figuring out how to compile a program without a makefile."
date: 2012-03-16
forum: Packaging and Compiling Programs
---

### Post by Zellonous on 2012-03-16
Hello everyone. I'm kinda new to Linux and new to these forums. I've been tinkering with Xubuntu for a week or two now and I like it.

I know pretty much nothing about programming and I'm almost a complete newbie at compiling source code and I've searched for hours on Google for an answer. I'm trying to compile source code of a little game called "Decker" made for Windoze. The developer released the source code but he did not make any makefiles or give info on how to compile it. I realize that the game would probably work without a hitch in Wine... but I figured attempting to migrate it to Linux entirely would be awesome. Not exactly easy.

At first, I tried the Make routine that tutorials on compiling teach us. But it doesn't have a makefile. Then, after looking for info on how to use gcc itself, I learned that I needed a C++ compiler. After installing g++, I tried to compile what seems to be the main source code file (decker.cpp). Didn't work. The code pointed to another file with a lowercase name. I knew then that I had to rename all the files to have lowercase names. Even after that, it pointed to a file that didn't even exist (afxwin.h) in any of the directories. I looked at decker.cpp with Kdevelop and noticed that the code deals with Windoze registry in some way. NO idea what to do. I've searched for a while on Google on porting Windoze programs to Linux and all I ever came up with was compiling programs on Linux for Windoze. I know this is a small issue... but I'd like to learn about these things.

I'm assuming that I would have to know programming and actually edit the files to work with Linux right? I guess I mainly just need clarification on that. I always thought that source code was basically universal, and that when you compile it, it is set to your OS' specifications. Am I wrong?

Here's a link to the SourceForge: [http://sourceforge.net/projects/decker/](http://sourceforge.net/projects/decker/)

I tried to upload an archive of it, but it was too big.

---

### Post by SevenMachines on 2012-03-16
Some programs use cross platform languages and libraries so that they can be used or ported easily to other platforms, some don't. Porting a program like the one you're talking about that uses windows specific (i'm guessing afxwin is?) libraries means working on the code to replace that functionality with another linux compatible library or program the replacement code yourself. Either way it's likely to be a tough job for beginning programming.

---

### Post by Ghostmn on 2012-03-17
g++ -Wall -o decker *.cpp

Doesn't compile evidently since it was written for Windows. Good luck.

Edit 1: Working on a game is the best way to learn how to program, since it involves a lot of logic and algorithms. I would recommend just making your own though since you're just a beginner, and the code found in this game is somewhat obscure and hard to follow.

---

### Post by Zellonous on 2012-03-17
Thank you both for your replies. I thought I wouldn't have the know-how to do it. Maybe later I guess. Til then I'll use Wine for what it was made for.

---

