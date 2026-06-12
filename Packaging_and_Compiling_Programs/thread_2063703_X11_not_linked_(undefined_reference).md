---
title: "X11 not linked (undefined reference)"
date: 2012-09-27
forum: Packaging and Compiling Programs
---

### Post by IlluminatiBG on 2012-09-27
I'm trying to test some snippets on X11 library. Tried to compile and run following:
```
// main.c
#include <X11/Xlib.h>

int main(int argc, char** argv) {
    Display* display = XOpenDisplay(0);
    XCloseDisplay(display);
    return 0;
}

```I'm using Ubuntu 12.04. I've noticed following:
1. No error "Cannot find X11", so ld actually finds it.
2. No error on opening header files (/usr/include is in path, header is opened with <X11/Xlib.h> (e.g. X11 folder is specified explicitly).
3. libX11.so exists and it is places in /usr/lib/x86_64-linux-gnu/, I suppose on the verbose version of gcc, '-march=x86-64 build for the same architecture, so it must be linked.
4. libx11-dev is present on the system.
5. Compiling main.c to main.o, then explicitly call the "ld -lX11 main.o" passes. However a.out cannot be opened (it says it doesn't exists from bash, gdb, strace etc. but ls sees it??? Why?).

gcc version: gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
ld version: GNU ld (GNU Binutils for Ubuntu) 2.22

The question is why XOpenDisplay and XCloseDisplay report undefined references as I link the libX11?

I include bash log with my attempts (little long).
```
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ locate *.pc | grep x11
/usr/lib/x86_64-linux-gnu/pkgconfig/gdk-x11-2.0.pc
/usr/lib/x86_64-linux-gnu/pkgconfig/gdk-x11-3.0.pc
/usr/lib/x86_64-linux-gnu/pkgconfig/gtk+-x11-2.0.pc
/usr/lib/x86_64-linux-gnu/pkgconfig/gtk+-x11-3.0.pc
/usr/lib/x86_64-linux-gnu/pkgconfig/x11.pc
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ pkg-config --cflags --libs x11
 -lX11  
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ gcc `pkg-config --cflags --libs x11` main.c
/tmp/cc7Yoe1C.o: In function `main':
main.c:(.text+0x15): undefined reference to `XOpenDisplay'
main.c:(.text+0x25): undefined reference to `XCloseDisplay'
collect2: ld returned 1 exit status
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ gcc -lX11 main.c
/tmp/ccVJ9eKW.o: In function `main':
main.c:(.text+0x15): undefined reference to `XOpenDisplay'
main.c:(.text+0x25): undefined reference to `XCloseDisplay'
collect2: ld returned 1 exit status
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ locate libx11.so
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ locate libX11.so
/usr/lib/i386-linux-gnu/libX11.so.6
/usr/lib/i386-linux-gnu/libX11.so.6.3.0
/usr/lib/x86_64-linux-gnu/libX11.so
/usr/lib/x86_64-linux-gnu/libX11.so.6
/usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ gcc -L/usr/lib/x86_64-linux-gnu -lX11 main.c
/tmp/ccfi4emn.o: In function `main':
main.c:(.text+0x15): undefined reference to `XOpenDisplay'
main.c:(.text+0x25): undefined reference to `XCloseDisplay'
collect2: ld returned 1 exit status
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ uname -a
Linux Illuminati-PC 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ gcc -c main.c
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ ll
total 16
drwxrwxr-x 2 illuminati illuminati 4096 &#1089;&#1077;&#1087; 27 22:29 ./
drwxrwxr-x 7 illuminati illuminati 4096 &#1089;&#1077;&#1087; 27 21:39 ../
-rw-rw-r-- 1 illuminati illuminati  143 &#1089;&#1077;&#1087; 27 22:20 main.c
-rw-rw-r-- 1 illuminati illuminati 1456 &#1089;&#1077;&#1087; 27 22:29 main.o
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ ld -lX11 main.o
ld: warning: cannot find entry symbol _start; defaulting to 0000000000400300
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ ll
total 20
drwxrwxr-x 2 illuminati illuminati 4096 &#1089;&#1077;&#1087; 27 22:29 ./
drwxrwxr-x 7 illuminati illuminati 4096 &#1089;&#1077;&#1087; 27 21:39 ../
-rwxrwxr-x 1 illuminati illuminati 2990 &#1089;&#1077;&#1087; 27 22:29 a.out*
-rw-rw-r-- 1 illuminati illuminati  143 &#1089;&#1077;&#1087; 27 22:20 main.c
-rw-rw-r-- 1 illuminati illuminati 1456 &#1089;&#1077;&#1087; 27 22:29 main.o
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ ./a.out
bash: ./a.out: No such file or directory
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ strace ./a.out
execve("./a.out", ["./a.out"], [/* 55 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f5ccce15000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x7f5ccce15000, 4096)            = 0
exit_group(1)                           = ?
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ rm main.o a.out
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ gcc -v -lX11 main.c
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5)
COLLECT_GCC_OPTIONS='-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.6/cc1 -quiet -v -imultilib . -imultiarch x86_64-linux-gnu main.c -quiet -dumpbase main.c -mtune=generic -march=x86-64 -auxbase main -version -fstack-protector -o /tmp/ccGp5req.s
GNU C (Ubuntu/Linaro 4.6.3-1ubuntu5) version 4.6.3 (x86_64-linux-gnu)
    compiled by GNU C version 4.6.3, GMP version 5.0.2, MPFR version 3.1.0-p3, MPC version 0.9
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/x86_64-linux-gnu/4.6/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.6/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
GNU C (Ubuntu/Linaro 4.6.3-1ubuntu5) version 4.6.3 (x86_64-linux-gnu)
    compiled by GNU C version 4.6.3, GMP version 5.0.2, MPFR version 3.1.0-p3, MPC version 0.9
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 75e879ed14f91af504f4150eadeaa0e6
COLLECT_GCC_OPTIONS='-v' '-mtune=generic' '-march=x86-64'
 as --64 -o /tmp/ccWWZtEj.o /tmp/ccGp5req.s
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.6/:/usr/lib/gcc/x86_64-linux-gnu/4.6/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.6/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.6/:/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-v' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.6/collect2 --sysroot=/ --build-id --no-add-needed --as-needed --eh-frame-hdr -m elf_x86_64 --hash-style=gnu -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro /usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.6/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.6 -L/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.6/../../.. -lX11 /tmp/ccWWZtEj.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/4.6/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crtn.o
/tmp/ccWWZtEj.o: In function `main':
main.c:(.text+0x15): undefined reference to `XOpenDisplay'
main.c:(.text+0x25): undefined reference to `XCloseDisplay'
collect2: ld returned 1 exit status
illuminati@Illuminati-PC:/usr/local/projects/CPP/Linux/Test/X1$ dpkg --get-selections | grep libx11
libx11-6                    install
libx11-6:i386                    install
libx11-data                    install
libx11-dev                    install
libx11-doc                    install
libx11-xcb1                    install
libx11-xcb1:i386                install

```

---

### Post by steeldriver on 2012-09-27
probably the order you are linking? if main.c depends on libX11 then the link order needs reflect that

> It makes a difference where in the command you write this option;  the linker searches and processes libraries and object files in the  order they are specified.  Thus, `foo.o -lz bar.o' searches library `z'  after file foo.o but before bar.o.  If bar.o refers to functions in `z',  those functions may not be loaded.       [http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html)

---

