---
title: "linking shared 64-bit libpcre3 - missing something simple?"
date: 2011-11-07
forum: Packaging and Compiling Programs
---

### Post by jcwoods on 2011-11-07
I'm having a great deal of trouble linking libpcre to an application after moving from an older workstation running Ubuntu 11.04/32-bit to 11.10/64-bit on a new workstation.

First, libpcre3 does not install a libpcre.so symlink for the 64-bit libraries as the 32-bit package does.  This was resolved by manually creating a symbolic link in the appropriate (?) place.  The library is now found (see strace below) during the linking process.

When compiling with the "-lpcre" flag, I still get unresolved symbols even though the library was found:

[INDENT][FONT="Courier New"]$ gcc -Wall -lpcre -o regexlist regexlist.c 
/tmp/cchfHl80.o: In function `REL_LoadPatterns':
regexlist.c: (.text+0x4ec): undefined reference to `pcre_compile2'
regexlist.c: (.text+0x5f6): undefined reference to `pcre_study'
/tmp/cchfHl80.o: In function `REL_WhiteList':
regexlist.c: (.text+0x7ca): undefined reference to `pcre_exec'
collect2: ld returned 1 exit status[/FONT][/INDENT]

Confirming the library was found using strace:

[INDENT][FONT="Courier New"]$ strace -o /tmp/pcre.log -f gcc -Wall -lpcre -o regexlist regexlist.c 
/tmp/ccWGE4EP.o: In function `REL_LoadPatterns':
regexlist.c: (.text+0x4ec): undefined reference to `pcre_compile2'
regexlist.c: (.text+0x5f6): undefined reference to `pcre_study'
/tmp/ccWGE4EP.o: In function `REL_WhiteList':
regexlist.c: (.text+0x7ca): undefined reference to `pcre_exec'
collect2: ld returned 1 exit status
$ grep libpcre.so /tmp/pcre.log 
9057  stat("/usr/lib/gcc/x86_64-linux-gnu/4.6.1/libpcre.so", 0x7fff84c09240) = -1 ENOENT (No such file or directory)
9057  open("/usr/lib/gcc/x86_64-linux-gnu/4.6.1/libpcre.so", O_RDONLY) = -1 ENOENT (No such file or directory)
[B]9057  stat("/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../x86_64-linux-gnu/libpcre.so", {st_mode=S_IFREG|0644, st_size=243800, ...}) = 0
9057  open("/usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../x86_64-linux-gnu/libpcre.so", O_RDONLY) = 7
[/B][/FONT][/INDENT]

Resolving the symlink to the target library:

[INDENT][FONT="Courier New"]$ readlink -f /usr/lib/gcc/x86_64-linux-gnu/4.6.1/../../../x86_64-linux-gnu/libpcre.so
/lib/x86_64-linux-gnu/libpcre.so.3.12.1[/FONT][/INDENT]

Checking that the architecture of the resolved library is correct:

[INDENT][FONT="Courier New"]$ file /lib/x86_64-linux-gnu/libpcre.so.3.12.1
/lib/x86_64-linux-gnu/libpcre.so.3.12.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped[/FONT][/INDENT]

And verifying that my symbols are present in the library:

[INDENT][FONT="Courier New"]$ nm -D /lib/x86_64-linux-gnu/libpcre.so.3.12.1 | grep pcre_compile2
000000000000a410 T pcre_compile2
$ nm -D /lib/x86_64-linux-gnu/libpcre.so.3.12.1 | grep pcre_study
0000000000026c70 T pcre_study
$ nm -D /lib/x86_64-linux-gnu/libpcre.so.3.12.1 | grep pcre_exec
00000000000239a0 T pcre_exec[/FONT][/INDENT]

I'm sure that I'm missing something very simple, but I don't see it!  Any thoughts?

---

### Post by SevenMachines on 2011-11-07
This is due to to --as-needed being passed by default to gcc nowadays,  theres many unresolved symbol threads in the forum for further  explanation
[http://wiki.debian.org/ToolChain/DSO...eededlibraries]("http://wiki.debian.org/ToolChain/DSOLinking#Onlylinkwithneededlibraries")

In short, put the libraries to link to after the source, eg
```
$ gcc -lpcre -o pcredemo pcredemo.c       
/tmp/cc91X72q.o: In function `main':
pcredemo.c:(.text+0x124): undefined reference to `pcre_compile'
pcredemo.c:(.text+0x18e): undefined reference to `pcre_exec'
pcredemo.c:(.text+0x1ca): undefined reference to `pcre_free'
pcredemo.c:(.text+0x2ac): undefined reference to `pcre_fullinfo'
pcredemo.c:(.text+0x2ec): undefined reference to `pcre_fullinfo'
pcredemo.c:(.text+0x309): undefined reference to `pcre_fullinfo'
pcredemo.c:(.text+0x3ca): undefined reference to `pcre_free'
pcredemo.c:(.text+0x3fa): undefined reference to `pcre_fullinfo'
pcredemo.c:(.text+0x428): undefined reference to `pcre_config'
pcredemo.c:(.text+0x518): undefined reference to `pcre_exec'
pcredemo.c:(.text+0x5f4): undefined reference to `pcre_free'
pcredemo.c:(.text+0x7ad): undefined reference to `pcre_free'
collect2: ld returned 1 exit status

$ gcc -o pcredemo pcredemo.c -lpcre

$ ./pcredemo 
Two arguments required: a regex and a subject string

```

---

### Post by jcwoods on 2011-11-08
Yep... that did it.  Changing the compiler command from:

[INDENT]gcc -Wall -lpcre -o regexlist regexlist.c[/INDENT]

to:

[INDENT]gcc -Wall -o regexlist regexlist.c -lpcre[/INDENT]

was all that it took.  Thanks!!

---

