---
title: "unable to compile mplayer"
date: 2009-01-21
forum: Packaging and Compiling Programs
---

### Post by TheOne...more on 2009-01-21
greetings

I've had problems with gnome-mplayer since i began using my distro, and lately i decided to solve this problem and compile new one on my own. I red the docs that come with the source "mplayer-checkout-snapshot" and also the ones online. I installed the necessary libraries and the necessary dev packages.

Now while I was trying to compile i got this error

```
Error: The GUI requires libavcodec with PNG support (needs zlib).
```

All the dev packages are installed, and i don't know what is the problem.

This is the configure.log file

```
configuration: --prefix=/usr --enable-gui --enable-joystick --enable-radio-capture --disable-dvdread-internal --disable-cddb --disable-libdvdcss-internal --enable-menu --enable-rpath --disable-liba52-internal --disable-libmpeg2 --enable-xvmc --enable-runtime-cpudetection --enable-dynamic-plugins

============ Checking for cc version ============
Result is: 4.1.3 
##########################################

============ Checking for host cc ============
Result is: cc 
##########################################

============ Checking for cross compilation ============

int main(void) { return 0; }

cc  -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: no 
##########################################

============ Checking for GCC & CPU optimization abilities ============

int main(void) { return 0; }

cc  -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -mtune=generic



int main(void) { return 0; }

cc  -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -mtune=generic



int main(void) { return 0; }

cc  -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -march=x86-64 -mtune=generic


Result is:  
##########################################

============ Checking for byte order ============

short ascii_name[] = { (('M'<<8)|'P'),(('l'<<8)|'a'),(('y'<<8)|'e'),(('r'<<8)|'B'),
                       (('i'<<8)|'g'),(('E'<<8)|'n'),(('d'<<8)|'i'),(('a'<<8)|'n'),0};
int main(void) { return (int)ascii_name; }

cc  -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: little-endian 
##########################################

============ Checking for extern symbol prefix ============

int ff_extern;

cc  -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -c


Result is:  
##########################################

============ Checking for assembler support of -pipe option ============

int main(void) { return 0; }

cc  -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -pipe


Result is: yes 
##########################################

============ Checking for compiler support of named assembler arguments ============
Result is: yes 
##########################################

============ Checking for .align is a power of two ============

int main(void) { __asm__ (".align 3"); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
{standard input}: Assembler messages:
{standard input}:9: Error: alignment not a power of 2


Result is: no 
##########################################

============ Checking for yasm ============

pabsw xmm0, xmm0

yasm -f elf -DARCH_X86_64 -m amd64 -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.S 
./configure: 2498: yasm: not found


Result is: no 
##########################################

============ Checking for -lposix ============

int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lposix
/usr/bin/ld: cannot find -lposix
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for -lm ============

int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lm


Result is: yes 
##########################################

============ Checking for langinfo ============

#include <langinfo.h>
int main(void) { nl_langinfo(CODESET); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for language ============
Result is: messages: en - man pages: en - documentation: en 
##########################################

============ Checking for enable sighandler ============
Result is: yes 
##########################################

============ Checking for runtime cpudetection ============
Result is: yes 
##########################################

============ Checking for restrict keyword ============

void foo(char * restrict p); int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c:1: error: expected ';', ',' or ')' before 'p'



void foo(char * __restrict p); int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: __restrict 
##########################################

============ Checking for __builtin_expect ============

int foo(int a) {
    a = __builtin_expect(a, 10);
    return a == 10 ? 0 : 1;
}
int main(void) { return foo(10) && foo(0); }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for kstat ============

#include <kstat.h>
int main(void) { (void) kstat_open(); (void) kstat_close(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lkstat
/tmp/mplayer-conf--28003.c:1:19: error: kstat.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'kstat_open'
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'kstat_close'


Result is: no 
##########################################

============ Checking for posix4 ============

#include <time.h>
int main(void) { (void) nanosleep(0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lposix4
/usr/bin/ld: cannot find -lposix4
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for llrint ============

#include <math.h>
int main(void) { long (*foo)(float); foo = llrint; (void)(*foo)(0.0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -D_ISOC99_SOURCE -lm
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: assignment from incompatible pointer type


Result is: yes 
##########################################

============ Checking for lrint ============

#include <math.h>
int main(void) { long (*foo)(float); foo = lrint; (void)(*foo)(0.0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -D_ISOC99_SOURCE -lm
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: assignment from incompatible pointer type


Result is: yes 
##########################################

============ Checking for lrintf ============

#include <math.h>
int main(void) { long (*foo)(float); foo = lrintf; (void)(*foo)(0.0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for round ============

#include <math.h>
int main(void) { long (*foo)(float); foo = round; (void)(*foo)(0.0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -D_ISOC99_SOURCE -lm
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: assignment from incompatible pointer type


Result is: yes 
##########################################

============ Checking for roundf ============

#include <math.h>
int main(void) { long (*foo)(float); foo = roundf; (void)(*foo)(0.0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -D_ISOC99_SOURCE -lm
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: assignment from incompatible pointer type


Result is: yes 
##########################################

============ Checking for truncf ============

#include <math.h>
int main(void) { long (*foo)(float); foo = truncf; (void)(*foo)(0.0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -D_ISOC99_SOURCE -lm
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: assignment from incompatible pointer type


Result is: yes 
##########################################

============ Checking for mkstemp ============

#include <stdlib.h>
int main(void) { char a;  mkstemp(&a); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for nanosleep ============

#include <time.h>
int main(void) { (void) nanosleep(0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for socklib ============

#include <netdb.h>
#include <sys/socket.h>
int main(void) { (void) gethostbyname(0); (void) socket(AF_INET, SOCK_STREAM, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c



#include <winsock2.h>
int main(void) { (void) gethostbyname(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lws2_32
/tmp/mplayer-conf--28003.c:1:22: error: winsock2.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'gethostbyname'


Result is: yes 
##########################################

============ Checking for inet_pton() ============

#include <sys/types.h>
#include <sys/socket.h>
#include <arpa/inet.h>
int main(void) { (void) inet_pton(0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for socklen_t ============

#include <sys/socket.h>
int main(void) { socklen_t v = 0; return v; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for closesocket() ============

#include <winsock2.h>
int main(void) { closesocket(~0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c:1:22: error: winsock2.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'closesocket'


Result is: no 
##########################################

============ Checking for network ============
Result is: yes 
##########################################

============ Checking for inet6 ============

#include <sys/types.h>
#if !defined(_WIN32) || defined(__CYGWIN__)
#include <sys/socket.h>
#include <netinet/in.h>
#else
#include <ws2tcpip.h>
#endif
int main(void) { struct sockaddr_in6 six; socket(AF_INET6, SOCK_STREAM, AF_INET6); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:8: warning: unused variable 'six'


Result is: yes 
##########################################

============ Checking for gethostbyname2 ============

#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>
int main(void) { gethostbyname2("", AF_INET); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for inttypes.h (required) ============

#include <inttypes.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for int_fastXY_t in inttypes.h ============

#include <inttypes.h>
int main(void) {
volatile int_fast16_t v= 0;
return v; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for malloc.h ============

#include <malloc.h>
int main(void) { (void) malloc(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for memalign() ============

#include <malloc.h>
int main(void) { (void) memalign(64, sizeof(char)); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for alloca.h ============

#include <alloca.h>
int main(void) { (void) alloca(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c



#include <alloca.h>
int main(void) { (void) alloca(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for fastmemcpy ============
Result is: yes 
##########################################

============ Checking for mman.h ============

#include <sys/types.h>
#include <sys/mman.h>
int main(void) { (void) mmap(0, 0, 0, 0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################


#include <sys/types.h>
#include <sys/mman.h>
int main(void) { void *p = MAP_FAILED; return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: unused variable 'p'


============ Checking for dynamic loader ============

#include <stddef.h>
#include <dlfcn.h>
int main(void) { dlopen(NULL, 0); dlclose(NULL); dlsym(NULL, NULL); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: null argument where non-null required (argument 1)
/tmp/mplayer-conf--28003.c:3: warning: null argument where non-null required (argument 2)
/tmp/cciMNekO.o: In function `main':
mplayer-conf--28003.c:(.text+0x9): undefined reference to `dlopen'
mplayer-conf--28003.c:(.text+0x10): undefined reference to `dlclose'
mplayer-conf--28003.c:(.text+0x19): undefined reference to `dlsym'
collect2: ld returned 1 exit status



#include <stddef.h>
#include <dlfcn.h>
int main(void) { dlopen(NULL, 0); dlclose(NULL); dlsym(NULL, NULL); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ldl
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: null argument where non-null required (argument 1)
/tmp/mplayer-conf--28003.c:3: warning: null argument where non-null required (argument 2)


Result is: yes 
##########################################

============ Checking for dynamic a/v plugins support ============
Result is: yes 
##########################################

============ Checking for pthread ============

#include <pthread.h>
void* func(void *arg) { return arg; }
int main(void) { pthread_t tid; return pthread_create(&tid, 0, func, 0) == 0 ? 0 : 1; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lpthreadGC2
/usr/bin/ld: cannot find -lpthreadGC2
collect2: ld returned 1 exit status



#include <pthread.h>
void* func(void *arg) { return arg; }
int main(void) { pthread_t tid; return pthread_create(&tid, 0, func, 0) == 0 ? 0 : 1; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/cc7LnGE5.o: In function `main':
mplayer-conf--28003.c:(.text+0x23): undefined reference to `pthread_create'
collect2: ld returned 1 exit status



#include <pthread.h>
void* func(void *arg) { return arg; }
int main(void) { pthread_t tid; return pthread_create(&tid, 0, func, 0) == 0 ? 0 : 1; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lpthread


Result is: yes (using -lpthread)
##########################################

============ Checking for w32threads ============
Result is: no (using pthread instead)
##########################################

============ Checking for rpath ============
Result is: yes 
##########################################

============ Checking for iconv ============

#include <stdio.h>
#include <unistd.h>
#include <iconv.h>
#define INBUFSIZE 1024
#define OUTBUFSIZE 4096

char inbuffer[INBUFSIZE];
char outbuffer[OUTBUFSIZE];

int main(void) {
  size_t numread;
  iconv_t icdsc;
  char *tocode="UTF-8";
  char *fromcode="cp1250";
  if ((icdsc = iconv_open(tocode, fromcode)) != (iconv_t)(-1)) {
    while ((numread = read(0, inbuffer, INBUFSIZE))) {
      char *iptr=inbuffer;
      char *optr=outbuffer;
      size_t inleft=numread;
      size_t outleft=OUTBUFSIZE;
      if (iconv(icdsc, (const char **)&iptr, &inleft, &optr, &outleft)
          != (size_t)(-1)) {
        write(1, outbuffer, OUTBUFSIZE - outleft);
      }
    }
    if (iconv_close(icdsc) == -1)
      ;
  }
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.      -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lm
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:21: warning: passing argument 2 of 'iconv' from incompatible pointer type


Result is: yes 
##########################################

============ Checking for soundcard.h ============

#include <sys/soundcard.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes (sys/soundcard.h)
##########################################

============ Checking for sys/dvdio.h ============

#include <unistd.h>
#include <sys/dvdio.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c:2:23: error: sys/dvdio.h: No such file or directory


Result is: no 
##########################################

============ Checking for sys/cdio.h ============

#include <unistd.h>
#include <sys/cdio.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c:2:22: error: sys/cdio.h: No such file or directory


Result is: no 
##########################################

============ Checking for linux/cdrom.h ============

#include <sys/types.h>
#include <linux/cdrom.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for dvd.h ============

#include <dvd.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c:1:17: error: dvd.h: No such file or directory


Result is: no 
##########################################

============ Checking for termcap ============

#include <stddef.h>
#include <term.h>
int main(void) { tgetent(NULL, NULL); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.       -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lncurses


Result is: yes (using -lncurses)
##########################################

============ Checking for termios ============

#include <sys/termios.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes (using sys/termios.h)
##########################################

============ Checking for shm ============

#include <sys/types.h>
#include <sys/shm.h>
int main(void) { shmget(0, 0, 0); shmat(0, 0, 0); shmctl(0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for strsep() ============

#include <string.h>
int main(void) { char *s = "Hello, world!"; (void) strsep(&s, ","); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for vsscanf() ============

#define _ISOC99_SOURCE
#include <stdarg.h>
#include <stdio.h>
int main(void) { vsscanf(0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:4: warning: null argument where non-null required (argument 2)
/tmp/mplayer-conf--28003.c:4: warning: too many arguments for format
/tmp/mplayer-conf--28003.c:4: warning: too many arguments for format


Result is: yes 
##########################################

============ Checking for swab() ============

#include <unistd.h>
int main(void) { swab(0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'swab'


Result is: yes 
##########################################

============ Checking for POSIX select() ============

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <string.h>
#include <sys/time.h>
#include <unistd.h>
int main(void) {int nfds = 1; fd_set readfds; struct timeval timeout; select(nfds,&readfds,NULL,NULL,&timeout); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for audio select() ============
Result is: yes 
##########################################

============ Checking for gettimeofday() ============

#include <stdio.h>
#include <sys/time.h>
int main(void) {struct timeval tv_start; gettimeofday(&tv_start, NULL); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for glob() ============

#include <stdio.h>
#include <glob.h>
int main(void) { glob_t gg; glob("filename",0,NULL,&gg); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for setenv() ============

#include <stdlib.h>
int main(void) { setenv("","",0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for sys/sysinfo.h ============

#include <sys/sysinfo.h>
int main(void) {
  struct sysinfo s_info;
  sysinfo(&s_info);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c


Result is: yes 
##########################################

============ Checking for Apple IR ============

#include <linux/types.h>
#include <linux/input.h>
int main(void) {
  struct input_event ev;
  struct input_id id;
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
In file included from /usr/include/sys/time.h:31,
                 from /usr/include/linux/input.h:12,
                 from /tmp/mplayer-conf--28003.c:2:
/usr/include/sys/select.h:78: error: conflicting types for 'fd_set'
/usr/include/linux/types.h:12: error: previous declaration of 'fd_set' was here
In file included from /usr/include/linux/input.h:14,
                 from /tmp/mplayer-conf--28003.c:2:
/usr/include/sys/types.h:46: error: conflicting types for 'loff_t'
/usr/include/linux/types.h:30: error: previous declaration of 'loff_t' was here
/usr/include/sys/types.h:62: error: conflicting types for 'dev_t'
/usr/include/linux/types.h:13: error: previous declaration of 'dev_t' was here
In file included from /usr/include/sys/types.h:133,
                 from /usr/include/linux/input.h:14,
                 from /tmp/mplayer-conf--28003.c:2:
/usr/include/time.h:105: error: conflicting types for 'timer_t'
/usr/include/linux/types.h:22: error: previous declaration of 'timer_t' was here
In file included from /usr/include/linux/input.h:14,
                 from /tmp/mplayer-conf--28003.c:2:
/usr/include/sys/types.h:198: error: conflicting types for 'int64_t'
/usr/include/linux/types.h:98: error: previous declaration of 'int64_t' was here
/usr/include/sys/types.h:204: error: conflicting types for 'u_int64_t'
/usr/include/linux/types.h:97: error: previous declaration of 'u_int64_t' was here
In file included from /usr/include/linux/input.h:14,
                 from /tmp/mplayer-conf--28003.c:2:
/usr/include/sys/types.h:235: error: conflicting types for 'blkcnt_t'
/usr/include/linux/types.h:124: error: previous declaration of 'blkcnt_t' was here
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:5: warning: unused variable 'id'
/tmp/mplayer-conf--28003.c:4: warning: unused variable 'ev'


Result is: no 
##########################################

============ Checking for pkg-config ============
Result is: yes 
##########################################

============ Checking for Samba support (libsmbclient) ============

#include <libsmbclient.h>
int main(void) { smbc_opendir("smb://"); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lsmbclient
/tmp/mplayer-conf--28003.c:1:26: error: libsmbclient.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'smbc_opendir'



#include <libsmbclient.h>
int main(void) { smbc_opendir("smb://"); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lsmbclient -ldl
/tmp/mplayer-conf--28003.c:1:26: error: libsmbclient.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'smbc_opendir'



#include <libsmbclient.h>
int main(void) { smbc_opendir("smb://"); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lsmbclient -ldl -lnsl
/tmp/mplayer-conf--28003.c:1:26: error: libsmbclient.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'smbc_opendir'



#include <libsmbclient.h>
int main(void) { smbc_opendir("smb://"); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lsmbclient -ldl -lssl -lnsl
/tmp/mplayer-conf--28003.c:1:26: error: libsmbclient.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'smbc_opendir'


Result is: no 
##########################################

============ Checking for tdfxfb ============
Result is: no 
##########################################

============ Checking for s3fb ============
Result is: no 
##########################################

============ Checking for wii ============
Result is: no 
##########################################

============ Checking for tdfxvid ============
Result is: no 
##########################################

============ Checking for xvr100 ============

#include <unistd.h>
#include <sys/fbio.h>
#include <sys/visual_io.h>
int main(void) {
struct vis_identifier ident;
struct fbgattr attr;
ioctl(0, VIS_GETIDENTIFIER, &ident);
ioctl(0, FBIOGATTR, &attr);
return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
/tmp/mplayer-conf--28003.c:2:22: error: sys/fbio.h: No such file or directory
/tmp/mplayer-conf--28003.c:3:27: error: sys/visual_io.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:5: error: storage size of 'ident' isn't known
/tmp/mplayer-conf--28003.c:6: error: storage size of 'attr' isn't known
/tmp/mplayer-conf--28003.c:7: warning: implicit declaration of function 'ioctl'
/tmp/mplayer-conf--28003.c:7: error: 'VIS_GETIDENTIFIER' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:7: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:7: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:8: error: 'FBIOGATTR' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:6: warning: unused variable 'attr'
/tmp/mplayer-conf--28003.c:5: warning: unused variable 'ident'


Result is: no 
##########################################

============ Checking for tga ============
Result is: yes 
##########################################

============ Checking for md5sum support ============
Result is: yes 
##########################################

============ Checking for yuv4mpeg support ============
Result is: yes 
##########################################

============ Checking for bl ============
Result is: no 
##########################################

============ Checking for DirectFB ============

#include <directfb.h>
int main(void) { IDirectFB *foo; DirectFBInit(0,0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ldirectfb
/tmp/mplayer-conf--28003.c:1:22: error: directfb.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: error: 'IDirectFB' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:2: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:2: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:2: error: 'foo' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'DirectFBInit'



#include <directfb.h>
int main(void) { IDirectFB *foo; DirectFBInit(0,0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/local/include/directfb -ldirectfb
/tmp/mplayer-conf--28003.c:1:22: error: directfb.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: error: 'IDirectFB' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:2: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:2: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:2: error: 'foo' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'DirectFBInit'



#include <directfb.h>
int main(void) { IDirectFB *foo; DirectFBInit(0,0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.     -lncurses   -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/include/directfb -ldirectfb
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: unused variable 'foo'


Result is: yes (0.9.25)
##########################################

============ Checking for X11 headers presence ============
Result is: yes 
##########################################

============ Checking for X11 ============

#include <X11/Xlib.h>
#include <X11/Xutil.h>
int main(void) { (void) XCreateWindow(0,0,0,0,0,0,0,0,0,0,0,0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXext -lX11 -lpthread


Result is: yes 
##########################################

============ Checking for Xss screensaver extensions ============

#include <X11/Xlib.h>
#include <X11/extensions/scrnsaver.h>
int main(void) { XScreenSaverSuspend(NULL, True); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXss
/tmp/mplayer-conf--28003.c:2:38: error: X11/extensions/scrnsaver.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: implicit declaration of function 'XScreenSaverSuspend'


Result is: no 
##########################################

============ Checking for DPMS ============

#include <X11/Xmd.h>
#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/Xatom.h>
#include <X11/extensions/dpms.h>
int main(void) { (void) DPMSQueryExtension(0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXdpms
/usr/bin/ld: cannot find -lXdpms
collect2: ld returned 1 exit status



#include <X11/Xlib.h>
#include <X11/extensions/dpms.h>
int main(void) { (void) DPMSQueryExtension(0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXext


Result is: yes (using Xdpms 4)
##########################################

============ Checking for Xv ============

#include <X11/Xlib.h>
#include <X11/extensions/Xvlib.h>
int main(void) {
  (void) XvGetPortAttribute(0, 0, 0, 0);
  (void) XvQueryPortAttributes(0, 0, 0);
  return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXv
/tmp/mplayer-conf--28003.c:2:34: error: X11/extensions/Xvlib.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:4: warning: implicit declaration of function 'XvGetPortAttribute'
/tmp/mplayer-conf--28003.c:5: warning: implicit declaration of function 'XvQueryPortAttributes'


Result is: no 
##########################################

============ Checking for XvMC ============
Result is: yes (using )
##########################################

============ Checking for Xinerama ============

#include <X11/Xlib.h>
#include <X11/extensions/Xinerama.h>
int main(void) { (void) XineramaIsActive(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXinerama
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for Xxf86vm ============

#include <X11/Xlib.h>
#include <X11/extensions/xf86vmode.h>
int main(void) { (void) XF86VidModeQueryExtension(0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXxf86vm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:2:38: error: X11/extensions/xf86vmode.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: implicit declaration of function 'XF86VidModeQueryExtension'


Result is: no 
##########################################

============ Checking for XF86keysym ============

#include <X11/Xlib.h>
#include <X11/XF86keysym.h>
int main(void) { return XF86XK_AudioPause; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for DGA ============

#include <X11/Xlib.h>
#include <X11/extensions/xf86dga.h>
int main(void) { (void) XDGASetViewport(0, 0, 0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lXxf86dga
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:2:36: error: X11/extensions/xf86dga.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: implicit declaration of function 'XDGASetViewport'


Result is: no 
##########################################

============ Checking for 3dfx ============
Result is: no 
##########################################

============ Checking for OpenGL ============

#ifdef GL_WIN32
#include <windows.h>
#include <GL/gl.h>
#else
#include <GL/gl.h>
#include <X11/Xlib.h>
#include <GL/glx.h>
#endif
int main(void) {
#ifdef GL_WIN32
  HDC dc;
  wglCreateContext(dc);
#else
  glXCreateContext(NULL, NULL, NULL, True);
#endif
  glFinish();
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lGL -lm
cc: /tmp/mplayer-conf--28003: No such file or directory



#ifdef GL_WIN32
#include <windows.h>
#include <GL/gl.h>
#else
#include <GL/gl.h>
#include <X11/Xlib.h>
#include <GL/glx.h>
#endif
int main(void) {
#ifdef GL_WIN32
  HDC dc;
  wglCreateContext(dc);
#else
  glXCreateContext(NULL, NULL, NULL, True);
#endif
  glFinish();
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lGL -lm -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory



#ifdef GL_WIN32
#include <windows.h>
#include <GL/gl.h>
#else
#include <GL/gl.h>
#include <X11/Xlib.h>
#include <GL/glx.h>
#endif
int main(void) {
#ifdef GL_WIN32
  HDC dc;
  wglCreateContext(dc);
#else
  glXCreateContext(NULL, NULL, NULL, True);
#endif
  glFinish();
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -DGL_WIN32 -lopengl32
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:2:21: error: windows.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:11: error: 'HDC' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:11: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:11: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:11: error: expected ';' before 'dc'
/tmp/mplayer-conf--28003.c:12: warning: implicit declaration of function 'wglCreateContext'
/tmp/mplayer-conf--28003.c:12: error: 'dc' undeclared (first use in this function)


Result is: no 
##########################################

============ Checking for VIDIX ============
Result is: yes 
##########################################

============ Checking for VIDIX PCI device name database ============
Result is: yes 
##########################################

============ Checking for VIDIX dhahelper support ============
Result is: no 
##########################################

============ Checking for VIDIX svgalib_helper support ============
Result is: no 
##########################################

============ Checking for /dev/mga_vid ============
Result is: no 
##########################################

============ Checking for xmga ============
Result is: no 
##########################################

============ Checking for GGI ============

#include <ggi/ggi.h>
int main(void) { ggiInit(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lggi
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:21: error: ggi/ggi.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'ggiInit'


Result is: no 
##########################################

============ Checking for GGI extension: libggiwmh ============

#include <ggi/ggi.h>
#include <ggi/wmh.h>
int main(void) { ggiInit(); ggiWmhInit(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lggi -lggiwmh
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:21: error: ggi/ggi.h: No such file or directory
/tmp/mplayer-conf--28003.c:2:21: error: ggi/wmh.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: implicit declaration of function 'ggiInit'
/tmp/mplayer-conf--28003.c:3: warning: implicit declaration of function 'ggiWmhInit'


Result is: no 
##########################################

============ Checking for AA ============

#include <aalib.h>
extern struct aa_hardware_params aa_defparams;
extern struct aa_renderparams aa_defrenderparams;
int main(void) {
aa_context *c;
aa_renderparams *p;
(void) aa_init(0, 0, 0);
c = aa_autoinit(&aa_defparams);
p = aa_getrenderparams();
aa_autoinitkbd(c,0);
return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -laa
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:19: error: aalib.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:5: error: 'aa_context' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:5: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:5: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:5: error: 'c' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:6: error: 'aa_renderparams' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:6: error: 'p' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:7: warning: implicit declaration of function 'aa_init'
/tmp/mplayer-conf--28003.c:8: warning: implicit declaration of function 'aa_autoinit'
/tmp/mplayer-conf--28003.c:9: warning: implicit declaration of function 'aa_getrenderparams'
/tmp/mplayer-conf--28003.c:10: warning: implicit declaration of function 'aa_autoinitkbd'


Result is: no 
##########################################

============ Checking for CACA ============
./configure: 4624: caca-config: not found
Result is: no 
##########################################

============ Checking for SVGAlib ============

#include <vga.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lvga -lm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:17: error: vga.h: No such file or directory


Result is: no 
##########################################

============ Checking for FBDev ============
Result is: yes 
##########################################

============ Checking for DVB ============

#include <poll.h>
#include <sys/ioctl.h>
#include <stdio.h>
#include <time.h>
#include <unistd.h>
#include <ost/dmx.h>
#include <ost/frontend.h>
#include <ost/sec.h>
#include <ost/video.h>
#include <ost/audio.h>
int main(void) {return 0;}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:6:21: error: ost/dmx.h: No such file or directory
/tmp/mplayer-conf--28003.c:7:26: error: ost/frontend.h: No such file or directory
/tmp/mplayer-conf--28003.c:8:21: error: ost/sec.h: No such file or directory
/tmp/mplayer-conf--28003.c:9:23: error: ost/video.h: No such file or directory
/tmp/mplayer-conf--28003.c:10:23: error: ost/audio.h: No such file or directory



#include <poll.h>
#include <sys/ioctl.h>
#include <stdio.h>
#include <time.h>
#include <unistd.h>
#include <ost/dmx.h>
#include <ost/frontend.h>
#include <ost/sec.h>
#include <ost/video.h>
#include <ost/audio.h>
int main(void) {return 0;}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/src/DVB/ost/include
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:6:21: error: ost/dmx.h: No such file or directory
/tmp/mplayer-conf--28003.c:7:26: error: ost/frontend.h: No such file or directory
/tmp/mplayer-conf--28003.c:8:21: error: ost/sec.h: No such file or directory
/tmp/mplayer-conf--28003.c:9:23: error: ost/video.h: No such file or directory
/tmp/mplayer-conf--28003.c:10:23: error: ost/audio.h: No such file or directory


Result is: no 
##########################################

============ Checking for DVB HEAD ============

#include <poll.h>
#include <sys/ioctl.h>
#include <stdio.h>
#include <time.h>
#include <unistd.h>
#include <linux/dvb/dmx.h>
#include <linux/dvb/frontend.h>
#include <linux/dvb/video.h>
#include <linux/dvb/audio.h>
int main(void) {return 0;}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory



#include <poll.h>
#include <sys/ioctl.h>
#include <stdio.h>
#include <time.h>
#include <unistd.h>
#include <linux/dvb/dmx.h>
#include <linux/dvb/frontend.h>
#include <linux/dvb/video.h>
#include <linux/dvb/audio.h>
int main(void) {return 0;}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/src/DVB/include
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for PNG support ============

#include <png.h>
#include <string.h>
int main(void) {
  printf("png.h : %s\n", PNG_LIBPNG_VER_STRING);
  printf("libpng: %s\n", png_libpng_ver);
  return strcmp(PNG_LIBPNG_VER_STRING, png_libpng_ver);
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lpng -lz -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for MNG support ============

#include <libmng.h>
int main(void) {
  const char * p_ver = mng_version_text();
  return !p_ver || p_ver[0] == 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lmng -lz -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for JPEG support ============

#include <stdio.h>
#include <stdlib.h>
#include <setjmp.h>
#include <string.h>
#include <jpeglib.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ljpeg -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for PNM support ============
Result is: yes 
##########################################

============ Checking for GIF support ============

#include <gif_lib.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lungif
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:21: error: gif_lib.h: No such file or directory



#include <gif_lib.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lgif
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:21: error: gif_lib.h: No such file or directory


Result is: no 
##########################################

============ Checking for VESA support ============

#include <vbe.h>
int main(void) { vbeVersion(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lvbe -llrmi
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:17: error: vbe.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'vbeVersion'


Result is: no 
##########################################

============ Checking for SDL ============
1.2.11
1.2.11

#include <SDL.h>
int main(void) {
  SDL_Init(SDL_INIT_VIDEO|SDL_INIT_NOPARACHUTE);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -L/usr/lib -lSDL
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for DXR2 ============

#include <dxr2ioctl.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:23: error: dxr2ioctl.h: No such file or directory



#include <dxr2ioctl.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/local/include/dxr2
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:23: error: dxr2ioctl.h: No such file or directory



#include <dxr2ioctl.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/include/dxr2
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:23: error: dxr2ioctl.h: No such file or directory


Result is: no 
##########################################

============ Checking for DXR3/H+ ============

#include <linux/em8300.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:26: error: linux/em8300.h: No such file or directory


Result is: no 
##########################################

============ Checking for IVTV TV-Out (pre linux-2.6.24) ============

#include <stdlib.h>
#include <inttypes.h>
#include <linux/types.h>
#include <linux/videodev2.h>
#include <linux/ivtv.h>
#include <sys/ioctl.h>
int main(void) {
struct ivtv_cfg_stop_decode sd;
struct ivtv_cfg_start_decode sd1;
ioctl(0, IVTV_IOC_START_DECODE, &sd1);
ioctl(0, IVTV_IOC_STOP_DECODE, &sd);
return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:5:24: error: linux/ivtv.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:8: error: storage size of 'sd' isn't known
/tmp/mplayer-conf--28003.c:9: error: storage size of 'sd1' isn't known
/tmp/mplayer-conf--28003.c:10: error: 'IVTV_IOC_START_DECODE' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:10: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:10: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:11: error: 'IVTV_IOC_STOP_DECODE' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:9: warning: unused variable 'sd1'
/tmp/mplayer-conf--28003.c:8: warning: unused variable 'sd'


Result is: no 
##########################################

============ Checking for V4L2 MPEG Decoder ============

#include <stdlib.h>
#include <inttypes.h>
#include <linux/types.h>
#include <linux/videodev2.h>
#include <linux/version.h>
int main(void) {
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,22)
#error kernel headers too old, need 2.6.22
  bad_kernel_version();
#endif
  struct v4l2_ext_controls ctrls;
  ctrls.ctrl_class = V4L2_CTRL_CLASS_MPEG;
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for OSS Audio ============

#include <sys/ioctl.h>
#include <sys/soundcard.h>
int main(void) { int arg = SNDCTL_DSP_SETFRAGMENT; return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: unused variable 'arg'


Result is: no 
##########################################

============ Checking for aRts ============
./configure: 5258: artsc-config: not found
Result is: no 
##########################################

============ Checking for EsounD ============
./configure: 5283: esd-config: not found
Result is: no 
##########################################

============ Checking for NAS ============

#include <audio/audiolib.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lm -laudio -lXt
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for pulse ============
Result is: no 
##########################################

============ Checking for JACK ============

#include <jack/jack.h>
int main(void) { jack_client_open("test", JackUseExactName, NULL); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ljack
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:23: error: jack/jack.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'jack_client_open'
/tmp/mplayer-conf--28003.c:2: error: 'JackUseExactName' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:2: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:2: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:2: error: 'NULL' undeclared (first use in this function)



#include <jack/jack.h>
int main(void) { jack_client_open("test", JackUseExactName, NULL); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:23: error: jack/jack.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'jack_client_open'
/tmp/mplayer-conf--28003.c:2: error: 'JackUseExactName' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:2: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:2: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:2: error: 'NULL' undeclared (first use in this function)


Result is: no 
##########################################

============ Checking for OpenAL ============

#ifdef OPENAL_AL_H
#include <OpenAL/al.h>
#else
#include <AL/al.h>
#endif
int main(void) {
  alSourceQueueBuffers(0, 0, 0);
//  alGetSourcei(0, AL_SAMPLE_OFFSET, 0);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lopenal
cc: /tmp/mplayer-conf--28003: No such file or directory



#ifdef OPENAL_AL_H
#include <OpenAL/al.h>
#else
#include <AL/al.h>
#endif
int main(void) {
  alSourceQueueBuffers(0, 0, 0);
//  alGetSourcei(0, AL_SAMPLE_OFFSET, 0);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -DOPENAL_AL_H=1 -lopenal
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:2:23: error: OpenAL/al.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:7: warning: implicit declaration of function 'alSourceQueueBuffers'



#ifdef OPENAL_AL_H
#include <OpenAL/al.h>
#else
#include <AL/al.h>
#endif
int main(void) {
  alSourceQueueBuffers(0, 0, 0);
//  alGetSourcei(0, AL_SAMPLE_OFFSET, 0);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lopenal32
cc: /tmp/mplayer-conf--28003: No such file or directory



#ifdef OPENAL_AL_H
#include <OpenAL/al.h>
#else
#include <AL/al.h>
#endif
int main(void) {
  alSourceQueueBuffers(0, 0, 0);
//  alGetSourcei(0, AL_SAMPLE_OFFSET, 0);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -DOPENAL_AL_H=1 -lopenal32
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:2:23: error: OpenAL/al.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:7: warning: implicit declaration of function 'alSourceQueueBuffers'



#ifdef OPENAL_AL_H
#include <OpenAL/al.h>
#else
#include <AL/al.h>
#endif
int main(void) {
  alSourceQueueBuffers(0, 0, 0);
//  alGetSourcei(0, AL_SAMPLE_OFFSET, 0);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -framework OpenAL
cc: /tmp/mplayer-conf--28003: No such file or directory
cc: OpenAL: No such file or directory
cc1: error: unrecognized command line option "-framework"



#ifdef OPENAL_AL_H
#include <OpenAL/al.h>
#else
#include <AL/al.h>
#endif
int main(void) {
  alSourceQueueBuffers(0, 0, 0);
//  alGetSourcei(0, AL_SAMPLE_OFFSET, 0);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -DOPENAL_AL_H=1 -framework OpenAL
cc: /tmp/mplayer-conf--28003: No such file or directory
cc: OpenAL: No such file or directory
cc1: error: unrecognized command line option "-framework"


Result is: no 
##########################################

============ Checking for ALSA audio ============

#include <sys/time.h>
#include <sys/asoundlib.h>
#if !((SND_LIB_MAJOR == 0) && (SND_LIB_MINOR == 5))
#error "alsa version != 0.5.x"
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lasound -ldl -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory
In file included from /tmp/mplayer-conf--28003.c:2:
/usr/include/sys/asoundlib.h:1:2: warning: #warning This header is deprecated, use <alsa/asoundlib.h> instead.
/tmp/mplayer-conf--28003.c:4:2: error: #error "alsa version != 0.5.x"



#include <sys/time.h>
#include <sys/asoundlib.h>
#if !((SND_LIB_MAJOR == 0) && (SND_LIB_MINOR == 9))
#error "alsa version != 0.9.x"
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lasound -ldl -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory
In file included from /tmp/mplayer-conf--28003.c:2:
/usr/include/sys/asoundlib.h:1:2: warning: #warning This header is deprecated, use <alsa/asoundlib.h> instead.
/tmp/mplayer-conf--28003.c:4:2: error: #error "alsa version != 0.9.x"



#include <sys/time.h>
#include <alsa/asoundlib.h>
#if !((SND_LIB_MAJOR == 0) && (SND_LIB_MINOR == 9))
#error "alsa version != 0.9.x"
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lasound -ldl -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:4:2: error: #error "alsa version != 0.9.x"



#include <sys/time.h>
#include <sys/asoundlib.h>
#if !((SND_LIB_MAJOR == 1) && (SND_LIB_MINOR == 0))
#error "alsa version != 1.0.x"
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lasound -ldl -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory
In file included from /tmp/mplayer-conf--28003.c:2:
/usr/include/sys/asoundlib.h:1:2: warning: #warning This header is deprecated, use <alsa/asoundlib.h> instead.



#include <sys/time.h>
#include <alsa/asoundlib.h>
#if !((SND_LIB_MAJOR == 1) && (SND_LIB_MINOR == 0))
#error "alsa version != 1.0.x"
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lasound -ldl -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for Sun audio ============

#include <sys/types.h>
#include <sys/audioio.h>
int main(void) { audio_info_t info; AUDIO_INITINFO(&info); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:2:25: error: sys/audioio.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: error: 'audio_info_t' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:3: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:3: error: for each function it appears in.)
/tmp/mplayer-conf--28003.c:3: error: expected ';' before 'info'
/tmp/mplayer-conf--28003.c:3: warning: implicit declaration of function 'AUDIO_INITINFO'
/tmp/mplayer-conf--28003.c:3: error: 'info' undeclared (first use in this function)


Result is: no 
##########################################

============ Checking for VCD support ============
Result is: yes 
##########################################

============ Checking for dvdread ============

#include <inttypes.h>
#include <dvdread/dvd_reader.h>
#include <dvdread/ifo_types.h>
#include <dvdread/ifo_read.h>
#include <dvdread/nav_read.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -ldl
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for internal libdvdcss ============
Result is: no 
##########################################

============ Checking for cdparanoia ============

#include <cdda_interface.h>
#include <cdda_paranoia.h>
// This need a better test. How ?
int main(void) { void *test = cdda_verbose_set; return test == (void *)1; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lcdda_interface -lcdda_paranoia -lm
cc: /tmp/mplayer-conf--28003: No such file or directory



#include <cdda_interface.h>
#include <cdda_paranoia.h>
// This need a better test. How ?
int main(void) { void *test = cdda_verbose_set; return test == (void *)1; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/include/cdda -lcdda_interface -lcdda_paranoia -lm
cc: /tmp/mplayer-conf--28003: No such file or directory



#include <cdda_interface.h>
#include <cdda_paranoia.h>
// This need a better test. How ?
int main(void) { void *test = cdda_verbose_set; return test == (void *)1; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/local/include/cdda -lcdda_interface -lcdda_paranoia -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for libcdio ============

#include <stdio.h>
#include <cdio/version.h>
#include <cdio/cdda.h>
#include <cdio/paranoia.h>
int main(void) {
    void *test = cdda_verbose_set;
    printf("%s\n", CDIO_VERSION);
    return test == (void *)1;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lcdio_cdda -lcdio -lcdio_paranoia -lm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:3:23: error: cdio/cdda.h: No such file or directory
/tmp/mplayer-conf--28003.c:4:27: error: cdio/paranoia.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:6: error: 'cdda_verbose_set' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:6: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:6: error: for each function it appears in.)



#include <stdio.h>
#include <cdio/version.h>
#include <cdio/cdda.h>
#include <cdio/paranoia.h>
int main(void) {
    void *test = cdda_verbose_set;
    printf("%s\n", CDIO_VERSION);
    return test == (void *)1;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lcdio_cdda -lcdio -lcdio_paranoia -lwinmm -lm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:3:23: error: cdio/cdda.h: No such file or directory
/tmp/mplayer-conf--28003.c:4:27: error: cdio/paranoia.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:6: error: 'cdda_verbose_set' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:6: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:6: error: for each function it appears in.)


Result is: no 
##########################################

============ Checking for bitmap font support ============
Result is: yes 
##########################################

============ Checking for freetype >= 2.0.9 ============

#include <stdio.h>
#include <ft2build.h>
#include FT_FREETYPE_H
#if ((FREETYPE_MAJOR < 2) || ((FREETYPE_MINOR == 0) && (FREETYPE_PATCH < 9)))
#error "Need FreeType 2.0.9 or newer"
#endif
int main(void) {
    FT_Library library;
    FT_Int major=-1,minor=-1,patch=-1;
    int err=FT_Init_FreeType(&library);
    if (err) {
	printf("Couldn't initialize freetype2 lib, err code: %d\n",err);
	exit(err);
    }
    FT_Library_Version(library,&major,&minor,&patch); // in v2.1.0+ only :(((
    printf("freetype2  header version: %d.%d.%d  library version: %d.%d.%d\n",
	FREETYPE_MAJOR,FREETYPE_MINOR,FREETYPE_PATCH,
	(int)major,(int)minor,(int)patch );
    if (major!=FREETYPE_MAJOR || minor!=FREETYPE_MINOR) {
	printf("Library and header version mismatch! Fix it in your distribution!\n");
	exit(1);
    }
    return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/include/freetype2 -lfreetype -lz
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for fontconfig ============
Result is: no (FreeType support needed)
##########################################

============ Checking for SSA/*** support ============
Result is: no (FreeType support needed)
##########################################

============ Checking for fribidi with charsets ============

#include <stdio.h>
/* workaround for fribidi 0.10.4 and below */
#define FRIBIDI_CHARSET_UTF8 FRIBIDI_CHAR_SET_UTF8
#include <fribidi/fribidi.h>
int main(void) {
    if (fribidi_parse_charset("UTF-8") != FRIBIDI_CHAR_SET_UTF8) {
       printf("Fribidi headers are not consistents with the library!\n");
       exit(1);
    }
    return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/include -L/usr/lib -lfribidi
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:8: warning: implicit declaration of function 'exit'
/tmp/mplayer-conf--28003.c:8: warning: incompatible implicit declaration of built-in function 'exit'


Result is: no 
##########################################

============ Checking for ENCA ============

#include <sys/types.h>
#include <enca.h>
int main(void) {
    const char **langs;
    size_t langcnt;
    langs = enca_get_languages(&langcnt);
    return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lenca -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for zlib ============

#include <zlib.h>
int main(void) { (void) inflate(0, Z_NO_FLUSH); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lz
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for RTC ============

#include <sys/ioctl.h>
#ifdef __linux__
#include <linux/rtc.h>
#else
#include <rtc.h>
#define RTC_PIE_ON RTCIO_PIE_ON
#endif
int main(void) { return RTC_PIE_ON; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for liblzo2 support ============

#include <lzo/lzo1x.h>
int main(void) { lzo_init();return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -llzo2
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for mad support ============

#include <mad.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lmad
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for Twolame ============

#include <twolame.h>
int main(void) { twolame_init(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ltwolame -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for Toolame ============

#include <toolame.h>
int main(void) { toolame_init(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ltoolame -lm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:21: error: toolame.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: implicit declaration of function 'toolame_init'


Result is: no 
##########################################

============ Checking for OggVorbis support ============
Result is: yes (internal Tremor)
##########################################

============ Checking for libspeex (version >= 1.1 required) ============

#include <speex/speex.h>
int main(void) { SpeexBits bits; void *dec; speex_decode_int(dec, &bits, dec); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lspeex -lm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: 'dec' is used uninitialized in this function


Result is: no 
##########################################

============ Checking for OggTheora support ============

#include <theora/theora.h>
#include <string.h>
int main(void) {
  /* Theora is in flux, make sure that all interface routines and datatypes
   * exist and work the way we expect it, so we don't break MPlayer. */
  ogg_packet op;
  theora_comment tc;
  theora_info inf;
  theora_state st;
  yuv_buffer yuv;
  int r;
  double t;

  theora_info_init(&inf);
  theora_comment_init(&tc);

  return 0;

  /* we don't want to execute this kind of nonsense; just for making sure
   * that compilation works... */
  memset(&op, 0, sizeof(op));
  r = theora_decode_header(&inf, &tc, &op);
  r = theora_decode_init(&st, &inf);
  t = theora_granule_time(&st, op.granulepos);
  r = theora_decode_packetin(&st, &op);
  r = theora_decode_YUVout(&st, &yuv);
  theora_clear(&st);

  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ltheora -logg
cc: /tmp/mplayer-conf--28003: No such file or directory



#include <theora/theora.h>
#include <string.h>
int main(void) {
  /* Theora is in flux, make sure that all interface routines and datatypes
   * exist and work the way we expect it, so we don't break MPlayer. */
  ogg_packet op;
  theora_comment tc;
  theora_info inf;
  theora_state st;
  yuv_buffer yuv;
  int r;
  double t;

  theora_info_init(&inf);
  theora_comment_init(&tc);

  return 0;

  /* we don't want to execute this kind of nonsense; just for making sure
   * that compilation works... */
  memset(&op, 0, sizeof(op));
  r = theora_decode_header(&inf, &tc, &op);
  r = theora_decode_init(&st, &inf);
  t = theora_granule_time(&st, op.granulepos);
  r = theora_decode_packetin(&st, &op);
  r = theora_decode_YUVout(&st, &yuv);
  theora_clear(&st);

  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c tremor/bitwise.c -ltheora -logg
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for internal mp3lib support ============
Result is: yes 
##########################################

============ Checking for liba52 support ============

#include <inttypes.h>
#include <a52dec/a52.h>
int main(void) { a52_state_t *testHand; testHand=a52_init(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -la52
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for internal libmpeg2 support ============
Result is: no 
##########################################

============ Checking for libdca support ============

#include <inttypes.h>
#include <dts.h>
int main(void) { dts_init(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ldts -lm
cc: /tmp/mplayer-conf--28003: No such file or directory



#include <inttypes.h>
#include <dts.h>
int main(void) { dts_init(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ldca -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for libmpcdec (musepack, version >= 1.2.1 required) ============

#include <stddef.h>
#include <mpcdec/mpcdec.h>
int main(void) {
  mpc_streaminfo info;
  mpc_decoder decoder;
  mpc_decoder_set_streaminfo(&decoder, &info);
  mpc_decoder_decode_frame(&decoder, NULL, 0, NULL);
  return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lmpcdec -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for FAAC support ============

#include <inttypes.h>
#include <faac.h>
int main(void) { unsigned long x, y; faacEncOpen(48000, 2, &x, &y); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -O4 -lfaac -lm
cc: /tmp/mplayer-conf--28003: No such file or directory



#include <inttypes.h>
#include <faac.h>
int main(void) { unsigned long x, y; faacEncOpen(48000, 2, &x, &y); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -O4 -lfaac -lmp4v2 -lstdc++ -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no (in libavcodec: no)
##########################################

============ Checking for FAAD2 support ============
Result is: yes (internal floating-point)
##########################################

============ Checking for LADSPA plugin support ============

#include <stdio.h>
#include <ladspa.h>
int main(void) {
const LADSPA_Descriptor *ld = NULL;
return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:2:20: error: ladspa.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:4: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/tmp/mplayer-conf--28003.c:4: error: 'ld' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:4: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:4: error: for each function it appears in.)


Result is: no 
##########################################

============ Checking for Win32 codecs ============
Result is: no 
##########################################

============ Checking for XAnim codecs ============
Result is: yes (using /usr/lib/codecs)
##########################################

============ Checking for RealPlayer codecs ============
Result is: yes (using /usr/lib/codecs)
##########################################

============ Checking for QuickTime codecs ============
Result is: auto 
##########################################

============ Checking for Nemesi Streaming Media libraries ============
Result is: no 
##########################################

============ Checking for LIVE555 Streaming Media libraries ============

#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I./liveMedia/include -I./UsageEnvironment/include -I./groupsock/include -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>



#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I/usr/include/directfb/liveMedia/include -I/usr/include/directfb/UsageEnvironment/include -I/usr/include/directfb/groupsock/include -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>



#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I/usr/lib/live/liveMedia/include -I/usr/lib/live/UsageEnvironment/include -I/usr/lib/live/groupsock/include -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>



#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I/usr/lib/live/liveMedia/include -I/usr/lib/live/UsageEnvironment/include -I/usr/lib/live/groupsock/include -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>



#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I/usr/lib64/live/liveMedia/include -I/usr/lib64/live/UsageEnvironment/include -I/usr/lib64/live/groupsock/include -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>



#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I/usr/local/live/liveMedia/include -I/usr/local/live/UsageEnvironment/include -I/usr/local/live/groupsock/include -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>



#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I/usr/local/lib/live/liveMedia/include -I/usr/local/lib/live/UsageEnvironment/include -I/usr/local/lib/live/groupsock/include -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>



#include <liveMedia.hh>
#if (LIVEMEDIA_LIBRARY_VERSION_INT < 1141257600)
#error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>
#endif
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.cpp -I/usr/include/liveMedia -I/usr/include/UsageEnvironment -I/usr/include/groupsock -lstdc++
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.cpp:1:24: error: liveMedia.hh: No such file or directory
/tmp/mplayer-conf--28003.cpp:3:2: error: #error Please upgrade to version 2006.03.03 or later of the "LIVE555 Streaming Media" libraries - available from <www.live555.com/liveMedia/>


Result is: no 
##########################################

============ Checking for FFmpeg libavutil ============
Result is: yes (static)
##########################################

============ Checking for FFmpeg libavcodec ============
Result is: yes (static)
##########################################

============ Checking for FFmpeg libavformat ============
Result is: yes (static)
##########################################

============ Checking for FFmpeg libpostproc ============
Result is: yes (static)
##########################################

============ Checking for FFmpeg libswscale ============
Result is: yes (static)
##########################################

============ Checking for libamr narrowband ============

#include <amrnb/sp_dec.h>
int main(void) { Speech_Decode_Frame_init(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lamrnb
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for libamr wideband ============

#include <amrwb/dec_if.h>
int main(void) { D_IF_init(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lamrwb
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for libdv-0.9.5+ ============

#include <libdv/dv.h>
int main(void) { dv_encoder_t* enc=dv_encoder_new(1,1,1); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -ldv -lpthread -lm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:2: warning: unused variable 'enc'


Result is: no 
##########################################

============ Checking for Xvid ============

#include <xvid.h>
int main(void) { xvid_global(0, 0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lxvidcore -lm
cc: /tmp/mplayer-conf--28003: No such file or directory



#include <xvid.h>
int main(void) { xvid_global(0, 0, 0, 0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lxvidcore -lm -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for Xvid two pass plugin ============
Result is: no 
##########################################

============ Checking for x264 ============

#include <inttypes.h>
#include <x264.h>
#if X264_BUILD < 59
#error We do not support old versions of x264. Get the latest from SVN.
#endif
int main(void) { x264_encoder_open((void*)0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lx264 -lpthread
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:4:2: error: #error We do not support old versions of x264. Get the latest from SVN.



#include <inttypes.h>
#include <x264.h>
#if X264_BUILD < 59
#error We do not support old versions of x264. Get the latest from SVN.
#endif
int main(void) { x264_encoder_open((void*)0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lx264 -lpthread -lm
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:4:2: error: #error We do not support old versions of x264. Get the latest from SVN.


Result is: no (in libavcodec: no)
##########################################

============ Checking for libdirac ============

#include <libdirac_encoder/dirac_encoder.h>
#include <libdirac_decoder/dirac_parser.h>
int main(void)
{
    dirac_encoder_context_t enc_ctx;
    dirac_decoder_t *dec_handle;
    dirac_encoder_context_init(&enc_ctx, VIDEO_FORMAT_SD_576I50);
    dec_handle = dirac_decoder_init(0);
    if (dec_handle)
        dirac_decoder_close(dec_handle);
    return 0;
}

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -I/usr/include/dirac -ldirac_encoder -ldirac_decoder
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:7: error: 'VIDEO_FORMAT_SD_576I50' undeclared (first use in this function)
/tmp/mplayer-conf--28003.c:7: error: (Each undeclared identifier is reported only once
/tmp/mplayer-conf--28003.c:7: error: for each function it appears in.)


Result is: no 
##########################################

============ Checking for libschroedinger ============
Result is: no 
##########################################

============ Checking for libnut ============

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>
#include <libnut.h>
int main(void) { (void)nut_error(0); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lnut
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:4:20: error: libnut.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:5: warning: implicit declaration of function 'nut_error'


Result is: no 
##########################################

============ Checking for zr ============
Result is: no 
##########################################

============ Checking for libmp3lame ============

#include <lame/lame.h>
int main(void) { lame_version_t lv; (void) lame_init();
    get_lame_version_numerical(&lv);  printf("%d%d\n",lv.major,lv.minor);
    return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lmp3lame -lm
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no (in libavcodec: no)
##########################################

============ Checking for mencoder ============
Result is: yes 
##########################################

============ Checking for UnRAR executable ============
Result is: yes 
##########################################

============ Checking for TV interface ============
Result is: yes 
##########################################

============ Checking for DirectShow TV interface ============
Result is: no 
##########################################

============ Checking for Video 4 Linux TV interface ============

#include <stdlib.h>
#include <linux/videodev.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for Video 4 Linux 2 TV interface ============

#include <stdlib.h>
#include <linux/types.h>
#include <linux/videodev2.h>
int main(void) { return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c
cc: /tmp/mplayer-conf--28003: No such file or directory


Result is: no 
##########################################

============ Checking for TV teletext interface ============
Result is: no 
##########################################

============ Checking for Radio interface ============
Result is: no 
##########################################

============ Checking for Capture for Radio interface ============
Result is: no 
##########################################

============ Checking for Video 4 Linux 2 Radio interface ============
Result is: no 
##########################################

============ Checking for Video 4 Linux Radio interface ============
Result is: no 
##########################################

============ Checking for Video 4 Linux 2 MPEG PVR interface ============
Result is: no 
##########################################

============ Checking for ftp ============
Result is: yes 
##########################################

============ Checking for vstream client ============

#include <vstream-client.h>
void vstream_error(const char *format, ... ) {}
int main(void) { vstream_start(); return 0; }

cc -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=x86-64 -mtune=generic -pipe -ffast-math -fomit-frame-pointer -I.  -I/usr/include/directfb    -lncurses  -ldirectfb  -lXext -lX11 -lpthread -lXvMC -l  -o /tmp/mplayer-conf--28003 /tmp/mplayer-conf--28003.c -lvstream-client
cc: /tmp/mplayer-conf--28003: No such file or directory
/tmp/mplayer-conf--28003.c:1:28: error: vstream-client.h: No such file or directory
/tmp/mplayer-conf--28003.c: In function 'main':
/tmp/mplayer-conf--28003.c:3: warning: implicit declaration of function 'vstream_start'


Result is: no 
##########################################

============ Checking for OSD menu ============
Result is: yes 
##########################################

============ Checking for Subtitles sorting ============
Result is: yes 
##########################################

============ Checking for XMMS inputplugin support ============
Result is: no 
##########################################

============ Checking for GUI ============
```

