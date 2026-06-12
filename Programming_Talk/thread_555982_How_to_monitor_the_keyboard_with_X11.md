---
title: "How to monitor the keyboard with X11"
date: 2007-09-20
forum: Programming Talk
---

### Post by fyplinux on 2007-09-20
I intend to code a program that can capture all the input from the keyboard with the X11 library,in advance, the program can write something into the output stream, e.g,  "a" is hitted, the program monitor this, and output “A”&#65292;where there is some mapping.

 I think I need some guidelines to show me how to start. Could  you give some websites or sample code, or anything else on this subject.

Regards.

Paul.

---

### Post by gnusci on 2007-09-21
I do not use directly X11, cause Xlib is not practical for directly applications programming:

[http://tronche.com/gui/x/xlib-tutorial/2nd-program-anatomy.html](http://tronche.com/gui/x/xlib-tutorial/2nd-program-anatomy.html)
[http://www.linuxjournal.com/article/4879](http://www.linuxjournal.com/article/4879)
[http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html](http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html)


for this purpose various toolkits have been written that give you layer with all appropriate the method for GUI app development instead:

[http://www.sai.msu.su/sal/F/5/](http://www.sai.msu.su/sal/F/5/)

In fact I use: [www.fltk.org](www.fltk.org)

---

### Post by fyplinux on 2007-09-21
> **gnusci said:**
> I do not use directly X11, cause Xlib is not practical for directly applications programming:

[http://tronche.com/gui/x/xlib-tutorial/2nd-program-anatomy.html](http://tronche.com/gui/x/xlib-tutorial/2nd-program-anatomy.html)
[http://www.linuxjournal.com/article/4879](http://www.linuxjournal.com/article/4879)
[http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html](http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html)


for this purpose various toolkits have been written that give you layer with all appropriate the method for GUI app development instead:

[http://www.sai.msu.su/sal/F/5/](http://www.sai.msu.su/sal/F/5/)

In fact I use: [www.fltk.org](www.fltk.org)

 I think if whatever these package can do, X11 can also do it. right ??

---

### Post by gnusci on 2007-09-21
Yeah, in theory you can do what ever you want the question is how long time can take.... anyway if you want to use X11 it is ok... I gave you links with some info...

---

