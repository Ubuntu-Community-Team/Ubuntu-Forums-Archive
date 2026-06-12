---
title: "Makefile that does everything?"
date: 2010-09-23
forum: Packaging and Compiling Programs
---

### Post by Trifud on 2010-09-23
Hi,
I have a little program that consists of two .c and one .h file:

my_math.c
funcs.c
funcs.h

I build a shared library from the funcs.* files manually and then I create a Makefile that installs the program my_math which uses the funcs library. Is it possible to write the Makefile so that the library is created automatically and then the program that uses it is also created and installed? I experimented a lot but I am new to the topic and nothing happened. I will appreciate any help.

---

### Post by Bachstelze on 2010-09-23
What does your Makefile look like so far?

---

### Post by ljrmorgan on 2010-09-23
> **Trifud said:**
> Hi,
I have a little program that consists of two .c and one .h file:

my_math.c
funcs.c
funcs.h

I build a shared library from the funcs.* files manually and then I create a Makefile that installs the program my_math which uses the funcs library. Is it possible to write the Makefile so that the library is created automatically and then the program that uses it is also created and installed? I experimented a lot but I am new to the topic and nothing happened. I will appreciate any help.

How about something like
```

objects = my_math.o funcs.o

my_prog : $(objects)
	cc -o my_prog $(objects)

$(objects) : funcs.h

.PHONY : clean
clean :
	rm my_prog $(objects)

```

I'm new to makefiles too, so I might be totally wrong. The idea is that to build "my_prog" you depend on the my_math.o and funcs.o, and to build each of these you need funcs.h. make automatically figures out that to get my_math.o it needs to compile my_math.c.

The objects array is just to make things easier and save typing. Take a look at the [GNU make tutorial]("http://www.gnu.org/software/make/manual/make.html") - it's pretty good, and although it's really really long you can get a pretty good idea of what's going on by just skimming the first couple of sections.

---

### Post by Trifud on 2010-09-24
Thanks! I fixed the problem. Specified both the creation of the library and the creation of the executable in the all target and it worked.

---

### Post by Simian Man on 2010-09-24
> **ljrmorgan said:**
> How about something like
```

objects = my_math.o funcs.o

my_prog : $(objects)
	cc -o my_prog $(objects)

$(objects) : funcs.h

.PHONY : clean
clean :
	rm my_prog $(objects)

```

That will rebuild your executable if you modify the header, but not if you modify only the sources.  Also there is no rule that compiles the object files in the first place.

I *really* recommend people to look at using scons if you want to compile from the command line.  There is pretty much no reason for anybody to write makefiles in this day and age.

---

