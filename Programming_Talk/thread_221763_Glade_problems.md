---
title: "Glade problems"
date: 2006-07-24
forum: Programming Talk
---

### Post by goodfella on 2006-07-24
I am trying to compile a program I made in glade however when I run the autogen.sh script I get the following error:

You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/local/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from

I don't understand why it requires so much extra work to compile this after installing glade through the package manager.  Any help on this would be great.

---

### Post by simonn on 2006-07-24
> 
I don't understand why it requires so much extra work to compile this after installing glade through the package manager. 


Because you are compiling your own software. 

Welcome to the wonderful world of autotools... mwahahahahaaaaa!

Quit your moanin' and get a readin' the autoconf, automake, libtool and pkgconfig manuals.

Alternatively, just do what the message (which the developers have helpfully included, tells you EXACTLY what to do and is right there in front of you in black and white) says. No, really, they did not just add that message for their own amusement.

---

### Post by tomcio on 2006-07-24
...then, after you read those manuals, generate some project with Glade and build some code for it using Glade. I will be very helpful to understood how autotools work in practice ;) 

Have fun, I personally hate this stuff:p

---

