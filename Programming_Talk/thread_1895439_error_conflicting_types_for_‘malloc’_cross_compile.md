---
title: "error: conflicting types for ‘malloc’ cross compiler"
date: 2011-12-14
forum: Programming Talk
---

### Post by kr651129 on 2011-12-14
Well the title says it all but heres a little background.

I'm building a cross compiler I need to compile binutils and gcc, binutils being first.

Here's what I'm doing

```

$> export target=i586-elf
$> export prefix=/usr/local/cross
$> cd /usr/src
$> sudo su
#> mkdir build-binutils build-gcc
#> cd build-binutils
#> ../binutils-2.9.1/configure --target=$TARGET --prefix=$PREFIX --disable-nls
(top part of code cut off, showing the last few lines of output)
../../binutils-2.9.1/binutils/../libiberty/cplus-dem.c: At top level:
../../binutils-2.9.1/binutils/../libiberty/cplus-dem.c:3269:8: error: conflicting types for ‘malloc’
../../binutils-2.9.1/binutils/../libiberty/cplus-dem.c:3270:8: warning: conflicting types for built-in function ‘realloc’ [enabled by default]
make[1]: *** [cplus-dem.o] Error 1
make[1]: Leaving directory `/usr/src/build-binutils/binutils'
make: *** [all-binutils] Error 2

```

This worked under virtualbox but not under my main OS, no idea what I'md doing wrong, thought?

---

### Post by Bachstelze on 2011-12-14
Please provide the entire output. If necessary, gzip it and send it as an attachment.

---

### Post by Bachstelze on 2011-12-14
But for starters, what you are doing with your environment variables is wrong. For one thing, they are case-sensitive (like everything else in *NIX), and for another, they are not passed over when you use sudo.

---

### Post by kr651129 on 2011-12-14
I hand types my steps but I did have the correct case when trying to make ;)

I've attached the full output

---

### Post by Bachstelze on 2011-12-14
I get the same error here, it's a bug in the code:

```
char * malloc ();
```

but malloc returns void*. Any reason why you want to compile code from 14 years ago?

---

### Post by kr651129 on 2011-12-14
No idea, I thought I was downloading current code.  I'm interested in kernel dev so I can learn more about it and the tutorial I'm using is telling me this is the source to download

---

### Post by kr651129 on 2011-12-14
OOOOHHHH, I'm an idiot, I scrolled to far down the tree and downloaded the wrong version, my bad.  THANKS

---

### Post by Bachstelze on 2011-12-14
Well you can try with a [more recent binutils](ftp://ftp.gnu.org/gnu/binutils/) but chances are the tutorial you are using is outdated as well.

---

