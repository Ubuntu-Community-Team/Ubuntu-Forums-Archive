---
title: "gcc: autodetect my library, please?"
date: 2011-02-01
forum: Packaging and Compiling Programs
---

### Post by Fatman_UK on 2011-02-01
Hi all,

I've written a library, libReu2.a. It works completely except that I have to specify the full path each time I use it, even if it's in /usr/lib. The linker just doesn't see it. If I have CMake do:

```

/usr/bin/c++ -std=c++0x -Wno-long-long -Wno-comment -Wwrite-strings -pedantic-errors -pedantic -Wall -W -Weffc++ -Wmain -Wextra -DBOOST_THREAD_USE_LIB=1 -g -gdwarf-2   CMakeFiles/mailer.dir/src/Mailer.cc.o  -o ../bin/mailer-d -rdynamic -l/usr/lib/libReu2.a -Wl,-Bstatic -lboost_filesystem-mt -lboost_system-mt -lboost_thread-mt -lboost_regex-mt -lboost_date_time-mt -Wl,-Bdynamic -lpthread 

```

all is fine, but if I try:

```

/usr/bin/c++ -std=c++0x -Wno-long-long -Wno-comment -Wwrite-strings -pedantic-errors -pedantic -Wall -W -Weffc++ -Wmain -Wextra -DBOOST_THREAD_USE_LIB=1 -g -gdwarf-2   CMakeFiles/mailer.dir/src/Mailer.cc.o  -o ../bin/mailer-d -rdynamic -lReu2 -Wl,-Bstatic -lboost_filesystem-mt -lboost_system-mt -lboost_thread-mt -lboost_regex-mt -lboost_date_time-mt -Wl,-Bdynamic -lpthread 

```

(the same except for the -l option in the middle) I get "/usr/bin/ld: cannot find -lReu2".

CMake is linking my library like this:

```

/usr/bin/ar cr ../bin/libReu2.a  CMakeFiles/Reu2.dir/Reu2/src/Socket.cc.o CMakeFiles/Reu2.dir/Reu2/src/Serialiser.cc.o CMakeFiles/Reu2.dir/Reu2/src/Log.cc.o CMakeFiles/Reu2.dir/Reu2/src/Endian.cc.o CMakeFiles/Reu2.dir/Reu2/src/CommonFunctions.cc.o CMakeFiles/Reu2.dir/Reu2/src/Buffer.cc.o
/usr/bin/ranlib ../bin/libReu2.a

```

which I think is correct, and I have moved it into /usr/lib:

```

mv ../bin/libReu2.a /usr/lib/

```

I'm sure I've missed a step somewhere, but what is it?

Thanks,
Adam J Richardson

---

### Post by gmargo on 2011-02-01
What happens if you put the "-lReu2" after the "-Bstatic"?  i.e.
```

-Wl,-Bstatic -lReu2

```instead of 
```

-lReu2 -Wl,-Bstatic

```I'm guessing this because of this highlighted section from the **ld(1)** man page:

> 
       -Bstatic
       -dn
       -non_shared
       -static

           Do not link against shared libraries.  This is only meaningful on
           platforms for which shared libraries are supported.  The different
           variants of this option are for compatibility with various systems.
           You may use this option multiple times on the command line: [COLOR=Red]it
           affects library searching for -l options which follow it.[/COLOR]  This
           option also implies --unresolved-symbols=report-all.  This option
           can be used with -shared.  Doing so means that a shared library is
           being created but that all of the library's external references
           must be resolved by pulling in entries from static libraries.


---

