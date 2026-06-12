---
title: "Error while building Linux/ARM tool chain"
date: 2009-12-14
forum: Packaging and Compiling Programs
---

### Post by subash_patel on 2009-12-14
Hi,

I am rebuilding a ARM tool chain for one of the boards on Linux(Ubuntu). I am referring to this [link]("http://frank.harvard.edu/~coldwell/toolchain/") for the steps. WRT stages defined in the link mentioned before, I am having problem during the Stage 2 GCC (rebuilding gcc with stage-1 gcc and cross-compiled glibc). I am getting the below error, which I am not able to resolve. Can someone here help me with this?

Thanks,
Subash

$../../gcc-3.4.4/configure --prefix=${PREFIX} --target=${TARGET} --enable-languages=c --with-sysroot=${SYSROOT} 2>&1 | tee configure.out
$make
.....
.....
Configuring in gcc
configure: loading cache ./config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... arm-iMX-linux-gnu
checking LIBRARY_PATH variable... ok
checking GCC_EXEC_PREFIX variable... ok
checking whether to place generated files in the source directory... no
checking whether a default linker was specified... no
checking whether a default assembler was specified... no
checking for i686-pc-linux-gnu-gcc... arm-iMX-linux-gnu-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
make: *** [configure-gcc] Error 1

$ readlink `which gcc`
/usr/bin/gcc-4.3
$ echo $CC
arm-iMX-linux-gnu-gcc


Versions used =>
GCC : 3.4.4
GLIBC : 2.3.5
BINUTILS : 2.16

---

### Post by subash_patel on 2009-12-21
This is to help someone in future, who may face the same problem:

I think I have now solved the problem after googling a bit more. In the configure, we need to add --build=i686-linux (or anything to specify your host) to solve the error.

Thanks for viewing this post.

---

