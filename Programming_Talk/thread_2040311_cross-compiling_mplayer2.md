---
title: "cross-compiling mplayer2"
date: 2012-08-10
forum: Programming Talk
---

### Post by active1 on 2012-08-10
hi, i'm trying to cross-compile mplayer2 for windows

i compiled all the dependencies, but i have this problem (when configure):
```
Unable to find iconv which should be part of standard compilation environment. Aborting. If you really mean to compile without iconv support use --disable-iconv.
```

(configured with: "./configure --enable-cross-compile --target=i586-mingw32msvc")

but libiconv is already compiled!

and this is the config.log:
```
Parameters configure was run with:
./configure --enable-cross-compile --target=i586-mingw32msvc

============ Checking for cross compilation ============
Result is: yes 
##########################################

============ Checking for i586-mingw32msvc-gcc version ============
Result is: 4.2.1-sjlj 
##########################################

============ Checking for working compiler ============

int main(void) { return 0; }

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


============ Checking for host cc ============
Result is: cc 
##########################################

============ Checking for CPU vendor ============
Result is: GenuineIntel (6:37:2) 
##########################################

============ Checking for CPU type ============
Result is:  Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz 
##########################################

============ Checking for kernel support of mmx ============

#include <stdlib.h>
#include <signal.h>
static void catch(int sig) { exit(1); }
int main(void) {
  signal(SIGILL, catch);
  __asm__ volatile ("emms":::"memory"); return 0;
}

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for kernel support of mmxext ============

#include <stdlib.h>
#include <signal.h>
static void catch(int sig) { exit(1); }
int main(void) {
  signal(SIGILL, catch);
  __asm__ volatile ("sfence":::"memory"); return 0;
}

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for kernel support of sse ============

#include <stdlib.h>
#include <signal.h>
static void catch(int sig) { exit(1); }
int main(void) {
  signal(SIGILL, catch);
  __asm__ volatile ("xorps %%xmm0, %%xmm0":::"memory"); return 0;
}

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for kernel support of sse2 ============

#include <stdlib.h>
#include <signal.h>
static void catch(int sig) { exit(1); }
int main(void) {
  signal(SIGILL, catch);
  __asm__ volatile ("xorpd %%xmm0, %%xmm0":::"memory"); return 0;
}

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for kernel support of ssse3 ============

#include <stdlib.h>
#include <signal.h>
static void catch(int sig) { exit(1); }
int main(void) {
  signal(SIGILL, catch);
  __asm__ volatile ("pabsd %%xmm0, %%xmm0":::"memory"); return 0;
}

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for kernel support of cmov ============

#include <stdlib.h>
#include <signal.h>
static void catch(int sig) { exit(1); }
int main(void) {
  signal(SIGILL, catch);
  __asm__ volatile ("cmovb %%eax,  %%ebx":::"memory"); return 0;
}

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for GCC & CPU optimization abilities ============

int main(void) { return 0; }

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe -march=native


Result is: i586 
##########################################

============ Checking for byte order ============

short ascii_name[] = {
  'M' << 8 | 'P', 'l' << 8 | 'a', 'y' << 8 | 'e', 'r' << 8 | 'B',
  'i' << 8 | 'g', 'E' << 8 | 'n', 'd' << 8 | 'i', 'a' << 8 | 'n', 0 };
int main(void) { return (long)ascii_name; }

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: little-endian 
##########################################

============ Checking for extern symbol prefix ============

int ff_extern;

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe -c
i586-mingw32msvc-gcc: -lwinmm: linker input file unused because linking not done


Result is: _ 
##########################################

============ Checking for assembler support of -pipe option ============

int main(void) { return 0; }

i586-mingw32msvc-gcc    /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm  -o /tmp/mplayer-configure--23026/tmp.exe -pipe -I.


Result is: yes 
##########################################


int main(void) { return 0; }

i586-mingw32msvc-gcc -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -Wundef



int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -std=gnu99



int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -Wno-pointer-sign



int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -Wdisabled-optimization



int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -Wmissing-prototypes



int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -Wstrict-prototypes



int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -mno-omit-leaf-frame-pointer



int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -MD -MP


============ Checking for assembler (/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/as ) ============
Result is: ok 
##########################################

============ Checking for PIC ============

int main(void) {
#if !(defined(__PIC__) || defined(__pic__) || defined(PIC))
#error PIC not enabled
#endif
    return 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:3:2: error: #error PIC not enabled


Result is: no 
##########################################

============ Checking for .align is a power of two ============

int main(void) { __asm__ volatile (".align 3"); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
{standard input}: Assembler messages:
{standard input}:15: Error: alignment not a power of 2


Result is: no 
##########################################

============ Checking for ebx availability ============

int main(void) {
    int x;
    __asm__ volatile(
        "xor %0, %0"
        :"=b"(x)
        // just adding ebx to clobber list seems unreliable with some
        // compilers, e.g. Haiku's gcc 2.95
    );
    // and the above check does not work for OSX 64 bit...
    __asm__ volatile("":::"%ebx");
    return 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for yasm ============

pabsw xmm0, xmm0

i586-mingw32msvc-yasm -f win32 -DPREFIX -o /tmp/mplayer-configure--23026/tmp.exe /tmp/mplayer-configure--23026/tmp.S 
./configure: 2486: i586-mingw32msvc-yasm: not found


Result is: no 
##########################################

============ Checking for bswap ============
Result is: yes 
##########################################

============ Checking for -lposix ============

int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lposix
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -lposix
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for -lm ============

int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lm


Result is: yes 
##########################################

============ Checking for langinfo ============

#include <langinfo.h>
int main(void) { nl_langinfo(CODESET); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:22: error: langinfo.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'nl_langinfo'
/tmp/mplayer-configure--23026/tmp.c:2: error: 'CODESET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:2: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:2: error: for each function it appears in.)


Result is: no 
##########################################

============ Checking for translation support ============
Result is: no 
##########################################

============ Checking for language ============
Result is: messages (en+):  - man pages: en - documentation: en 
##########################################

============ Checking for enable sighandler ============
Result is: yes 
##########################################

============ Checking for runtime cpudetection ============
Result is: no 
##########################################

============ Checking for restrict keyword ============

void foo(char * restrict p); int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: restrict 
##########################################

============ Checking for __builtin_expect ============

static int foo(int a) {
    a = __builtin_expect(a, 10);
    return a == 10 ? 0 : 1;
}
int main(void) { return foo(10) && foo(0); }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for kstat ============

#include <kstat.h>
int main(void) { kstat_open(); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lkstat
/tmp/mplayer-configure--23026/tmp.c:1:19: error: kstat.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'kstat_open'


Result is: no 
##########################################

============ Checking for posix4 ============

#include <time.h>
int main(void) { nanosleep(0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lposix4
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'nanosleep'
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -lposix4
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for exp2 ============

#include <math.h>
int main(void) { exp2(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for exp2f ============

#include <math.h>
int main(void) { exp2f(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for llrint ============

#include <math.h>
int main(void) { llrint(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for log2 ============

#include <math.h>
int main(void) { log2(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for log2f ============

#include <math.h>
int main(void) { log2f(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for lrint ============

#include <math.h>
int main(void) { lrint(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for lrintf ============

#include <math.h>
int main(void) { lrintf(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for round ============

#include <math.h>
int main(void) { round(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for roundf ============

#include <math.h>
int main(void) { roundf(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for truncf ============

#include <math.h>
int main(void) { truncf(2.0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -D_ISOC99_SOURCE -lm


Result is: yes 
##########################################

============ Checking for mkstemp ============

#define _XOPEN_SOURCE 600
#include <stdlib.h>
int main(void) { mkstemp(""); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'mkstemp'
/tmp/ccn8hh5Q.o:tmp.c:(.text+0x1c): undefined reference to `_mkstemp'
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for nanosleep ============

