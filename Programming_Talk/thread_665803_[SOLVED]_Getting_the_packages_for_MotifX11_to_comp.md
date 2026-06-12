---
title: "[SOLVED] Getting the packages for Motif/X11 to compile"
date: 2008-01-12
forum: Programming Talk
---

### Post by bigb_thedestroyer on 2008-01-12
Hi, I'm trying to get all the stuff I need to do Motif development for school.  This is the program im trying to compile
```
#include <stdio.h>
#include <stdlib.h>
#include <Xm/Xm.h>
#include <Xm/Label.h>

/* Xt part of the X Toolkit */
XtAppContext context;
/* Xm part of Motif */ 

XmStringCharSet char_set = XmSTRING_DEFAULT_CHARSET;
Widget toplevel, label;
int main(int argc, char* argv[]){
  Arg al[10]; /* argument list */
  int ac;	/* argument counter */

  /* Creat the toplevel shell */
  toplevel = XtAppInitialize(&context,"XmLabelDemo",NULL,0,&argc,argv,NULL,NULL,0);
  /*  Create label widget*/
  ac = 0;
  XtSetArg(al[ac],XmNlabelString,XmStringCreateLtoR("Hello World", char_set));
  ac++;
  label = XmCreateLabel(toplevel,"label",al,ac);
  XtManagerChild(label);
  XtRealizeWidget(toplevel);
  XtAppMainLoop(context);
  exit(EXIT_SUCCESS);
}
```

This compiles in my classroom computer.

I installed alot of packages that had motif or X11 in the name and from going to over a couple hundred errors, im down to 2.  

```
gcc label.c 
In file included from label.c:3:
/usr/include/Xm/Xm.h:59:34: error: X11/extensions/Print.h: No such file or directory
In file included from label.c:3:
/usr/include/Xm/Xm.h:827: error: expected specifier-qualifier-list before ‘XPContext’

```

Could someone help me clear up these errors.  Thanks

Brian

---

### Post by stroyan on 2008-01-13
You can search for missing header files using the apt-get package and command.
```
$ sudo apt-get install apt-file
$ sudo apt-file update
$ apt-file search X11/extensions/Print.h
x11proto-print-dev: usr/include/X11/extensions/Print.h
```
X11/extensions/Print.h is in the x11proto-print-dev package.

---

### Post by bigb_thedestroyer on 2008-01-13
Thanks stroyan,
That did get me the header file I was after.

Now, when I compile with...
```
gcc -o label label.c -lXm -lXt -lX11
```

I get an error,
```

/tmp/ccWcYiQW.o: In function `main':
label.c:(.text+0xc6): undefined reference to `XtManagerChild'
collect2: ld returned 1 exit status

```

I dont know what other lib I have to link, and some webpages I found told to like the three libs I did above.  Any help is appreciated.

Thanks,
Brian

---

### Post by llonesmiz on 2008-01-13
After a little googling, and knowing absolutely nothing about motif or x, I would say that the function you want to use is "XtManageChild" and not "XtManagerChild".

---

### Post by Compyx on 2008-01-13
Don't know much about X11 development, but looking at the man-pages, there is no XtManagerChild() function, there is, however, an XtManageChild() function.
Perhaps a little typo?

---

### Post by bigb_thedestroyer on 2008-01-13
That was the problem!  I probably did typo after pulling it off my prof's website and playing around with it.
heh, I should try to troubleshoot more!

Thanks alot guys (or gals!)

brian

---

