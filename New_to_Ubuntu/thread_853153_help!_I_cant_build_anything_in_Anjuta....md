---
title: "help! I cant build anything in Anjuta..."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by hammeraxe on 2008-07-08
here is my problem:
1.I create a new project in anjuta and choose generic c++
2.all the necessary files are created
3.the only source file is main.cc which contains some hello world code
4.I compile main.cc without any problems
5.then i want to build the executable, which is not possible because the Build->Build menu entry is greyed out...

what is it with this? what am i missing?

---

### Post by KIAaze on 2008-07-08
Mmh, I don't even have a "Build executable" option. What version are you using?

If you managed to compile it, that means you already have created the executable.

It should be src/<project_name>.

Personally, I'm having problems when trying to "run the program in a terminal" (build execute program).
Anjuta just hangs when I do this.
My solution was to run Anjuta from a terminal and uncheck the "run in terminal" box. That way I get the output in the terminal from which I ran Anjuta.

P.S:
I started with Anjuta too in GNU/Linux, but now I mostly use Kate and KDevelop.
Here's a quite exhaustive list of programming IDEs:
[http://www.linuxquestions.org/questions/programming-9/list-of-free-software-and-freeware-ides-469623/](http://www.linuxquestions.org/questions/programming-9/list-of-free-software-and-freeware-ides-469623/)

---

### Post by hammeraxe on 2008-07-09
it does compile but when i try to run the program (by pressing F3 or selecting the menu item) it just says the executable doesnt exist... therefore i assumed that i have to build it after compiling

anyway my xubuntu 8.04 comp died yesterday so unfortunately cannot try any other IDEs but i start to think that the problem was caused by the lack of some ubuntu packages rather than an anjuta glitch..

---

