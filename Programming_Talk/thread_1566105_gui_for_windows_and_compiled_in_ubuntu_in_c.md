---
title: "gui for windows and compiled in ubuntu in c"
date: 2010-09-01
forum: Programming Talk
---

### Post by n3cr0 on 2010-09-01
soooo i been working with gtk gui.,. but i wanted to build a program that i made for ubuntu 10.04 to work on windows xp soo i started searching for a gui for windows or win32 rather and my searches are coming up short .,. if someone could point me in the right direction to compile a windows program that would support a graphical user interface in ubuntu that would help me out a ton thank you in advance .,.

---

### Post by n3cr0 on 2010-09-01
forgot to mention that im working with c language

---

### Post by lisati on 2010-09-01
I haven't done anything quite like this myself, but I suspect that [GTK+]("http://www.gtk.org/") *might* be ***part*** of the answer for you. If I understand their website correctly, it is cross-platform, meaning that you can use it develop software that is portable across Linux & Windows.

---

### Post by n3cr0 on 2010-09-02
turns out your right i came across this little snipet to compile it but it still doesnt seem to work 

gcc \
-o NameOfExecutable \
`pkg-config --cflags gtk+-win32-2.0` \
-mno-cygwin -mms-bitfields \
-DPACKAGE_DATA_DIR="\"/mingw/share\"" \
-DPACKAGE="\"GladeProjectName\"" \
*.c \
`pkg-config --libs gtk+-win32-2.0`

i just get this error :s

cc1: error: unrecognized command line option "-mno-cygwin"

is there something im over looking????

---

### Post by worksofcraft on 2010-09-02
Doesn't Glade work on Windows?

---

### Post by n3cr0 on 2010-09-02
okay yeah glade does work on i installed it via spm and then i found something wrong with my compiling code i was missing a \ before -mno-cygwin hence the error i got .,. now on the up note this method seems to work on the bad note i got alot of errors due to my code but thats hardly the compilers fault lol .,. yup almost an error on every line of the code :S
oh and btw thank you kindly for your fast responses

---

### Post by spupy on 2010-09-02
> **n3cr0 said:**
> turns out your right i came across this little snipet to compile it but it still doesnt seem to work 

gcc \
-o NameOfExecutable \
`pkg-config --cflags gtk+-win32-2.0` \
-mno-cygwin -mms-bitfields \
-DPACKAGE_DATA_DIR="\"/mingw/share\"" \
-DPACKAGE="\"GladeProjectName\"" \
*.c \
`pkg-config --libs gtk+-win32-2.0`

i just get this error :s

cc1: error: unrecognized command line option "-mno-cygwin"

is there something im over looking????

To cross-compile for Windows you need to:
1. Compile it on Windows
 OR
2. Install Cygwin/Mingw **in Linux** and compile from it.
*EDIT: AFAIK.*

---

### Post by James78 on 2010-09-03
> **spupy said:**
> To cross-compile for Windows you need to:
1. Compile it on Windows
 OR
2. Install Cygwin/Mingw **in Linux** and compile from it.
*EDIT: AFAIK.*
+1 for MingW. I ported one of my Linux apps to be able to compile for Windows, and work on it, and I finally finished after 3 or 4 days of hours and hours of work. It's pretty sweet.

Something to note about MingW though, is that you can compile to 32-bit, but I don't know if you can completely compile to 64-bit. If you install mingw32-gcc (or named something similar to that), it comes with the MingW 64-bit compilers, but then you encounter an error where it says it can't link the binary with libgcc; I took a look around and it doesn't even exist. Sorta frustrating. :( But other than that you're good to go.

---

### Post by n3cr0 on 2010-09-03
on that note i think i should mark this thread as solved thank you much for your direction :D

---

