---
title: "Developing Win32 QT/MySQL Applications with Ubuntu, Wine, and MinGW"
date: 2009-02-14
forum: Outdated Tutorials &amp; Tips
---

### Post by nautilus on 2009-02-14
Hey Obento lovers!

I thought this might be fun for other OSS developers, or for folks who like to play with cross compiling.

I've found a somewhat kinky way of porting my simple QT4/MySQL program to Win32, and I'm sharing my method with you all.

There's quite a lot of work to do in the Terminal.  If you aren't familiar with the terminal, you could have some trouble with a few steps.  I'd suggest reading a primer on the Linux CLI system, unless you're feeling brave.

Here's what you'll need:

[LIST=1]
[*]Wine
[*]Unzip program
[*]MinGW
[*]MinGW Utils
[*]Windows version of MySQL (with development libraries)
[*]Windows version of CMake
[*]Windows source for QT
[/LIST]

A quick google should locate these for you, then run the installers using Wine as you would with any windows app.

If you don't need MySQL support in your program(s), just grab the binary version from Trolltech.  Keep in mind that it only comes with SQLite by default, though.

--

Ensure Wine works.  The easiest way to do that is to run the program 'regedit'.  If it runs, then it works!

We'll need to use regedit in a minute, but for now go back to your terminal and cd to the directory where your MinGW installer is, and run that:

```
$ wine MinGW-3.4.2.exe
```

.. simple enough.  Now the good ol' Win32 clickthrough.  Remember, the faster you click that Next button to the next screen, the more hardcore you are.

At this point, you may as well spew the MinGW utilities into their new home also:

```
$ cd ~/.wine/drive_c/MinGW
$ tar zvxf <path to mingw utils>/mingw-utils-0.3.tar.gz
```

Now we need that effervescent MySQL installed:
```

$ msiexec /i <path to mysql win32 package>/mysql-essential-5.1.31-win32.msi
```

After the first 'Next', you'll be able to customize the install.  Do.  Look for "_C Include Files / Lib Files_", and set it to "_Install Locally_".

Got it?  Good, let's get ready to build QT!

First, it's easier on QT if we copy the MySQL installation to a path without spaces in the name.  "Program Files/MySQL/MySQL Server 5.1/" and such won't work, so I did this:

```
$ cp -Rad ~/.wine/drive_c/Program\ Files/MySQL/MySQL\ Server\ 5.1/ ~/.wine/drive_c/mysql
```

The last bit we need to install is CMake, which we'll use to build our QT program:

```
$ wine <Path to downloaded installer>/cmake-2.6.2-win32-x86.exe
```

Click Next until it stops asking you difficult questions...

Perfect.  Now, we need to add our MinGW path to our system search path, and possibly CMake, so that the QT build can find our compiler and make program:
```

$ regedit
```

Now, navigate the tree to **HKEY_CURRENT_USER -> Environment** and look for a key named **PATH**.  If there isn't one, right click in the right-side pane and select _New->String Value_.

Once you have your **PATH** key, double click it to edit the value.  We need to add the MinGW executable path to this value.  Entries are delimited by semicolons.  My value looks like this:

> C:\Program Files\CMake 2.6\bin;C:\Program Files\MySQL\MySQL Server 5.1\lib\opt;c:\MinGW\bin

My MySQL installer added its path for me, but I tacked the MinGW path on myself.  It will depend where you chose to install yours, but I believe this is the default installation spot.  CMake may or may not install its own entry, so make sure it's in there somewhere.

For MySQL to be linkable for our MinGW compiler, we need to get a proper .a to link against and .dll to execute against from MySQL:

```
$ cd ~/.wine/drive_c/mysql/lib/opt
$ wine reimp -d libmysql.lib
$ wine dlltool -d libmysql.def -D libmysql.dll -k -l libmysql.a
```

If you saw a 'command not found' on reimp or dlltool, go back to the regedit step and ensure you have a correct path to your MinGW utils installation.

Time to build our custom Qt installation!  (If you downloaded the binary installer, just install Qt and skip this bit.)

```
$ cd ~/.wine/drive_c
$ unzip -x <path to qt source download>/qt-win-opensource-src-4.4.3.zip
$ cd qt-win-opensource-src-4.4.3
$ wine configure.exe -platform win32-g++ -I 'c:\mysql\include' -L 'c:\mysql\lib\opt' -lmysql
```

It will ask you to agree to the Nokia licence, and of course doesn't give you much choice aside from using GTK instead (snicker).

Once the configure finishes, with any luck, you'll be back to your bash prompt.  Now:
```

$ wine mingw32-make
```

... and away it goes.

This part takes about 5 hours to complete on my Phenom.  If you have a quad-core like me, I suggest installing MSYS and putting *sh.exe* (or *bash.exe*) in your Wine **PATH** registry variable, and executing like this:

```
$ wine mingw32-make -j4
```

You now have a proper QT build environment (possibly) with MySQL capabilities!

As you can see, the curveball of this whole process is the registry mangling required.  Once you have this mastered, the process is simple and quick, and can be easily modified to accommodate most any software buildable with mingw.

For Qt, it requires knowing about where the Qt installation is.  If your installation doesn't set this for you, you can either create a new String Value registry entry in your **Environment** section of the registry key (like with **PATH**) and set the value to your installed Qt path, or set it in your shell environment prior to configuring and building whatever software you're trying to create a Win32 build for:
```

$ QTDIR='C:\Program Files\Trolltech\Qt\4.4' wine configure.bat
$ QTDIR='C:\Program Files\Trolltech\Qt\4.4' wine mingw32-make
```

.. for example.

For CMake, it's important to specify the QTDIR and Makefile Generator when you launch.  CMake can't 'find' MinGW properly or detect the MinGW generator, at least on my system.  Cmake flags and variables will greatly influence your build, some programs won't build without them.  Here are a few that I use regularly, and what they mean:

QTDIR='c:\qt-win-opensource-src-4.4.3'
Where your Qt is compiled, or installed.

CMAKE_MAKE_PROGRAM=mingw32-make.exe
The make program, full path or just the executable name if the path to it is defined in your PATH

CMAKE_C_COMPILER=gcc.exe
CMAKE_CXX_COMPILER=g++.exe
Again, you can specify the full path as well, but it's tricky from a shell.

Once you have your paths sorted (if you need them at all), you would typically pass them on your cmake command line.  Here are some examples of my CMake project compilation jobs using Wine:

$ cd build
$ wine cmake.exe -G "MinGW Makefiles" ..

Or, if you use MSYS:

$ wine cmake.exe -G "MSYS Makefiles" ..

If you want to hold the reigns and specify everything:

$ QTDIR='c:\qt-win-opensource-src-4.4.3' wine cmake.exe -G "MSYS Makefiles" .. -DCMAKE_MAKE_PROGRAM=mingw32-make.exe -DCMAKE_C_COMPILER=gcc.exe -DCMAKE_CXX_COMPILER=g++.exe

Feedback is appreciated!

---

