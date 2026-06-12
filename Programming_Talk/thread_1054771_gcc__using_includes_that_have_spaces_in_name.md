---
title: "gcc  using includes that have spaces in name"
date: 2009-01-30
forum: Programming Talk
---

### Post by anewguy on 2009-01-30
I have a cross-platform application that compiles and runs in both Windows and Linux.  I used gcc in both OS's to compile the application.  In Windows I had to do something wastefull - I had to copy a complete subdirectory from "Program Files" to the root drive because I seem to be unable to get gcc to recognize an include with spaces in the name, such as:

gcc ........-I c:/Program Files/LibUSB_Win32-0.1.10.1/include

I've tried single quotes - doesn't work, I've tried double quotes, still doesn't work.  I tried (my first attempt and I'm sure I messed it up) creating a specs file by -dumpspec then adding the -I's as per above but get syntax error in specs file.

Since the particular library and support package installs in Program Files as most other apps do, I really need to get at them.

Any ideas?

Thanks in advance!
Dave :)

---

### Post by Cypher on 2009-01-30
If you're trying to compile this in Windows, then use 
```

c:/progra~1

```
instead of Program Files and since the rest of your path has underscores or other markers, it should work..

---

### Post by mrbiggbrain on 2009-01-30
> **Cypher said:**
> If you're trying to compile this in Windows, then use 
```

c:/progra~1

```
instead of Program Files and since the rest of your path has underscores or other markers, it should work..

that is the dos completion way, and really isnt used outside dos apps. the better easier, and more accurate way is to simply use
"c:\file path\file path 2\file name" which all modern OS's accept. anything in quotes will be treated as a single argument, and any program will see it as a single instance of argv[] instead of multiple instances. the command prompt/shell simply passes the whole string.

note after rereading, maybe a problem with gcc? i know from a fact that command lines in bot linux and windows simply pass "this info here" to the command line, its built into the verry fabric of the OS and C++ to handle things this way, maybe when gcc does something ti dosnt parse spaces right... confuses me

---

### Post by anewguy on 2009-01-30
gcc for Windows (I'm using mingw and msys) does not parse the quotes apparently.

I tried the 8 character filename as recommended - had to make a couple of changes but it now works!  Apparently, gcc being of Linux descent?), case is important also.  Below is the gcc line that finally worked!

gcc -o c:/cvs/cvscl *.c -I c:/Progra~1/LibUSB-Win32-0.1.10.1/include -I c:/Progra~1/LibUSB-win32-0.1.10.1/lib/gcc -lusb


So that fixed half of my application - the part that lets it run from the command line.  Now have one last problem to work out for the GUI version (using GTK):

How do I get gcc via mingw and msys to accept a quoted string for the pkgconfig string?

I have:

set PKG_CONFIG_PATH=c:/gtk/lib/pkgconfig
gcc *.c -o cvsgtk -I c:/Progra~1/LibUSB-Win32-0.1.10.1/include -L c:/Progra~1/LibUSB-Win32-0.1.10.1/lib/gcc -lusb `pkgconfig --cflags --libs gtk+-2.0`

in a .bat file to compile the GTK version.  It always comes up with this error:

gcc: `pkgconfig: No such file or directory
gcc: gtk+-2': No such file or directory
cc1.exe: error: unrecognized command line option "-fcflags"
cc1.exe: error: unrecognized command line option "-flibs"

It's as if the gcc version for Windows (mingw/msys) is not interpretting the string in the tick marks.  I have tried replacing the tick marks with single quotes and with double quotes - always with the same result.

The only way I have been able to get this to work in Windows is to create a shell script with the above (set becomes EXPORT) and run it within an mingw command window.

If someone can help me on that so that it can just be run in a .bat file, it would be immensly helpful - imagine distributing the package now and telling them that build it "run this .bat file, then when it finishes run this shell script with mingw" to users who are expecting it to just install and compile on its own.

Thank you so very much for the help so far, and thanks in advance for any help you may be for the rest of my problem!

dave :)

---

### Post by anewguy on 2009-01-31
Okay, I think I understand what's going on, but not sure what to do about it.  Since this same line works in mingw/msys window, I have to assume the tick marks and the string within them are actually signals to cli (or in the case of mingw/msys, the shell) to "run pkg-config with the string and place the output here".  I don't believe the command line interpretter for DOS/Windows has a way of doing this.

So, perhaps I need to make a specs file for gcc, but I have no clue how to do that given my compilation string:

gcc a_start.c -o c:/cvs/cvsgtk -I c:/Progra~1/LibUSB-Win32-0.1.10.1/include  -L c:/Progra~1/LibUSB-Win32-0.1.10.1/lib/gcc -lusb `pkg-config --cflags --libs gtk+-2.0`

I have tried to read the documentation but I really just don't have a clue on how to do this - it assumes a whole lot of knowledge I don't have.

Any help would be greatly appreciated!

Thanks in advance!
Dave :)

---

### Post by WW on 2009-01-31
There may be better solutions, but a simple one is to run the pkg-config command by itself:
```

pkg-config --cflags --libs gtk+-2.0

```
and in your gcc command, replace `pkg-config --cflags --libs gtk+-2.0` with whatever it prints.  In other words, do by hand what the back-ticks are supposed to do automatically.

---

### Post by anewguy on 2009-01-31
Well, I tried including the list in the gcc command, but for some reason it didn't work.  I then successfully did the following:

- leaving my original shell scrip as is (includes the pkg-conf string in tick marks) since mingw/msys can run it as it always has

- changed my Windows batch file to execute mingw and the sh and passed in the shell script name.

Now you just run single batch file and everything is done.

Thanks for the replies!!

Dave :)

---

