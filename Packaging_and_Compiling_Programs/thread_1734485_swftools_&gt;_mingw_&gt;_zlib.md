---
title: "swftools &gt; mingw &gt; zlib"
date: 2011-04-20
forum: Packaging and Compiling Programs
---

### Post by DannyT on 2011-04-20
Hi there, my ultimate goal is to compile a windows binary of [swftools]("http://www.swftools.org"). 

After having reviewed the process for doing so on windows it seemed as if it might be easier to just do it in Linux and cross-compile for windows. I'm also keen to increase my understanding of working with Linux (from zero knowledge) so have dived in.

So far I have managed to get the Linux build working after:

Creating a Windows Virtual PC
Trying to install Ubuntu in to the Windows Virtual PC, failing
Scrapping the Windows Virtual PC
Installing Virtualbox
Successfully Installing Ubuntu 10.10
Installing Git
Cloning the swftools source repository
Failing to compile the swftools source many times
Installing numerous dependencies
Evntually successfully compiling the swftools source

 - All of which was done by somewhat fumbling my way around and lots of Googling, I've learned a lot but I've mainly learned how much I don't know :S

Anyway I'm currently trying to cross compile swftools to end up with some windows binaries. So far I have installed mingw (using Ubuntu Software Centre) and attempted to:

```

 ./configure --host=i586-mingw32msvc && make

```

the result of which contained:
```

ERROR: You need zlib to compile swftools

```

Which is a message I saw and resolved when trying to compile normally. So I've deduced mingw needs access to some version of zlib that isn't the same as the one I've already isntalled. This led me to [this blog post]("http://kemovitra.blogspot.com/2009/06/mingw-compiling-zlib.html")

Unfortunately the first command suggested there for compiling zlib for mingw:
```

make -f win32/Makefile.gcc

```

fails with
```

unrecognized option '--out-implib'

```

Which I can only assume is because things have changed since then or I have something else missing. This is as far as I can get and seemingly no amount of google-fu is getting me any further hence my registering and submission of plea to your good selves.

Any pointers as to where to go from here much appreciated!

---

### Post by DannyT on 2011-04-26
Sorry to bump, but if anyone has any suggestions or if I need to provide more info please let me know :)

---

