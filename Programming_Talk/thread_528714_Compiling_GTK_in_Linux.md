---
title: "Compiling GTK in Linux"
date: 2007-08-18
forum: Programming Talk
---

### Post by punong_bisyonaryo on 2007-08-18
Good day!

I have some programming background and wanted to make "front ends" and other GUI apps for Linux, so I thought I'd download the GTK tutorial from GTK.org.

They make it sound so easy. The GTK tutorial should have a warning: Before you get into GTK programming, you need to be quite adept at installing things from source first.

I am currently installing a virtual machine where I can try again compiling GTK. The first time, I completely borked my Ubuntu, [boxes displaying instead of letters]("http://ubuntuforums.org/showthread.php?t=527234&page=2").

Can anyone point me to a good "GTK installation for dummies" tutorial/page/link/whatever? I want to learn GTK programming to gain more knowledge on Linux, but I can't install GTK and start programming until I know more knowledge on Linux.

Thanks in advance!

---

### Post by kostkon on 2007-08-18
> **punong_bisyonaryo said:**
> Good day!

I have some programming background and wanted to make "front ends" and other GUI apps for Linux, so I thought I'd download the GTK tutorial from GTK.org.

They make it sound so easy. The GTK tutorial should have a warning: Before you get into GTK programming, you need to be quite adept at installing things from source first.

I am currently installing a virtual machine where I can try again compiling GTK. The first time, I completely borked my Ubuntu, [boxes displaying instead of letters]("http://ubuntuforums.org/showthread.php?t=527234&page=2").

Can anyone point me to a good "GTK installation for dummies" tutorial/page/link/whatever? I want to learn GTK programming to gain more knowledge on Linux, but I can't install GTK and start programming until I know more knowledge on Linux.

Thanks in advance!

:confused::confused::confused:

Compile GTK?

You can find it in Synaptic. Also, you don't need to program the GUI, just install Glade, it's a user interface builder.

By installing Glade, Synaptic will install the necessary GTK libraries for you.

---

### Post by Compyx on 2007-08-18
There's no need to install Gtk+ from source, if I'm not mistaken, this command should install the library and its headers:
```

sudo apt-get install libgtk2.0-0 libgtk2.0-dev
```

It has been quite a while since I installed my gtk libs, so there might be something missing.

Anyway, once you've installed the correct libraries and their headers, you want to make use of a Makefile to avoid retyping those nasty `pkg-config ...` lines each time you compile and link. Perhaps something like this:

```

# Generic Makefile for new Gtk+ 2.x projects

CC = gcc
LD = gcc
VPATH =

CFLAGS = -Wall -Wextra -Wundef -Wshadow -Wpointer-arith -Wbad-function-cast \
         -Wcast-qual -Wcast-align -Wwrite-strings -Wmissing-prototypes \
         -Wmissing-declarations -Wredundant-decls -Wformat-nonliteral \
         -Wnested-externs -g -pedantic -ansi -O2 `pkg-config --cflags gtk+-2.0`

LDFLAGS = `pkg-config --libs gtk+-2.0`

PROG = 
OBJS = 

all : $(PROG)

%.o : %.c
        $(CC) $(CFLAGS) -c $< -o $@

$(PROG) : $(OBJS)
        $(LD) $(LDFLAGS) $(OBJS) -o $(PROG)

clean :
        $(RM) $(OBJS) $(PROG)

```

Fill in the line after PROG with the name of your binary and OBJS with the object files you want to create (including the '.o' suffix).

Hope this helps..

---

### Post by kostkon on 2007-08-18
For many reasons it is better to use Glade to create the GUI of an application. Especially, if you have many persons working on your project, it's much easier to maintain and change the GUI. It saves the file as an XML file and then with libglade you can load it very easily.

It does not mean that you don't need to study the GTK tutorial. If you read it it will help you to understand how it works. Also, you will need to learn about GLib and GTK data types, GtkObjects, etc, that there are chances you will use in your code.

---

### Post by punong_bisyonaryo on 2007-08-18
Wow! Thanks for all your tips! I didn't know it was this easy, especially in contrast to compiling those gtk libraries, with all their dependencies, and with no explanation which depends on what.

I'll be trying out the glade path first. Thanks compyx for the pkg-config tip, I'll keep that Makefile in my records.:)

---

### Post by kostkon on 2007-08-18
> **punong_bisyonaryo said:**
> Wow! Thanks for all your tips! I didn't know it was this easy, especially in contrast to compiling those gtk libraries, with all their dependencies, and with no explanation which depends on what.

I'll be trying out the glade path first. Thanks compyx for the pkg-config tip, I'll keep that Makefile in my records.:)

Just a tip: prefer to install the *glade3* package, which is for the new version of Glade.

---

### Post by punong_bisyonaryo on 2007-08-22
I tried out glade3, it looks great! Haven't had a time to do much though, just explore the interface. I've read somewhere about Anjuta being able to use Glade for a complete ground-up programming solution. Can Anjuta use Glade3 as well or are there other ideas that integrate with Glade3?

---

### Post by kostkon on 2007-08-24
> **punong_bisyonaryo said:**
> I tried out glade3, it looks great! Haven't had a time to do much though, just explore the interface. I've read somewhere about Anjuta being able to use Glade for a complete ground-up programming solution. Can Anjuta use Glade3 as well or are there other ideas that integrate with Glade3?

Yes, indeed, *Anjuta* is a very good *IDE* and has *Glade* integrated in it. I recommend you to install it. 

There is a new version, 2.20, which you can install easily. Go [here at the downloads section of the *Anjuta* site]("http://anjuta.sourceforge.net/downloads") and in the middle of the page you will find instructions how to add its repository to your software sources list. 

This way you will get the new version, because the *Ubuntu* official repositories offer an older version. Also, if you add the repository, you will get automatic updates every time there is a new version :)

If you have any question regarding installing *Anjuta*, don't hesitate to ask here.

---

### Post by shan0027 on 2007-08-31
Guys ,I am new to Linux :(
I am facing one problem while compiling one package..
When i give command  ./configure which is not in root directory..
it gives below error..I m not sure what it makes to cause this..
==============================================
Searching for canlib... 
Could not find Kvaser canlib header file. I looked for
/usr/include/canlib.h
but it does not seem to exist.

Searching for GTK... not found. 
I tried to execute pkg-config gtk+-2.0
and got this response:

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
===============================

I gave command  locate pkg-config
It gives following data
====================
/var/lib/dpkg/info/pkg-config.list
/var/lib/dpkg/info/pkg-config.md5sums
/usr/bin/pkg-config
/usr/lib/ruby/1.8/pkg-config.rb
/usr/share/doc/pkg-config
/usr/share/doc/pkg-config/AUTHORS
/usr/share/doc/pkg-config/NEWS.gz
/usr/share/doc/pkg-config/README
/usr/share/doc/pkg-config/changelog.Debian.gz
/usr/share/doc/pkg-config/changelog.gz
/usr/share/doc/pkg-config/copyright
/usr/share/man/man1/pkg-config.1.gz
==================================
Please help me to resolve this problem..I am very beginner to Linux package ..I am experience programmer in Windows :(

---

