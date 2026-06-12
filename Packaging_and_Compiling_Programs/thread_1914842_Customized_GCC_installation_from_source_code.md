---
title: "Customized GCC: installation from source code"
date: 2012-01-25
forum: Packaging and Compiling Programs
---

### Post by erotavlas on 2012-01-25
Hi,

I have some questions about installing GCC from source code. I have read the guide here [http://gcc.gnu.org/install/.]("http://gcc.gnu.org/install/") I need to install GCC in this way to enable performance optimization available for different system architectures.
In  particular I would like to add the support of graphite tool for the  auto parallelize capabilities of GCC. It requires the libraries Parma  Polyhedra Library (PPL) and CLooG-PPL. I have installed them from  repository. Let me begin with the questions:
1) the options  -mtune=native and -march=native allow to detect the current CPU and then  to optimize the code. For instance if the CPU is Intel Corei7 then the  specific options like -maes for AES or -msse4 for SSE4 or -mavx for AVX  are already enabled by default if the options the -mtune=native and  -march=native are provided? Another instance is for the AMD Bulldozer  architecture where the XOP, FMA4, and LWP instruction sets can be  enabled by -mxop, -mfma4, and -mlwp options.
2) the options  --with-arch-32, --with-arch-64, --with-cpu-32, --with-cpu-64,  --with-tune-32 and --with-tune-64 are used to control the default  optimization separately for 32-bit and 64-bit modes. I don't understand  how can I use them. For instance with a 64 bit system for instance  Ubuntu 11.10, what are the best setting? --with-arch64 --with-cpu-64 and  --with-tune-64?
3) I have ever installed the GCC from source code,  so I follow the GCC guide. I have to make a folder for compiling and  then I have to type the command

```

/my-source-gcc-path/configure -v  --enable-languages=c,c++,fortran --prefix=/my-build-gcc-path  --program-suffix=-4.6 --enable-shared --enable-linker-build-id  --with-system-zlib --libexecdir=/usr/lib --without-included-gettext  --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6  --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu  --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin  --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=native  --enable-checking=release --build=x86_64-linux-gnu  --host=x86_64-linux-gnu --target=x86_64-linux-gnu --with-fpmath=avx  --with-ppl --with-cloog
```

Finally, from the my-build-gcc folder, I have to type

```

make prolifiledbootstrap

```
Is it correct?
Any suggestions or questions are welcome.

Thank you in advance

---

### Post by oldos2er on 2012-01-25
Moved to Packaging and Compiling Programs.

---

### Post by erotavlas on 2012-01-27
Hi,

can someone help me?

---