### Post by SevenMachines on 2011-04-26
Hi, you'll need the win32 binaries for zlib, you might want to cross compile them yourself or you can download them here,
[http://gnuwin32.sourceforge.net/downlinks/zlib-lib-zip.php](http://gnuwin32.sourceforge.net/downlinks/zlib-lib-zip.php)

then extract, here i've placed everything in a directory zlib on my desktop,
```
~/Desktop/zlib$ ls -R
.:
include  lib  manifest

./include:
zconf.h  zlib.h

./lib:
libz.a  libz.dll.a  zlib-bcc.lib  zlib.def  zlib.lib

./manifest:
zlib-1.2.3-lib.mft  zlib-1.2.3-lib.ver

```...and pass the directories to configure
 ```
$ CFLAGS+="-I/home/seven/Desktop/zlib/include -L/home/seven/Desktop/zlib/lib" ./configure --host=i586-mingw32msvc
$ make
```Doesnt actually cross compile here on natty 64 bit( error: two or more data types in declaration specifiers
os.c: In function &#8216;getRegistryEntry&#8217;)  but you may be more lucky. might be worth cross compiling zlib against whatever mingw32 version your using if it doesnt work for you

---

### Post by SevenMachines on 2011-04-26
Just to add, building zlib using the following works for me

 * get zlib
[http://gnuwin32.sourceforge.net/downlinks/zlib-src-zip.php](http://gnuwin32.sourceforge.net/downlinks/zlib-src-zip.php)

* unzip and cd 
```
$ cd src/zlib/1.2.3/zlib-1.2.3/
```* configure for cross
```
$ CC=i586-mingw32msvc-gcc ./configure --prefix=/usr/local/win32
```* make should work now
```
$ make
$ sudo make install
3$ ls -R /usr/local/win32/
/usr/local/win32/:
include  lib  share

/usr/local/win32/include:
zconf.h  zlib.h

/usr/local/win32/lib:
libz.a

/usr/local/win32/share:
man

/usr/local/win32/share/man:
man3

/usr/local/win32/share/man/man3:
zlib.3
```so in the swftools directory, configure would be
```
$  CFLAGS+="-I/usr/local/win32/include -L/usr/local/win32/lib" ./configure --host=i586-mingw32msv
```

---

### Post by DannyT on 2011-04-26
Thanks SevenMachines, will give this a try and report back! Your help is ***very*** much appreciated :)

---

### Post by DannyT on 2011-04-26
> **SevenMachines said:**
> Just to add, building zlib using the following works for me

 * get zlib
[http://gnuwin32.sourceforge.net/downlinks/zlib-src-zip.php](http://gnuwin32.sourceforge.net/downlinks/zlib-src-zip.php)

* unzip and cd 
```
$ cd src/zlib/1.2.3/zlib-1.2.3/
```* configure for cross
```
$ CC=i586-mingw32msvc-gcc ./configure --prefix=/usr/local/win32
```

When I do this, I'm getting:
```
./configure: command not found
```
should I be seeing a configure file in the extracted /zlib/1.2.3/zlib-1.2.3/ folder?

---

### Post by SevenMachines on 2011-04-26
If you downloaded the version i linked to then it should be there. you may need to change the permissions on the configure file though
```
 $ chmod +x configure
```

---

### Post by DannyT on 2011-05-15
Sorry this has taken so long to respond to, am now picking this back up. Your previous response was, of course, the solution to that problem.

My next issue is I believe I need another library of some sort as after getting zlib working with mingw I now get the following:
```
checking for sin in -lm... no
Error: Math library not found.
```

Any suggestions as to how I can identify which math library I need and how to let mingw know about it?

---

### Post by DannyT on 2011-05-16
Running the following gets me past the math library error but I get zlib err again -

```
CFLAGS+="-I/usr/local/win32/include -L/usr/local/win32/lib" CXX=i586-mingw32msvc-g++ CPP=i586-mingw32msvc-cpp CC=i586-mingw32msvc-gcc ./configure --host=i586-mingw32msv
```

---

### Post by DannyT on 2011-05-16
Sorry for spamming my own thread :S

I've just tried to go back through the steps to cross compile zlib with the latest version and now get the following:

Download and extract latest zlib from [http://zlib.net](http://zlib.net), then cd and:
```

$ CC=i586-mingw32msvc-gcc ./configure --prefix=/usr/local/win32
Checking for shared library support...
Building shared library libz.so.1.2.5 with i586-mingw32msvc-gcc.
Checking for off64_t... Yes.
Checking for fseeko... Yes.
Checking for unistd.h... Yes.
Checking whether to use vs[n]printf() or s[n]printf()... using vs[n]printf().
Checking for vsnprintf() in stdio.h... Yes.
Checking for return value of vsnprintf()... Yes.
Checking for attribute(visibility) support... No.

```

Then try to make:
```


$ make
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o example.o example.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o adler32.o adler32.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o compress.o compress.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o crc32.o crc32.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o deflate.o deflate.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o gzclose.o gzclose.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o gzlib.o gzlib.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o gzread.o gzread.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o gzwrite.o gzwrite.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o infback.o infback.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o inffast.o inffast.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o inflate.o inflate.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o inftrees.o inftrees.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o trees.o trees.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o uncompr.o uncompr.c
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ   -c -o zutil.o zutil.c
ar rc libz.a adler32.o compress.o crc32.o deflate.o gzclose.o gzlib.o gzread.o gzwrite.o infback.o inffast.o inflate.o inftrees.o trees.o uncompr.o zutil.o 
i586-mingw32msvc-gcc -O3 -D_LARGEFILE64_SOURCE=1 -DNO_VIZ -o example example.o -L. libz.a
libz.a: could not read symbols: Archive has no index; run ranlib to add one
collect2: ld returned 1 exit status
make: *** [example] Error 1

```

I get this same error on the version suggested above also, very grateful for any suggestions

---

