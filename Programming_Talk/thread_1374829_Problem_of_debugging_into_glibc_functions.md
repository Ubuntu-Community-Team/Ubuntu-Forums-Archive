---
title: "Problem of debugging into glibc functions?"
date: 2010-01-07
forum: Programming Talk
---

### Post by davyzhu on 2010-01-07
Problem of debugging into glibc functions?

Hi all,

I want to debug into glibc functions like nftw() in Ubuntu Linux (nftw
require a function pointer argument and I want to step into this
function). 

But after installed libc6.dbg and set environment
LD_LIBRARY_PATH(I have to set it in gdb by "set env LD_LIBRARY_PATH
/usr/lib/debug"), my emacs/gdb still cannot step into the glibc
function.

Shall I compile the glibc by myself, or shall I set other environment
parameters?

Thanks!
Davy

---

### Post by dwhitney67 on 2010-01-07
Why not just set a breakpoint at the beginning of the function that you *really* need to debug?

You only need to debug something if you suspect there is a problem with it.  Do you suspect that there is a problem with the nftw() library function?  Is it not working according to the API description as outlined in the man-page?


P.S.  When you compile your application, why are you not linking with the library that contains the debugging symbols?  It seems, from your post, that you are linking your application with the regular, stripped-down, library... yet hoping to step through the one with the symbols at a later time.

---

### Post by jpkotta on 2010-01-07
I'm not sure if there is an easier way that this (there might be).

Example program:
```

#define _XOPEN_SOURCE 500
#include <ftw.h>

#include <stdio.h>
#include <errno.h>

int nftwfunc(const char *filename,
             const struct stat *statptr,
             int fileflags,
             struct FTW *pfwt)
{
    printf("Found file '%s'\n", filename);
    return 0;
}

int main(void)
{
    char *startpath = "/tmp";
    int fd_limit = 5;
    int flags = FTW_CHDIR | FTW_DEPTH | FTW_MOUNT;
    int err;

    err = nftw(startpath, nftwfunc, fd_limit, flags);
    if (err) {
        perror("Error!");
    }

    return 0;
}

```

You need the libc-dbg package and the libc source package.

```
sudo apt-get install libc6-dbg
mkdir ~/libc ; cd ~/libc
apt-get source libc6
rgrep --include=*.[ch] nftw ~/libc

```
It turns out that nftw is defined in ftw.c in ~/libc/glibc-2.9/io/.

So I can run gdb like so:
```

gcc -o nftw nftw.c
gdb ./nftw
```
```

directory ~/libc/glibc-2.9/io/ # tab completion works here
br nftwfunc
run
```
It should break when nftwfunc is called, and from there you can get a stack trace including nftw().  But it isn't actually called nftw() - there is a bunch of #define magic happening in ftw.c.  The real function is called ftw_startup().

---

### Post by felucca on 2010-02-15
Hi 

I am trying to do the same thing, but want to step through the malloc().

I installed the libc6-dbg and the source of the libc.

The following is the foo program that calls malloc,

>  15 #include <stdio.h>
 16 #include <stdlib.h>
 17
 18 int main() {
 19   int* pa = (int*)malloc(sizeof(int)*100);
 20
 21   printf("%p", pa);
 22   return 0;
 23 }

I compiled the source code with 

> /usr/lib/debug/libc.so.6

I've set the LD_LIBRARY_PATH to /usr/lib/debug, so the following is the ldd result

 > mjeong@hopper:~$ ldd ./a.out 
	linux-vdso.so.1 =>  (0x00007fff685ff000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007fb164f4e000)
	libm.so.6 => /usr/lib/debug/libm.so.6 (0x00007fb164cc9000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007fb164ab1000)
	libc.so.6 => /usr/lib/debug/libc.so.6 (0x00007fb16473f000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fb16525b000)

when I run gdb and set a breakpoint at malloc, it doesn't stop at the  /usr/lib/debug/libc.so.6, but at /lib64/ld-linux-x86-64.so.2.

> mjeong@hopper:~$ gdb --args ./a.out 
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(gdb) directory ~/libc/glibc-2.8~20080505/glibc-20080505/malloc
Source directories searched: /home/mjeong/libc/glibc-2.8~20080505/glibc-20080505/malloc:$cdir:$cwd
(gdb) b malloc
Function "malloc" not defined.
Make breakpoint pending on future shared library load? (y or [n]) y
Breakpoint 1 (malloc) pending.
(gdb) run
Starting program: /home/mjeong/a.out 

Breakpoint 1, 0x00007f62cebd2900 in malloc () from /lib64/ld-linux-x86-64.so.2
(gdb) n
Single stepping until exit from function malloc, 
which has no line number information.
0x00007f62cebbc9f8 in __libc_memalign@plt () from /lib64/ld-linux-x86-64.so.2
(gdb) 
Single stepping until exit from function __libc_memalign@plt, 
which has no line number information.
0x00007f62cebd27e0 in __libc_memalign () from /lib64/ld-linux-x86-64.so.2
(gdb) 
Single stepping until exit from function __libc_memalign, 
which has no line number information.
0x00007f62cebc708b in _dl_new_object () from /lib64/ld-linux-x86-64.so.2
(gdb) 
Single stepping until exit from function _dl_new_object, 
which has no line number information.
0x00007f62cebbea23 in dl_main () from /lib64/ld-linux-x86-64.so.2
(gdb) 
Single stepping until exit from function dl_main, 
which has no line number information.

What I want to do is to step through the malloc source code - just out of curiosity. My distro is Ubuntu 8.10 64-bit. 

Any help/comment/pointer to read would be much appreciated! Thanks!

---

### Post by felucca on 2010-02-16
Okay. Instead of putting breakpoint at malloc, I put breakpoint at the caller and stepped in. Of course the name of the real name of the malloc function isn't malloc!

> mjeong@hopper:~$ gdb a.out
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(gdb) directory libc/glibc-2.8~20080505/glibc-20080505/malloc/
Source directories searched: /home/mjeong/libc/glibc-2.8~20080505/glibc-20080505                                   /malloc:$cdir:$cwd
(gdb) l
10      //
11      //  cout << pa << endl;
12      //  cout << pb << endl;
13      //}
14
15      #include <stdio.h>
16      #include <stdlib.h>
17
18      int main() {
19        int* pa = (int*)malloc(sizeof(int)*100);
(gdb) b 19
Breakpoint 1 at 0x400644: file foo.cpp, line 19.
(gdb) run
Starting program: /home/mjeong/a.out

Breakpoint 1, main () at foo.cpp:19
19        int* pa = (int*)malloc(sizeof(int)*100);
(gdb) step
*__GI___libc_malloc (bytes=400) at malloc.c:3540
3540    {
Current language:  auto; currently c
(gdb) step
3544      __malloc_ptr_t (*hook) (size_t, __const __malloc_ptr_t) = __malloc_hoo                                   k;

---

