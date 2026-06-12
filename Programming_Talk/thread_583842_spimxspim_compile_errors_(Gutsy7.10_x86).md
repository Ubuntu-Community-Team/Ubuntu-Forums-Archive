---
title: "spim/xspim compile errors (Gutsy/7.10 x86)"
date: 2007-10-20
forum: Programming Talk
---

### Post by negated on 2007-10-20
Hey everyone,

Just did a clean install of Gutsy (7.10, x86) and I'm having a problem compiling spim/xspim ([http://pages.cs.wisc.edu/~larus/spim.html](http://pages.cs.wisc.edu/~larus/spim.html)). I had NO problem at all doing this on my Feisty (7.04, x86) install, so I'm puzzled as to why this isn't installing.

I've already DLed and installed the following packages:

byacc
flex
bison
libx11-dev
libxaw7-dev

As root, when I run make from the spim directory I get:

```


root@rise-above:~/spim-7.3/spim# make
./Configure
cc
Check if this machine is big-endian or little-endian.
This may take a few minutes.
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
./Configure: line 47: ./endian: No such file or directory
I believe this is a little-endian machine.

Checking if libc on this machine contains:
grep: library_contents: No such file or directory
  vsprintf: No, I don't think
grep: library_contents: No such file or directory
    _doprnt: NO, THIS IS A PROBLEM: NO VSPRINTF AND NO _DOPRNT
SPIM WILL NOT RUN PROPERLY
grep: library_contents: No such file or directory
  vfprintf: No, I don't think
grep: library_contents: No such file or directory
    _doprnt: NO, THIS IS A PROBLEM: NO VFPRINTF AND NO _DOPRNT
SPIM WILL NOT RUN PROPERLY
grep: library_contents: No such file or directory
  strtoul: No, I don't think
grep: library_contents: No such file or directory
  strtol: No, I don't think
grep: library_contents: No such file or directory
  memcpy: No, I don't think

Checking for /usr/include/termios.h
No, it is not there
make -f Makefile spim2
make[1]: Entering directory `/root/spim-7.3/spim'
bison -d --file-prefix=y ../CPU/parser.y
../CPU/parser.y: conflicts: 25 shift/reduce
gcc -I. -I../CPU `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER="\"/usr/local/lib/exceptions.s\"" -DSPIM_VERSION="\"`cat ../VERSION`\"" -g -Wall   -c -o spim-utils.o ../CPU/spim-utils.c
../CPU/spim-utils.c:28:19: error: stdio.h: No such file or directory
../CPU/spim-utils.c:29:19: error: ctype.h: No such file or directory
../CPU/spim-utils.c:30:20: error: string.h: No such file or directory
In file included from ../CPU/spim-utils.c:33:
../CPU/spim.h:73:20: error: stdlib.h: No such file or directory
In file included from ../CPU/spim-utils.c:33:
../CPU/spim.h:209: error: expected specifier-qualifier-list before 'FILE'
In file included from ../CPU/spim-utils.c:40:
../CPU/scanner.h:29: error: expected ')' before '*' token
../CPU/spim-utils.c: In function 'initialize_world':
../CPU/spim-utils.c:111: warning: implicit declaration of function 'strdup'
../CPU/spim-utils.c:111: warning: incompatible implicit declaration of built-in function 'strdup'
../CPU/spim-utils.c:114: warning: implicit declaration of function 'strtok'
../CPU/spim-utils.c:114: warning: assignment makes pointer from integer without a cast
../CPU/spim-utils.c:114: warning: assignment makes pointer from integer without a cast
../CPU/spim-utils.c:122: warning: implicit declaration of function 'free'
../CPU/spim-utils.c:134: warning: implicit declaration of function 'initialize_scanner'
../CPU/spim-utils.c:134: error: 'stdin' undeclared (first use in this function)
../CPU/spim-utils.c:134: error: (Each undeclared identifier is reported only once
../CPU/spim-utils.c:134: error: for each function it appears in.)
../CPU/spim-utils.c: In function 'initialize_registers':
../CPU/spim-utils.c:158: warning: implicit declaration of function 'bzero'
../CPU/spim-utils.c:158: warning: incompatible implicit declaration of built-in function 'bzero'
../CPU/spim-utils.c: In function 'read_assembly_file':
../CPU/spim-utils.c:193: error: 'FILE' undeclared (first use in this function)
../CPU/spim-utils.c:193: error: 'file' undeclared (first use in this function)
../CPU/spim-utils.c:193: warning: implicit declaration of function 'fopen'
../CPU/spim-utils.c:207: warning: implicit declaration of function 'fclose'
../CPU/spim-utils.c:212: warning: control reaches end of non-void function
../CPU/spim-utils.c: In function 'copy_str_to_stack':
../CPU/spim-utils.c:287: warning: implicit declaration of function 'strlen'
../CPU/spim-utils.c:287: warning: incompatible implicit declaration of built-in function 'strlen'
../CPU/spim-utils.c: At top level:
../CPU/spim-utils.c:501: warning: conflicting types for built-in function 'vsprintf'
../CPU/spim-utils.c: In function 'vsprintf':
../CPU/spim-utils.c:504: error: 'FILE' undeclared (first use in this function)
../CPU/spim-utils.c:504: error: expected ';' before '_strbuf'
../CPU/spim-utils.c:506: error: '_strbuf' undeclared (first use in this function)
../CPU/spim-utils.c:506: error: '_IOWRT' undeclared (first use in this function)
../CPU/spim-utils.c:506: error: '_IOSTRG' undeclared (first use in this function)
../CPU/spim-utils.c:509: warning: implicit declaration of function '_doprnt'
../CPU/spim-utils.c:510: warning: implicit declaration of function 'putc'
../CPU/spim-utils.c: In function 'strtol':
../CPU/spim-utils.c:527: warning: implicit declaration of function 'sscanf'
../CPU/spim-utils.c:527: warning: incompatible implicit declaration of built-in function 'sscanf'
../CPU/spim-utils.c:531: warning: incompatible implicit declaration of built-in function 'sscanf'
../CPU/spim-utils.c:535: warning: incompatible implicit declaration of built-in function 'sscanf'
../CPU/spim-utils.c: In function 'strtoul':
../CPU/spim-utils.c:552: warning: incompatible implicit declaration of built-in function 'sscanf'
../CPU/spim-utils.c:556: warning: incompatible implicit declaration of built-in function 'sscanf'
../CPU/spim-utils.c:560: warning: incompatible implicit declaration of built-in function 'sscanf'
../CPU/spim-utils.c: In function 'str_copy':
../CPU/spim-utils.c:570: warning: implicit declaration of function 'strcpy'
../CPU/spim-utils.c:570: warning: incompatible implicit declaration of built-in function 'strcpy'
../CPU/spim-utils.c:570: warning: incompatible implicit declaration of built-in function 'strlen'
../CPU/spim-utils.c: In function 'xmalloc':
../CPU/spim-utils.c:577: warning: implicit declaration of function 'malloc'
../CPU/spim-utils.c:577: warning: incompatible implicit declaration of built-in function 'malloc'
../CPU/spim-utils.c: In function 'zmalloc':
../CPU/spim-utils.c:590: warning: incompatible implicit declaration of built-in function 'malloc'
../CPU/spim-utils.c:595: warning: incompatible implicit declaration of built-in function 'bzero'
make[1]: *** [spim-utils.o] Error 1
make[1]: Leaving directory `/root/spim-7.3/spim'
make: *** [spim] Error 2
root@rise-above:~/spim-7.3/spim# 


