---
title: "again i have a problem with GUI's"
date: 2006-03-24
forum: Programming Talk
---

### Post by sharperguy on 2006-03-24
OK FORGET WHAT WAS HERE B4!

I fixed that but it would be more apropriate to keep this here:

Ok

I am trying to compile a program a wrote in gtkmm with the help of glade

I ran autogen.sh 

configure ran and exited with no errors
however make did not:

/usr/bin/make  all-recursive
make[1]: Entering directory `/home/sharp/Projects/piepie'
Making all in m4
make[2]: Entering directory `/home/sharp/Projects/piepie/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sharp/Projects/piepie/m4'
Making all in po
make[2]: Entering directory `/home/sharp/Projects/piepie/po'
make[2]: *** No rule to make target `/config.status', needed by `Makefile'.  Stop.
make[2]: Leaving directory `/home/sharp/Projects/piepie/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sharp/Projects/piepie'
make: *** [all] Error 2


I have no idea what  to make of this

Does anyone else?

---

### Post by sharperguy on 2006-03-25
<removed too long and unnesesary due to later posts>

---

### Post by sharperguy on 2006-03-30
ok forget that ive started using glade with gnomemm instead of gtk mm and when i run ./configure i get:
```
Package libgnomemm-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomemm-2.0.pc'
to the PKG_CONFIG_PATH environment variable
```

Even though libgnomemm-2.0 is installed (and so is -dev)

After that when i run make i get:
```

make: *** No rule to make target `@MAINTAINER_MODE_TRUE@', needed by `Makefile.in'.  Stop.
```

Which is weird.

Now i am really confused!

---

### Post by TitusDalwards on 2006-03-31
for compiling a code under GTK you must follow these:
at fisrt goto projrct directorry
```
cd ~/Projects/project1
```
and then
```
./autogen.sh
```
if you do not have erros 
```
make
```
again no erros
```
cd src
```
```
./project1
```
you compile a program and run it with these commands

---

### Post by sharperguy on 2006-04-01
yea i know
thing is it's those commands that are giving me errors. You should read over what i have written.

i maneged to get it recognising libgnomemm2.0 (by installing 2.0 rather than 2.6) and now it wants libgnomeuimm2.0 which is nowhere to be found in synaptic with all possible repositoroies activated! (ie all the ones in synaptic)

---

### Post by sharperguy on 2006-04-02
Ok, i got libgnomeuimm

However when i ru autogen.sh i get (and have always been getting):
```
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.59
checking for automake = 1.4...
  testing automake-1.4... found 1.4
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.8.3
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running aclocal-1.4...
Running autoconf2.50...
Running autoheader2.50...
Running automake-1.4...
configure.in: 7: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'

```
Not sure where to put the files when i find them.

Also after that (i assume because of the latter) when i run ./configure it works fine but it says at the top that makeinfo is missing (dunno if thats impostant).

Then when i run make i get:
```
 make: *** No rule to make target `@MAINTAINER_MODE_TRUE@', needed by `Makefile.in'.  Stop.

```

---

### Post by sharperguy on 2006-04-05
problem is still persitiing

---

