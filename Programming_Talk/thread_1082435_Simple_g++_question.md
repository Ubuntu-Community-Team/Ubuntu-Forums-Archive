---
title: "Simple g++ question"
date: 2009-02-27
forum: Programming Talk
---

### Post by ForMar on 2009-02-27
I recently started a programing class and we are learning how to use objects for now we are learning how to do simple c++ graphics and my teacher says we need to use X11 terminal, so my question is where is or how do I install this X11 terminal.
Thanks alot!

---

### Post by dwhitney67 on 2009-02-27
Your teacher probably meant that you need to use a window manager that supports X11 applications.  If you are using Ubuntu, then you are set; it uses Gnome.

Other usable window managers include KDE, XFCE, twm, etc.

---

### Post by mnasimh on 2009-02-27
Applications > Accessories > Terminal

---

### Post by ForMar on 2009-02-27
hummm then I must be doing something wrong when compiling because he told us to put in this command;

```
g++ -o executableName sourceFile.cpp ccc_x11.cpp ccc_shap.cpp -L/usr/X11R6/lib -lX11
``` 
if you are using *nix, but I get a whole bunch of errors prob not even worth mentioning and it probably has something to do with the fact that there is no /usr/X11R6/lib
anyone know maybe what I am supposed to put in?

---

### Post by krzysz00 on 2009-02-27
Post the errors please. Try changing /usr/X11R6/lob to /usr/lib

---

### Post by ForMar on 2009-02-27
> **krzysz00 said:**
> Post the errors please. Try changing /usr/X11R6/lob to /usr/lib

```
anthony@bread:~/Documents/cs11/lib$ g++ -o test test.cpp ccc_x11.cpp ccc_shap.cpp -L/usr/lib -lX11
In file included from ccc_win.h:18,
                 from turtlelib.h:5,
                 from turtlelib.cpp:5,
                 from test.cpp:1:
ccc_x11.h:5:22: error: X11/Xlib.h: No such file or directory
ccc_x11.h:6:23: error: X11/Xutil.h: No such file or directory
ccc_x11.h:7:23: error: X11/Xatom.h: No such file or directory
ccc_x11.h:8:24: error: X11/keysym.h: No such file or directory
ccc_x11.h:9:21: error: X11/Xos.h: No such file or directory
In file included from ccc_win.h:18,
                 from turtlelib.h:5,
                 from turtlelib.cpp:5,
                 from test.cpp:1:
ccc_x11.h:100: error: &#8216;Display&#8217; has not been declared
ccc_x11.h:100: error: &#8216;Window&#8217; has not been declared
ccc_x11.h:188: error: ISO C++ forbids declaration of &#8216;XFontStruct&#8217; with no type
ccc_x11.h:188: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
ccc_x11.h:189: error: &#8216;Pixmap&#8217; does not name a type
ccc_x11.h:191: error: &#8216;Window&#8217; does not name a type
ccc_x11.h:192: error: ISO C++ forbids declaration of &#8216;Display&#8217; with no type
ccc_x11.h:192: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
ccc_x11.h:194: error: &#8216;GC&#8217; does not name a type
In file included from ccc_x11.cpp:15:
ccc_x11.h:5:22: error: X11/Xlib.h: No such file or directory
ccc_x11.h:6:23: error: X11/Xutil.h: No such file or directory
ccc_x11.h:7:23: error: X11/Xatom.h: No such file or directory
ccc_x11.h:8:24: error: X11/keysym.h: No such file or directory
ccc_x11.h:9:21: error: X11/Xos.h: No such file or directory
In file included from ccc_x11.cpp:15:
ccc_x11.h:100: error: &#8216;Display&#8217; has not been declared
ccc_x11.h:100: error: &#8216;Window&#8217; has not been declared
ccc_x11.h:188: error: ISO C++ forbids declaration of &#8216;XFontStruct&#8217; with no type
ccc_x11.h:188: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
ccc_x11.h:189: error: &#8216;Pixmap&#8217; does not name a type
ccc_x11.h:191: error: &#8216;Window&#8217; does not name a type
ccc_x11.h:192: error: ISO C++ forbids declaration of &#8216;Display&#8217; with no type
ccc_x11.h:192: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
ccc_x11.h:194: error: &#8216;GC&#8217; does not name a type
ccc_x11.cpp:45: error: variable or field &#8216;open&#8217; declared void
ccc_x11.cpp:45: error: &#8216;Display&#8217; was not declared in this scope
ccc_x11.cpp:45: error: &#8216;d&#8217; was not declared in this scope
ccc_x11.cpp:45: error: &#8216;Window&#8217; was not declared in this scope
anthony@bread:~/Documents/cs11/lib$ 


```

its the same error either way

also I'm not sure if its worth mentioning but I'm using PPC

---

### Post by dwhitney67 on 2009-02-27
Try specifying these libraries when you link:
```

-lXm -lXt -lX11

```

Do not specify the -L option; I do not believe it is necessary because the X libraries are (nowadays) located in /usr/lib.  The proper names for the libraries listed above are:
[LIST]
[*]libXm.so
[*]libXt.so
[*]libX11.so
[/LIST]
These are all symbolic links in /usr/lib.

P.S.  Header files are in /usr/include/X11; since your compiler is telling you that the files cannot be found, this is indicating that you do not have the X11 development package installed on your system.  Go through the Synaptic Package Manager to install the appropriate package(s).

---

### Post by ForMar on 2009-02-27
> **dwhitney67 said:**
> Try specifying these libraries when you link:

P.S.  Header files are in /usr/include/X11; since your compiler is telling you that the files cannot be found, this is indicating that you do not have the X11 development package installed on your system.  Go through the Synaptic Package Manager to install the appropriate package(s).

Thanks A lot! I really appreciate it! 
But now it seems im having another issues but if I'm not mistaken it has something to do with the provided lib for the obj and not with anything on ubuntu but I'm hoping someone can let me know if im right :)

```
anthony@bread:~/Documents/cs11/lib$ g++ -o test test.cpp ccc_x11.cpp ccc_shap.cpp -lXm -lXt -lX11
ccc_x11.cpp: In function ‘int main(int, char**)’:
ccc_x11.cpp:429: warning: deprecated conversion from string constant to ‘char*’
ccc_x11.cpp:498: warning: deprecated conversion from string constant to ‘char*’
/usr/bin/ld: cannot find -lXm
collect2: ld returned 1 exit status

```


again thanks for your time and help!

---

### Post by monkeyking on 2009-02-27
you are likely to have something like

[PHP]
char *name ="John doe"
[/PHP]
do something like

[PHP]
const *char name= "john doe"
[/PHP]
If it makes sense in the context of your program
But this will just fix the warning

Try also removing -lXm

---

