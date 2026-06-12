---
title: "problem with long names in library"
date: 2012-07-10
forum: Programming Talk
---

### Post by whatsup1 on 2012-07-10
hey all.
i created a library
that has functions with longnames.
now if i have 2 functions like this:
MyLongNameFunction1
MyLongNameFunction2

and i create a program that call one of them

in the linking process,
i get an error,
that the function is not found.

i'm using g++ (on windows),
 and the switches command line for creating the libray are:
Set GPPFLAGS=-c -pipe -mconsole -mwin32 -w -s -O

is there a switch to allow longnames, or it's a bug or something ?

thanks in advanced

---

### Post by Barrucadu on 2012-07-11
What command are you using to link it?

---

### Post by whatsup1 on 2012-07-11
set DEFCFLAGS=-s -pipe -m32 -D_WIN32_WINNT=0x0501

set DEFLFLAGS=-lwControls -lcb_RT -lcb_ZLib -lcb_Lzma -lcb_LodePNG -lcb_RT -lkernel32 -luser32 -lwinmm -lws2_32 -lcomdlg32 -ladvapi32 -lgdi32 -lcomctl32 -limagehlp -lwinspool -lshell32 -lodbc32 -lodbccp32 -lversion -lole32 -lolepro32 -loleaut32 -luuid -lopengl32 -lmoldname -lwininet -lvfw32 -lmsimg32 -lpsapi

g++ -Wno-write-strings -w -mwindows -mwin32 -masm=intel -omyFileName.exe %DEFCFLAGS% %CFLAGS% myFileName.c myFileName.rc %DEFLFLAGS% %LFLAGS%

this is the batch file
the compiling and linking, all done in one command by g++

---

### Post by whatsup1 on 2012-07-11
when i create the library i'm using this switch -rf
for ar.exe
'f' means, truncate file names.
i tried to build the library without this switch,
and everything seems to work fine.

thanks for your try.

---

