---
title: "How to use Mingw32?"
date: 2006-01-09
forum: Programming Talk
---

### Post by Viro on 2006-01-09
Now, I know that Mingw32 is meant to be a cross compiler, allowing you to create win32 binaries on Linux. However, I have no idea how you use it? For example, how do I use it to build wxWidgets for Windows on Linux? I have no idea where to start with Mingw32 and the information on the net seems quite sparse.

---

### Post by toojays on 2006-01-09
You use mingw just like you would use a regular gcc. The whole GNU build toolchain is available, with the prefix i586-mingw32msvc-

Here's a fragment of a script file I use when going into a mingw cross-compiling environment. There's some extra bits you may need to build the wxWidgets libs, but I don't have that script on my home computer atm.
```
export CC=i586-mingw32msvc-gcc
export CXX=i586-mingw32msvc-g++
export LD=i586-mingw32msvc-ld
export AR=i586-mingw32msvc-ar
export AS=i586-mingw32msvc-as
export NM=i586-mingw32msvc-nm
export STRIP=i586-mingw32msvc-strip
export RANLIB=i586-mingw32msvc-ranlib
export DLLTOOL=i586-mingw32msvc-dlltool
export OBJDUMP=i586-mingw32msvc-objdump
export RC=i586-mingw32msvc-windres
```I build the wxWidgets libs and have it install to a seperate tree (~/mingw/bin, ~/mingw/lib, etc). Then your makefile can look at the mingw wx-config script or the Ubuntu one, depending on what system you want to compile for.

---

### Post by Viro on 2006-01-09
Thanks for the info. Shame the forums don't have a feature to mod up posts. I'd give you a +1 for that succinct answer.

---

### Post by kperkins on 2006-01-09
You canrate the thread though.  See the top.

---

### Post by kumoshk on 2009-09-05
So &#8230; What's the actual command you type to build with Mingw32 (particularly for make files: e.g. instead of typing make, what do I type)?

Looks like for a single file, I could type such as
i586-mingw32msvc-gcc
in place of gcc
or
i586-mingw32msvc-g++
in place of g++

I think I get how to compile single files and all, but how do I use make files with this?

Using Jaunty, I want to compile [LuaGnome]("http://luaforge.net/frs/download.php/3881/lua-gnome-2008-12-01.tar.gz") for Windows.

---

