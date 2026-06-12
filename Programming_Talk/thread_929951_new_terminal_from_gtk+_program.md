---
title: "new terminal from gtk+ program"
date: 2008-09-25
forum: Programming Talk
---

### Post by Ulrik04 on 2008-09-25
hello :)

I'm making a program in c++/gtk+, and I have to tun another terminal c++ program from it. I've tried system("./program"); but that just shows the program in the terminal the gtk program was run from, and if I doesn't run the gtk program from a terminal, nothing will happen. (did that make sense? :/)
my question is just: how do i open a terminal window, that is executing a file, from a c++ program?

---

### Post by Zugzwang on 2008-09-26
You can try system("xterm -e \"./program\"") or something like that. I'm afraid that you will have to explicitly specify a terminal program.

Alternative, you can get the output of the called program using popen() and display them somewhere in your application.

---

### Post by Ulrik04 on 2008-09-26
thanks that worked ok :D

---

