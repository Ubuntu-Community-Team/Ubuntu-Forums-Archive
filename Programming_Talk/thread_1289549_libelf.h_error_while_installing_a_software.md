---
title: "libelf.h error while installing a software"
date: 2009-10-12
forum: Programming Talk
---

### Post by vernam on 2009-10-12
Hi, 
I am trying to install a network simulator "atemu" on my lab machine, but when I run "make", it gives me an error about libelf.h. I have checked from synaptic manager that in my system "libelf1" - 131.4 version is installed.
I have installed the same simulator on my laptop, and it got installed without any trouble. I am not sure why is it so. Any help in this regard is highly appreciated. 
I am using Ubuntu Jaunty 9.04 version with 32-bit core duo processor. Following is the error snapshot.

In file included from os.h:59,
                 from defs.h:61,
                 from atmega128.c:52:
/usr/include/libelf.h:98: error: expected specifier-qualifier-list before ‘off64_t’
/usr/include/libelf.h:160: error: expected specifier-qualifier-list before ‘off64_t’
/usr/include/libelf.h:201: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elf_update’
/usr/include/libelf.h:207: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elf_getbase’
/usr/include/libelf.h:305: error: expected declaration specifiers or ‘...’ before ‘off64_t’
/usr/include/libelf.h:317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elf_getaroff’
atmega128.c: In function ‘atemu_load_file’:
atmega128.c:801: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
make[2]: *** [atmega128.o] Error 1

Thanks,
V

---

### Post by lloyd_b on 2009-10-13
It's a little hard to be certain, but I *think* you need the packages "libelfg0" and "libelfg0-dev", rather than "libelf1" and "libelf-dev".  I'm not sure exactly what the difference is between the two, but the "...elfg..." packages have a version number that's consistent with the version required by "atemu".

Lloyd B.

---

### Post by vernam on 2009-10-13
Hi lloyd_b,
Thanks for your reply. Problem got resolved. 

By the way, have you worked with atemu? I have installed atemu-0.3 version for now. I have source code for atemu-0.4 too but till now  I have been unsuccessful in building that. I appreciate help in this regard.

Following is the error snapshot.

$ make
make  all-recursive
make[1]: Entering directory `/home/v/atemu/atemu-0.4'
Making all in .
make[2]: Entering directory `/home/v/atemu/atemu-0.4'
if gcc -DHAVE_CONFIG_H -I. -I. -I.   -DRUNDIR=\"/usr/local/share/atemu/run\" -DCONFDIR=\"/usr/local/share/atemu/conf\" -DAPPDIR=\"/usr/local/share/atemu/apps\" -DDEVICEDIR=\"/usr/local/share/atemu/devices\" -I/usr/include/libxml2  -g -O2  -MT main.o -MD -MP -MF ".deps/main.Tpo" \
      -c -o main.o `test -f 'main.c' || echo './'`main.c; \
    then mv ".deps/main.Tpo" ".deps/main.Po"; \
    else rm -f ".deps/main.Tpo"; exit 1; \
    fi
main.c: In function ‘fork_compress’:
main.c:208: warning: incompatible implicit declaration of built-in function ‘execlp’
In function ‘open’,
    inlined from ‘fork_compress’ at main.c:174,
    inlined from ‘main’ at main.c:964:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/v/atemu/atemu-0.4'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/v/atemu/atemu-0.4'
make: *** [all] Error 2

Thanks,
V

---

### Post by lloyd_b on 2009-10-13
Not really familiar with "atemu", but it looks like a couple of minor bugs.

First:```
main.c:208: warning: incompatible implicit declaration of built-in function ‘execlp’
```can be fixed by adding```
#include <unistd.h>
``` at around line 58 of "main.c".

Second:```
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
```is correct - calling open() with the O_CREAT operation requires that the third parameter ("mode") must be provided.  You can clear this error by changing the line```
fd = open(fn, O_CREAT | O_WRONLY);
``` at around line 175 of main.c to ```
fd = open(fn, O_CREAT | O_WRONLY, 0700);
```Note that I'm not sure if this is the *correct* mode setting for this, but 700 (rwx------) seems reasonable.

Once you make these two changes, you should be able to get it to fully compile (though there are a few warnings along the way).

Lloyd B.

---

### Post by vernam on 2009-10-13
Thanks again,
It worked and fixed my problem. I appreciate your help. You just made my day :)

Thanks,
V

---

