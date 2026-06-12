---
title: "SFML Linking Issue [C++]"
date: 2012-05-17
forum: Programming Talk
---

### Post by Carpentr on 2012-05-17
Hey everyone,

I have been following the tutorial ([http://tinyurl.com/cekfjeo](http://tinyurl.com/cekfjeo)) that allows me to get a basic SFML Application up and running. 

I've run this and get the following error:
```

$ g++ -o sfml_test  sfml_test.o -lsfml-system
$ ./sfml_test
./sfml_test: error while loading shared libraries: libsfml-system.so.1.6: cannot open shared object file: No such file or directory


```

I'm pretty new to C++ development on Linux (was taught on windows in college), so I was wondering if anyone had an idea on how to fix this. I am guessing that the executable cannot find the library. Is there a way for me to point the compiler toward it?

---

### Post by steeldriver on 2012-05-17
yes iirc you should be able to use -L /path/to/lib on the command line e.g. if you unpacked the SFML archive in /usr/local it would be

```
$ g++ -o sfml_test  sfml_test.o -L /usr/local/SFML-1.6/lib -lsfml-system
```alternatively you could symlink the libs to somewhere on the standard library search path

---

### Post by Carpentr on 2012-05-17
> **steeldriver said:**
> yes iirc you should be able to use -L /path/to/lib on the command line e.g. if you unpacked the SFML archive in /usr/local it would be

```
$ g++ -o sfml_test  sfml_test.o -L /usr/local/SFML-1.6/lib -lsfml-system
```alternatively you could symlink the libs to somewhere on the standard library search path

I have tried the edited command and I am still getting the same error. I have restarted the entire project, from creation of the source file to compilation, and even then I still get the error.

I have the sfml folder in my /home/me directory. 

Thank you for your help. If you have any other suggestions it would be appreciated. Thanks again.

Edit: Also, I am running Red Hat Enterprise Linux Desktop Edition, V6, if that makes a difference.

Edit 2: After looking at /usr/local/ because of the advice of steeldriver, I spotted the library files in the /usr/local/lib folder. I then added the path of /usr/local/lib to the /etc/ld.so.conf and /etc/ld.so.conf.d/* files using emacs. I then ran ldconfig -v. (citation: [http://stackoverflow.com/questions/3606166/problems-linking-to-a-library-with-gcc](http://stackoverflow.com/questions/3606166/problems-linking-to-a-library-with-gcc))

I hope this thread helps anyone who runs into a similiar problem! 

Thanks, steeldriver, for the help!

Ubuntu:
```
g++ -o  test  test.o -L /usr/local/lib  -lsfml-system
```
Redhat Enterprise Linux Desktop v6 [utilizing Development Toolset 1.0 Beta]:
```
scl enable devtoolset-1.0 'g++ -o  test  test.o -L /usr/local/lib  -lsfml-system'

```

---

### Post by steeldriver on 2012-05-17
oops sorry about that - I kind of missed that you were linking to a shared lib - that means ld needs to be able to find it at runtime not just when you build

fwiw there's an old school way to tell ld about non-standard runtime library locations (without making system-wide conf changes) via an LD_LIBRARY_PATH environment variable - that may be deprecated now, I am out of touch with these things but you might want to check that out too

anyhow glad you got it working

---

