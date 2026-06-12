---
title: "Howto install arm-linux-gcc"
date: 2007-02-13
forum: Programming Talk
---

### Post by frodux on 2007-02-13
Hi!

I'm trying to configure binutils(version not important at this point) for the arm architecture.
During the configuration however, I see that I need some cross compiler.
Some of the results from the configuration output is:

> /build-binutils$ ../binutils-2.17/configure --target=arm-linux --prefix=${PRJOOT}/tools
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... arm-unknown-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln works... (cached) yes
checking whether ln -s works... (cached) yes
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gnatbind... (cached) no
checking whether compiler driver understands Ada... (cached) no
checking how to compare bootstrapped objects... (cached) cmp --ignore-initial=16 $$f1 $$f2
checking for correct version of gmp.h... yes
checking for MPFR... yes
checking for bison... (cached) bison -y
checking for bison... (cached) bison
checking for gm4... (cached) m4
checking for flex... no
checking for lex... no
checking for flex... no
checking for makeinfo... no
checking for expect... no
checking for runtest... no
checking for i686-pc-linux-gnu-ar... (cached) ar
checking for i686-pc-linux-gnu-as... (cached) as
checking for i686-pc-linux-gnu-dlltool... no
checking for dlltool... no
checking for i686-pc-linux-gnu-ld... (cached) ld
checking for i686-pc-linux-gnu-lipo... no
checking for lipo... no
checking for i686-pc-linux-gnu-nm... (cached) nm
checking for i686-pc-linux-gnu-ranlib... (cached) ranlib
checking for i686-pc-linux-gnu-strip... (cached) strip
checking for i686-pc-linux-gnu-windres... no
checking for windres... no
checking for i686-pc-linux-gnu-objcopy... (cached) objcopy
checking for i686-pc-linux-gnu-objdump... (cached) objdump
checking for arm-linux-cc... no
checking for arm-linux-gcc... no
checking for arm-linux-c++... no
checking for arm-linux-g++... no
checking for arm-linux-cxx... no
checking for arm-linux-gxx... no
checking for arm-linux-gcc... no
checking for arm-linux-gcj... no
checking for arm-linux-gfortran... no
checking for ar... no
checking for arm-linux-ar... no
checking for as... no
checking for arm-linux-as... no
checking for dlltool... no
checking for arm-linux-dlltool... no
checking for ld... no
checking for arm-linux-ld... no
checking for lipo... no
checking for arm-linux-lipo... no
checking for nm... no
checking for arm-linux-nm... no
checking for objdump... no
checking for arm-linux-objdump... no
checking for ranlib... no
checking for arm-linux-ranlib... no
checking for strip... no
checking for arm-linux-strip... no
checking for windres... no
checking for arm-linux-windres... no
checking where to find the target ar... just compiled
checking where to find the target as... just compiled
checking where to find the target cc... pre-installed
checking where to find the target c++... pre-installed
checking where to find the target c++ for libstdc++... pre-installed
checking where to find the target dlltool... just compiled
checking where to find the target gcc... pre-installed
checking where to find the target gcj... pre-installed
checking where to find the target gfortran... pre-installed
checking where to find the target ld... just compiled
checking where to find the target lipo... pre-installed
checking where to find the target nm... just compiled
checking where to find the target objdump... just compiled
checking where to find the target ranlib... just compiled
checking where to find the target strip... just compiled
checking where to find the target windres... just compiled
checking whether to enable maintainer-specific portions of Makefiles... no
creating ./config.status
creating Makefile


Obviously the config script not finding any cross compiler is a problem as I need to cross compile the binutils. Forgive me if I'm wrong, but I'm backtracing a bug where this seems to  be the main error.
So I need to enable my native gcc to be able to cross compile or maybe install arm-linux-gcc on its own.

