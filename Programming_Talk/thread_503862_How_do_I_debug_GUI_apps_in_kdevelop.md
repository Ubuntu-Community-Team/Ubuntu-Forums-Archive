---
title: "How do I debug GUI apps in kdevelop?"
date: 2007-07-18
forum: Programming Talk
---

### Post by IFailAtLinux on 2007-07-18
I installed kdevelop manually from .deb packages I downloaded from places pointed by synaptic(I don't have access to net from linux so I had to do it like that). When I try to run debug of any qt application it just doesn't start. I use kubuntu-desktop.

For example, if I choose new project -> Simple KDE application with everything on default I should be able to see hello world window when running the program, while nothing happens. I'm adding some things that gather in outputs:

```

Messages:
cd '/home/l/Programming/Cpp/Simple' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/l/Programming/Cpp/Simple/debug' && cd '/home/l/Programming/Cpp/Simple/debug' && CXXFLAGS="-O0 -g3" "/home/l/Programming/Cpp/Simple/configure" --enable-debug=full && cd '/home/l/Programming/Cpp/Simple/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
installing -c
compiling yes (gcc)
compiling yes (g++)
compiling main.cpp (g++)
generating simple.moc (moc)
compiling simple.cpp (g++)
linking simple (g++)
*** Success ***

```

```

GDB:
/bin/sh -c libtool gdb /home/l/Programming/Cpp/Simple/debug/./src/simple --interpreter=mi2 -quiet(gdb) Process exited

```

Now the question is, what do I have to do to make my programs debug, it doesn't help me much that they compile. By the way, simple console programs I tried making worked nice.

---

### Post by mmmiiikkkeee on 2008-01-08
I had a similar error and it seemed that libtool was not installed.
try to run:
sudo apt-get install libtool 

it fixed it for me.
works for you???

---

### Post by polrus on 2008-07-08
You saved my life - libtool is what is lacking - it HAS to be added to package "require" dependency because it's very hard to troubleshoot even for experience guys

---

