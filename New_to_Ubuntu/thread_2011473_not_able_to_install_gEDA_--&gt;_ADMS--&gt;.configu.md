---
title: "not able to install gEDA --&gt; ADMS--&gt;./configure   on 12.04"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by idom on 2012-06-27
I want to try out AMDS along with ngspice for some personal R&D .

I did following stuff.

1. Downloaded and unzipped the adms-2.2.9.tar.gz  from [http://vacomp.noovela.com/](http://vacomp.noovela.com/)
2. Tried to follow instruction in README ( also attached ) for linux installation as I have unbuntu 12.04 on my machine.

0- Prerequisites
    0- gnu make is required (do not use other native make)
 
1- Description
  ADMS is a code generator that converts electrical compact device models
  specified in high-level description language into ready-to-compile c code
  for the API of spice simulators.

2- Installation - Unix or Linux
    0- run: ./configure - see file INSTALLATION for more options
    1- run: gmake
    2- run: gmake install
  If the installation fails try:
    0- run: autoheader
    1- run: aclocal
    2- run: automake
    3- run: autoconf
    4- run: ./configure - see file INSTALLATION for more options
    5- run: gmake
    6- run: gmake install
    In two shots:
      autoheader && aclocal && automake && autoconf && ./configure
      gmake && gmake install



I have following queries.

searched google and found that gmake =make in ubuntu and confirmed by  <make --version> command and output is pasted below.

GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

./configure is giving following outputs

9$ ./configure
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name...
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

Please help.
is there any other way to fix this

---

### Post by idom on 2012-06-27
I was able to progress further. figured out that g++/bison/flex are not installed so I used ubuntu software centre and install all of them and this is the new status.


./configure went through.
make 
make install ( I had to do sudo as some permission were denied)

now what do ?

$ admsXml -v 
admsXml: error while loading shared libraries: libadmsElement.so.0: cannot open shared object file: No such file or directory

Help is greatly appreciated

idom 

> **idom said:**
> I want to try out AMDS along with ngspice for some personal R&D .

I did following stuff.

1. Downloaded and unzipped the adms-2.2.9.tar.gz  from [http://vacomp.noovela.com/](http://vacomp.noovela.com/)
2. Tried to follow instruction in README ( also attached ) for linux installation as I have unbuntu 12.04 on my machine.

0- Prerequisites
    0- gnu make is required (do not use other native make)
 
1- Description
  ADMS is a code generator that converts electrical compact device models
  specified in high-level description language into ready-to-compile c code
  for the API of spice simulators.

2- Installation - Unix or Linux
    0- run: ./configure - see file INSTALLATION for more options
    1- run: gmake
    2- run: gmake install
  If the installation fails try:
    0- run: autoheader
    1- run: aclocal
    2- run: automake
    3- run: autoconf
    4- run: ./configure - see file INSTALLATION for more options
    5- run: gmake
    6- run: gmake install
    In two shots:
      autoheader && aclocal && automake && autoconf && ./configure
      gmake && gmake install



I have following queries.

searched google and found that gmake =make in ubuntu and confirmed by  <make --version> command and output is pasted below.

GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

./configure is giving following outputs

9$ ./configure
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name...
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

Please help.
is there any other way to fix this

---