As seen on
[http://gcc.gnu.org/install/configure.html]("http://gcc.gnu.org/install/configure.html") 
I should be able to use some of these commands to install a gcc that supports cross compiling :

> --with-cpu=cpu
Specify which cpu variant the compiler should generate code for by default. cpu will be used as the default value of the -mcpu= switch. This option is only supported on some targets, including ARM, i386, M68k, PowerPC, and SPARC. 
--with-schedule=cpu
--with-arch=cpu
--with-tune=cpu
--with-abi=abi
--with-fpu=type
--with-float=type
These configure options provide default values for the -mschedule=, -march=, -mtune=, -mabi=, and -mfpu= options and for -mhard-float or -msoft-float. As with --with-cpu, which switches will be accepted and acceptable values of the arguments depend on the target. 
--with-mode=mode
Specify if the compiler should default to -marm or -mthumb. This option is only supported on ARM targets.

But this will make my nativ gcc use cross compilation as default, which I do not want.
Does anybody have any good ideas on how to do this? Do I need to install a separate gcc for cross compiling? And if so, does anybody have a good howto on that. I have seen that there is also possible to install own packages with "arm-linux-gcc" cross compilers, but I have still not found any good HOWTO or good sources for this.

All ideas are welcome.
I'm currently using Kubuntu Edgy.

Thanxs.
F

---

### Post by frodux on 2007-02-14
Sorry, my bad.

It was late at night and I was tired. The configuration works well.

F

---

### Post by anuragccsu on 2009-06-15
Hi Frodux,

i also tried all those same things like building binutils, gcc and insight. everything worked. ultimately i am left with the installed tools for cross compilation.
Now forgive me as i am very new to this domain:
can you tell how to compile an ARM assembly program or a C program for ARM target and how to generate assembly file for a C program and after that how to run and check the result like suppose i write a simple C program in C.

int i;
i = 5;
the how to compile and run to check (if i use printf family of functions)...


Mailme: [email]anuragccsu@gmail.com[/email]

---

### Post by LiaGalanodel on 2009-10-14
Hi!

I have the same problems. I want to install acrooq compiler for arm but whan I try to install binulties for example I have many errors.

If you have a solution anuragccsu. Can you help me?

Thank you,

Best regards,

---

### Post by MindSz on 2009-10-14
I use a separate compiler. So in my computer I have the gcc compiler, but I also have an arm-linux-gcc compiler.

To compile using the ARM gcc compiler type 

```
arm-linux-gcc -mcpu=arm9 -Wall -o progName progCode.c
```

I think you can get the compiler off of the internet for free. I got it at [www.embeddedARM.com](www.embeddedARM.com) (I use those cards a lot at work)

---

### Post by LiaGalanodel on 2009-10-15
Thank you very much!

I try to install it now.

---

### Post by LiaGalanodel on 2009-10-15
Ok! It's good!

My arm-linux-gcc is install. Now I want install a debugger arm. I search a solution ;)

Well,

Thank you very much!

Best regards,

---

### Post by LiaGalanodel on 2009-10-16
I have a new question about arm-gcc-linux.

I use :
```

export PATH=/usr/local/arm/3.3.2/bin:$PATH 
```

And when I restart my computer I can't use arm-linux-gcc but if I write again export. arm-gcc-linux is like reinstall and I can use it.

Why I must write again the code?

Thank you,

---

### Post by MindSz on 2009-10-16
Since I have to use both compilers (gcc and arm-linux-gcc) I have a small shell script (which I stored in /bin) to take care of the compilation.

It compiles the program and produces an executable file with the same name as the code file (so for 'example.c' it will produce the executable 'example') and shows any warnings/errors on the screen.

I'm not a shell expert, so it's probably not the best way to do it, but it works for me. Here:

```
#!/bin/bash

#variables por parametros
archivoEntrada=$1.c
archivoSalida=$1

echo
echo
echo
echo
clear
#echo $archivoEntrada
#echo "Exportando path"
export PATH=$PATH:/usr/local/opt/crosstool/arm-linux/gcc-3.3.4-glibc-2.3.2/bin
#echo 

#echo "Compilando con arm-linux-gcc"
#echo "$archivoEntrada to> $archivoSalida"
arm-linux-gcc -mcpu=arm9 -Wall -o $archivoSalida $archivoEntrada
echo

#echo "Integridad del ejecutable ARM-Binary:"
#file $archivoSalida
#echo

#echo "Modificando permisos to> a+rwx"
chmod a+rx $archivoSalida
echo

#echo "---Ok---"
echo 
echo
echo
echo

```

If you want to use it, then to compile a program you need to type the name of the file without the '.c'. So if you have a program called 'code.c', you should type ```
compile code
``` and it will produce an executable called 'code'

Note: If you understand spanish then it should be easy to figure out what's going on in the code ;)

---

### Post by LiaGalanodel on 2009-10-26
I don't speak spanish very well but I can try :)

Thank you for your answer I will try to use this file.

Best regards.

---

### Post by LiaGalanodel on 2009-10-29
Thank you very very much! It's work good!

Best regards!

---

