---
title: "Ubuntu newbie requesting help running programs"
date: 2007-08-16
forum: Programming Talk
---

### Post by snappyjack on 2007-08-16
Hey I just fired up Ubuntu a few days ago, and I'm starting to write Perl and C++ files. I have no trouble writing/compiling/checking for errors.
However (for example, my cpp program is called cpp1.cpp), when I enter ./cpp1.cpp into the terminal, I get a "Permission denied" message. The same happens whene i try to do ./[perl filename].pl. I assumed it wanted me to run them under sudo, but i guess that's not right.

Can anyone help me run my programs? Thanks.

---

### Post by jnorthr on 2007-08-16
if you want  to run a .cpp program that you compile then typical sequence would be:
1) write xxx.cpp in gedit or kate or another editor.
2) from a terminal command line issue command 'g++ xxx.cpp'
3) if compile is successful, type './a.out' cos thats the name given to your executable if you do not ask for another name whn you create the program, else 'man gcc' to review the manual documentation for the gcc and/or g++ compilers.
good luck. :)

---

### Post by snappyjack on 2007-08-16
I made my program in a text editor, entered

g++ cpp1.cpp -o cpp1

then ./cpp1.cpp.

^but i get a "Permission denied" message.

For perl i entered perl -c [filename.pl], but when i enter ./[filename.pl] it asks for permission again.
I'm pretty sure it compiled correctly, i just want to know what kind of "permission" it wants.

---

### Post by vexorian on 2007-08-16
ok, regarding cpp, C++ is not an scripting language, you must compile the .cpp files into executables, there are plenty of howtos out there.

Regarding p

you need:

perl ./filename.pl

if you want it to run just by ./filename.pl

you need to set the file as executable (using chmod or your file manager) then you need to add this line to the top of the .pl file:

#!/usr/bin/perl

(note: I might have the wrong path to perl, excuse but I don't use it too much and I am away of ubuntu to test)

---

### Post by pmasiar on 2007-08-16
If you are new to programming, and have no preference, I would recommend learning Python first (see wiki in my sig for links).

If you think you need C++, some people recommend to learn Python first anyway, bacause you need learn first basics of programming (language independent), and Python is just so much simpler.

Even more it is valid for Perl. Python pretty much replaces Perl: same dynamic typing etc, but just so much more readable. There is hardly any reason why to prefer Perl over Python these days.

---

### Post by snappyjack on 2007-08-16
Thanks for the advice guys, I got it working.

And I think i might just look into Python...

---

### Post by batrick on 2007-08-16
If you're in the mood for trying languages, you may want to give Lua a shot.

---

### Post by PandaGoat on 2007-08-16
I know you got it working, but you might not like python and, the advice given here was somewhat poor.  a .o file is created by the compiler for the linker to link.  The linker links them together into the binary.  For g++ use this command [You got this part]:

```

g++ cpp1.cpp -o cpp1

```
The last argument 'cpp1' is the name of the binary file.

This will create the binary file which is not the .o file[s].
In the same directory type
```

./cpp1

```

---

### Post by pmasiar on 2007-08-16
Not sure who gave poor advice, but with python, you don't need to bother about compilig at all, you can try big part of language directly in python shell :-) 

No compiling, no linking: no problems :-)

---

### Post by PandaGoat on 2007-08-16
I didn't mean about python.  It was targetted towards the idea given that a .o file is a binary and could be ran.  And in case he did not like python he might go back to c++ with that idea.  So I clarified the situation.

---

### Post by aks44 on 2007-08-16
Did anyone mention to **chmod +x *outputfile*** between running **g++ *file.cpp* -o *outputfile*** and launching **./*ouputfile***?

:-\"

---

### Post by snappyjack on 2007-08-16
I ended up doing that. I just gave read/write/execute to myself by chmod 750ing the file.

Whats Lua all about? And what are some of the downsides of Python? I'm just arbitrarily learning every language I can get my hands on because there are NO comp sci classes in my highschool and I don't know anyone who understands code, so I really have no direction and aren't approaching this with any rhyme or reason. Just books and tutorials, trying to gain a good basic understanding of what I might want to learn in college. Plus its a fun way to eat up time.

---

### Post by pmasiar on 2007-08-16
> **snappyjack said:**
> what are some of the downsides of Python? 

Anyone can learn it easily, you have no bragging rights for learning Python :-)

> I'm just arbitrarily learning every language I can ... I really have no direction and aren't approaching this with any rhyme or reason. Just books and tutorials, trying to gain a good basic understanding of what I might want to learn in college. Plus its a fun way to eat up time.

Language syntax is about 10% of the skills you need for programming. Another one are data structures, program design skills (modules, functions, and refactoring code), testing and debugging. Big part of it is language independent. Then there are libraries - libraries are often much bigger and more complicated than language syntax.

On level 0 you write "hello world".
Level 1: "99 bottles of beer on the wall"
Level 2: Simple text game, like "guess a number", which does not require data structures
Level 3: Simple text game with data structures, like "boats"
Level 4: Complicated text game, like RPG.
Level 5: Simple GUI game

BTW this is log10 scale: next level is 10 times as difficult :-)

---

