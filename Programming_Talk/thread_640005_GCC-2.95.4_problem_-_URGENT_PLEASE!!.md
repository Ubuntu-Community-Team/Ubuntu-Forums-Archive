---
title: "GCC-2.95.4 problem - URGENT PLEASE!!"
date: 2007-12-13
forum: Programming Talk
---

### Post by zanak on 2007-12-13
Hello world!

I have to build the OCERA project using a gcc-2.95.4 compiler, I have successfully installed the gcc-2.95.3 (using synaptic ), and patched the new compiler with the 2.95.4 patch. BUT whe I try to config gcc using :


zanak@MCServer:~/Desktop/gcc-2.95.3/objdir$ sudo ../configure  --prefix=../local/ --host =i486-pc-linux-gnu

but the problem is that I got an error messsage :

Invalid configuration `=i486-pc-linux-gnu': machine `=i486-pc' not recognized
Invalid configuration `=i486-pc-linux-gnu': machine `=i486-pc' not recognized
Unrecognized host system name =i486-pc-linux-gnu.


I tried to get the right target using this command :

# gcc -v 

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

----------------------

Where is the problem please ? how can I get the right target (host) ?

there is any HOWTO (rather than the one int the tarball ) 

tkx a lot, human community

---

### Post by ZipoTe on 2007-12-13
Try sudo ./configure instead...

---

### Post by zanak on 2007-12-13
tkx for the quick reply.
it gives the same error !

ps: I did that on the post above

---

### Post by samjh on 2007-12-13
First of all, it looks like the correct target is i486-linux-gnu, not i486-pc-linux-gnu.

Secondly, the build process is trying to use the gcc 4.1.2/3 compiler, not the version you want to use.  I'm not sure how to overcome this properly.  Is there a particular reason that you must use 2.95 instead of 4.1.2?

See the bold-font parts below.

```
# gcc -v

Using built-in specs.
**Target: i486-linux-gnu**
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
**gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)**
```

---

### Post by zanak on 2007-12-13
I tried i486-pc-linux-gnu and i486-pc-linux-gnu 
it gives me the same error (+/- pc)
actually I'm just configuring the new compiler. 
 any comments ?

---

### Post by samjh on 2007-12-13
Oh, you're compiling gcc!

