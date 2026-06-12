---
title: "can not compile using gcc 3.4 or 4.0"
date: 2006-10-07
forum: Programming Talk
---

### Post by newsman on 2006-10-07
i am trying to compile mspgcc utility using the instructions given on :

[http://www.chadmetcalf.com/tinyos-1x-on-ubuntu/](http://www.chadmetcalf.com/tinyos-1x-on-ubuntu/)

for purposes of this forum the specific instructions which i am stuck on are copied and pasted below:

There is a script in tinyos-1.x/tools/src/mspgcc/ to download, compile and install MSPGCC. The download location that the script tried to use to download GCC was down. So edit the following line on line 62.

GCC32_URL="ftp://mirrors.rcn.net/pub/sourceware/gcc/releases/gcc-3.2.3/gcc-core-3.2.3.tar.bz2"

with:

GCC32_URL="ftp://sources.redhat.com/pub/gcc/releases/gcc-3.2.3/gcc-core-3.2.3.tar.bz2"

Now we can run the build script. You need to use gcc 3.3 or 3.4 because 4.0 will fail to compile.

export CC=gcc-3.4
export CXX=gcc-3.4
sudo ./build-mspgcc install


When i follow the above instructions i get:

processing MSPGCC_CVS
download MSPGCC_CVS: found archive/mspgcc-cvs.tar.gz, skipping download
found build/mspgcc-cvs, skipping decompress
found build/mspgcc-cvs/build-complete, skipping build
installing MSPGCC_CVS

processing BINUTILS
download BINUTILS: found archive/binutils-2.17.tar.bz2, skipping download
found build/binutils-2.17, skipping decompress
building BINUTILS
loading cache ./config.cache
checking host system type... i686-pc-linux-gnulibc1
checking target system type... msp430-unknown-none
checking build system type... i686-pc-linux-gnulibc1
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc-3.4
checking whether the C compiler (gcc-3.4  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
-----------------------------------------------------------------------
using gcc 4.0 it results in exactly same error:


processing MSPGCC_CVS
download MSPGCC_CVS: found archive/mspgcc-cvs.tar.gz, skipping download
found build/mspgcc-cvs, skipping decompress
found build/mspgcc-cvs/build-complete, skipping build
installing MSPGCC_CVS

processing BINUTILS
download BINUTILS: found archive/binutils-2.17.tar.bz2, skipping download
found build/binutils-2.17, skipping decompress
building BINUTILS
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... msp430-unknown-none
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
umar@umar-laptop:~/tinyos-1.x/tools/src/mspgcc$ export CC=gcc-4.0
umar@umar-laptop:~/tinyos-1.x/tools/src/mspgcc$ export CXX=gcc-4.0
umar@umar-laptop:~/tinyos-1.x/tools/src/mspgcc$ sudo ./build-mspgcc install

processing MSPGCC_CVS
download MSPGCC_CVS: found archive/mspgcc-cvs.tar.gz, skipping download
found build/mspgcc-cvs, skipping decompress
found build/mspgcc-cvs/build-complete, skipping build
installing MSPGCC_CVS

processing BINUTILS
download BINUTILS: found archive/binutils-2.17.tar.bz2, skipping download
found build/binutils-2.17, skipping decompress
building BINUTILS
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... msp430-unknown-none
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc-4.0
checking whether the C compiler (gcc-4.0  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

---

### Post by yannael on 2006-10-27
Hi,

I had the same problem. It worked after installing the build-essential package.

Cheers,

Yann-Aël

---

