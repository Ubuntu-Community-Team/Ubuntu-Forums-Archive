---
title: "How to install GTK with C development??"
date: 2006-02-22
forum: Programming Talk
---

### Post by sands on 2006-02-22
Hi,Im a newbie to linux programming. I want to prgram in C with GTK.
Can anyone guide me how to install the packages required..I installed a anjuta ide .
But some errors are comming wile compiling and building.

while compiling in terminal

gcc 1.c -o base 'gtk-config -cflags -libs'

gcc: gtk-config -cflags -libs: No such file or directory
1.c:2:21: error: gtk/gtk.h: No such file or directory
1.c: In function ‘main’:
1.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
1.c:6: error: (Each undeclared identifier is reported only once
1.c:6: error: for each function it appears in.)
1.c:6: error: ‘window’ undeclared (first use in this function)
1.c:8: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)


Help me!!

---

### Post by sapo on 2006-02-22
```
sudo apt-get install libgtk2.0-dev
```

this should solve your problem :)

---

### Post by sands on 2006-02-22
again the same error!!!

sandesh@sandesh:~/gtk$ gcc 1.c -o base 'gtk-config -cflags -libs'
gcc: gtk-config -cflags -libs: No such file or directory
1.c:2:21: error: gtk/gtk.h: No such file or directory
1.c: In function ‘main’:
1.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
1.c:6: error: (Each undeclared identifier is reported only once
1.c:6: error: for each function it appears in.)
1.c:6: error: ‘window’ undeclared (first use in this function)
1.c:8: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)

---

### Post by fct on 2006-02-22
From the way you are compiling (gtk-config is obsolete) I guess you're using an outdated gtk1.2 manual. Check the current 2.0 tutorial instead:

[http://gtk.org/tutorial/](http://gtk.org/tutorial/)

---

### Post by sands on 2006-02-22
I downloaded the latest manual (GTK+ 2.0 Tutoria)l  frm [www.gtk.org](www.gtk.org) .
the syntax tat is given to compile, I copy pasted it in the terminal.
I guess there is some prob with my installation.

---

### Post by andrew4558 on 2008-03-16
To compile a gtk program, do this in console ( i.e: your program is called base.c):
$ gcc -Wall -g base.c -o base `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`

Note: You must have the tick key ( `) before and after the pkg-config -cflags and libs.
The tick key is found on the left below the Esc key on your keyboard. To check if pkg-config
is installed in your system, type:  pkg-config --cflags --libs glib-2.0

---

### Post by bruce89 on 2008-03-16
> **andrew4558 said:**
> To compile a gtk program, do this in console ( i.e: your program is called base.c):
$ gcc -Wall -g base.c -o base `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`


More short:

```
gcc -g -Wall `pkg-config --cflags --libs gtk+-2.0` -o base base.c
```

---

### Post by WW on 2008-03-16
andrew4558 called the delimiting character a "tick". I've also heard it called a "single back quote" or a "back tick".

I've been told that this character is not standard on some keyboards in Europe (German?).  An alternative method to achieve the effect is to use $(comands...) instead of `commands...`, i.e.
```

gcc -g -Wall $(pkg-config --cflags --libs gtk+-2.0) -o base base.c

```

---

### Post by ementos on 2010-01-15
I wrote that and I gon new error:
```
$ gcc -g -Wall $(pkg-config --cflags --libs gtk+-2.0) -o base gtkpp.cpp
/tmp/ccyFeV8e.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```
What's that?

---

### Post by Zugzwang on 2010-01-15
> **ementos said:**
> 
What's that?

This error occurs when you try to compile a C++ program with "gcc" instead of "g++". BTW: A quick google search would have told you that.

---

### Post by ementos on 2010-01-15
Thanks a lot =)

---

### Post by ementos on 2010-11-02
I have only one question... cause some of GTK examples programms is able to compile, but at least one because I was writing some exercises to set label text, but any worked... even when I coppied last example from this site (Increase - Decrease): [http://zetcode.com/tutorials/gtktutorial/firstprograms/](http://zetcode.com/tutorials/gtktutorial/firstprograms/)
and it wasn't able to compile... Is something wrong with my library?
Greet
Józek

---

### Post by kiranmatrixlee on 2013-05-04
could you please advice me the latest setup for gtk development.

we have qt creator for developing application easly.Is there any ide for gtk now???

---

