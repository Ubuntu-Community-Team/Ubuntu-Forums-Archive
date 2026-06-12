---
title: "gcc  didn't generate any .o or .exe"
date: 2010-11-26
forum: Programming Talk
---

### Post by dkramer on 2010-11-26
Brand new newbie. Running ubuntu 10.4 from flash drive in live mode (not sure what that is)
Loaded sudo....get_essentials
Used editor to create "hello world" test
stored in both a new docs folder and ubuntu root
from terminal prompt line ran gcc hello_world.c
terminal prompt line comes back no errors I guess
can't find the object file or the .exe from the gcc compile
help
Dennis

---

### Post by KIAaze on 2010-11-26
> **dkramer said:**
> Brand new newbie. Running ubuntu 10.4 from flash drive in live mode (not sure what that is)

Live mode means the OS runs without being installed on the local hard-disk.
So if you reboot your PC without the USB-stick or live-CD, it will boot as usual (unless you made changes to the hard-disk while using the live-mode, like partitioning or installing Ubuntu for example).
> **dkramer said:**
> 
Loaded sudo....get_essentials

I assume you mean:
```
sudo apt-get install build-essential
```

> 
Used editor to create "hello world" test
stored in both a new docs folder and ubuntu root

"ubuntu root" = "/"(usually called "root") or "/home/$USER" (usually called "home directory", equivalent of "My documents" under Windows)?

Compiling things directly in the root directory is usually a bad idea.
Creating a new folder for program development is a good idea however.

> 
from terminal prompt line ran gcc hello_world.c
terminal prompt line comes back no errors I guess
can't find the object file or the .exe from the gcc compile
help
Dennis

With the command you ran, it should have created an executable "a.out" by default.

I think you should read this: [http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html)

Here's a quick rundown:
```

$  gcc hello_world.c

```
creates "a.out" from hello_world.c

```

$  gcc -c hello_world.c

```
creates "hello_world.o" from hello_world.c

```

$  gcc hello_world.o -o foo.bar

```
creates "foo.bar" from hello_world.o

```

$  gcc hello_world.c -o bar.foo

```
creates "bar.foo" from hello_world.c

g++ (C++ code) works almost the same way as gcc (C code).

_Additional notes:_
Executables rarely carry the ".exe" extension on GNU/Linux systems.
Compiled programs, i.e. "executable binaries", usually either have no extension at all or the ".bin" extension.
In the GNU/Linux world, "executable" just means that the file can be run as a command with "./FILE".
An executable is not necessarily a compiled program (binary). It can also just be a script (executable text file).

---

### Post by dkramer on 2010-11-26
thanks so much KIAaze
I guess it was working - didn't know what the a.out was
 
I've tried to wade through the compile options some more - is there
an example of a way to tell the compiler where the source directory is
if its not in /
 
Dennis

---

### Post by KIAaze on 2010-11-27
Mmh, as far as I know, you don't specify a "source directory" with gcc.
But you can specify include dirs (-I flag) and library dirs (-L and -l flag):
```
gcc -I/path/to/includedir -L/path/to/libs -lfoo hello1.c hello2.c -o hello
```

This will compile the program "hello" from the files "hello1.c" and  "hello2.c" using any headers in "/path/to/includedir" and linking to the library "libfoo.so" in "/path/to/libs".

I recommend looking at Makefiles (to use "make" to compile) and IDEs (KDevelop, Anjuta, Eclipse, etc) for projects using a lot of source files.

You should be able to find a lot of useful links in the stickies here: [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")
(ah, the thread has already been moved here :) )

---

### Post by smartbei on 2010-11-27
Sure you can specify a source directory - the filename for the source file can be the path to it:
```

gcc /home/username/Desktop/main.c -o test

```

---

### Post by KIAaze on 2010-11-27
Well, yeah, but if you have multiple source files, that makes it quite long. ^^
However, yes, it is specifying a source directory in a certain way... :)

---

