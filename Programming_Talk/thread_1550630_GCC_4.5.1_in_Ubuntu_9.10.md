---
title: "GCC 4.5.1 in Ubuntu 9.10?"
date: 2010-08-11
forum: Programming Talk
---

### Post by christian.convey on 2010-08-11
Anyone know where I can get pre-built packages (or tarballs) of GCC 4.5.1 for use on a 64-bit Ubuntu 9.10 system?  Is there a PPA?
 
I've tried downloading the source for GCC 4.5.1 (plus the three helper libraries needed to built it), but I'm getting a build error.

---

### Post by interval1066 on 2010-08-11
This is  a sucky answer but let me ask; why do you want 4.5.1? Lucid is only on 4.4.3, and that is sufficient to give you stuff like C++0x, if your after the latest stuff:

$ gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
$

Is there some funky-fresh feature you want that only 4.5.1 provides? Forcing an application as massive as gcc into a platform that may not be ready for it can have implications you may not want to deal with.

---

### Post by MadCow108 on 2010-08-11
gcc 4.5 has a link time optimizer :)
also it is always a good idea to test if your program compiles also in the newer versions and the static analyzing gets better with each release (although it still sucks ^^)

I'm using this on my testing installation:
[https://launchpad.net/~ubuntu-toolchain/+archive/test](https://launchpad.net/~ubuntu-toolchain/+archive/test)

---

### Post by ssam on 2010-08-11
there is a gcc-snapshot package, the version in lucid is 20100414-0ubuntu1 (which i guess is pretty close to gcc 4.5.0).

or you could build your own. it is quite a challenge to build. i made some scripts to install gcc4.4.4 and 4.5.1 on to a scientific linux machine. the 4.4.4 contains some dependencies needed for both. it creates the actual binaries as gcc451-real, and then makes a gcc451 wrapper script, because otherwise i had issues with libraries.

```

#!/bin/bash -e
set -v

export PREFIX=/opt/gcc
export PATH=$PREFIX/bin:$PATH
export BUILDDIR=/tmp/sam/build
export CC="/usr/bin/gcc"
export CXX="/usr/bin/g++"
export MAKE_ARG=" -j4"


#rm -rf $PREFIX
mkdir -p $PREFIX
mkdir -p $PREFIX/lib
mkdir -p $BUILDDIR

#if false; then
cd $BUILDDIR
wget -c ftp://gcc.gnu.org/pub/gcc/infrastructure/gmp-4.3.2.tar.bz2
rm -rf gmp-4.3.2
tar xf gmp-4.3.2.tar.bz2
cd gmp-4.3.2
./configure --prefix=$PREFIX --enable-cxx
make $MAKE_ARG
#make check
make install


#if false; then
cd $BUILDDIR
wget -c ftp://gcc.gnu.org/pub/gcc/infrastructure/mpfr-2.4.2.tar.bz2
rm -rf mpfr-2.4.2
tar xf mpfr-2.4.2.tar.bz2
cd mpfr-2.4.2
./configure --prefix=$PREFIX  --with-gmp=$PREFIX
#./configure --prefix=$PREFIX --with-libgmp=$GMPPREFIX
make $MAKE_ARG
make check
make install
#fi

cd $BUILDDIR
wget -c http://www.cs.unipr.it/ppl/Download/ftp/releases/0.10.2/ppl-0.10.2.tar.bz2
rm -rf ppl-0.10.2
tar xf ppl-0.10.2.tar.bz2
cd ppl-0.10.2
./configure --prefix=$PREFIX --enable-interfaces="c cxx" --with-libgmp-prefix=$PREFIX --with-libgmpxx-prefix=$PREFIX
make $MAKE_ARG
make install

export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH

cd $BUILDDIR
wget -c ftp://gcc.gnu.org/pub/gcc/infrastructure/cloog-ppl-0.15.9.tar.gz
rm -rf cloog-ppl-0.15.9
tar xf cloog-ppl-0.15.9.tar.gz
cd cloog-ppl-0.15.9
./configure --prefix=$PREFIX --with-ppl=$PREFIX  --with-gmp=$PREFIX
make $MAKE_ARG
#make check
make install



cd $BUILDDIR
wget -c ftp://ftp.mirrorservice.org/sites/sourceware.org/pub/gcc/releases/gcc-4.4.4/gcc-4.4.4.tar.bz2
rm -rf gcc-4.4.4
tar xf gcc-4.4.4.tar.bz2
cd gcc-4.4.4
mkdir objdir
cd objdir
../configure --prefix=$PREFIX --program-suffix=444-real --with-ppl --with-cloog --with-mpfr=$PREFIX --with-gmp --enable-languages=c,c++,fortran  --enable-shared --enable-multiarch --enable-linker-build-id --enable-threads=posix --enable-checking --with-system-zlib --with-pkgversion="tygier"
nice make $MAKE_ARG
make install


cd $PREFIX/bin
for f in *-real
do
	binname=`echo $f | sed "s/-real//"`
	echo $binname "->" $f
	echo '#!/bin/sh' > $binname
	echo "export LD_LIBRARY_PATH=$PREFIX/lib:\$LD_LIBRARY_PATH" >> $binname
	echo "exec ${PREFIX}/bin/$f \"\$@\"" >>$binname
	chmod +x $binname
done


```

and

```

#!/bin/bash -e
set -v

export PREFIX=/opt/gcc
export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH
export PATH=$PREFIX/bin:$PATH
export BUILDDIR=/tmp/sam/build
export CC="$PREFIX/bin/gcc444"
export CXX="$PREFIX/bin/g++444"
export MAKE_ARG=" -j4"


#rm -rf $PREFIX
mkdir -p $PREFIX
mkdir -p $PREFIX/lib
mkdir -p $BUILDDIR


#if false; then
cd $BUILDDIR
wget -c http://www.multiprecision.org/mpc/download/mpc-0.8.1.tar.gz
rm -rf mpc-0.8.1
tar xf mpc-0.8.1.tar.gz
cd mpc-0.8.1
./configure --prefix=$PREFIX --with-mpfr=$PREFIX --with-gmp=$PREFIX
make $MAKE_ARG
make check
make install

cd $BUILDDIR
wget -c http://www.mr511.de/software/libelf-0.8.13.tar.gz
rm -rf libelf-0.8.13
tar xf libelf-0.8.13.tar.gz
cd libelf-0.8.13
./configure --prefix=$PREFIX
nice make $MAKE_ARG
make install
#fi

cd $BUILDDIR
wget -c ftp://gcc.gnu.org/pub/gcc/releases/gcc-4.5.1/gcc-4.5.1.tar.bz2
rm -rf gcc-4.5.1
tar xf gcc-4.5.1.tar.bz2
cd gcc-4.5.1


mkdir objdir
cd objdir
../configure --prefix=$PREFIX --program-suffix=451-real --with-pplr=$PREFIX --with-cloogr=$PREFIX --with-mpfr=$PREFIX --with-gmp=$PREFIX --enable-languages=c,c++,fortran --enable-lto --with-libelf=$PREFIX --enable-shared --enable-multiarch --enable-linker-build-id --enable-threads=posix --enable-checking --with-system-zlib  --with-pkgversion="tygier"

nice make $MAKE_ARG
make install


cd $PREFIX/bin
for f in *-real
do
	binname=`echo $f | sed "s/-real//"`
	echo $binname "->" $f
	echo '#!/bin/sh' > $binname
	echo "export LD_LIBRARY_PATH=$PREFIX/lib:\$LD_LIBRARY_PATH" >> $binname
	echo "exec ${PREFIX}/bin/$f \"\$@\"" >>$binname
	chmod +x $binname
done

for f in c++ cpp g++ gcc gccbug gcov gfortran
do
	ln -s ${f}451 $f
done


```

---

