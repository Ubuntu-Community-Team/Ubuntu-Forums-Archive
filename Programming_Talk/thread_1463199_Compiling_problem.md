---
title: "Compiling problem"
date: 2010-04-26
forum: Programming Talk
---

### Post by BiggoCharley on 2010-04-26
I was not able to find a binary for this program <ttf2cxf> which is a program to convert true type fonts to .cxf fonts (for use in qcad).  I was able to download a tarball of the source code. It contains a folder called ttf2cxf-0.0.0.1-src.

charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$ ls
main.cpp  Makefile  ttf2cxf

This folder has the three files named above.

I am not a programmer and am new to compiling from source --this is my first try.  I found some old postings on some other forums which, among other things, tell me to run the configure script with the command <./configure> 
I tried this with the following results:
charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$ ./configure
bash: ./configure: No such file or directory

So I tried again as root:
charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$ sudo ./configure
[sudo] password for charley: 
sudo: ./configure: command not found

I'm stuck --any help would be appreciated.

---

### Post by ronnielsen1 on 2010-04-26
I'm not in Ubuntu right now (Puppy) but make sure you have build-essential installed. I'm not sure what else you need but that's a start

---

### Post by dv3500ea on 2010-04-26
try:
```
make
make install
```

---

### Post by BiggoCharley on 2010-04-26
I do have build essential installed

I tried make:

charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$ make
g++ -o ttf2cxf -I/usr/include/freetype2 -lfreetype main.cpp
main.cpp:25:22: error: ft2build.h: No such file or directory
main.cpp:26:10: error: #include expects "FILENAME" or <FILENAME>
main.cpp:27:10: error: #include expects "FILENAME" or <FILENAME>
main.cpp:28:10: error: #include expects "FILENAME" or <FILENAME>
main.cpp:30: error: ‘FT_Library’ does not name a type
main.cpp:31: error: ‘FT_Face’ does not name a type
main.cpp:45: error: ‘FT_Vector’ was not declared in this scope
main.cpp:45: error: ‘to’ was not declared in this scope
main.cpp:45: error: expected primary-expression before ‘void’
main.cpp:45: error: initializer expression list treated as compound expression
main.cpp:46: error: ‘FT_Vector’ was not declared in this scope
main.cpp:46: error: ‘to’ was not declared in this scope
main.cpp:46: error: expected primary-expression before ‘void’
main.cpp:46: error: initializer expression list treated as compound expression
main.cpp:47: error: ‘FT_Vector’ was not declared in this scope
main.cpp:47: error: ‘control’ was not declared in this scope
main.cpp:47: error: ‘FT_Vector’ was not declared in this scope
main.cpp:47: error: ‘to’ was not declared in this scope
main.cpp:47: error: expected primary-expression before ‘void’
main.cpp:47: error: initializer expression list treated as compound expression
main.cpp:48: error: ‘FT_Vector’ was not declared in this scope
main.cpp:48: error: ‘control1’ was not declared in this scope
main.cpp:48: error: ‘FT_Vector’ was not declared in this scope
main.cpp:48: error: ‘control2’ was not declared in this scope
main.cpp:48: error: ‘FT_Vector’ was not declared in this scope
main.cpp:48: error: ‘to’ was not declared in this scope
main.cpp:48: error: expected primary-expression before ‘void’
main.cpp:48: error: initializer expression list treated as compound expression
main.cpp:51: error: ‘FT_Outline_Funcs’ does not name a type
main.cpp:62: error: redefinition of ‘int moveTo’
main.cpp:45: error: ‘int moveTo’ previously defined here
main.cpp:62: error: ‘FT_Vector’ was not declared in this scope
main.cpp:62: error: ‘to’ was not declared in this scope
main.cpp:62: error: expected primary-expression before ‘void’
main.cpp:70: error: redefinition of ‘int lineTo’
main.cpp:46: error: ‘int lineTo’ previously defined here
main.cpp:70: error: ‘FT_Vector’ was not declared in this scope
main.cpp:70: error: ‘to’ was not declared in this scope
main.cpp:70: error: expected primary-expression before ‘void’
make: *** [all] Error 1
charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$

don't know where to go from here.

---

### Post by nmccrina on 2010-04-26
Try installing libfreetype6-dev

I think ft2build.h is related to that package (from Google). I'm on Windows so I can't experiment with it.

---

### Post by BiggoCharley on 2010-04-26
I installed libreetype6-dev
and tried make again with the following results:

charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$ make
g++ -o ttf2cxf -I/usr/include/freetype2 -lfreetype main.cpp
main.cpp: In function ‘int conicTo(FT_Vector*, FT_Vector*, void*)’:
main.cpp:92: error: ‘pow’ was not declared in this scope
main.cpp: In function ‘FT_Error convertGlyph(FT_ULong)’:
main.cpp:152: warning: format ‘%04X’ expects type ‘unsigned int’, but argument 3 has type ‘FT_ULong’
make: *** [all] Error 1
charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$

---

### Post by Bachstelze on 2010-04-26
> **BiggoCharley said:**
> 
main.cpp:92: error: &#8216;pow&#8217; was not declared in this scope


The code must be linked with [font=monospace]-lm[/font] if is uses functions from the math library.

---

### Post by BiggoCharley on 2010-04-26
> **Bachstelze said:**
> The code must be linked with [font=monospace]-lm[/font] if is uses functions from the math library.

I tried this and please note my syntax ---is it correct??

charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$ make -lm
g++ -o ttf2cxf -I/usr/include/freetype2 -lfreetype main.cpp
main.cpp: In function ‘int conicTo(FT_Vector*, FT_Vector*, void*)’:
main.cpp:92: error: ‘pow’ was not declared in this scope
main.cpp: In function ‘FT_Error convertGlyph(FT_ULong)’:
main.cpp:152: warning: format ‘%04X’ expects type ‘unsigned int’, but argument 3 has type ‘FT_ULong’
make: *** [all] Error 1
charley@ubuntu1:/usr/local/src/ttf2cxf-0.0.0.1-src$

---

### Post by Bachstelze on 2010-04-26
> **BiggoCharley said:**
> I tried this and please note my syntax ---is it correct??

No, you will have to hack the Makefile. Apparently, it was not supposed to be used on Linux.

---

### Post by BiggoCharley on 2010-04-26
> **Bachstelze said:**
> No, you will have to hack the Makefile. Apparently, it was not supposed to be used on Linux.

This the contents of the Makefile:
all:
		g++ -o ttf2cxf -I/usr/include/freetype2 -lfreetype main.cpp

Now I'm more lost than before I started this thread (if that is possible)  It sure looks like it was meant for linux with the directory structure.

---

### Post by Bachstelze on 2010-04-26
> **BiggoCharley said:**
> 
all:
		g++ -o ttf2cxf -I/usr/include/freetype2 -lfreetype main.cpp

Change it to

```
all:
		g++ -o ttf2cxf -I/usr/include/freetype2 -lfreetype -lm main.cpp
```

---

