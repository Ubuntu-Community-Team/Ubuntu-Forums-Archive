---
title: "Compiling with mingw32"
date: 2010-09-06
forum: Packaging and Compiling Programs
---

### Post by dades88 on 2010-09-06
I want compile a c program from Ubuntu to Windows. So I use mingw32. 
But there are mistakes:
```
 i586-mingw32msvc-gcc ricevi_comandi.c -o ricevi.exe
/tmp/ccgbfCSk.o:ricevi_comandi.c:(.text+0x10): undefined reference to `_socket@12'
/tmp/ccgbfCSk.o:ricevi_comandi.c:(.text+0x34): undefined reference to `_htons@4'
/tmp/ccgbfCSk.o:ricevi_comandi.c:(.text+0x4d): undefined reference to `_bind@12'
/tmp/ccgbfCSk.o:ricevi_comandi.c:(.text+0x5e): undefined reference to `_listen@8'
/tmp/ccgbfCSk.o:ricevi_comandi.c:(.text+0x9f): undefined reference to `_accept@12'
collect2: ld returned 1 exit status

```How can this be done???

P.S. My program started with this code:
```
#ifdef linux
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#endif

#ifdef _WIN32
#include <winsock2.h>
#endif

```

---

### Post by stevebu56 on 2010-09-07
Is this the cmd line you're using to compile? 
```
i586-mingw32msvc-gcc ricevi_comandi.c -o ricevi.exe
```

The linker can't find the code for those functions (_htons, _bind, etc).  They are in the ws2_32 library.  You will need to link to the library like so. 
```
i586-mingw32msvc-gcc ricevi_comandi.c -o ricevi.exe -lws2_32
```

Here's some links that mention this as well. 
[http://stackoverflow.com/questions/2033608/mingw-linker-error-winsock]("http://stackoverflow.com/questions/2033608/mingw-linker-error-winsock")
[http://ubuntuforums.org/showthread.php?t=441397]("http://ubuntuforums.org/showthread.php?t=441397")

---

