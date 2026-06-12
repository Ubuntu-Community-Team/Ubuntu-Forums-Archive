---
title: "gcc help"
date: 2008-11-27
forum: Programming Talk
---

### Post by phanipalagummi on 2008-11-27
Thanks to ubuntuforums without which i maynot think of starting GCC.
however i need some more help ,to get in to it,please help me in clarifying this

1.How to increase the font size in emacs


2.I need to organise all my .out files , .c files at seperate places
  i.e i need to send all .out files at one dir and .c at other dir    during the compiling and running on terminal.


3.where to see all the headerfiles and associated functions with it

---

### Post by monkeyking on 2008-11-27
> **phanipalagummi said:**
> Thanks to ubuntuforums without which i maynot think of starting GCC.
however i need some more help ,to get in to it,please help me in clarifying this

1.How to increase the font size in emacs


2.I need to organise all my .out files , .c files at seperate places
  i.e i need to send all .out files at one dir and .c at other dir    during the compiling and running on terminal.


3.where to see all the headerfiles and associated functions with it

1. I need to make it smaller,
so I did
```

(setq default-frame-alist '(
   (font . "6x10")
  }
)

```
In my .emacs

2. I don't understand what you want.
Do you want the compiler to move your sourcecode around your system at compile time?
I can recommend the internal emacs command 
```
alt x - compile
```
This will invoke the make command as default. This of cause requires you to use a Makefile. But you should use Makefiles.

3. try the speedbar, or the emacs code browser

---

### Post by crazyfuturamanoob on 2008-11-27
Font size can be decreased/increased in almost every program by holding down ctrl and rolling mouse wheel either up or down.

Works also with firefox too. And this way font size changes should be persistent.

---

### Post by jpkotta on 2008-11-27
> **crazyfuturamanoob said:**
> Font size can be decreased/increased in almost every program by holding down ctrl and rolling mouse wheel either up or down.

Emacs is not most programs.  

It's in the customization system, under "Faces".  The way Emacs faces (fonts) work is a hierarchy.  There is a default face, and other faces are based on that, possibly with some changes (e.g. color, bold, etc.).  So if you change that, it should get inherited by all other faces.

---

