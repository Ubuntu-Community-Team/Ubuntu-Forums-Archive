---
title: "Problems with compiling in terminal and netbeans"
date: 2008-06-14
forum: Programming Talk
---

### Post by AnthonyArde2 on 2008-06-14
Hi, i`m trying to set up my netbeans c++ ide and have it able to make gtkmm projects, i have installed pkg-config and gtkmm2.4 and all dependencies that i am aware of but i cannot compile my project, i recieve the same error in netbeans as i do in the terminal: here is the error:

anthony@Anthony-linux:~/Desktop/Application_1$ g++ newmain.cc -o newmain ‘pkg-config gtkmm-2.4 --cflags --libs‘
g++: ‘pkg-config: No such file or directory
g++: gtkmm-2.4: No such file or directory
cc1plus: error: unrecognized command line option "-fcflags"
cc1plus: error: unrecognized command line option "-flibs‘"
anthony@Anthony-linux:~/Desktop/Application_1$ 

please assist if you know what this is, i`m also trying to include the gtkmm.h in my project but i cant find the file anywhere on my computer, where is this file, shouldnt it be installed with the gtkmm package?

thanks

Anthony

---

### Post by geirha on 2008-06-14
You are using the wrong quotes. You need to use ``, and not &#8216;&#8216;. Alternatively you can use $(), so try one of: ```
g++ newmain.cc -o newmain `pkg-config gtkmm-2.4 --cflags --libs`
g++ newmain.cc -o newmain $(pkg-config gtkmm-2.4 --cflags --libs)
```

---

### Post by AnthonyArde2 on 2008-06-14
Thanks i got it working on the terminal but not on netbeans or eclipse, do you know how to add gtkmm.h to an eclipse or netbeans project? because if i add the code include <gtkmm.h> it wont find the file, in eclipe under the includes folder i have added /usr/include/gtkmm-2.4 and it still doesnt work.

also what is the difference between a make file project and an executable project? because with the make file project in ecplise there is a few extra files that i dont know about eg: a .o file.

Thanks for your assistance

---

