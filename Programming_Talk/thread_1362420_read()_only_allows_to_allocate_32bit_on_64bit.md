---
title: "read() only allows to allocate 32bit on 64bit"
date: 2009-12-23
forum: Programming Talk
---

### Post by monkeyking on 2009-12-23
Hi I've found a strange problem on ubuntu64bit, that limits the data you are allowed to allocate on a 64bit platform using the c function 'read()'

The following program wont allow to allocate more that 2.1gig memory.

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <err.h>
#include <fcntl.h>
#include <sysexits.h>
#include <unistd.h>
#include <sys/stat.h>

// get bytesize of file
size_t fsize(const char* fname){
  struct stat st ;
  stat(fname,&st);
  return st.st_size;
}

int main() {
  const char *infile = "bigfile.dat";
  int fd;
  size_t bytes_read, bytes_expected = fsize(infile);
  char *data;
 printf("\nLONG_MAX:%lu\n",LONG_MAX);

  if ((fd = open(infile,O_RDONLY)) < 0)
    err(EX_NOINPUT, "%s", infile);

  if ((data =(char *) malloc(bytes_expected)) == NULL)
    err(EX_OSERR, "data malloc");


  bytes_read = read(fd, data, bytes_expected);

  if (bytes_read != bytes_expected)
    err(EX_DATAERR, "Read only %lu of %lu bytes",bytes_read, bytes_expected);

  /* ... operate on data ... */

  free(data);

  exit(EX_OK);
}
[/PHP]

```

./a.out
LONG_MAX:9223372036854775807
a.out: Read only 2147479552 of 2163946253 bytes: Success

```
According to man 2 read, the maximum is limited by SSIZE_MAX
which is defined in

/usr/include/bits/posix1_lim.h
# define SSIZE_MAX  LONG_MAX

And LONG_MAX is defined in /usr/include/limits.h as
#  if __WORDSIZE == 64
#   define LONG_MAX     9223372036854775807L
#  else
#   define LONG_MAX     2147483647L
#  endif
#  define LONG_MIN      (-LONG_MAX - 1L)

Either this is a bug in the ubuntu buildsystem,
or my build system is broken.

Can anyone with a 64 try to run the above program.

Thanks

edit:

by the way
```

readelf -h ./a.out
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              EXEC (Executable file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x400750
  Start of program headers:          64 (bytes into file)
  Start of section headers:          5312 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         9
  Size of section headers:           64 (bytes)
  Number of section headers:         37
  Section header string table index: 34

```

```

ldd ./a.out
        linux-vdso.so.1 =>  (0x00007fff689ff000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007ffee433e000)
        libm.so.6 => /lib/libm.so.6 (0x00007ffee40ba000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007ffee3ea3000)
        libc.so.6 => /lib/libc.so.6 (0x00007ffee3b34000)
        /lib64/ld-linux-x86-64.so.2 (0x00007ffee464e000)


```

---

### Post by MadCow108 on 2009-12-23
edit: misinterpreted something

---

### Post by geirha on 2009-12-23
Reading this thread made me remember a similar thread where the problem was writing files larger than 2GiB. By default the maximum file size is 2GiB unless you do some magic ...

[http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)
[http://ubuntuforums.org/showthread.php?t=955420](http://ubuntuforums.org/showthread.php?t=955420)

---

### Post by MadCow108 on 2009-12-23
> **geirha said:**
> Reading this thread made me remember a similar thread where the problem was writing files larger than 2GiB. By default the maximum file size is 2GiB unless you do some magic ...

[http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)
[http://ubuntuforums.org/showthread.php?t=955420](http://ubuntuforums.org/showthread.php?t=955420)

this is only important for 32 bit systems.
on 64bit systems it should be enabled by default.

---

### Post by Andrey2009 on 2009-12-24
Just a sentence. Probably there is an error here that is alike the one described:
[Problems of 64-bit code in real programs: FreeBSD]("http://www.viva64.com/blog/en/2009/02/02/9/")

---

### Post by monkeyking on 2009-12-25
Thanks,
does anyone know how i browse the sourcecode for the 'read' function defined in /usr/include/unistd.h

I tried
dpkh -S /usr/include/unistd.h
which told me I had to use sourcepackage
So I did a
apt-get source libc
which gave me a 150 meg directory eglibc-2.10.1/, with alot of source code.

Does anyone know how to find a specific function, in this mess.


Thanks

---

### Post by Hellkeepa on 2009-12-25
HELLo!

This should do it:
```
grep -iHnrE "function \([^)]*\)" *
```
Call that from the root path of the source, and it'll traverse everything looking for the function "function". 

Happy codin'!

---

### Post by monkeyking on 2009-12-26
Thanks for all your replies,
but it seems that its not possible to use posix read to read files larger than 2.1 gig.
This is according to the uberpenguin linus
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=e28cc715](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=e28cc715)

At somepoint I guess it was possible but the kernel has regressed to only allow smaller chunks being read.

kernelsourcetree/fs/read_write.c
[PHP]
/*
 * rw_verify_area doesn't like huge counts. We limit
 * them to something that fits in "int" so that others
 * won't have to do range checks all the time.
 */
#define MAX_RW_COUNT (INT_MAX & PAGE_CACHE_MASK)

int rw_verify_area(int read_write, struct file *file, loff_t *ppos, size_t count);
[/PHP]
This was rather annoying, it would have been nice if this had been documented outside of the kernelsource and kernelmailinglist.

---