```

Again as root, when I run xmkmf in the xspim directory I get:

```


root@rise-above:~/spim-7.3/xspim# xmkmf
mv -f Makefile Makefile.bak
imake -DUseInstalled -I/usr/lib/X11/config
<stdin>:1:19: error: stdio.h: No such file or directory
<stdin>:2:19: error: ctype.h: No such file or directory
<stdin>: In function 'main':
<stdin>:18: error: 'NULL' undeclared (first use in this function)
<stdin>:18: error: (Each undeclared identifier is reported only once
<stdin>:18: error: for each function it appears in.)
<stdin>:45: warning: incompatible implicit declaration of built-in function 'sscanf'
<stdin>:49: warning: incompatible implicit declaration of built-in function 'printf'
Aborted (core dumped)


```

Anyone know what's going on? I'd really appreciate some insight...

Thanks!

-S

---

### Post by negated on 2007-10-20
I solved the xspim portion of the problem; I had to install:

libc6-dev

However, when I try to compile spim, I now get this instead:

```


root@rise-above:~/spim-7.3/spim# make
make -f Makefile spim2
make[1]: Entering directory `/root/spim-7.3/spim'
bison -d --file-prefix=y ../CPU/parser.y
../CPU/parser.y: conflicts: 25 shift/reduce
gcc -I. -I../CPU `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER="\"/usr/local/lib/exceptions.s\"" -DSPIM_VERSION="\"`cat ../VERSION`\"" -g -Wall   -c -o spim-utils.o ../CPU/spim-utils.c
../CPU/spim-utils.c:501: error: conflicting types for 'vsprintf'
../CPU/spim-utils.c: In function 'vsprintf':
../CPU/spim-utils.c:506: error: 'FILE' has no member named '_flag'
../CPU/spim-utils.c:506: error: '_IOWRT' undeclared (first use in this function)
../CPU/spim-utils.c:506: error: (Each undeclared identifier is reported only once
../CPU/spim-utils.c:506: error: for each function it appears in.)
../CPU/spim-utils.c:506: error: '_IOSTRG' undeclared (first use in this function)
../CPU/spim-utils.c:507: error: 'FILE' has no member named '_ptr'
../CPU/spim-utils.c:508: error: 'FILE' has no member named '_cnt'
../CPU/spim-utils.c:509: warning: implicit declaration of function '_doprnt'
../CPU/spim-utils.c: At top level:
../CPU/spim-utils.c:519: error: conflicting types for 'strtol'
/usr/include/stdlib.h:186: error: previous declaration of 'strtol' was here
make[1]: *** [spim-utils.o] Error 1
make[1]: Leaving directory `/root/spim-7.3/spim'
make: *** [spim] Error 2


```

Of course, there is spim in the repository, but I'd still like to know why it won't compile...

If anyone has any ideas, let me know!

Thanks,

-S

---

### Post by Dancingwllamas on 2007-10-20
This may not be your issue (I built spim back with feisty), but you may want to try running "sudo apt-get build-dep spim" in the console to ensure all the dependencies for building SPIM are satisfied.

Hope this helps.

---

### Post by negated on 2007-10-21
Thanks for the idea, but it didn't work. It installed some packages (g++, x-dev, etc.) but trying to compile spim afterwards gives me the same error as before. How strange.

Anyway, now that I have xspim working, I am not too worried about it.

-S

---

