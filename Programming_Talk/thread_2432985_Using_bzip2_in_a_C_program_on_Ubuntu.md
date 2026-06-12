---
title: "Using bzip2 in a C program on Ubuntu"
date: 2019-12-11
forum: Programming Talk
---

### Post by nniranjhana on 2019-12-11
Hi, I have done "sudo apt-get install libbz2-dev" so that my #include <bzlib.h> in my C file works.

But now, it doesn't compile because it cannot find reference, even though I used the -lbz2 flag too as mentioned in [this post]("https://ubuntuforums.org/showthread.php?t=1451603"):

```
niranjhana@niranjhana-XPS-13-9360:~$ gcc -lbz2 main.c
/tmp/ccy3Z1M5.o: In function `main':
main.c: (.text+0x13): undefined reference to `BZ2_bzlibVersion'
main.c: (.text+0x8e): undefined reference to `BZ2_bzBuffToBuffCompress'
collect2: error: ld returned 1 exit status
```

How can I get it to work? What's missing here?

---

### Post by Skaperen on 2019-12-11
do the standard bz2 commands work on that system?  i'm guessing that they need the same libraries.  but i don't even know if those are the correct names to reference as i have never used bz2 in C, before.  i'd look to see what these libs have in them and see how close my coding is.

the bzip2 command works for me and my system has these installed:
```

lt2a/forums /home/forums 1> dpkg -l|fgrep bz
ii  aptdaemon                    1.1.1+bzr982-0ubunt all                 transaction based package management service
ii  aptdaemon-data               1.1.1+bzr982-0ubunt all                 data files for clients
ii  bzip2                        1.0.6-8.1ubuntu0.2  amd64               high-quality block-sorting file compressor - utilities
ii  libbz2-1.0:amd64             1.0.6-8.1ubuntu0.2  amd64               high-quality block-sorting file compressor library - runtime
ii  libzbar0:amd64               0.10+doc-10.1build2 amd64               bar code scanner and decoder (library)
ii  libzephyr4:amd64             3.1.2-1build2       amd64               Project Athena's notification service - non-Kerberos librarie
ii  libzmq5:amd64                4.2.5-1ubuntu0.2    amd64               lightweight messaging kernel (shared library)
ii  libzstd1:amd64               1.3.3+dfsg-2ubuntu1 amd64               fast lossless compression algorithm
ii  libzvbi-common               0.2.35-13           all                 Vertical Blanking Interval decoder (VBI) - common files
ii  libzvbi0:amd64               0.2.35-13           amd64               Vertical Blanking Interval decoder (VBI) - runtime files
ii  pike8.0-bzip2                8.0.498-1build1     amd64               Bzip2 module for Pike
ii  python3-aptdaemon            1.1.1+bzr982-0ubunt all                 Python 3 module for the server and client of aptdaemon
ii  python3-aptdaemon.gtk3widget 1.1.1+bzr982-0ubunt all                 Python 3 GTK+ 3 widgets to run an aptdaemon client
lt2a/forums /home/forums 2>
```

---

### Post by spjackson on 2019-12-12
```
gcc main.c -lbz2
```
Some time ago, gcc was changed to require libraries to occur after the code that used them. Once upon a time it didn't matter.

---

### Post by nniranjhana on 2019-12-12
This worked, thanks!

---

