---
title: "Quick Scons Help: How To Pass Flags"
date: 2008-06-20
forum: Programming Talk
---

### Post by solarwind on 2008-06-20
Hey all, I have a simple SCONS build set up.

I only have one problem.

Currently, the build is working like this:

```
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...

g++ -o bin\wxGCCApp.o -c -mthreads -mwindows -march=i686 -DHAVE_W32API_H -D__WXMSW__ -DWXUSINGDLL -Wno-ctor-dtor-privacy -pipe -fmessage-length=0 -Ibi
n -Isrc -Ibin\src -Isrc\src -IC:\SourceCode\Libraries\wxWidgets2.8\include -IC:\SourceCode\Libraries\wxWidgets2.8\contrib\include -IC:\SourceCode\Libr
aries\wxWidgets2.8\lib\gcc_dll\mswud src\wxGCCApp.cpp

g++ -o bin\wxGCCMain.o -c -mthreads -mwindows -march=i686 -DHAVE_W32API_H -D__WXMSW__ -DWXUSINGDLL -Wno-ctor-dtor-privacy -pipe -fmessage-length=0 -Ib
in -Isrc -Ibin\src -Isrc\src -IC:\SourceCode\Libraries\wxWidgets2.8\include -IC:\SourceCode\Libraries\wxWidgets2.8\contrib\include -IC:\SourceCode\Lib
raries\wxWidgets2.8\lib\gcc_dll\mswud src\wxGCCMain.cpp

windres --include-dir bin --include-dir src --include-dir bin\src --include-dir src\src --include-dir C:\SourceCode\Libraries\wxWidgets2.8\include --i
nclude-dir C:\SourceCode\Libraries\wxWidgets2.8\contrib\include --include-dir C:\SourceCode\Libraries\wxWidgets2.8\lib\gcc_dll\mswud --include-dir src
 -i src\resource.rc -o bin\resource.o

g++ -o bin\main.exe bin\wxGCCApp.o bin\wxGCCMain.o bin\resource.o -Lbin -Lsrc -LC:\SourceCode\Libraries\wxWidgets2.8\lib\gcc_dll -lwxmsw28
scons: done building targets.
```

The first two compile commands pass a "-mwindows" option like I told it to in my SConscript file.

However, for my program to compile successfully, I need it to also pass the flag to the LAST g++ command as well, but no flag is being passed.

My SConscript is as follows:

```
# === Includes ===
includes = [".", "src", "C:\SourceCode\Libraries\wxWidgets2.8\include", "C:\SourceCode\Libraries\wxWidgets2.8\contrib\include", "C:\SourceCode\Libraries\wxWidgets2.8\lib\gcc_dll\mswud"]
libpath = [".", "C:\SourceCode\Libraries\wxWidgets2.8\lib\gcc_dll"]

# === Libraries ===
libraries = ["wxmsw28"]

# === Flags ===
#-mwindows removes console
flags = "-mthreads -mwindows -march=i686 -DHAVE_W32API_H -D__WXMSW__ -DWXUSINGDLL -Wno-ctor-dtor-privacy -pipe -fmessage-length=0"

# === Program ===
env = Environment(CXXFLAGS = flags, LIBPATH = libpath, LIBS = libraries, CPPPATH = includes, RC = "windres", tools = ["mingw"])
#env.Program(target = "main", source = ["main.cpp", env.RES("resource.rc")])
env.Program(target = "main", source = ["wxGCCApp.cpp", "wxGCCMain.cpp", env.RES("resource.rc")])
```

How do I get it to pass the "-mwindows" option to the last g++ command?

---

### Post by solarwind on 2008-06-21
Can anyone please help me?

---

