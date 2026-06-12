---
title: "Glibc_2.15"
date: 2012-10-17
forum: Packaging and Compiling Programs
---

### Post by claudiuhks on 2012-10-17
Hey!

I'm trying to compile an extension with CPP and C files for a gaming server.
The problem is that the systems where the game servers are hosted doesn't support GLIBC_2.15.

How should I compile my extension to be able to work without GLIBC_2.15?
Or how should I include that in my extension to not require it from other machine?

I'm compiling it with the next Makefile:

[php]
COMPILER = g++-4.6
OBJECTS = indungi_zombie.o amxxmodule.o GeoIP.o GeoIPCity.o regionName.o timeZone.o
FILENAME = indungi_zombie_amxx_i386.so

$(FILENAME) : $(OBJECTS)
  $(COMPILER) -o $@ $(OBJECTS) libmysqlclient.a -shared -ldl -lm -s

%.o : %.cpp
  $(COMPILER) -O2 -ffast-math -fpermissive -IHeaders -IMySQL -o $@ -c $<
[/php]

I underline that I'm really new in Linux and I just use Linux to compile things for Linux hosted applications.

Thanks in advance!
Have a good day!

- Claudiu

---

### Post by MadCow108 on 2012-10-19
the simplest way is to just get a copy of the old libc and compile against that

otherwise this works:
[http://stackoverflow.com/a/8862631/1633169](http://stackoverflow.com/a/8862631/1633169)
[http://www.trevorpounds.com/blog/?p=103](http://www.trevorpounds.com/blog/?p=103)

to figure out the symbols needing the newer glibc use objdump -x
search for stuff like this:
memcpy@@GLIBC_2.14

---

