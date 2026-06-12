---
title: "How do I make my c++ program executable by a single command via terminal?"
date: 2009-09-16
forum: Programming Talk
---

### Post by daweefolk on 2009-09-16
I have a program I've written in c++. I can load it by cd'ing to the correct directory and using ./myprogram. 
What I want to know is how can I make it so rather than doing that I could simply type "myprogram" in the terminal and it would load? I need some guidance. a tutorial or how-to thread, if available, would be nice.
thanks in advance

---

### Post by MadCow108 on 2009-09-16
add the path where the program is to the $PATH variable:
export PATH=$PATH:/path/to/program

or copy the program to one of the path's already specified in the $PATH variable (usually /usr/bin etc, view it with "echo $PATH")

or make an alias of the program:
alias myprogram='/path/to/program/program.exe'
and add this to your .bashrc

---

### Post by Habbit on 2009-09-16
You need the program to reside in a directory that appears in the PATH environment variable. As the popular saying involving Muhammad and a mountain (that has requested anonymity) goes, you either copy the program to a directory in the PATH, or add the directory containing the program to the PATH.

---

### Post by TheBuzzSaw on 2009-09-16
You can also just add ./ to your PATH. That lets you run programs in the current folder.

---

### Post by sunchiqua on 2009-09-16
Create an alias in [COLOR=Magenta]~/.bashrc[/COLOR].

---

### Post by daweefolk on 2009-09-16
Thanks everybody! I used the export PATH method and it works great! between this forum and a c++ forum I've gotten my program working great

---

