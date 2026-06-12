---
title: "Linker not searching for lib in /usr/local/lib"
date: 2010-01-27
forum: Packaging and Compiling Programs
---

### Post by _doits_ on 2010-01-27
Hello,

I'm having a weird linking problem.

I compiled latest x264 and ffmpegsource by myself. 

first ffmpegsource: it gave me a libffms2.so.0, installed into /usr/local/lib

> $ file /usr/local/lib/libffms2.so.0.0.0 
/usr/local/lib/libffms2.so.0.0.0: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

$ ls -lh /usr/local/lib/libffms2.so*
lrwxrwxrwx 1 root root   17 2010-01-26 18:05 /usr/local/lib/libffms2.so -> libffms2.so.0.0.0
lrwxrwxrwx 1 root root   17 2010-01-26 18:05 /usr/local/lib/libffms2.so.0 -> libffms2.so.0.0.0
-rwxr-xr-x 1 root root 213K 2010-01-26 18:05 /usr/local/lib/libffms2.so.0.0.0
now x264: it detected the libffms2.so.0 in /usr/local/lib on configure and linked against it accordingly

> gcc -o x264 x264.o [...] -lm -lpthread -Wl,-Bsymbolic -s -L. -lavformat -lswscale -lpostproc -lavcodec -lavutil -lm -lz -lbz2 -lpthread **-lffms2** -lgpac_staticlooks like everything went fine, but...:

> $ x264 
x264: error while loading shared libraries: libffms2.so.0: cannot open shared object file: No such file or directory

$ strace `which x264` 2>&1 | grep ffms2
open("/lib/tls/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/libffms2.so.0", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/x86_64/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libffms2.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
writev(2, [{"/usr/local/bin/x264", 19}, {": ", 2}, {"error while loading shared libra"..., 36}, {": ", 2}, {"libffms2.so.0", 13}, {": ", 2}, {"cannot open shared object file", 30}, {": ", 2}, {"No such file or directory", 25}, {"\n", 1}], 10/usr/local/bin/x264: error while loading shared libraries: libffms2.so.0: cannot open shared object file: No such file or directory
so it does not even look at /usr/local/lib for that library. the weird part is, it does load other libs from /usr/local/lib:

> $ ldd `which x264`
        linux-vdso.so.1 =>  (0x00007fff6ab43000)
        libm.so.6 => /lib/libm.so.6 (0x00007fe096da0000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007fe096b84000)
        libavformat.so.52 => /usr/local/lib/libavformat.so.52 (0x00007fe0968c8000)
        libswscale.so.0 => /usr/local/lib/libswscale.so.0 (0x00007fe096696000)
        libpostproc.so.51 => /usr/local/lib/libpostproc.so.51 (0x00007fe096488000)
        libavcodec.so.52 => /usr/local/lib/libavcodec.so.52 (0x00007fe0958a4000)
        libavutil.so.50 => /usr/local/lib/libavutil.so.50 (0x00007fe095693000)
        libz.so.1 => /lib/libz.so.1 (0x00007fe09547c000)
        libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00007fe09526b000)
        libffms2.so.0 => not found
        libc.so.6 => /lib/libc.so.6 (0x00007fe094efc000)
        [...]Since I do not know much about the way libraries get linked, I wonder how this can happen. Why does it not look int /usr/local/lib for this one library? Is this a problem of x264 or of my system?

I asked on x264-mailing-list about this, too, so for reference: [http://mailman.videolan.org/pipermail/x264-devel/2010-January/006771.html](http://mailman.videolan.org/pipermail/x264-devel/2010-January/006771.html). but there's no clue, yet.

Thanks for your help.
Markus

---

### Post by Some Penguin on 2010-01-27
Hm.  Have you ran 'ldconfig'?

---

### Post by _doits_ on 2010-01-28
you got it.... damn, this was a stupid one.

thanks :)

---

