---
title: "KDevelop: Small scale project"
date: 2006-12-13
forum: Programming Talk
---

### Post by Verminox on 2006-12-13
KDevelop is really cool as an IDE, and works well with gcc, etc. so it's great for my development needs.

However, everytime I create a project it creates a whole load of files, such as readme, license, debugging information, etc. and it always compiles first into debug mode. My hello world program was around 100KB in size.

When I want to test something out quickly... such as... if I find a c/c++ snippet online and I want to test it by compiling a small source file, I have to always make a big project.

Is there any way to make a small project or be able to compile a single file into an executable binary without a big hassle?

---

### Post by oly on 2006-12-13
lol, i often want to do this i ended up with loads of project files littered all over the place just trying out snippets of code.

i usually fine gedit and terminal to compile the best solution but would like to hear of a gui one if anyone has suggestions

---

### Post by Verminox on 2006-12-13
whats the best way to compile via terminal? Say I have a hello.cpp with a main() function... or maybe a header file or two with it... will it be really complicated to compile through command line?

---

### Post by kaamos on 2006-12-13
> 
Say I have a hello.cpp with a main() function... or maybe a header file or two with it... will it be really complicated to compile through command line?


```
g++ -Wall hello.cpp
```

Not actually rocket science. :) IDEs are not really meant for programs like that since those are much simpler to compile with just a text editor and terminal. So very few IDEs support any simple way to just test out snippets.

---

### Post by oly on 2006-12-14
i came up with a neat solution, use gedit and add in the plugin external tools then you can run commands on your code.

gnome-terminal -x "python $GEDIT_CURRENT_DOCUMENT_NAME"

could do something similar for c or c++ i should think, you do not need the gnome terminal bit i wanted the window to stay open for errors but have not found away yet.

---

