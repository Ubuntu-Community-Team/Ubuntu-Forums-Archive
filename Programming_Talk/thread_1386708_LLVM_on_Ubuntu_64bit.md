---
title: "LLVM on Ubuntu 64bit"
date: 2010-01-21
forum: Programming Talk
---

### Post by strange_1889 on 2010-01-21
I'm trying to build & install the LLVM 2.6 & the LLVM-GCC front-end. but have run into numerous issues. 

i was told i cant use the build's in the repo's, but not given a reason why.

I've got moderate experience with K/Ubuntu (was my main system for a year)
Current System:
Ubuntu9.04 64bit running in VirtualBox on a Win7 amd64 host. the VM reports the processor as amd athlon x2 QL-65 (same as host)
GCC 4.3.3
LLVM source is at /usr/local/src/llvm-2.6
LLVM-gcc source is at /usr/local/src/llvm-gcc4.2-2.6.source
             llvm-gcc obj is at /usr/local/src/obj
             llvm-gcc install is at /usr/local/src/install


followed installation instructions in the llvm-gcc readme.llvm

my configure line reads:

LLVM-GCC

/usr/local/src/obj$ /usr/local/src/llvm-gcc4.2-2.6.source/configure --prefix=/usr/local/src/install --program-prefix=llvm-     --enable-llvm=/usr/local/src/llvm-2.6 --enable-languages=c,c++

then make spits out:

configure: error: You must specify valid path to your LLVM tree with --enable-llvm=DIR

---

i read the linux-specific config but I couldn't get that to work either

/usr/local/src/llvm-gcc4.2-2.6.source/configure --prefix=/usr/local/src/install --program-prefix=llvm-     --enable-llvm=/usr/local/src/llvm-2.6 --enable-languages=c,c++ --target=i686-pc-linux-gnu --with-tune=generic --with-arch=amd64

make spits out

checking for C compiler default output file name... configure: error: C compiler cannot create executables

------ 

LLVM

/usr/local/src/llvm-2.6/configure --prefix=/usr/local/src/obj --enable-optimized

spits out "already configured"

while that may be true I need to reconfigure with these options.

I havent tried to make yet b/c whatever it gives me wont be right.

i've read several conflicting posts about what to set your environment var's to & if its neccessary. i can't quite make sense of the instructions from the dev b/c it seems you need to have llvm installed to install the gcc front end & you need the gcc front end installed before llvm in order to hook it up!

---

