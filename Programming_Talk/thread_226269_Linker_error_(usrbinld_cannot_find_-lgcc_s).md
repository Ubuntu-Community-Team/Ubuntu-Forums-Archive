---
title: "Linker error: (/usr/bin/ld: cannot find -lgcc_s)"
date: 2006-07-31
forum: Programming Talk
---

### Post by mvdw on 2006-07-31
[list]Hi All:

I have a problem with ld/collect2/g++. The basic problem is a linker error of
```

/usr/lib/libgmodule.a(gmodule.o): In function `g_module_open': warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/bin/ld: cannot find -lgcc_s

```

in a project I've inherited.

The project is built in a rather strange way. It turns out that the previous developers had little to no knowledge of the Linux Way, and had managed to make a mish-mash hack job of the build process. Anwyay, to cut a long story short, the project consists of a number of components, which are all mashed together in a single top-level directory.

The components are fairly straightforward in the way they are written, except for the UI component which was originally a glade project, turned into a c++ project, which meant all the hard work glade et al did for the developer was lost since the generated Makefile was hand-edited. This is all a GTK 1.2 project, originally developed on a fedora core 1 box, now ported to try to use something more recent.

All of the components (including the UI component) are c++ source built as libraries, that is, they are compiled into .o files then run through 'ar', dumped into a common directory (used to be /usr/local/lib, which meant the user had to be root to even make the executable. I've fixed all the Makefiles so they all are much simpler than they used to be, however I still can't get a successful build.

The basic build process is as follows:

(Each sub-component):
```

g++ -c foo,cc -o foo.o

```
The above is done however many is times required, once for each .cc file There are of course some cflags; these are simply the -I options to search the relevent include directories, plus -Wall for all warnings (minus whatever gcc decides doesn't belong to the set of "all").

Then the .o files are strung together into an archive, and copied into a common "libs" directory off the main build directory:
```

ar rcs $(TARGET) $(OBJECTS)
install -m 644 $(TARGET) $(LIBDIR)

```

The components all build fine; the problem is in what comes next:

There is a top-level source file which is supposed to be a common link point for the executable. It provides a main() function, and some glue to get it all started, relying on the libs created earlier to provide the functionality. It's built like this:
```

LDFLAGS = -Wl,-Ur -Llibs $(patsubst %,-l%,$(LIBS))
g++ -c base.cc $(EXTRACFLAGS) $(GNORBA_CFLAGS) -o $(BASE).o
g++ $(BASE).o $(LDFLAGS) $(LIBDIRS)  -o $(BASE)

```

A couple of notable points:
[list]
[*]The linker is called via the g++ wrapper - this is on recommendation.
[*]The Makefiles are custom ones I've re-written. I haven't changed any of the cflags etc that I can tell
[*]All the libraries linked are static - even the built-in ones. I can't see where I've told either gcc or ld to link statically (this is the root cause of the failure to find gcc_s, I believe.
[*]I've tried compiling using both g++ 4.03 and g++ 3.4.3 with the same error on both occasions.
[*]I've tried various incarnations of -rdynamic, -Bdynamic, -static-libgcc, -dynamic-libgcc etc with no luck.
[/list]

I'd really appreciate any help on this one - it's had me stumped for quite a few days now.

Cheers,
mvdw
[/list]

---

### Post by moma on 2006-07-31
Do you have libgcc_s.so library in your system?  Should your code linkt to it?
-lgcc_s  -L/usr/lib/gcc/xxxxxxx/

BTW:  You may also send your question to these newsgroups
[news://comp.os.linux.development](news://comp.os.linux.development)

[news://comp.os.linux.development.apps](news://comp.os.linux.development.apps)

---

### Post by mvdw on 2006-07-31
> Do you have libgcc_s.so library in your system? Should your code linkt to it?
-lgcc_s -L/usr/lib/gcc/xxxxxxx/

Yes, I do have libgcc_s.so - the problem is that the linker can't find libgcc_s.a (due to it not being there). For some reason it's trying to statically link the application, and I can't for the life of me work out why. I'd much rather it being dynamically linked; I had thought that ld would prefer the dynamic versions unless specifically told to but in this instance it doesn't seem that is the case.

Thanks for the tips regarding the newsgroups, although I haven't got direct access due to my ISP being lax in the services they offer (these are the prices you pay for going with the cheapest offer). Google groups may well be my friend, but I haven't yet signed up.

---

### Post by larytet on 2010-05-18
gcc -Wl -shared -o ....

---

### Post by larytet on 2010-05-19
or

<code>
ld -r  -o merged-object-file-name  file1.o file2.o ...
</code>

---

