---
title: "[SOLVED] Including Libraries and Dependencies"
date: 2008-03-14
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-03-14
Hi everyone,

This is my first time using nonstandard libraries, so excuse the question for being stupid.

"main.cpp" contains```
#include <libxml++>
```
"Makefile" contains```

userGrab.ose:  main.cpp
	g++ -o userGrab.ose main.cpp
```

If I comment out the libxml++ includes, it compiles my "hello world".  After digging into the [manual]("http://libxmlplusplus.sourceforge.net/docs/manual/html/index.html#id2472502"), I found that it said to run ```
pkg-config libxml++-2.6 --cflags --libs
```
which output
```

-I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  

```

But after attaching it to my g++ command in the Makefile ```

userGrab.ose:  main.cpp
	g++ -o userGrab.ose main.cpp -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  

```

I get an error of ```

userGrab.ose:  main.cpp
main.cpp:2:20: error: libxml++: No such file or directory
make: *** [userGrab.ose] Error 1

```

How do I fix this?

Thanks

---

### Post by WW on 2008-03-14
Take another looks at the [docs](http://libxmlplusplus.sourceforge.net/docs/manual/html/ar01s02.html).  Your include statement should be
```

#include <libxml++/libxml++.h>

```

By the way, instead of copying the output of the pkg-config command into your Makefile, you can set it up so that the Makefile runs pkg-config on its own.
For example, something like this:
```

userGrab.ose:  main.cpp
	g++ main.cpp $(pkg-config --libs --cflags libxml++-2.6) -o userGrab.ose

```

---

### Post by 71fnRVVm on 2008-03-14
Great.  Except that when I do that (run pkg-config in the Makefile and change the #include), it returns:
```
main.cpp:2:31: error: libxml++/libxml++.h: No such file or directory
make: *** [userGrab.ose] Error 1

```

Thanks

---

### Post by WW on 2008-03-14
That's strange.  If you installed the package **libxml++2.6-dev** (and I assume that you did, since the pkg-config command for the library apparently works), the headers should be in /usr/include/libxml++-2.6/libxml++, and the pkg-config command is giving the option -I/usr/include/libxml++-2.6, so I don't see why the compiler doesn't find the header.  Can you check that the directory /usr/include/libxml++-2.6/libxml++ exists, and contains the files shown [here](http://packages.ubuntu.com/gutsy/amd64/libxml++2.6-dev/filelist)?

---

### Post by 71fnRVVm on 2008-03-14
I *did* install dev, and I have all the files.  I pulled an ls -Rl and they were all there.

...am I just doing something wrong?

Thanks again

---

### Post by WW on 2008-03-16
Sorry, I don't see any obvious source of the problem.  I installed the library, and compiled a trivial example, as you can see here:
> 
$ pkg-config --cflags libxml++-2.6
-I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
$ pkg-config --libs libxml++-2.6
-lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0 
$ ls
xmltest.cpp
$ cat xmltest.cpp
#include <libxml++/libxml++.h>

int main(int argc, char *argv[])
{
return(0);
}

$ g++ -c xmltest.cpp $(pkg-config --cflags libxml++-2.6)  # Compile only, don't link
$ ls
xmltest.cpp  xmltest.o
$

Can you successfully compile a trivial file like the one above?

---

### Post by 71fnRVVm on 2008-03-16
Interesting.

I can compile the code, more or less the same as yours, if I do it by command line.  But running the exact same command in my Makefile still returns the same error.

Exact same command.

Makefile```

dataCrawl.ose:  main.cpp
	g++ -c main.cpp $(pkg-config --cflags libxml++-2.6) -o dataCrawl.ose
```

Commandline ```

g++ -c main.cpp $(pkg-config --cflags libxml++-2.6) -o dataCrawl.ose

```

---

### Post by WW on 2008-03-16
OK, so it's a question of how much "quoting" or "escaping" that is needed in the Makefile.  This worked for me:

Makefile:
```

xmltest.o: xmltest.cpp
        g++ -c xmltest.cpp $$(pkg-config --cflags libxml++-2.6)

```
(Note the extra $.)

With this file, it works:
> 
$ ls
Makefile  xmltest.cpp
$ make
g++ -c xmltest.cpp $(pkg-config --cflags libxml++-2.6)
$ ls
Makefile  xmltest.cpp  xmltest.o
$ 


---

### Post by 71fnRVVm on 2008-03-16
Wow.  That was really it?

Apparently, because it now compiles.

Thanks for all the help, especially for such a "noob" problem!

---

