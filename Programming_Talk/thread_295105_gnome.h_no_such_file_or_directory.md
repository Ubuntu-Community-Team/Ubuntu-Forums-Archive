---
title: "gnome.h: no such file or directory"
date: 2006-11-07
forum: Programming Talk
---

### Post by pyter on 2006-11-07
after building a project with glade-2, when i do *make* i got the following error:

```
main.c:10:19: error: gnome.h: No such file or directory
```

well actually it wasn't just that... this i what i got:

```
psemeano@psemeano-laptop:~/fct/rit1/trab2/gui_t2$ make
make all-recursive
make[1]: Entering directory `/home/psemeano/fct/rit1/trab2/gui_t2'
Making all in src
make[2]: Entering directory `/home/psemeano/fct/rit1/trab2/gui_t2/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.c:10:19: error: gnome.h: No such file or directory
In file included from main.c:13:
interface.h:5: error: syntax error before &#8216;*&#8217; token
interface.h:5: warning: data definition has no type or storage class
main.c: In function &#8216;main&#8217;:
main.c:32: error: &#8216;LIBGNOMEUI_MODULE&#8217; undeclared (first use in this function)
main.c:32: error: (Each undeclared identifier is reported only once
main.c:32: error: for each function it appears in.)
main.c:34: error: &#8216;GNOME_PARAM_APP_DATADIR&#8217; undeclared (first use in this function)
main.c:42: warning: assignment from incompatible pointer type
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/psemeano/fct/rit1/trab2/gui_t2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/psemeano/fct/rit1/trab2/gui_t2'
make: *** [all] Error 2
```

can someone help me please?

thanks in advance.

---

### Post by llonesmiz on 2006-11-08
You need to install *-dev packages to be able to compile programs using libraries. For gnome.h you will probably need libgnomeui-dev. Maybe you will need to install other packages after that, if there are problems post the errors. Good luck.

---

### Post by pyter on 2006-11-08
thank you for the answer, but i already got that package installed.

```
psemeano@psemeano-laptop:~$ sudo apt-get install libgnomeui-dev
Reading package lists... Done
Building dependency tree... Done
libgnomeui-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

help... :-|

---

### Post by llonesmiz on 2006-11-08
Acording to packages.ubuntu.com, the only packages that contain a file called gnome.h are libgnomeui-dev and gnome1.0-dev. Is it possible that your program uses that old library? Could you post the complete source code as an attachment so I can try it?

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gnome.h&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gnome.h&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

---

### Post by pyter on 2006-11-09
yes i think it uses gnome1.0-dev. and that package i don't have.

here you have the folder. the only thing you have to do is *make*.

[http://students.fct.unl.pt/~pns16676/gui_t2.tar.gz]("http://students.fct.unl.pt/~pns16676/gui_t2.tar.gz")

thanks for the help ;)

---

### Post by llonesmiz on 2006-11-09
I'm not an expert in autotools but I think I found a problem in the makefiles. I solved it  by changing the file "configure.in" in the root directory and "makefile.am" in the "src" directory. 
You need to change:

pkg_modules="gtk+-2.0 >= 2.0.0"->pkg_modules="gtk+-2.0 >= 2.0.0 libgnomeui-2.0"

in "configure.in".

And add:

gui_t2_CFLAGS = @PACKAGE_CFLAGS@

at the end of "makefile.am".

After that you need to execute "./autogen.sh" from the root directory and then make.

Good luck.

---

### Post by pyter on 2006-11-11
it worked! thank you very much! ;) :D

---

