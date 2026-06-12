---
title: "install GTK"
date: 2007-04-07
forum: Programming Talk
---

### Post by NooBeee on 2007-04-07
what would i apitude(can this be used as a verb?) if i want to start tinkering around with gtk+ with C?

---

### Post by sdrubolo on 2007-04-07
sudo aptitude install gnome-core-devel build-essential

and then, here is a tutorial.
[www.gtk.org/tutorial](www.gtk.org/tutorial).

moreover, here there should be a post you may find interesting, [http://ubuntuforums.org/showthread.php?t=400956](http://ubuntuforums.org/showthread.php?t=400956)

---

### Post by NooBeee on 2007-04-08
i tried that but it didn't work--compiling a test helloworld file results in a unknown header error

gcc: pkg-config --cflags --libs gtk+-2.0: No such file or directory
gtk.c:1:21: error: gtk/gtk.h: No such file or directory
gtk.c: In function &#8216;main&#8217;:
gtk.c:6: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
gtk.c:6: error: (Each undeclared identifier is reported only once
gtk.c:6: error: for each function it appears in.)
gtk.c:6: error: &#8216;window&#8217; undeclared (first use in this function)
gtk.c:7: error: &#8216;label&#8217; undeclared (first use in this function)
gtk.c:11: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; undeclared (first use in this function)
gtk.c:17: error: &#8216;gtk_main_quit&#8217; undeclared (first use in this function)
gtk.c:18: error: &#8216;NULL&#8217; undeclared (first use in this function)
alvin@alvin-linuxbox:~$ gcc -o gtk gtk.c pkg-config --cflags --libs gtk+-2.0
gcc: pkg-config: No such file or directory
gcc: gtk+-2.0: No such file or directory
cc1: error: unrecognized command line option "-fcflags"
cc1: error: unrecognized command line option "-flibs"

---

### Post by sdrubolo on 2007-04-08
that's my same problem.
when you compile try this that should work
 gcc -o helloworld helloworld.c `pkg-config --cflags --libs gtk+-2.0`

---

### Post by NooBeee on 2007-04-09
lol....there was nothing wrong my gtk install.... i was tying a comma instead of the    `

---

### Post by chihuonbk on 2008-10-11
I am now facing the same problem,too. What was wrong? Or may be the command sudo aptitude install gnome-core-devel build-essential still not enough.

---

### Post by nvteighen on 2008-10-11
I fear that's some obsolete method... or one that is applied from some other distro... whatever, I never had heard of such gnome-core-devel package before.

Use:
```

sudo apt-get install libgtk2.0-dev

```

(and also install "build-essential" if you haven't).

But also, I highly recommend you to install GTK+'s docs and the very nice GNOME's Devhelp documentation browser (which you will be able to access from Applications->Programming):
```

sudo apt-get install libgtk2.0-doc devhelp

```

---

### Post by jespdj on 2008-10-11
You compile a GTK+ program like this:
```
gcc hello.c -o hello `pkg-config --cflags --libs gtk+-2.0`
```
Note the use of backticks ` instead of straight quotes '.

---

### Post by p0c4r1 on 2009-03-17
thanks nvteighen and jespdj... 

its work now... :)

so install gtk in ubuntu:

```

sudo apt get install gnome-core-devel build-essential install libgtk2.0-dev libgtk2.0-doc devhelp

```

---