#include <time.h>
int main(void) { nanosleep(0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'nanosleep'
/tmp/ccHKs5vT.o:tmp.c:(.text+0x1a): undefined reference to `_nanosleep'
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for socklib ============

#include <netdb.h>
#include <sys/socket.h>
int main(void) { gethostbyname(0); socket(AF_INET, SOCK_STREAM, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:19: error: netdb.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c:2:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'gethostbyname'
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'socket'
/tmp/mplayer-configure--23026/tmp.c:3: error: 'AF_INET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:3: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:3: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:3: error: 'SOCK_STREAM' undeclared (first use in this function)



#include <netdb.h>
#include <sys/socket.h>
int main(void) { gethostbyname(0); socket(AF_INET, SOCK_STREAM, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lsocket -lbind
/tmp/mplayer-configure--23026/tmp.c:1:19: error: netdb.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c:2:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'gethostbyname'
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'socket'
/tmp/mplayer-configure--23026/tmp.c:3: error: 'AF_INET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:3: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:3: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:3: error: 'SOCK_STREAM' undeclared (first use in this function)



#include <netdb.h>
#include <sys/socket.h>
int main(void) { gethostbyname(0); socket(AF_INET, SOCK_STREAM, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lsocket -ldnet
/tmp/mplayer-configure--23026/tmp.c:1:19: error: netdb.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c:2:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'gethostbyname'
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'socket'
/tmp/mplayer-configure--23026/tmp.c:3: error: 'AF_INET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:3: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:3: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:3: error: 'SOCK_STREAM' undeclared (first use in this function)



#include <netdb.h>
#include <sys/socket.h>
int main(void) { gethostbyname(0); socket(AF_INET, SOCK_STREAM, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lsocket -lnsl
/tmp/mplayer-configure--23026/tmp.c:1:19: error: netdb.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c:2:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'gethostbyname'
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'socket'
/tmp/mplayer-configure--23026/tmp.c:3: error: 'AF_INET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:3: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:3: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:3: error: 'SOCK_STREAM' undeclared (first use in this function)



#include <netdb.h>
#include <sys/socket.h>
int main(void) { gethostbyname(0); socket(AF_INET, SOCK_STREAM, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lnsl
/tmp/mplayer-configure--23026/tmp.c:1:19: error: netdb.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c:2:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'gethostbyname'
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'socket'
/tmp/mplayer-configure--23026/tmp.c:3: error: 'AF_INET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:3: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:3: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:3: error: 'SOCK_STREAM' undeclared (first use in this function)



#include <netdb.h>
#include <sys/socket.h>
int main(void) { gethostbyname(0); socket(AF_INET, SOCK_STREAM, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lsocket
/tmp/mplayer-configure--23026/tmp.c:1:19: error: netdb.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c:2:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'gethostbyname'
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'socket'
/tmp/mplayer-configure--23026/tmp.c:3: error: 'AF_INET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:3: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:3: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:3: error: 'SOCK_STREAM' undeclared (first use in this function)



#include <winsock2.h>
int main(void) { gethostbyname(0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lws2_32


Result is: no (using -lws2_32)
##########################################

============ Checking for arpa/inet.h ============

#include <arpa/inet.h>
int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:23: error: arpa/inet.h: No such file or directory


Result is: no 
##########################################

============ Checking for inet_pton() ============

#include <arpa/inet.h>
int main(void) { inet_pton(0, 0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lws2_32
/tmp/mplayer-configure--23026/tmp.c:1:23: error: arpa/inet.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'inet_pton'



#include <arpa/inet.h>
int main(void) { inet_pton(0, 0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lws2_32 -lresolv
/tmp/mplayer-configure--23026/tmp.c:1:23: error: arpa/inet.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'inet_pton'


Result is: no 
##########################################

============ Checking for inet_aton() ============

#include <arpa/inet.h>
int main(void) { inet_aton(0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lws2_32
/tmp/mplayer-configure--23026/tmp.c:1:23: error: arpa/inet.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'inet_aton'



#include <arpa/inet.h>
int main(void) { inet_aton(0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lws2_32 -lresolv
/tmp/mplayer-configure--23026/tmp.c:1:23: error: arpa/inet.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'inet_aton'


Result is: no 
##########################################

============ Checking for socklen_t ============

#include <sys/socket.h>
int main(void) { socklen_t v = 0; return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: error: 'socklen_t' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:2: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:2: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:2: error: expected ';' before 'v'



#include <ws2tcpip.h>
int main(void) { socklen_t v = 0; return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: unused variable 'v'


Result is: yes 
##########################################

============ Checking for closesocket() ============

#include <winsock2.h>
int main(void) { closesocket(~0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math  -o /tmp/mplayer-configure--23026/tmp.exe -lws2_32


Result is: yes 
##########################################

============ Checking for networking ============
Result is: yes 
##########################################

============ Checking for inet6 ============

#include <sys/types.h>
#if !defined(_WIN32)
#include <sys/socket.h>
#include <netinet/in.h>
#else
#include <ws2tcpip.h>
#endif
int main(void) { struct sockaddr_in6 six; socket(AF_INET6, SOCK_STREAM, AF_INET6); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -lws2_32
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:8: warning: unused variable 'six'


Result is: yes 
##########################################

============ Checking for gethostbyname2 ============

#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>
int main(void) { gethostbyname2("", AF_INET); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:2:24: error: sys/socket.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c:3:19: error: netdb.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:4: warning: implicit declaration of function 'gethostbyname2'
/tmp/mplayer-configure--23026/tmp.c:4: error: 'AF_INET' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:4: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:4: error: for each function it appears in.)


Result is: no 
##########################################

============ Checking for inttypes.h (required) ============

#include <inttypes.h>
int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for malloc.h ============

#include <malloc.h>
int main(void) { return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 


Result is: yes 
##########################################

============ Checking for memalign() ============

#include <malloc.h>
int main(void) { memalign(64, sizeof(char)); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'memalign'
/tmp/ccxaRzzM.o:tmp.c:(.text+0x1a): undefined reference to `_memalign'
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for posix_memalign() ============

#define _XOPEN_SOURCE 600
#include <stdlib.h>
int main(void) { posix_memalign(NULL, 0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:3: warning: implicit declaration of function 'posix_memalign'
/tmp/ccFTNd4O.o:tmp.c:(.text+0x1b): undefined reference to `_posix_memalign'
collect2: ld returned 1 exit status


Result is: no 
##########################################

============ Checking for alloca.h ============

#include <alloca.h>
int main(void) { alloca(0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:20: error: alloca.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'alloca'
/tmp/mplayer-configure--23026/tmp.c:2: warning: incompatible implicit declaration of built-in function 'alloca'



#include <alloca.h>
int main(void) { alloca(0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:20: error: alloca.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'alloca'
/tmp/mplayer-configure--23026/tmp.c:2: warning: incompatible implicit declaration of built-in function 'alloca'


Result is: no 
##########################################

============ Checking for fastmemcpy ============
Result is: yes 
##########################################

============ Checking for mman.h ============

#include <sys/mman.h>
int main(void) { mmap(0, 0, 0, 0, 0, 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:22: error: sys/mman.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'mmap'


Result is: no 
##########################################


#include <sys/mman.h>
int main(void) { void *p = MAP_FAILED; return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:22: error: sys/mman.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: error: 'MAP_FAILED' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:2: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:2: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:2: warning: unused variable 'p'


============ Checking for dynamic loader ============

#include <dlfcn.h>
int main(void) { dlopen("", 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:19: error: dlfcn.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'dlopen'



#include <dlfcn.h>
int main(void) { dlopen("", 0); return 0; }

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -ldl
/tmp/mplayer-configure--23026/tmp.c:1:19: error: dlfcn.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:2: warning: implicit declaration of function 'dlopen'


Result is: no 
##########################################

============ Checking for pthread ============

#include <pthread.h>
static void *func(void *arg) { return arg; }
int main(void) {
 pthread_t tid;
#ifdef PTW32_STATIC_LIB
 pthread_win32_process_attach_np();
 pthread_win32_thread_attach_np();
#endif
 return pthread_create (&tid, 0, func, 0) != 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -lpthreadGC2
/tmp/mplayer-configure--23026/tmp.c:1:21: error: pthread.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:4: error: 'pthread_t' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:4: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:4: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:4: error: expected ';' before 'tid'
/tmp/mplayer-configure--23026/tmp.c:9: warning: implicit declaration of function 'pthread_create'
/tmp/mplayer-configure--23026/tmp.c:9: error: 'tid' undeclared (first use in this function)



#include <pthread.h>
static void *func(void *arg) { return arg; }
int main(void) {
 pthread_t tid;
#ifdef PTW32_STATIC_LIB
 pthread_win32_process_attach_np();
 pthread_win32_thread_attach_np();
#endif
 return pthread_create (&tid, 0, func, 0) != 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe 
/tmp/mplayer-configure--23026/tmp.c:1:21: error: pthread.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:4: error: 'pthread_t' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:4: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:4: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:4: error: expected ';' before 'tid'
/tmp/mplayer-configure--23026/tmp.c:9: warning: implicit declaration of function 'pthread_create'
/tmp/mplayer-configure--23026/tmp.c:9: error: 'tid' undeclared (first use in this function)



#include <pthread.h>
static void *func(void *arg) { return arg; }
int main(void) {
 pthread_t tid;
#ifdef PTW32_STATIC_LIB
 pthread_win32_process_attach_np();
 pthread_win32_thread_attach_np();
#endif
 return pthread_create (&tid, 0, func, 0) != 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -lpthread
/tmp/mplayer-configure--23026/tmp.c:1:21: error: pthread.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:4: error: 'pthread_t' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:4: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:4: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:4: error: expected ';' before 'tid'
/tmp/mplayer-configure--23026/tmp.c:9: warning: implicit declaration of function 'pthread_create'
/tmp/mplayer-configure--23026/tmp.c:9: error: 'tid' undeclared (first use in this function)



#include <pthread.h>
static void *func(void *arg) { return arg; }
int main(void) {
 pthread_t tid;
#ifdef PTW32_STATIC_LIB
 pthread_win32_process_attach_np();
 pthread_win32_thread_attach_np();
#endif
 return pthread_create (&tid, 0, func, 0) != 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -pthread
i586-mingw32msvc-gcc: unrecognized option '-pthread'
/tmp/mplayer-configure--23026/tmp.c:1:21: error: pthread.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:4: error: 'pthread_t' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:4: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:4: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:4: error: expected ';' before 'tid'
/tmp/mplayer-configure--23026/tmp.c:9: warning: implicit declaration of function 'pthread_create'
/tmp/mplayer-configure--23026/tmp.c:9: error: 'tid' undeclared (first use in this function)



#include <pthread.h>
static void *func(void *arg) { return arg; }
int main(void) {
 pthread_t tid;
#ifdef PTW32_STATIC_LIB
 pthread_win32_process_attach_np();
 pthread_win32_thread_attach_np();
#endif
 return pthread_create (&tid, 0, func, 0) != 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -lpthreadGC2 -lws2_32 -DPTW32_STATIC_LIB
/tmp/mplayer-configure--23026/tmp.c:1:21: error: pthread.h: No such file or directory
/tmp/mplayer-configure--23026/tmp.c: In function 'main':
/tmp/mplayer-configure--23026/tmp.c:4: error: 'pthread_t' undeclared (first use in this function)
/tmp/mplayer-configure--23026/tmp.c:4: error: (Each undeclared identifier is reported only once
/tmp/mplayer-configure--23026/tmp.c:4: error: for each function it appears in.)
/tmp/mplayer-configure--23026/tmp.c:4: error: expected ';' before 'tid'
/tmp/mplayer-configure--23026/tmp.c:6: warning: implicit declaration of function 'pthread_win32_process_attach_np'
/tmp/mplayer-configure--23026/tmp.c:7: warning: implicit declaration of function 'pthread_win32_thread_attach_np'
/tmp/mplayer-configure--23026/tmp.c:9: warning: implicit declaration of function 'pthread_create'
/tmp/mplayer-configure--23026/tmp.c:9: error: 'tid' undeclared (first use in this function)


Result is: no (v4l, v4l2, ao_nas, win32 loader disabled)
##########################################

============ Checking for w32threads ============
Result is: yes 
##########################################

============ Checking for rpath ============
Result is: no 
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
      if (iconv(icdsc, &iptr, &inleft, &optr, &outleft)
          != (size_t)(-1)) {
        write(1, outbuffer, OUTBUFSIZE - outleft);
      }
    }
    if (iconv_close(icdsc) == -1)
      ;
  }
  return 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -lm
/tmp/cc9lwnJ6.o:tmp.c:(.text+0x23): undefined reference to `_libiconv_open'
/tmp/cc9lwnJ6.o:tmp.c:(.text+0x86): undefined reference to `_libiconv'
/tmp/cc9lwnJ6.o:tmp.c:(.text+0xb3): undefined reference to `_libiconv_close'
collect2: ld returned 1 exit status



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
      if (iconv(icdsc, &iptr, &inleft, &optr, &outleft)
          != (size_t)(-1)) {
        write(1, outbuffer, OUTBUFSIZE - outleft);
      }
    }
    if (iconv_close(icdsc) == -1)
      ;
  }
  return 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -lm -liconv
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -liconv
collect2: ld returned 1 exit status



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
      if (iconv(icdsc, &iptr, &inleft, &optr, &outleft)
          != (size_t)(-1)) {
        write(1, outbuffer, OUTBUFSIZE - outleft);
      }
    }
    if (iconv_close(icdsc) == -1)
      ;
  }
  return 0;
}

i586-mingw32msvc-gcc -Wundef -Wall -Wno-switch -Wno-parentheses -Wpointer-arith -Wredundant-decls -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -std=gnu99  -O2   -march=i586 -mtune=i586 -pipe -ffast-math -fomit-frame-pointer /tmp/mplayer-configure--23026/tmp.c -I.  -fno-common -D__USE_MINGW_ANSI_STDIO=1   -lwinmm -ffast-math -lws2_32  -o /tmp/mplayer-configure--23026/tmp.exe -lm -liconv
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -liconv
collect2: ld returned 1 exit status



```

(side question: when i compile libiconv on ubuntu,the iconv binary creates but there is no libiconv.a created.
but when i compiled it on windows before, the libiconv.a creates, why ? :confused: )

---

### Post by active1 on 2012-08-15
solved by cross compiling libiconv in /usr/i586-mingw32msvc

---

