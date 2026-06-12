---
title: "programming text editor with gcc/g++"
date: 2010-03-27
forum: Programming Talk
---

### Post by tooatw on 2010-03-27
hi, can anyone tell me if there is such a thing as a text editor that compiles the script as well and shows you where the error is?
currently i use codeblocks for writing a script and checking for errors and the konsole to compile / run it because the codeblocks console sucks really bad (the text is too small, and i'm just not used to it)
and it gets annoying to create a new project everytime and when i'm done to take the main.cpp and the other files and manually moving them when i could simply create what i needed with a text editor that does what codeblocks does (indicate the line with the error/warning) i do not want to run the program in the text editor just to check for errors
i'd rather use g++ when the program is working because it doesnt really point to the code and its just not as easy as something that shows exactly on the code

you can see how the konsole text is much easier to read than the codeblocks console)

---

### Post by Compyx on 2010-03-27
You could use Vi/Vim in combination with a makefile. You simple enter the command :make and Vim will run the makefile and automatically jump to the line which triggered the first warning or error. You can then jump to the next warning with :cn and to the previous one with :cp.

Vim takes a little time to get used to (it uses 'modes' such as insert mode, visual mode and command mode) but once you get used to it, you'll love it.

You can also write your own scripts to alter Vim's behaviour and write your own syntax highlighting files (which is surprisingly easy if you understand regular expressions).


There's also another powerful editor called Emacs, which I assume can do what Vim does as well, but I could never get used to that editor.

But you should give Vim a try, you'll love it once you get the hang of it ;)

---

### Post by tooatw on 2010-03-27
ok i installed vim
whats the command line for compiling and building a .cpp or .c file using vim? (normal gcc/g++ -o 1 filename.c)

---

### Post by SledgeHammer_999 on 2010-03-27
You could always tell Code::Blocks to use your favorite terminal program(eg konsole) instead of the default. Check options and you will find it.

---

### Post by tooatw on 2010-03-27
> **SledgeHammer_999 said:**
> You could always tell Code::Blocks to use your favorite terminal program(eg konsole) instead of the default. Check options and you will find it.
i tried to do that, please tell me where
i replace xterm -T $TITLE -e with?

---

### Post by SledgeHammer_999 on 2010-03-27
With "konsole". I don't what args konsole supports, you better check it's manpage.

---

### Post by gnometorule on 2010-03-27
Maybe I'm missing the point, but it seems you want to know about debugging alternatives. The usual, most basic way (that I am using) is to run

g++ -g (other options) -o <filename>
gdb -q <filename>

Option -g produces a core dump which then can be used in gdb. While this doesn't jump to the line you need in an editor (or maybe it does if you're an emacs pro, don't know - emacs might be able to do that), it's very easy, powerful debugging. You're up and running fast using, e.g., this reference:

[http://www.delorie.com/gnu/docs/gdb/gdb_toc.html](http://www.delorie.com/gnu/docs/gdb/gdb_toc.html)

I even use this with the editor many seem to look down on: nano. If you identify the error line, 

nano +<line>,1 <filename>.cpp

used in another console window to have both in parallel, gets you where you want to edit (assuming you file-extend with cpp).

Gdb comes, I think, with the package 'build-essentials' that you probably want to have installed anyway if you do C++ coding in Ubuntu.Gl.

---

### Post by tooatw on 2010-03-27
all of this seams really complicated, is there nothing as simple as a codeblocks text editor that compiles it
i only use codeblocks to write my code and when its done i ctrl+f11 for error checking then i move to the console to "g++/gcc -o ...." and to run it 
the annoying part about codebloks is that it builds a folder for each thing and i'd rather just have one .c or .cpp 
gedit seams to be really nice, if only it had codeblocks' ctrl+F11 to display errors / warnings it would be perfect

---

### Post by johnb820 on 2010-03-27
I'd suggest Geany personally. It is a simple text editor with built in compilation. It supports a multitude of languages and all sorts of neat features. No live compilation to give you warnings as you type though, if that is what you were looking for.

---

### Post by slavik on 2010-03-27
Look into geany.

---

### Post by tooatw on 2010-03-28
geany seams to be what i was looking for
thanks everyone

---

### Post by tooatw on 2010-03-28
wow geany is really awesome

---

