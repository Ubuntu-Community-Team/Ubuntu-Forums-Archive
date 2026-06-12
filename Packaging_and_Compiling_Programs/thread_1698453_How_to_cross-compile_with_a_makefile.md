---
title: "How to cross-compile with a makefile?"
date: 2011-03-02
forum: Packaging and Compiling Programs
---

### Post by Viper187 on 2011-03-02
Every example of calling i586-mingw32msvc-gcc I've seen uses a "something.c -o whatever.exe". I've got a makefile that I used with MinGW on windows successfully, but I'll be damned if I can figure out how to make it compile on Ubuntu. I don't want to switch back to Windows to work on this. It's an old school C/win32 API app that runs fine in wine when compiled. No MFC crap and definitely no .NET.

---

### Post by dodle on 2011-03-02
Is it a makefile that you created? Can you post it? I don't remember for sure, but I think you have to explicitly tell the compiler where the libraries are located:

```
i586-mingw32msvc-gcc example.c -I/usr/i586-mingw32msvc/include -L/usr/i586-mingw32msvc/lib -o example
```

---

### Post by Viper187 on 2011-03-02
> **dodle said:**
> Is it a makefile that you created? Can you post it? I don't remember for sure, but I think you have to explicitly tell the compiler where the libraries are located:

```
i586-mingw32msvc-gcc example.c -I/usr/i586-mingw32msvc/include -L/usr/i586-mingw32msvc/lib -o example
```

  Problem is I don't even know the right syntax to use a makefile this way.  

name@computer:/media/mydata/Private/gsctoolz2k/ArtemisSVN/trunk/ps2cc$ i586-mingw32msvc-gcc 
Makefile Makefile: file not recognized: File format not recognized   Edit:  

WTF? It won't preserve the line breaks in the code tags for the makefile. I'll [Pastebin]("http://pastebin.com/LfKqtxcp") it instead.

---

### Post by dodle on 2011-03-02
Okay, I think I understand. This is somebody else's source? So it probably comes with a configure script. So you configure it then compile?

If that is the case you want to set the "--host" and "--build" flags when running ./configure. I believe it should be something like this:

```
./configure --build=i686-linux --host=i586-mingw32msvc
```

I'm not sure if the "--build" flag is necessary, but that's how wxWidgets is cross compiled. Look here for some information: [http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux](http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux)

---

### Post by Viper187 on 2011-03-02
> **dodle said:**
> Okay, I think I understand. This is somebody else's source? So it probably comes with a configure script. So you configure it then compile?

If that is the case you want to set the &quot;--host&quot; and &quot;--build&quot; flags when running ./configure. I believe it should be something like this:

```
./configure --build=i686-linux --host=i586-mingw32msvc
```I'm not sure if the &quot;--build&quot; flag is necessary, but that's how wxWidgets is cross compiled. Look here for some information: [http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux](http://wiki.wxwidgets.org/Cross-Compiling_Under_Linux)

 No. There's no config script. I never needed one. I wrote it for windows and compiled it in MinGW for windows. It works in Wine though, and I want to update it without booting windows. I had actually done this with a similar app of mine back when I was on Ubuntu 8 or 9, but I'll be damned if I remember how it worked. I think I had some script that dropped me into a terminal configured so it worked when I just typed make.

---

### Post by SevenMachines on 2011-03-03
have you not tried setting CC in your makefile to mingw32 instead of gcc?
```
 CC=i586-mingw32msvc-gcc
```
To be honest, i'd rename/copy your makefile to Makefile.win32 or something and then alter it, calling it with 
```
make -f Makefile.win32
```
I tend towards thinking there'll be other tinkering, flags and stuff you'll want to use or need to change

---

### Post by Viper187 on 2011-03-03
> **SevenMachines said:**
> have you not tried setting CC in your makefile to mingw32 instead of gcc?
```
 CC=i586-mingw32msvc-gcc
```To be honest, i'd rename/copy your makefile to Makefile.win32 or something and then alter it, calling it with 
```
make -f Makefile.win32
```I tend towards thinking there'll be other tinkering, flags and stuff you'll want to use or need to change

 Funny somebody would post that while I was finally figuring it out. I looked at the makefile again and spotted that "cc=gcc.exe" and I'm like "hmmmmmmm" That's what worked. I dunno why I didn't think of it sooner. I remember that's what I had to do before too. I think 4 months of nothing but Halo Reach is frying my brain. lol  Thanks

---

