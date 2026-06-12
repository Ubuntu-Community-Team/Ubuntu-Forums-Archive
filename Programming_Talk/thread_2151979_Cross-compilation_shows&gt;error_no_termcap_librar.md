---
title: "Cross-compilation shows&gt;error: no termcap library found, why?"
date: 2013-06-06
forum: Programming Talk
---

### Post by indarkness on 2013-06-06
I'm experiencing a frustrating error trying to cross-compile gdbserver for arm. I've downloaded and crosscompiled termcap with this command

```
    export CC="/bin/arm-mv5sft-linux-gnueabi-gcc"
    export CXX="/bin/arm-mv5sft-linux-gnueabi-g++"
    export AR="/bin/arm-mv5sft-linux-gnueabi-ar"
    CONFOPTS+="--target=arm-linux --host=arm-linux --build=i686-pc-linux-gnu --prefix=/usr --exec-prefix=/usr --enable-static"
    ./configure ${CONFOPTS} 
    make &&
    
    make DESTDIR=~/gdb-7.6/toInst install
```

Being such crosscompilation successful since I wasn't prompted any error, I got the libtermcap.a which is arm, as you can see below, and located on ~/termcap/

```
    :$ file *.o
    termcap.o: ELF 32-bit LSB relocatable, ARM, version 1 (SYSV), not stripped
    tparam.o:  ELF 32-bit LSB relocatable, ARM, version 1 (SYSV), not stripped
    version.o: ELF 32-bit LSB relocatable, ARM, version 1 (SYSV), not strippe
```

However, if I try to do the same for cross-compiling gdbserver for arm, with the same options and calling the cross compiled lib

```
    export CC="/bin/arm-mv5sft-linux-gnueabi-gcc"
    export CXX="/bin/arm-mv5sft-linux-gnueabi-g++"
    export AR="/bin/arm-mv5sft-linux-gnueabi-ar"
    
    CONFOPTS+="--target=arm-linux --host=arm-linux --build=i686-pc-linux-gnu --prefix=/usr --exec-prefix=/usr --sysconfdir=/etc --enable-static --with-termcap=~/termcap/libtermcap.a"
    ./configure ${CONFOPTS} $@
    make &&
    
    make DESTDIR=~/gdb-7.6/toInst install
```

I get this

```
    checking for library containing waddstr... no
    configure: WARNING: no enhanced curses library found; disabling TUI
    checking for library containing tgetent... no
    configure: error: no termcap library found
    make[1]: *** [configure-gdb] Error 1
    make[1]: Leaving directory `~/gdb-7.6'
    make: *** [all] Error 2
```

I have found several sites on the internet suggesting installing the library libncurses5-dev, but have I already installed!
 

```
    $ sudo apt-get install libncurses5-dev
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    libncurses5-dev is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.
```

SO, I don't know what can I do to crosscompile gdbserver, please help!

Thanks in advance!!

regards

---

### Post by indarkness on 2013-06-07
I have found a workaround to cross-compile gbd, since i was only interested in crosscompiling the gdbserver, I went to that folder and using the cofigure there located, with my cross-compiling options, I hadn't got any trouble and now I get the gbd server for arm.

I hope this can help aother one with my same issue.

regards

---

