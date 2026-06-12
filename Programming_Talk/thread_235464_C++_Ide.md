---
title: "C++ Ide?"
date: 2006-08-13
forum: Programming Talk
---

### Post by mikesena on 2006-08-13
Hi,

I want to learn / am learning c++.  I have anjuta and kdevelop, but i am having trouble with kdevelop and automake, so ive been using anjuta.

Is there a IDE for linux that's like visual c++, where y ou can drag and drop, or:
a)  there isn't, sorry
b)  i should be learning how to do it without that style
c)  i can in either anjuta or develop, if so, how
d)  there is, it is...:

please help ;)

---

### Post by simonn on 2006-08-13
Assuming you mean d'n'd for GUI creation, have a look at Glade.

EDIT: IMO you are better to code GTK by hand though.

---

### Post by jeff_ on 2006-08-13
What problems were you having with KDevelop and automake? Would you like to get that to work?

---

### Post by mikesena on 2006-08-14
When I open KDevelop, I click 'New Project', 'C', 'GNOME', 'GNOME 1 Application Framework', enter project name of 'MyGnome' and click next until the wizard closes.

I click build, 'Run Them', and get this error:```
cd '/home/meo/KDevelop/mygnome' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/meo/KDevelop/mygnome/debug' && cd '/home/meo/KDevelop/mygnome/debug' && CFLAGS="-O0 -g3" "/home/meo/KDevelop/mygnome/configure" --enable-debug=full && cd '/home/meo/KDevelop/mygnome/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
srcdir=`pwd` NOCONFIGURE=1 sh macros/autogen.sh
sh: macros/autogen.sh: No such file or directory
make: *** [all] Error 127
*** Exited with status: 2 ***
```

What's wrong?

---

### Post by jeff_ on 2006-08-14
heh, actually I just installed KDevelop and got those same errors. I usually use Anjuta though. If I find a solution I'll post it here for you.

---

### Post by mikesena on 2006-08-14
Thanks, it's really bugging me, a solution would be nice ;)

---

### Post by X.Cyclop on 2006-08-15
Glade, QtDesigner.;) 

> EDIT: IMO you are better to code GTK by hand though.
:-k

---

### Post by simonn on 2006-08-15
> **X.Cyclop said:**
> :-k

Correct me if I am wrong, but glade does not allow you to use the user_data parameter on most GTK function calls. This is pretty fundamental to how GTK is meant to be used.

It is good for doing quick mock-ups etc.

---

### Post by X.Cyclop on 2006-08-15
> **simonn said:**
> Correct me if I am wrong, but glade does not allow you to use the user_data parameter on most GTK function calls. This is pretty fundamental to how GTK is meant to be used.

It is good for doing quick mock-ups etc.
I really don't know.:sad: 
I prefer coding by hand instead of using a Visual Editor (yes, i hate Dreamweaver, Frontpage, Glade, KDevelop...).

---

