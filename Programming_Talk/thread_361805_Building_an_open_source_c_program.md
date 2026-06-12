---
title: "Building an open source c program"
date: 2007-02-14
forum: Programming Talk
---

### Post by Andrea_44 on 2007-02-14
Hi,

I have only installed build-essential.
What other packages are required to build an open source C++ program?

I am trying to build "mucus-1.1" from the source under Edgy, but having a really tough time, returning many errors. :-(

The source can be downloaded here:
[http://www.cs.ucsb.edu/~rsg/projects/mucus/index.html](http://www.cs.ucsb.edu/~rsg/projects/mucus/index.html)

or please find the attachment.

Would anyone please tell me what packages they have installed to build this program?

Any help will be greatly appreciated!

Cheers~
Andrea

---

### Post by Mirrorball on 2007-02-14
It depends on what packages this program depends on. Please post the errors you are getting so that we can find out whatelse you need to install.

---

### Post by Andrea_44 on 2007-02-14
Thank you for the reply!

I did a ./configure
```
 :~/mucus-1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ANSI C header files... (cached) yes
checking antlr/config.hpp usability... no
checking antlr/config.hpp presence... no
checking for antlr/config.hpp... no
checking libnet.h usability... no
checking libnet.h presence... no
checking for libnet.h... no
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands

```

And then make
```
:~/mucus-1.1$ make
Making all in src
make[1]: Entering directory `/home/jflaptop2/Downloaded/remoteExploit/mucus-1.1/src'
if g++ -DPACKAGE_NAME=\"mucus\" -DPACKAGE_TARNAME=\"mucus\" -DPACKAGE_VERSION=\"1.1\" -DPACKAGE_STRING=\"mucus\ 1.1\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"mucus\" -DVERSION=\"1.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DTIME_WITH_SYS_TIME=1  -I. -I.     -g -O2 -MT Main.o -MD -MP -MF ".deps/Main.Tpo" -c -o Main.o Main.cpp; \
        then mv -f ".deps/Main.Tpo" ".deps/Main.Po"; else rm -f ".deps/Main.Tpo"; exit 1; fi
In file included from mucus.hpp:9,
                 from Main.cpp:2:
/usr/include/libnet.h:87:2: error: #error "byte order has not been specified, you'll
In file included from mucus.hpp:9,
                 from Main.cpp:2:
/usr/include/libnet.h:88: error: stray &#8216;#&#8217; in program
/usr/include/libnet.h:89: error: missing terminating " character
In file included from mucus.hpp:13,
                 from Main.cpp:2:
snortlexer.hpp:4:28: error: antlr/config.hpp: No such file or directory
snortlexer.hpp:6:33: error: antlr/CommonToken.hpp: No such file or directory
snortlexer.hpp:7:33: error: antlr/InputBuffer.hpp: No such file or directory
snortlexer.hpp:8:28: error: antlr/BitSet.hpp: No such file or directory
snortlexer.hpp:10:33: error: antlr/CharScanner.hpp: No such file or directory
In file included from mucus.hpp:14,
                 from Main.cpp:2:
snortparser.hpp:6:33: error: antlr/TokenStream.hpp: No such file or directory
snortparser.hpp:7:33: error: antlr/TokenBuffer.hpp: No such file or directory
snortparser.hpp:9:31: error: antlr/LLkParser.hpp: No such file or directory
/usr/include/libnet.h:88: error: &#8216;need&#8217; does not name a type
snortlexer.hpp:24: error: expected class-name before &#8216;(&#8217; token
snortlexer.hpp:24: error: expected `{' before &#8216;(&#8217; token
snortlexer.hpp:24: error: expected initializer before &#8216;CharScanner&#8217;
snortparser.hpp:24: error: expected class-name before &#8216;(&#8217; token
snortparser.hpp:24: error: expected `{' before &#8216;(&#8217; token
snortparser.hpp:24: error: expected initializer before &#8216;LLkParser&#8217;
mucus.hpp:87: error: &#8216;class snortparser::Rule&#8217; has not been declared
mucus.hpp:88: error: &#8216;class snortparser::Rule&#8217; has not been declared
mucus.hpp:91: error: &#8216;class snortparser::Rule&#8217; has not been declared
mucus.hpp:119: error: &#8216;class snortparser::Rule&#8217; has not been declared
mucus.hpp:149: error: &#8216;class snortparser::Rule&#8217; has not been declared
mucus.hpp:170: error: type &#8216;snortparser&#8217; is not a base type for type &#8216;MucusPacket&#8217;
mucus.hpp:170: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mucus.hpp:204: error: field &#8216;_icmp_hdr&#8217; has incomplete type
mucus.hpp:211: error: ISO C++ forbids declaration of &#8216;libnet_t&#8217; with no type
mucus.hpp:211: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mucus.hpp:221: error: &#8216;class snortparser::Rule&#8217; has not been declared
mucus.hpp:223: error: &#8216;libnet_context&#8217; has not been declared
mucus.hpp:225: error: ISO C++ forbids declaration of &#8216;libnet_pblock_t&#8217; with no type
mucus.hpp:225: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
mucus.hpp:233: error: &#8216;class snortparser::Rule&#8217; has not been declared
mucus.hpp:317: error: &#8216;class snortparser::Rule&#8217; has not been declared
Main.cpp:4: error: expected constructor, destructor, or type conversion before &#8216;(&#8217; token
Main.cpp: In function &#8216;void generateAttackInstances(snortparser*, int, int, int, bool, char*, bool, char*, unsigned int, bool, float, bool, bool, int, bool, bool, bool, bool, bool, char*)&#8217;:
Main.cpp:42: error: invalid use of undefined type &#8216;class snortparser&#8217;
snortparser.hpp:24: error: forward declaration of &#8216;class snortparser&#8217;
Main.cpp:44: error: incomplete type &#8216;snortparser&#8217; used in nested name specifier
Main.cpp:44: error: &#8216;currentRule&#8217; was not declared in this scope
Main.cpp:103: error: incomplete type &#8216;snortparser&#8217; used in nested name specifier
Main.cpp:103: error: incomplete type &#8216;snortparser&#8217; used in nested name specifier
Main.cpp:103: error: template argument 1 is invalid
Main.cpp:103: error: template argument 2 is invalid
Main.cpp:103: error: invalid type in declaration before &#8216;=&#8217; token
Main.cpp:103: error: invalid use of undefined type &#8216;class snortparser&#8217;
snortparser.hpp:24: error: forward declaration of &#8216;class snortparser&#8217;
Main.cpp:104: error: incomplete type &#8216;snortparser&#8217; used in nested name specifier
Main.cpp:104: error: incomplete type &#8216;snortparser&#8217; used in nested name specifier
Main.cpp:104: error: template argument 1 is invalid
Main.cpp:104: error: template argument 2 is invalid
Main.cpp:104: error: invalid type in declaration before &#8216;=&#8217; token
Main.cpp:104: error: invalid use of undefined type &#8216;class snortparser&#8217;
snortparser.hpp:24: error: forward declaration of &#8216;class snortparser&#8217;
Main.cpp:118: error: invalid types &#8216;int[int]&#8217; for array subscript
Main.cpp:121: error: invalid types &#8216;int[int]&#8217; for array subscript
Main.cpp:123: error: invalid types &#8216;int[int]&#8217; for array subscript
Main.cpp: In function &#8216;int main(int, char**)&#8217;:
Main.cpp:304: error: invalid use of undefined type &#8216;class snortlexer&#8217;
snortlexer.hpp:24: error: forward declaration of &#8216;class snortlexer&#8217;
Main.cpp:305: error: invalid use of undefined type &#8216;class snortparser&#8217;
snortparser.hpp:24: error: forward declaration of &#8216;class snortparser&#8217;
Main.cpp:307: error: &#8216;antlr&#8217; has not been declared
Main.cpp:307: error: &#8216;mucus_ast_factory&#8217; was not declared in this scope
Main.cpp:307: error: expected type-specifier before &#8216;antlr&#8217;
Main.cpp:307: error: expected `;' before &#8216;antlr&#8217;
Main.cpp:308: error: invalid use of undefined type &#8216;class snortparser&#8217;
snortparser.hpp:24: error: forward declaration of &#8216;class snortparser&#8217;
Main.cpp:309: error: invalid use of undefined type &#8216;class snortparser&#8217;
snortparser.hpp:24: error: forward declaration of &#8216;class snortparser&#8217;
Main.cpp:312: error: invalid use of undefined type &#8216;class snortparser&#8217;
snortparser.hpp:24: error: forward declaration of &#8216;class snortparser&#8217;
Main.cpp:313: error: expected type-specifier before &#8216;RecognitionException&#8217;
Main.cpp:313: error: expected `)' before &#8216;&&#8217; token
Main.cpp:313: error: expected `{' before &#8216;&&#8217; token
Main.cpp:313: error: &#8216;r&#8217; was not declared in this scope
Main.cpp:313: error: expected `;' before &#8216;)&#8217; token
Main.cpp:317: error: expected primary-expression before &#8216;catch&#8217;
Main.cpp:317: error: expected `;' before &#8216;catch&#8217;
make[1]: *** [Main.o] Error 1
make[1]: Leaving directory `/home/jflaptop2/Downloaded/remoteExploit/mucus-1.1/src'
make: *** [all-recursive] Error 1
```

Cheers~
Andrea

---

### Post by Mirrorball on 2007-02-14
I'd try to install antlr.
```
sudo apt-get install antlr
```

---

### Post by Mirrorball on 2007-02-14
Or rather libantlr-dev, sorry.

---

### Post by Andrea_44 on 2007-02-14
That's great! For the first time, I am receiving a slightly different error msg.
 ```
$./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ANSI C header files... (cached) yes
checking antlr/config.hpp usability... yes
checking antlr/config.hpp presence... yes
checking for antlr/config.hpp... yes
checking libnet.h usability... no
checking libnet.h presence... no
checking for libnet.h... no
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
```

```
$ make
Making all in src
make[1]: Entering directory `/home/jflaptop2/Downloaded/remoteExploit/mucus-1.1/src'
if g++ -DPACKAGE_NAME=\"mucus\" -DPACKAGE_TARNAME=\"mucus\" -DPACKAGE_VERSION=\"1.1\" -DPACKAGE_STRING=\"mucus\ 1.1\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"mucus\" -DVERSION=\"1.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -DHAVE_ANTLR_CONFIG_HPP=1 -DTIME_WITH_SYS_TIME=1  -I. -I.     -g -O2 -MT Main.o -MD -MP -MF ".deps/Main.Tpo" -c -o Main.o Main.cpp; \
        then mv -f ".deps/Main.Tpo" ".deps/Main.Po"; else rm -f ".deps/Main.Tpo"; exit 1; fi
In file included from mucus.hpp:9,
                 from Main.cpp:2:
/usr/include/libnet.h:87:2: error: #error "byte order has not been specified, you'll
In file included from mucus.hpp:9,
                 from Main.cpp:2:
/usr/include/libnet.h:88: error: stray ‘#’ in program
/usr/include/libnet.h:89: error: missing terminating " character
/usr/include/libnet.h:88: error: ‘need’ does not name a type
/usr/include/antlr/Token.hpp:86: error: expected `)' before ‘other’
/usr/include/antlr/Token.hpp:88: error: declaration of ‘operator=’ as non-function
/usr/include/antlr/Token.hpp:88: error: expected ‘;’ before ‘(’ token
/usr/include/antlr/Token.hpp:93: error: ‘RefToken’ does not name a type
/usr/include/antlr/CommonToken.hpp:66: error: ‘RefToken’ does not name a type
/usr/include/antlr/TokenStream.hpp:24: error: ‘RefToken’ does not name a type
/usr/include/antlr/CharScanner.hpp:88: error: expected identifier before ‘*’ token
/usr/include/antlr/CharScanner.hpp:88: error: ‘RefToken’ declared as function returning a function
/usr/include/antlr/CharScanner.hpp:347: error: ‘getTokenObject’ declared as function returning a function
/usr/include/antlr/CharScanner.hpp:411: error: ‘factory_type’ has not been declared
/usr/include/antlr/CharScanner.hpp:484: error: ‘factory_type’ does not name a type
/usr/include/antlr/CharScanner.hpp:502: error: ‘makeToken’ declared as function returning a function
/usr/include/antlr/CharScanner.hpp: In member function ‘virtual int antlr::CharScanner::getTokenObject() const’:
/usr/include/antlr/CharScanner.hpp:349: error: argument of type ‘int (antlr::CharScanner::)(int*)’ does not match ‘int’
/usr/include/antlr/CharScanner.hpp: In member function ‘virtual void antlr::CharScanner::setTokenObjectFactory(int)’:
/usr/include/antlr/CharScanner.hpp:413: error: ‘tokenFactory’ was not declared in this scope
/usr/include/antlr/CharScanner.hpp: In member function ‘virtual int antlr::CharScanner::makeToken(int)’:
/usr/include/antlr/CharScanner.hpp:504: error: function ‘int antlr::tok(int*)’ is initialized like a variable
/usr/include/antlr/CharScanner.hpp:504: error: ‘tokenFactory’ was not declared in this scope
/usr/include/antlr/CharScanner.hpp:505: error: request for member ‘setType’ in ‘antlr::tok’, which is of non-class type ‘int ()(int*)’
/usr/include/antlr/CharScanner.hpp:506: error: request for member ‘setColumn’ in ‘antlr::tok’, which is of non-class type ‘int ()(int*)’
/usr/include/antlr/CharScanner.hpp:507: error: request for member ‘setLine’ in ‘antlr::tok’, which is of non-class type ‘int ()(int*)’
/usr/include/antlr/CharScanner.hpp:508: error: invalid conversion from ‘int (*)(int*)’ to ‘int’
snortlexer.hpp: At global scope:
snortlexer.hpp:39: error: ‘RefToken’ in namespace ‘antlr’ does not name a type
/usr/include/antlr/TokenBuffer.hpp:55: error: ‘RefToken’ does not name a type
/usr/include/antlr/TokenBuffer.hpp:96: error: ‘RefToken’ was not declared in this scope
/usr/include/antlr/TokenBuffer.hpp:96: error: template argument 1 is invalid
/usr/include/antlr/TokenBuffer.hpp: In member function ‘void antlr::TokenBuffer::reset()’:
/usr/include/antlr/TokenBuffer.hpp:48: error: request for member ‘clear’ in ‘((antlr::TokenBuffer*)this)->antlr::TokenBuffer::queue’, which is of non-class type ‘int’
/usr/include/antlr/TokenBuffer.hpp: In member function ‘void antlr::TokenBuffer::syncConsume()’:
/usr/include/antlr/TokenBuffer.hpp:111: error: request for member ‘removeItems’ in ‘((antlr::TokenBuffer*)this)->antlr::TokenBuffer::queue’, which is of non-class type ‘int’
/usr/include/antlr/AST.hpp: At global scope:
/usr/include/antlr/AST.hpp:84: error: ‘RefToken’ has not been declared
/usr/include/antlr/MismatchedTokenException.hpp:58: error: ‘RefToken’ has not been declared
/usr/include/antlr/MismatchedTokenException.hpp:69: error: ‘RefToken’ has not been declared
/usr/include/antlr/MismatchedTokenException.hpp:79: error: ‘RefToken’ has not been declared
/usr/include/antlr/MismatchedTokenException.hpp:93: error: ‘RefToken’ does not name a type
/usr/include/antlr/ASTFactory.hpp:74: error: ‘RefToken’ has not been declared
/usr/include/antlr/ASTFactory.hpp:74: error: ‘antlr::RefAST antlr::ASTFactory::create(int)’ cannot be overloaded
/usr/include/antlr/ASTFactory.hpp:68: error: with ‘antlr::RefAST antlr::ASTFactory::create(int)’
/usr/include/antlr/Parser.hpp:90: error: ‘RefToken’ does not name a type
/usr/include/antlr/Parser.hpp: In member function ‘virtual void antlr::Parser::match(int)’:
/usr/include/antlr/Parser.hpp:175: error: ‘LT’ was not declared in this scope
/usr/include/antlr/Parser.hpp: In member function ‘virtual void antlr::Parser::matchNot(int)’:
/usr/include/antlr/Parser.hpp:189: error: ‘LT’ was not declared in this scope
/usr/include/antlr/Parser.hpp: In member function ‘virtual void antlr::Parser::match(const antlr::BitSet&)’:
/usr/include/antlr/Parser.hpp:218: error: ‘LT’ was not declared in this scope
/usr/include/antlr/LLkParser.hpp: At global scope:
/usr/include/antlr/LLkParser.hpp:49: error: ‘RefToken’ does not name a type
mucus.hpp:204: error: field ‘_icmp_hdr’ has incomplete type
mucus.hpp:211: error: ISO C++ forbids declaration of ‘libnet_t’ with no type
mucus.hpp:211: error: expected ‘;’ before ‘*’ token
mucus.hpp:223: error: ‘libnet_context’ has not been declared
mucus.hpp:225: error: ISO C++ forbids declaration of ‘libnet_pblock_t’ with no type
mucus.hpp:225: error: expected ‘;’ before ‘*’ token
make[1]: *** [Main.o] Error 1
make[1]: Leaving directory `/home/jflaptop2/Downloaded/remoteExploit/mucus-1.1/src'
make: *** [all-recursive] Error 1

```

Thanks for your time, Mirrorball!

Cheers~
Andrea

---

### Post by Mirrorball on 2007-02-14
You might already have it, but try installing libnet1-dev.

---

### Post by Andrea_44 on 2007-02-14
Yes, I do already have the libnet1-dev. 
```
libnet1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 83 not upgraded.

```

Did you manage to build "mucus-1.1" successfully just by doing ./configure and make?

Cheers~
Andrea

---

### Post by Mirrorball on 2007-02-14
No, I'm not sure I want mucus on my computer. :P But let me try.

---

### Post by Mirrorball on 2007-02-14
Well, mucus compilation finished for me. Maybe I should upload it for you to finish it with make install?

---

### Post by Mirrorball on 2007-02-14
I was looking at your configure output and it says:
```

checking libnet.h usability... no
checking libnet.h presence... no
checking for libnet.h... no

```
I think you just uninstall and install libnet1-dev again.

---

### Post by Andrea_44 on 2007-02-14
No, worries, I understand. 

I still haven't learnt how to uninstall programs in Linux yet, 
may be something I would get on to later after I can actually install a program

Andrea

---

### Post by Andrea_44 on 2007-02-15
> **Mirrorball said:**
> I was looking at your configure output and it says:
```

checking libnet.h usability... no
checking libnet.h presence... no
checking for libnet.h... no

```
I think you just uninstall and install libnet1-dev again.

So the system cannot find the libnet that I have installed?

---

### Post by Mirrorball on 2007-02-15
```

sudo apt-get --purge remove libnet1-dev
sudo apt-get install libnet1-dev

```
Something must have gone wrong with your libnet installation, I don't know what it was, but I think this will fix it.

---

### Post by Andrea_44 on 2007-02-15
Thank you Mirrorball! You are a champion, very helpful : >

I have successfully 'make install' the program. 

Cheers~
Andrea

---

### Post by Mirrorball on 2007-02-15
You're welcome, I'm glad it worked.

---