According to the GCC Configuration page: [http://gcc.gnu.org/install/configure.html](http://gcc.gnu.org/install/configure.html)
> GCC has code to correctly determine the correct value for target for nearly all native systems. Therefore, we highly recommend you not provide a configure target when configuring a native compiler.So have you tried building without specifying a target?

---

### Post by zanak on 2007-12-13
yep, but in my case just DONT work :'( 

here is the code : 
zanak@MCServer:~/Desktop/gcc-2.95.3/objdir$ sudo ../configure  --prefix=../local/
Config.guess failed to determine the host type.  You need to specify one.
Usage: configure [OPTIONS] [HOST]

Options: [defaults in brackets]
 --prefix=MYDIR          install into MYDIR [/usr/local]
 --exec-prefix=MYDIR     install host-dependent files into MYDIR [/usr/local]
 --help                  print this message [normal config]
 --build=BUILD           configure for building on BUILD [BUILD=HOST]
 --host=HOST             configure for HOST [determined via config.guess]
 --norecursion           configure this directory only [recurse]
 --program-prefix=FOO    prepend FOO to installed program names [""]
 --program-suffix=FOO    append FOO to installed program names [""]
 --program-transform-name=P transform installed names by sed pattern P [""]
 --site=SITE             configure with site-specific makefile for SITE
 --srcdir=DIR            find the sources in DIR [. or ..]
 --target=TARGET         configure for TARGET [TARGET=HOST]
 --tmpdir=TMPDIR         create temporary files in TMPDIR [/tmp]
 --nfp                   configure for software floating point [hard float]
 --with-FOO, --with-FOO=BAR package FOO is available (parameter BAR)
 --without-FOO           package FOO is NOT available
 --enable-FOO, --enable-FOO=BAR include feature FOO (parameter BAR)
 --disable-FOO           do not include feature FOO

Where HOST and TARGET are something like "sparc-sunos", "mips-sgi-irix5", etc.

---

### Post by samjh on 2007-12-13
Man, I can't read properly this morning. lol

So it's the host you're trying to specify.  Right.

Specify both the --build and --host values to i486-pc-linux-gnu with/without the "pc".

The config.guess script should be able to guess the host type.  But if it doesn't you need to specify both the build-type and the host-type manually.

If that doesn't fix it, I'm stumped. :confused:

---

### Post by zanak on 2007-12-13
I foung thaht int the file config.gess they (MAYBE) use uname to get the type of processor. 
so I tried this :
shell # uname -p
unknown    

It seems that the processor is unknown !!!!

any suggestion ?

---

### Post by samjh on 2007-12-13
See my post above.

Yes, it uses uname.

Config.guess is obviously not "guessing" your architecture.  So specify both --build and --host and see what happens.

BTW, I also get "unknown" for both uname -p and uname -i.

---

### Post by zanak on 2007-12-13
PFFFFFFFFfffffffffffffffffffff

ok now i have a brand new problem :D

so the error was the blank space in target = i486-pc-linux-gnu !
(thats what hapen when you try to adopt a clean way to code in c++ :P) 

so here is the command :

zanak@MCServer:~/Desktop/gcc-2.95.3/objdir$ sudo ../configure  --prefix=../local/ --host=i486-linux-gnu
Created "Makefile" in /home/zanak/Desktop/gcc-2.95.3/objdir using "mt-frag"
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
*** The command 'gcc -o conftest -g -O2   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.
zanak@MCServer:~/Desktop/gcc-2.95.3/objdir$ make clean
rm -f *.a TEMP errs core *.o *~ \#* TAGS *.E *.log


any idea for this error ?

---

### Post by xeth_delta on 2007-12-13
> **zanak said:**
> PFFFFFFFFfffffffffffffffffffff

ok now i have a brand new problem :D

so the error was the blank space in target = i486-pc-linux-gnu !
(thats what hapen when you try to adopt a clean way to code in c++ :P) 

so here is the command :

zanak@MCServer:~/Desktop/gcc-2.95.3/objdir$ sudo ../configure  --prefix=../local/ --host=i486-linux-gnu
Created "Makefile" in /home/zanak/Desktop/gcc-2.95.3/objdir using "mt-frag"
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
*** The command 'gcc -o conftest -g -O2   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.
zanak@MCServer:~/Desktop/gcc-2.95.3/objdir$ make clean
rm -f *.a TEMP errs core *.o *~ \#* TAGS *.E *.log


any idea for this error ?

That seems to suggest the configure script cannot find your compiler. You can try:
```
CC=compiler_or_path_to_compiler ./configure [options]
```

Xeth

---

### Post by zanak on 2007-12-13
tks,

here is what i did :

shell # export CC= /usr/bin (also export CC= gcc)
shell # sudo ../configure  --prefix=../local/ --host=i486-linux-gnu

-----------
Created "Makefile" in /home/zanak/Desktop/gcc-2.95.3/objdir using "mt-frag"
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
*** The command '/usr/bin/gcc -o conftest -g -O2   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.
---------

any idea?

---

### Post by samjh on 2007-12-13
FFS, it's always the little stuff. :lolflag:

OK.  For the crt1.o problem, try:
```
locate crt1.o
```
It should be in /usr/lib.  If not you will need to install:
```
sudo apt-get install libc6-dev
```
If THAT doesn't fix it, set -B to the directory where your crt1.o is located.  Example: -B/usr/lib/

For the cc problem, try:
```
cc --version
```
If you get an error, then you will need to create a symlink in /usr/bin to point to your gcc compiler.

---

### Post by zanak on 2007-12-13
FINALY !!!

thks you guys for your help ! 

so samj the sudo apt-get install libc6-dev resolved the last problem.
I had a simlink to the gcc, and it works fine.

I'll post a quick howto in the forum this night ! 

now I have to deal with the OCERA   lol

tks again guys and have a nice day/night !

---

### Post by samjh on 2007-12-13
:) Good luck.

Now you'll never fear another build error! :p

---

