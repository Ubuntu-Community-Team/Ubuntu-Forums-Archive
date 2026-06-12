---
title: "Learning C++"
date: 2008-07-22
forum: Programming Talk
---

### Post by iampriteshdesai on 2008-07-22
I am new and learning C++. Which software to use? How do I start compiling.

---

### Post by Potatoj316 on 2008-07-22
in the terminal type
```
sudo aptitude install build-essential
```
the c++ complier is called g++, to compile your code you type (terminal again)
```
g++ NAME.cpp
```
(i think thats all you need, there might be a switch you need to use) you can also put a -o then the name of the output file (that part is optional) check out g++ --help for more info (or man g++)

your code can be written using any pain-text text editor.  (vim, emacs, gedit, nano...)

---

### Post by dracayr on 2008-07-22
its plain-text editor not pain text editor ;)

dracayr

---

### Post by Archimedes0212 on 2008-07-22
I like using emacs for writing or even gedit.  Both highlight the code which is the main thing I look for.  I compile and run from the terminal with g++.

---

### Post by Potatoj316 on 2008-07-22
I think vim highlights or maybe gvim as well.  

Oh, and dracayr is too picky.  Maybe I was talking about a text editor that hurts to use, its to discourage people from programing.

---

### Post by dracayr on 2008-07-22
> **Potatoj316 said:**
> Maybe I was talking about a text editor that hurts to use, its to discourage people from programing.


everything is possible : take a look at MS's 'editor' (I think that was the name, it's a standard program in Window$):D

dracayr

---

### Post by stump138 on 2008-07-22
I've been using geany alot lately for writing editing code and makefiles, then running make in a terminal.

---

### Post by KIAaze on 2008-07-22
Here's a nice exhaustive list of software:
[List of Free Software and Freeware IDEs]("http://www.linuxquestions.org/questions/programming-9/list-of-free-software-and-freeware-ides-469623/")
(But don't start with an IDE right away if you're just beginning. It actually makes things more complex sometimes. ^^)

As for C++ tutorials, I don't know any reference site, but google should know.

---

### Post by SteveNorman on 2008-07-22
I like the matching parenthesis feature in VIM..also the line numbering. I use vim or gedit (which can also be set to line number). save the text as whatever.cpp, where whatever is the name of the program you are making.

in a terminal just do:
```

g++ whatever.cpp -o whatever
```

to compile....

and do:

```
./whatever 
```

...to run

here is a good tutorial:

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by iampriteshdesai on 2008-07-22
iS There any GUI for G++? Rather than staring at terminal any thing with optins like menu> edit, compile?

---

### Post by lamego on 2008-07-22
Try code::blocks, you can get it from [http://www.getdeb.net/app/code::blocks](http://www.getdeb.net/app/code::blocks) .

---

### Post by Sef on 2008-07-22
Moved to programing talk.

---

### Post by era86 on 2008-07-22
> **lamego said:**
> Try code::blocks, you can get it from [http://www.getdeb.net/app/code::blocks](http://www.getdeb.net/app/code::blocks) .

+1

Anjuta also has the compile/project feature.

---

### Post by KIAaze on 2008-07-22
> **iampriteshdesai said:**
> iS There any GUI for G++? Rather than staring at terminal any thing with optins like menu> edit, compile?

I think you're looking for an IDE ([Integrated Development Environment]("http://en.wikipedia.org/wiki/Integrated_development_environment")).
That's what the list I gave you earlier is for.
(also contains Anjuta & Code::Blocks ;) )

Most IDEs (those available for GNU/Linux anyway) use gcc and g++ as compilers, so one could say that they're a "compiler GUI", altough they do much more than that, like giving auto-completion, syntax highlighting, package building, etc.
They also offer a GUI for debugging tools like gdb and valgrind.

---

### Post by StOoZ on 2008-07-22
I would suggest on using netbeans (use google to search it).
:guitar:

---

### Post by nvteighen on 2008-07-22
I suggest you not to go for a IDE and learn what's going on when you compile a program.

If you want to learn C++, you've better be prepared to know the internal of things... Afterwards, you can leave something automate things, but if for some reason the IDE doesn't work (more usual than you think), you'll be able to fix it by yourself. When using a compiled lower-level language, you have to be independent and know how stuff work.

If you want to have something simple that doesn't need know how to compile, go for Python or any other higher-level interpreted language. There's nothing bad at them.

"Compiled" doesn't mean "superior", just "compiled".

---

### Post by LaRoza on 2008-07-22
See the sticky.

---