I'm not sure about the cause of this problem, but i guess that the configure script is unable to find the right header files. And when i try to locate these header files i find them where they should be??!!

Could someone please help

regards

---

### Post by FakeOutdoorsman on 2009-01-21
I recommend taking a look at:

[[Howto] Install the svn Mplayer under Intrepid Ibex](http://ubuntuforums.org/showthread.php?t=1024592)

The author knows his stuff if you have any questions.

---

### Post by TheOne...more on 2009-01-22
Thanx FakeOutdoorsman, i red the guide and made all the steps he told about but the error is still persisting.

I'm running gutsy not Intrepid, but i thought i should give it a try first then post back.

Any help please??

---

### Post by TheOne...more on 2009-01-22
Any help please??

---

### Post by andrew.46 on 2009-01-22
Hi TheOne....

> **TheOne...more said:**
> Any help please??

There is a slightly older version of that MPlayer guide with a list of the appropriate dev files for Gutsy Gibbon:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

One small error your are making is with your configure options. Can I suggest you try simply:

```
./configure --enable-gui
```

MPlayer is a little different to other programs and usually does not require any '-enable-xxx' options, in fact this is actively discouraged and unless you are also prepared to give the paths to the various headers compilation will mostly fail.

All the best,

Andrew

---

### Post by TheOne...more on 2009-01-23
hi,

Sorry for being silent for so long...

Thanks andrew.46 for your post, some amazing guides you have.=D>

Thank you for the post, and thank you for the guides.

I waited that long before replying because i wanted to test and make perfect what you indicated in your guide.

Actually when i opened the first page, what i did was just take the code from the code block listing those too many packages for gutsy and pasted it in a terminal. It installed some 50 packages, and upgraded five, here is the code

```
root@VacuumMachine:/storage# apt-get install avifile-divx-plugin avifile-xvid-plugin gawk libxcursor-dev ladspa-sdk liba52-0.7.4 liba52-0.7.4-dev libaa1-dev libartsc0 libartsc0-dev libasound2-dev libatk1.0-dev libaudiofile-dev libavcodec1d libavcodec-dev libavformat1d libavformat-dev libavifile-0.7c2 libavifile-0.7-dev libavutil1d libavutil-dev libcaca-dev libcairo2-dev libcdparanoia0-dev libcucul-dev libdv4-dev libdirectfb-dev libdirectfb-extra libdbus-1-dev libdbus-glib-1-dev libdc1394-13 libdc1394-13-dev libdfb++-0.9-25 libdfb++-dev libdts-dev libdvdnav4 libdvdnav-dev libdvdread3 libdvdread-dev libebml0 libebml-dev libenca0 libenca-dev libesd0-dev libexpat1-dev libfaac0 libfaac-dev libfaad2-0 libfaad2-dev libfame-0.9 libfame-dev libflac++6 libflac-dev libflac++-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev libfribidi-dev libgdk-pixbuf2 libgdk-pixbuf-dev libgii1 libgii1-dev libgii1-target-x libgl1-mesa-dev libglib1.2 libglib1.2-dev libglib2.0-dev libglu1-mesa-dev libglu1-xorg-dev libgsm1 libgsm1-dev libgtk1.2 libgtk1.2-common libgtk1.2-dev libgtk2.0-dev libice-dev libggi2 libggi2-dev libggimisc2 libggimisc2-dev libggiwmh0 libggiwmh0-dev libjpeg62-dev liblame0 liblame-dev liblivemedia-dev liblzo1 liblzo-dev liblzo2-2 liblzo2-dev libmad0 libmad0-dev libmatroska0 libmatroska-dev libmikmod2 libmikmod2-dev libmp4v2-0 libmp4v2-dev libmpcdec3 libmpcdec-dev libncurses5-dev libogg-dev libpango1.0-dev libpng12-dev libpopt-dev libpostproc1d libpostproc-dev libraw1394-dev libsdl1.2-dev libslang2-dev libsmbclient-dev libsm-dev libspeex-dev libsvga1 libsvga1-dev libsysfs-dev libtheora-dev libungif4-dev libungif4g libvorbis-dev libx11-dev  libxau-dev libxcomposite-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxsharp-dev libxv-dev libxvidcore4 libxvidcore4-dev libxvmc1 libxvmc-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev pnet-interpreter sharutils toolame ttf-bitstream-vera x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xlibs-static-dev xtrans-dev zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxcursor-dev is already the newest version.
libxcursor-dev set to manual installed.
liba52-0.7.4 is already the newest version.
liba52-0.7.4-dev is already the newest version.
libartsc0 is already the newest version.
libartsc0 set to manual installed.
libasound2-dev is already the newest version.
libatk1.0-dev is already the newest version.
libatk1.0-dev set to manual installed.
libavcodec1d is already the newest version.
libavcodec-dev is already the newest version.
libavformat1d is already the newest version.
libavformat1d set to manual installed.
libavformat-dev is already the newest version.
libavutil1d is already the newest version.
libavutil-dev is already the newest version.
libavutil-dev set to manual installed.
libcairo2-dev is already the newest version.
libcairo2-dev set to manual installed.
libcdparanoia0-dev is already the newest version.
libdv4-dev is already the newest version.
libdirectfb-dev is already the newest version.
libdirectfb-extra is already the newest version.
libdirectfb-extra set to manual installed.
libdbus-1-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libdc1394-13 is already the newest version.
libdc1394-13 set to manual installed.
libdc1394-13-dev is already the newest version.
libdc1394-13-dev set to manual installed.
libdts-dev is already the newest version.
libdvdnav4 is already the newest version.
libdvdnav4 set to manual installed.
libdvdnav-dev is already the newest version.
libdvdread3 is already the newest version.
libdvdread-dev is already the newest version.
libebml0 is already the newest version.
libebml0 set to manual installed.
libenca0 is already the newest version.
libenca0 set to manual installed.
libenca-dev is already the newest version.
libexpat1-dev is already the newest version.
libexpat1-dev set to manual installed.
libfaac0 is already the newest version.
libfaac-dev is already the newest version.
libfaad2-0 is already the newest version.
libfaad2-dev is already the newest version.
libfontconfig1-dev is already the newest version.
libfontconfig1-dev set to manual installed.
libfribidi-dev is already the newest version.
libgdk-pixbuf2 is already the newest version.
libgdk-pixbuf2 set to manual installed.
libgii1 is already the newest version.
libgii1 set to manual installed.
libgii1-target-x is already the newest version.
libgii1-target-x set to manual installed.
libgl1-mesa-dev is already the newest version.
libgl1-mesa-dev set to manual installed.
libglib1.2 is already the newest version.
libglib1.2 set to manual installed.
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manual installed.
libglu1-mesa-dev is already the newest version.
libgsm1 is already the newest version.
libgsm1-dev is already the newest version.
libgsm1-dev set to manual installed.
libgtk1.2 is already the newest version.
libgtk1.2 set to manual installed.
libgtk1.2-common is already the newest version.
libgtk1.2-common set to manual installed.
libgtk2.0-dev is already the newest version.
libice-dev is already the newest version.
libice-dev set to manual installed.
libggi2 is already the newest version.
libggi2 set to manual installed.
libjpeg62-dev is already the newest version.
liblame0 is already the newest version.
liblame-dev is already the newest version.
liblzo1 is already the newest version.
liblzo1 set to manual installed.
liblzo2-2 is already the newest version.
liblzo2-dev is already the newest version.
libmad0 is already the newest version.
libmad0-dev is already the newest version.
libmatroska0 is already the newest version.
libmatroska0 set to manual installed.
libmikmod2 is already the newest version.
libmikmod2 set to manual installed.
libmp4v2-0 is already the newest version.
libmp4v2-dev is already the newest version.
libmp4v2-dev set to manual installed.
libmpcdec3 is already the newest version.
libmpcdec-dev is already the newest version.
libncurses5-dev is already the newest version.
libncurses5-dev set to manual installed.
libogg-dev is already the newest version.
libogg-dev set to manual installed.
libpango1.0-dev is already the newest version.
libpango1.0-dev set to manual installed.
libpng12-dev is already the newest version.
libpng12-dev set to manual installed.
libpopt-dev is already the newest version.
libpopt-dev set to manual installed.
libpostproc1d is already the newest version.
libpostproc1d set to manual installed.
libpostproc-dev is already the newest version.
libraw1394-dev is already the newest version.
libraw1394-dev set to manual installed.
libsdl1.2-dev is already the newest version.
libsdl1.2-dev set to manual installed.
libsm-dev is already the newest version.
libsm-dev set to manual installed.
libspeex-dev is already the newest version.
libsysfs-dev is already the newest version.
libsysfs-dev set to manual installed.
libtheora-dev is already the newest version.
libtheora-dev set to manual installed.
libungif4g is already the newest version.
libungif4g set to manual installed.
libvorbis-dev is already the newest version.
libx11-dev is already the newest version.
libx11-dev set to manual installed.
libxau-dev is already the newest version.
libxau-dev set to manual installed.
libxcomposite-dev is already the newest version.
libxcomposite-dev set to manual installed.
libxdamage-dev is already the newest version.
libxdamage-dev set to manual installed.
libxdmcp-dev is already the newest version.
libxdmcp-dev set to manual installed.
libxext-dev is already the newest version.
libxext-dev set to manual installed.
libxfixes-dev is already the newest version.
libxfixes-dev set to manual installed.
libxft-dev is already the newest version.
libxft-dev set to manual installed.
libxi-dev is already the newest version.
libxi-dev set to manual installed.
libxinerama-dev is already the newest version.
libxinerama-dev set to manual installed.
libxrandr-dev is already the newest version.
libxrandr-dev set to manual installed.
libxrender-dev is already the newest version.
libxrender-dev set to manual installed.
libxvidcore4 is already the newest version.
libxvidcore4-dev is already the newest version.
libxvmc1 is already the newest version.
libxvmc1 set to manual installed.
mesa-common-dev is already the newest version.
ttf-bitstream-vera is already the newest version.
x11proto-composite-dev is already the newest version.
x11proto-composite-dev set to manual installed.
x11proto-core-dev is already the newest version.
x11proto-core-dev set to manual installed.
x11proto-damage-dev is already the newest version.
x11proto-damage-dev set to manual installed.
x11proto-fixes-dev is already the newest version.
x11proto-fixes-dev set to manual installed.
x11proto-input-dev is already the newest version.
x11proto-input-dev set to manual installed.
x11proto-kb-dev is already the newest version.
x11proto-kb-dev set to manual installed.
x11proto-randr-dev is already the newest version.
x11proto-randr-dev set to manual installed.
x11proto-render-dev is already the newest version.
x11proto-render-dev set to manual installed.
x11proto-xext-dev is already the newest version.
x11proto-xext-dev set to manual installed.
x11proto-xinerama-dev is already the newest version.
x11proto-xinerama-dev set to manual installed.
xtrans-dev is already the newest version.
xtrans-dev set to manual installed.
zlib1g-dev is already the newest version.
The following extra packages will be installed:
  esound-common libesd-alsa0 libfreetype6 libsmbclient
Suggested packages:
  avifile-player avifile-utils avifile-mad-plugin avifile-mjpeg-plugin
  avifile-vorbis-plugin avifile-win32-plugin esound libgtk1.2-doc mailx
Recommended packages:
  esound-clients libggiwmh0-target-x pnetc pnet-assemblies
The following NEW packages will be installed:
  avifile-divx-plugin avifile-xvid-plugin gawk ladspa-sdk libaa1-dev
  libartsc0-dev libaudiofile-dev libavifile-0.7-dev libavifile-0.7c2
  libcaca-dev libcucul-dev libdfb++-0.9-25 libdfb++-dev libebml-dev
  libesd0-dev libfame-0.9 libfame-dev libflac++-dev libflac++6 libflac-dev
  libfontenc-dev libgdk-pixbuf-dev libggi2-dev libggimisc2 libggimisc2-dev
  libggiwmh0 libggiwmh0-dev libgii1-dev libglib1.2-dev libglu1-xorg-dev
  libgtk1.2-dev liblivemedia-dev liblzo-dev libmatroska-dev libmikmod2-dev
  libslang2-dev libsmbclient-dev libsvga1 libsvga1-dev libungif4-dev
  libxfont-dev libxsharp-dev libxv-dev libxvmc-dev libxxf86dga-dev
  libxxf86vm-dev pnet-interpreter sharutils toolame x11proto-fonts-dev
  x11proto-video-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev
  xlibs-static-dev
The following packages will be upgraded:
  esound-common libesd-alsa0 libfreetype6 libfreetype6-dev libsmbclient
5 upgraded, 54 newly installed, 0 to remove and 128 not upgraded.
Need to get 14.3MB of archives.
After unpacking 47.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main gawk 1:3.1.5.dfsg-4ubuntu1 [512kB]
Get:2 http://archive.ubuntu.com gutsy/main libfontenc-dev 1:1.0.4-2 [21.5kB]   
Get:3 http://archive.ubuntu.com gutsy/universe libglib1.2-dev 1.2.10-17build1 [196kB]
Get:4 http://archive.ubuntu.com gutsy/universe libgtk1.2-dev 1.2.10-18 [1301kB]
Get:5 http://archive.ubuntu.com gutsy/main x11proto-fonts-dev 2.0.2-5ubuntu1 [12.2kB]
Get:6 http://archive.ubuntu.com gutsy-updates/main libfreetype6-dev 2.3.5-1ubuntu4.7.10.1 [696kB]
Get:7 http://archive.ubuntu.com gutsy-updates/main libfreetype6 2.3.5-1ubuntu4.7.10.1 [364kB]
Get:8 http://archive.ubuntu.com gutsy-updates/main libxfont-dev 1:1.3.0-0ubuntu1.1 [284kB]
Get:9 http://archive.ubuntu.com gutsy/main x11proto-video-dev 2.2.2-4ubuntu1 [9838B]
Get:10 http://archive.ubuntu.com gutsy/main libxv-dev 2:1.0.3-1ubuntu1 [37.3kB]
Get:11 http://archive.ubuntu.com gutsy/main libxvmc-dev 2:1.0.4-2ubuntu1 [20.4kB]
Get:12 http://archive.ubuntu.com gutsy/main x11proto-xf86dga-dev 2.0.2-4ubuntu1 [7338B]
Get:13 http://archive.ubuntu.com gutsy/main libxxf86dga-dev 2:1.0.1-2 [18.0kB] 
Get:14 http://archive.ubuntu.com gutsy/main x11proto-xf86vidmode-dev 2.2.2-4ubuntu1 [6596B]
Get:15 http://archive.ubuntu.com gutsy/main libxxf86vm-dev 1:1.0.1-2 [15.1kB]  
Get:16 http://archive.ubuntu.com gutsy/universe libavifile-0.7c2 1:0.7.47.20070718-1ubuntu2 [2216kB]
Get:17 http://archive.ubuntu.com gutsy/multiverse avifile-divx-plugin 1:0.7.47.20070718-1ubuntu2 [1024B]
Get:18 http://archive.ubuntu.com gutsy/multiverse avifile-xvid-plugin 1:0.7.47.20070718-1ubuntu2 [972B]
Get:19 http://archive.ubuntu.com gutsy-updates/main esound-common 0.2.38-0ubuntu4.1 [42.3kB]
Get:20 http://archive.ubuntu.com gutsy/universe ladspa-sdk 1.1-6 [41.2kB]      
Get:21 http://archive.ubuntu.com gutsy/main libslang2-dev 2.0.7-2 [517kB]      
Get:22 http://archive.ubuntu.com gutsy/main libaa1-dev 1.4p5-32 [146kB]        
Get:23 http://archive.ubuntu.com gutsy/main libartsc0-dev 1.5.8-0ubuntu1 [22.6kB]
Get:24 http://archive.ubuntu.com gutsy/main libaudiofile-dev 0.2.6-6ubuntu3 [129kB]
Get:25 http://archive.ubuntu.com gutsy/universe libavifile-0.7-dev 1:0.7.47.20070718-1ubuntu2 [49.5kB]
Get:26 http://archive.ubuntu.com gutsy/main libcucul-dev 0.99.beta11.debian-3 [327kB]
Get:27 http://archive.ubuntu.com gutsy/main libcaca-dev 0.99.beta11.debian-3 [93.9kB]
Get:28 http://archive.ubuntu.com gutsy/universe libdfb++-0.9-25 0.9.25-2 [36.5kB]
Get:29 http://archive.ubuntu.com gutsy/universe libdfb++-dev 0.9.25-2 [51.5kB] 
Get:30 http://archive.ubuntu.com gutsy/universe libebml-dev 0.7.7-3 [101kB]    
Get:31 http://archive.ubuntu.com gutsy-updates/main libesd-alsa0 0.2.38-0ubuntu4.1 [24.0kB]
Get:32 http://archive.ubuntu.com gutsy-updates/main libesd0-dev 0.2.38-0ubuntu4.1 [25.4kB]
Get:33 http://archive.ubuntu.com gutsy/multiverse libfame-0.9 0.9.1-0.2 [134kB]
Get:34 http://archive.ubuntu.com gutsy/multiverse libfame-dev 0.9.1-0.2 [163kB]
Get:35 http://archive.ubuntu.com gutsy-updates/main libflac-dev 1.1.4-3ubuntu1.1 [219kB]
Get:36 http://archive.ubuntu.com gutsy-updates/main libflac++6 1.1.4-3ubuntu1.1 [38.8kB]
Get:37 http://archive.ubuntu.com gutsy-updates/main libflac++-dev 1.1.4-3ubuntu1.1 [49.4kB]
Get:38 http://archive.ubuntu.com gutsy/universe libgdk-pixbuf-dev 0.22.0-11 [157kB]
Get:39 http://archive.ubuntu.com gutsy/universe libgii1-dev 1:1.0.1-3 [206kB]  
Get:40 http://archive.ubuntu.com gutsy/universe libggi2-dev 1:2.2.1-5ubuntu1 [101kB]
Get:41 http://archive.ubuntu.com gutsy/universe libggimisc2 2.2.1-2 [33.6kB]   
Get:42 http://archive.ubuntu.com gutsy/universe libggimisc2-dev 2.2.1-2 [13.1kB]
Get:43 http://archive.ubuntu.com gutsy/universe libggiwmh0 0.3.1-2 [25.5kB]    
Get:44 http://archive.ubuntu.com gutsy/universe libggiwmh0-dev 0.3.1-2 [17.9kB]
Get:45 http://archive.ubuntu.com gutsy/main libglu1-xorg-dev 1:7.2-5ubuntu13 [958B]
Get:46 http://archive.ubuntu.com gutsy/universe liblivemedia-dev 2007.02.20-2 [963kB]
Get:47 http://archive.ubuntu.com gutsy/universe liblzo-dev 1.08-3 [109kB]      
Get:48 http://archive.ubuntu.com gutsy/universe libmatroska-dev 0.8.1-1 [348kB]
Get:49 http://archive.ubuntu.com gutsy/main libmikmod2-dev 3.1.11-a-6ubuntu3 [264kB]
Get:50 http://archive.ubuntu.com gutsy/universe libsvga1 1:1.4.3-24 [324kB]    
Get:51 http://archive.ubuntu.com gutsy/universe libsvga1-dev 1:1.4.3-24 [584kB]
Get:52 http://archive.ubuntu.com gutsy/main libungif4-dev 4.1.4-5 [43.7kB]     
Get:53 http://archive.ubuntu.com gutsy/universe pnet-interpreter 0.7.4-1build1 [594kB]
Get:54 http://archive.ubuntu.com gutsy/universe libxsharp-dev 0.7.4-1ubuntu1 [89.8kB]
Get:55 http://archive.ubuntu.com gutsy/main sharutils 1:4.6.3-1build1 [111kB]  
Get:56 http://archive.ubuntu.com gutsy/universe toolame 02l-6 [97.8kB]         
Get:57 http://archive.ubuntu.com gutsy/main xlibs-static-dev 1:7.2-5ubuntu13 [1094B]
Get:58 http://archive.ubuntu.com gutsy-updates/main libsmbclient 3.0.26a-1ubuntu2.5 [961kB]
Get:59 http://archive.ubuntu.com gutsy-updates/main libsmbclient-dev 3.0.26a-1ubuntu2.5 [1287kB]
Fetched 14.3MB in 10m25s (22.8kB/s)                                            
Extracting templates from packages: 100%
Selecting previously deselected package gawk.
(Reading database ... 158815 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.5.dfsg-4ubuntu1_amd64.deb) ...
Selecting previously deselected package libfontenc-dev.
Unpacking libfontenc-dev (from .../libfontenc-dev_1%3a1.0.4-2_amd64.deb) ...
Selecting previously deselected package libglib1.2-dev.
Unpacking libglib1.2-dev (from .../libglib1.2-dev_1.2.10-17build1_amd64.deb) ...
Selecting previously deselected package libgtk1.2-dev.
Unpacking libgtk1.2-dev (from .../libgtk1.2-dev_1.2.10-18_amd64.deb) ...
Selecting previously deselected package x11proto-fonts-dev.
Unpacking x11proto-fonts-dev (from .../x11proto-fonts-dev_2.0.2-5ubuntu1_all.deb) ...
Preparing to replace libfreetype6-dev 2.3.5-1ubuntu4 (using .../libfreetype6-dev_2.3.5-1ubuntu4.7.10.1_amd64.deb) ...
Unpacking replacement libfreetype6-dev ...
Preparing to replace libfreetype6 2.3.5-1ubuntu4 (using .../libfreetype6_2.3.5-1ubuntu4.7.10.1_amd64.deb) ...
Unpacking replacement libfreetype6 ...
Selecting previously deselected package libxfont-dev.
Unpacking libxfont-dev (from .../libxfont-dev_1%3a1.3.0-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package x11proto-video-dev.
Unpacking x11proto-video-dev (from .../x11proto-video-dev_2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxv-dev.
Unpacking libxv-dev (from .../libxv-dev_2%3a1.0.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libxvmc-dev.
Unpacking libxvmc-dev (from .../libxvmc-dev_2%3a1.0.4-2ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-xf86dga-dev.
Unpacking x11proto-xf86dga-dev (from .../x11proto-xf86dga-dev_2.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86dga-dev.
Unpacking libxxf86dga-dev (from .../libxxf86dga-dev_2%3a1.0.1-2_amd64.deb) ...
Selecting previously deselected package x11proto-xf86vidmode-dev.
Unpacking x11proto-xf86vidmode-dev (from .../x11proto-xf86vidmode-dev_2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86vm-dev.
Unpacking libxxf86vm-dev (from .../libxxf86vm-dev_1%3a1.0.1-2_amd64.deb) ...
Selecting previously deselected package libavifile-0.7c2.
Unpacking libavifile-0.7c2 (from .../libavifile-0.7c2_1%3a0.7.47.20070718-1ubuntu2_amd64.deb) ...
Selecting previously deselected package avifile-divx-plugin.
Unpacking avifile-divx-plugin (from .../avifile-divx-plugin_1%3a0.7.47.20070718-1ubuntu2_amd64.deb) ...
Selecting previously deselected package avifile-xvid-plugin.
Unpacking avifile-xvid-plugin (from .../avifile-xvid-plugin_1%3a0.7.47.20070718-1ubuntu2_amd64.deb) ...
Preparing to replace esound-common 0.2.38-0ubuntu4 (using .../esound-common_0.2.38-0ubuntu4.1_all.deb) ...
Unpacking replacement esound-common ...
Selecting previously deselected package ladspa-sdk.
Unpacking ladspa-sdk (from .../ladspa-sdk_1.1-6_amd64.deb) ...
Selecting previously deselected package libslang2-dev.
Unpacking libslang2-dev (from .../libslang2-dev_2.0.7-2_amd64.deb) ...
Selecting previously deselected package libaa1-dev.
Unpacking libaa1-dev (from .../libaa1-dev_1.4p5-32_amd64.deb) ...
Selecting previously deselected package libartsc0-dev.
Unpacking libartsc0-dev (from .../libartsc0-dev_1.5.8-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libaudiofile-dev.
Unpacking libaudiofile-dev (from .../libaudiofile-dev_0.2.6-6ubuntu3_amd64.deb) ...
Selecting previously deselected package libavifile-0.7-dev.
Unpacking libavifile-0.7-dev (from .../libavifile-0.7-dev_1%3a0.7.47.20070718-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libcucul-dev.
Unpacking libcucul-dev (from .../libcucul-dev_0.99.beta11.debian-3_amd64.deb) ...
Selecting previously deselected package libcaca-dev.
Unpacking libcaca-dev (from .../libcaca-dev_0.99.beta11.debian-3_amd64.deb) ...
Selecting previously deselected package libdfb++-0.9-25.
Unpacking libdfb++-0.9-25 (from .../libdfb++-0.9-25_0.9.25-2_amd64.deb) ...
Selecting previously deselected package libdfb++-dev.
Unpacking libdfb++-dev (from .../libdfb++-dev_0.9.25-2_amd64.deb) ...
Selecting previously deselected package libebml-dev.
Unpacking libebml-dev (from .../libebml-dev_0.7.7-3_amd64.deb) ...
Preparing to replace libesd-alsa0 0.2.38-0ubuntu4 (using .../libesd-alsa0_0.2.38-0ubuntu4.1_amd64.deb) ...
Unpacking replacement libesd-alsa0 ...
Selecting previously deselected package libesd0-dev.
Unpacking libesd0-dev (from .../libesd0-dev_0.2.38-0ubuntu4.1_amd64.deb) ...
Selecting previously deselected package libfame-0.9.
Unpacking libfame-0.9 (from .../libfame-0.9_0.9.1-0.2_amd64.deb) ...
Selecting previously deselected package libfame-dev.
Unpacking libfame-dev (from .../libfame-dev_0.9.1-0.2_amd64.deb) ...
Selecting previously deselected package libflac-dev.
Unpacking libflac-dev (from .../libflac-dev_1.1.4-3ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libflac++6.
Unpacking libflac++6 (from .../libflac++6_1.1.4-3ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libflac++-dev.
Unpacking libflac++-dev (from .../libflac++-dev_1.1.4-3ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libgdk-pixbuf-dev.
Unpacking libgdk-pixbuf-dev (from .../libgdk-pixbuf-dev_0.22.0-11_amd64.deb) ...
Selecting previously deselected package libgii1-dev.
Unpacking libgii1-dev (from .../libgii1-dev_1%3a1.0.1-3_amd64.deb) ...
Selecting previously deselected package libggi2-dev.
Unpacking libggi2-dev (from .../libggi2-dev_1%3a2.2.1-5ubuntu1_amd64.deb) ...
Selecting previously deselected package libggimisc2.
Unpacking libggimisc2 (from .../libggimisc2_2.2.1-2_amd64.deb) ...
Selecting previously deselected package libggimisc2-dev.
Unpacking libggimisc2-dev (from .../libggimisc2-dev_2.2.1-2_amd64.deb) ...
Selecting previously deselected package libggiwmh0.
Unpacking libggiwmh0 (from .../libggiwmh0_0.3.1-2_amd64.deb) ...
Selecting previously deselected package libggiwmh0-dev.
Unpacking libggiwmh0-dev (from .../libggiwmh0-dev_0.3.1-2_amd64.deb) ...
Selecting previously deselected package libglu1-xorg-dev.
Unpacking libglu1-xorg-dev (from .../libglu1-xorg-dev_1%3a7.2-5ubuntu13_all.deb) ...
Selecting previously deselected package liblivemedia-dev.
Unpacking liblivemedia-dev (from .../liblivemedia-dev_2007.02.20-2_amd64.deb) ...
Selecting previously deselected package liblzo-dev.
Unpacking liblzo-dev (from .../liblzo-dev_1.08-3_amd64.deb) ...
Replaced by files in installed package liblzo2-dev ...
Selecting previously deselected package libmatroska-dev.
Unpacking libmatroska-dev (from .../libmatroska-dev_0.8.1-1_amd64.deb) ...
Selecting previously deselected package libmikmod2-dev.
Unpacking libmikmod2-dev (from .../libmikmod2-dev_3.1.11-a-6ubuntu3_amd64.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-24_amd64.deb) ...
Selecting previously deselected package libsvga1-dev.
Unpacking libsvga1-dev (from .../libsvga1-dev_1%3a1.4.3-24_amd64.deb) ...
Selecting previously deselected package libungif4-dev.
Unpacking libungif4-dev (from .../libungif4-dev_4.1.4-5_amd64.deb) ...
Selecting previously deselected package pnet-interpreter.
Unpacking pnet-interpreter (from .../pnet-interpreter_0.7.4-1build1_amd64.deb) ...
Selecting previously deselected package libxsharp-dev.
Unpacking libxsharp-dev (from .../libxsharp-dev_0.7.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package sharutils.
Unpacking sharutils (from .../sharutils_1%3a4.6.3-1build1_amd64.deb) ...
Selecting previously deselected package toolame.
Unpacking toolame (from .../toolame_02l-6_amd64.deb) ...
Selecting previously deselected package xlibs-static-dev.
Unpacking xlibs-static-dev (from .../xlibs-static-dev_1%3a7.2-5ubuntu13_all.deb) ...
Preparing to replace libsmbclient 3.0.26a-1ubuntu2.3 (using .../libsmbclient_3.0.26a-1ubuntu2.5_amd64.deb) ...
Unpacking replacement libsmbclient ...
Selecting previously deselected package libsmbclient-dev.
Unpacking libsmbclient-dev (from .../libsmbclient-dev_3.0.26a-1ubuntu2.5_amd64.deb) ...
Setting up gawk (1:3.1.5.dfsg-4ubuntu1) ...

Setting up libfontenc-dev (1:1.0.4-2) ...
Setting up libglib1.2-dev (1.2.10-17build1) ...

Setting up libgtk1.2-dev (1.2.10-18) ...
Setting up x11proto-fonts-dev (2.0.2-5ubuntu1) ...
Setting up libfreetype6 (2.3.5-1ubuntu4.7.10.1) ...

Setting up libfreetype6-dev (2.3.5-1ubuntu4.7.10.1) ...

Setting up libxfont-dev (1:1.3.0-0ubuntu1.1) ...
Setting up x11proto-video-dev (2.2.2-4ubuntu1) ...
Setting up libxv-dev (2:1.0.3-1ubuntu1) ...
Setting up libxvmc-dev (2:1.0.4-2ubuntu1) ...
Setting up x11proto-xf86dga-dev (2.0.2-4ubuntu1) ...
Setting up libxxf86dga-dev (2:1.0.1-2) ...
Setting up x11proto-xf86vidmode-dev (2.2.2-4ubuntu1) ...
Setting up libxxf86vm-dev (1:1.0.1-2) ...
Setting up libavifile-0.7c2 (1:0.7.47.20070718-1ubuntu2) ...

Setting up avifile-divx-plugin (1:0.7.47.20070718-1ubuntu2) ...
Setting up avifile-xvid-plugin (1:0.7.47.20070718-1ubuntu2) ...
Setting up esound-common (0.2.38-0ubuntu4.1) ...
Setting up ladspa-sdk (1.1-6) ...

Setting up libslang2-dev (2.0.7-2) ...
Setting up libaa1-dev (1.4p5-32) ...

Setting up libartsc0-dev (1.5.8-0ubuntu1) ...
Setting up libaudiofile-dev (0.2.6-6ubuntu3) ...
Setting up libavifile-0.7-dev (1:0.7.47.20070718-1ubuntu2) ...
Setting up libcucul-dev (0.99.beta11.debian-3) ...
Setting up libcaca-dev (0.99.beta11.debian-3) ...
Setting up libdfb++-0.9-25 (0.9.25-2) ...

Setting up libdfb++-dev (0.9.25-2) ...
Setting up libebml-dev (0.7.7-3) ...
Setting up libfame-0.9 (0.9.1-0.2) ...

Setting up libfame-dev (0.9.1-0.2) ...
Setting up libflac-dev (1.1.4-3ubuntu1.1) ...
Setting up libflac++6 (1.1.4-3ubuntu1.1) ...

Setting up libflac++-dev (1.1.4-3ubuntu1.1) ...
Setting up libgdk-pixbuf-dev (0.22.0-11) ...
Setting up libgii1-dev (1:1.0.1-3) ...

Setting up libggi2-dev (1:2.2.1-5ubuntu1) ...
Setting up libggimisc2 (2.2.1-2) ...

Setting up libggimisc2-dev (2.2.1-2) ...

Setting up libggiwmh0 (0.3.1-2) ...

Setting up libggiwmh0-dev (0.3.1-2) ...
Setting up libglu1-xorg-dev (1:7.2-5ubuntu13) ...
Setting up liblivemedia-dev (2007.02.20-2) ...
Setting up liblzo-dev (1.08-3) ...
Setting up libmatroska-dev (0.8.1-1) ...
Setting up libmikmod2-dev (3.1.11-a-6ubuntu3) ...

Setting up libsvga1 (1:1.4.3-24) ...

Setting up libsvga1-dev (1:1.4.3-24) ...
Setting up libungif4-dev (4.1.4-5) ...
Setting up pnet-interpreter (0.7.4-1build1) ...

Setting up libxsharp-dev (0.7.4-1ubuntu1) ...
Setting up sharutils (1:4.6.3-1build1) ...

Setting up toolame (02l-6) ...
Setting up xlibs-static-dev (1:7.2-5ubuntu13) ...
Setting up libsmbclient (3.0.26a-1ubuntu2.5) ...

Setting up libsmbclient-dev (3.0.26a-1ubuntu2.5) ...
Setting up libesd-alsa0 (0.2.38-0ubuntu4.1) ...

Setting up libesd0-dev (0.2.38-0ubuntu4.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

What was really standing in the way was the --enable-gui option in the configure script, and one of these packages made some magic.

After i installed the packages, the ./configure && make worked fine. But after that was still mplayer didn't recognize many headers from packages i installed before. For instance the notorious libdvdnav and libdvdread packages, so i managed to get thier sources and compile, package then dpkg -i them. Actually i found my self doing this with some teen packages-i'm so tired to count.

That really made me wonder, isn't there a guide on how to know the prerequisites for compiling/installing a package to aid those who like to install latest software in manageable way?

I mean how did you identify the packages necessary for gutsy to be able to compile mplayer on it, i really wish to know.

I'm asking about this because i had some experience with cdrtools, when you  make install them they cannot be make uninstalled.

Well now the mplayer is working very fine, actually the dvd menus are working and i can navigate through them. But there is a quirk or two, the first is that once you choose an item the playing continues sequentially rather than going back to the menu, i tried that on "The power of nightmares" dvd. The other quirk is that, i use the number pad to navigate the menu items but the navigation is vertical -only up and down- this wasn't good for other dvds, if i was wrong please tell.

This page [http://www.nepherte.be/howto-enable-dvd-menus-in-mplayer](http://www.nepherte.be/howto-enable-dvd-menus-in-mplayer) helped me make the menus work, i think i read about the same steps somewhere else but i can't remember.

Now i'm trying to check on the gui stuff, and i would like to know if there was a way to experiment with different guis and skins before/without installation. I spent some time on this, and i want be as organized as possible, do you have any suggestions?

bye for now...

best wishes.

---

### Post by andrew.46 on 2009-01-23
Hi,

> **TheOne...more said:**
>  But after that was still mplayer didn't recognize many headers from packages i installed before. For instance the notorious libdvdnav and libdvdread packages, so i managed to get thier sources and compile, package then dpkg -i them. Actually i found my self doing this with some teen packages-i'm so tired to count.

Great news that it is all working for you! As regards libdvdnav and libdvdread if you are using the latest svn there is no longer any need to compile these individually as the svn MPlayer now draws these in and will automatically compile them with no intervention required on your part. This change is only a few weeks old now.

> That really made me wonder, isn't there a guide on how to know the prerequisites for compiling/installing a package to aid those who like to install latest software in manageable way?

I mean how did you identify the packages necessary for gutsy to be able to compile mplayer on it, i really wish to know.

Ubuntu / Debian do in fact make it a little difficult as the header files are separate from the main installation (the so-called -dev files). You can get some help with 'apt-get build-dep mplayer' but the rest is a slightly painful episode of trial and error :-).

> I'm asking about this because i had some experience with cdrtools, when you  make install them they cannot be make uninstalled.

Well actually you may find that the Ubuntu burning team has established a PPA that has the original cdrtools package [available for download]("https://launchpad.net/~ubuntu-burning/+archive").

> Well now the mplayer is working very fine, actually the dvd menus are working and i can navigate through them. But there is a quirk or two, the first is that once you choose an item the playing continues sequentially rather than going back to the menu, i tried that on "The power of nightmares" dvd. The other quirk is that, i use the number pad to navigate the menu items but the navigation is vertical -only up and down- this wasn't good for other dvds, if i was wrong please tell.

I will admit that I tend to use the mouse for the dvd menus. Try adding:

```
mouse-movements=yes
```

to your $HOME/.mplayer/config file. The dvd menus are not a complete work yet though so expect a few problems :-).

> Now i'm trying to check on the gui stuff, and i would like to know if there was a way to experiment with different guis and skins before/without installation. I spent some time on this, and i want be as organized as possible, do you have any suggestions?

The mplayer developers have pretty much abandoned the gui gmplayer and I will admit that I have as well in my own use. Have a look at smplayer and see if this is a better gui? Not sure if it is available for gutsy.

All the best,

Andrew

---

### Post by kingtiger01 on 2009-09-11
Congrats from my end too. 

i just compiled R:29671, :D. i was having some odd problems i thought to it not detecting the header's for alot of my sub apps(like X264), but then i realized, when checking the config.err and reading closely, it was failing on missing headers for things like smbclient. which was as simple as installing the devel packages for that and others.

copied in the newest Revision of ffmpeg from SVN and and she built easy as that!

---

