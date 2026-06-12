---
title: "[Newbie] Programmming tools (compilers) in Linux"
date: 2008-04-27
forum: Programming Talk
---

### Post by adriantc on 2008-04-27
Hello! I'm very new to Linux - a week or so. I've had some previews  experience, but was extremely disappointed. But I'm giving Linux a second chance. I'm a student and I do quite a lot of programming (Pascal and C++). I was wondering what compilers can I find on Linux. I'm looking for something like Visual C++ or Borland Delphi.

Thank you,


PS: I apologize if I haven't posted this thread in the right section!

---

### Post by LaRoza on 2008-04-27
> **adriantc said:**
> Hello! I'm very new to Linux - a week or so. I've had some previews  experience, but was extremely disappointed. But I'm giving Linux a second chance. I'm a student and I do quite a lot of programming (Pascal and C++). I was wondering what compilers can I find on Linux. I'm looking for something like Visual C++ or Borland Delphi.

Thank you,

PS: I apologize if I haven't posted this thread in the right section!

See the sticky.

You seem to be mixing compilers with IDE's. In Linux, languages are not tied to the tools so much. There is an IDE thread in the sticky, and howtos for compilers.

Delphi is proprietary, and not for Linux. Lazarus and Free Pascal I think are close to what it is.

---

### Post by Sinkingships7 on 2008-04-27
> **adriantc said:**
> Hello! I'm very new to Linux - a week or so. I've had some previews  experience, but was extremely disappointed. But I'm giving Linux a second chance. I'm a student and I do quite a lot of programming (Pascal and C++). I was wondering what compilers can I find on Linux. I'm looking for something like Visual C++ or Borland Delphi.

Thank you,


PS: I apologize if I haven't posted this thread in the right section!

Geany supports Pascal and C++ highlighting and compiling/linking. It's lightweight, and full of the most useful things (code completion, line numbers, etc...).

I use it and am rather impressed with it.

```
sudo apt-get install geany
```

---

### Post by adriantc on 2008-04-27
Thanks for the very fast reply. I'm sorry for the small confusion. I meant IDE. Something like Lazarus is what I'm looking for; I'm sorry it doesn't have a C++ compiler. If only  Borland continued the Kylix project... :(. So Lazarus for Pascal... What about C++? What IDE would you recommand?

Edit: @Sinkingships7: I guess that answers my question... I'll sure check them out! 10x!

---

### Post by danbuter on 2008-04-27
Also, make sure you do the following:

sudo aptitude install build-essential


I believe Geany is also good for C++.

---

### Post by steve8track on 2008-04-27
Code::Blocks, which you will probably have to install manually, is supposed to work very like Visual Studio.  I think it even imports Visual Studio project files.  I personally just use gedit (the default text editor) since it has text highlighting, and print statements to debug.  Recently I added a keyboard shortcut to clean, compile, and run the program when pressing F5, while printing erros to a file I had open in Epiphany (a nice web browser that automatically refreshes when viewing local files that are changed).  I used compiz-fusion to run my script to do this, but you could just use gconf-editor (like regedit in windows) to edit /apps/metacity/global_keybinding.  The problem with this method is when you switch projects you will have to make a new script each time and update the keyboard shortcut, and it seems easier to just make the script run in the console instead of mapping it to a key.  Here is how I saved output to a file (if you just use > to route the output, it will skip error output from gcc, which by the way is the compiler of choice)

```

#!/bin/bash
cd /projectDirectory/
bash -x run 2>output.txt
```

run was another script I wrote that just does:

```

make clean
make
./output
```

I used that more than the other script.

There is also Eclipse, but that IDE is mainly for java and I don't know about their c++ support.  KDevelop is another IDE you could try.  There is MonoDevelop, but MonoDevelop is for C#.

I hope that helps.  I will admit I haven't spent the time to really use an IDE in linux other than Eclipse.

Até mais,

Steve

---

### Post by samjh on 2008-04-27
> **steve8track said:**
> There is also Eclipse, but that IDE is mainly for java and I don't know about their c++ support.  KDevelop is another IDE you could try.  There is MonoDevelop, but MonoDevelop is for C#.

Eclipse has excellent support for C++ via the CDT plug-in.  You can install them on Ubuntu by:```
sudo apt-get install eclipse eclipse-cdt
```

MonoDevelop isn't just for C# (and VB.NET).  It has had C/C++ support since 1.0 beta.

[quote=adriantc]Hello! I'm very new to Linux - a week or so. I've had some previews experience, but was extremely disappointed. But I'm giving Linux a second chance. I'm a student and I do quite a lot of programming (Pascal and C++). I was wondering what compilers can I find on Linux. I'm looking for something like Visual C++ or Borland Delphi.[/quote]Firstly, I strongly recommend you to learn the compiler by itself, and IDE by itself.  What I mean is learn to compile programs using the command-line compiler.  This will give you a better understanding of the compilation process, and you can learn to make build scripts along the way for more complex projects, which will benefit you in the long-run.

After you've mastered building and compiling on the command-line, you will be able to evaluate IDEs in better light.

Keep in mind that there are two types of IDEs: code-editors (eg. gedit, vim, emacs), or true IDEs with project building capabilities (eg. Eclipse, CodeBlocks, Anjuta, MonoDevelop).

Go with editors and command-line compilers first.  After you're familiar with those tools, move onto IDEs for larger projects.

To learn how to compile using GCC and G++: [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

To deal with compilation problems: [http://ubuntuforums.org/showthread.php?t=691451](http://ubuntuforums.org/showthread.php?t=691451)

To learn how to write simple Makefiles: [http://www.oreilly.com/catalog/make3/book/ch01.pdf](http://www.oreilly.com/catalog/make3/book/ch01.pdf)

---

