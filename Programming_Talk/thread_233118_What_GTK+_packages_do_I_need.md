---
title: "What GTK+ packages do I need?"
date: 2006-08-09
forum: Programming Talk
---

### Post by CraigWilliamson on 2006-08-09
Hi There,

Please bare with me I am new to the forums.  I am wanting to do some command line GTK+ programming for a small university project I want to do.  But at the moment I don't know what packages in the repositories I need to get the project moving.  At the moment I get the following error messages when I compile using gcc:

```

craig@craiglap:~/University/ENEL350/Project 3/Test Program$ gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
base.c:1:21: error: gtk/gtk.h: No such file or directory
base.c: In function ‘main’:
base.c:5: error: ‘GtkWidget’ undeclared (first use in this function)
base.c:5: error: (Each undeclared identifier is reported only once
base.c:5: error: for each function it appears in.)
base.c:5: error: ‘window’ undeclared (first use in this function)
base.c:9: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
craig@craiglap:~/University/ENEL350/Project 3/Test Program$

```

I couldn't find the gtk source and other related packages in Synaptic, so I am either looking in the wrong place or I having a bad day ](*,) .  If you could help it would be greatly appreciated.  Thanks and good luck.


Craig Williamson

---

### Post by Engnome on 2006-08-09
You probably need the -dev packages of GTK. Search in synaptic. (youre nr 2 or 3 I've told to do this today.)

---

### Post by Daverz on 2006-08-09
You need libgtk2.0-dev.

---

### Post by jerstamb on 2006-10-13
Daverz;

Thanks for answering my question.  Didn't know I asked?  :-D 
I was gonna but saw your post before I had to.  

thanks,  My compile job ran without a flaw

Jerry

---

