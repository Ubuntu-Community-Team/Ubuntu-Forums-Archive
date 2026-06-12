---
title: "How to compile a program with static lib by automake?"
date: 2008-08-01
forum: Packaging and Compiling Programs
---

### Post by wangtao on 2008-08-01
Hi,

I got "undefined reference" error during compiling a program, which linked to a static library. I'm learning autoconf & automake tools, so I may make mistake in my Makefile.am. Following is my situation.

This is my file structure
```
.
.
|-- Makefile.am
|-- configure.in
|-- include
|   |-- BigInteger.h
|   |-- BigIntegerAlgorithms.h
|   |-- BigIntegerLibrary.h
|   |-- BigIntegerUtils.h
|   |-- BigUnsigned.h
|   |-- BigUnsignedInABase.h
|   |-- DiffieHellmanKeyExchange.h
|   |-- NumberlikeArray.h
|   |-- PracticalSocket.h
|   |-- RC4.h
|   |-- SecureChat.h
|   |-- SecureConnection.h
|   |-- Util.h
|   `-- ting.hpp
`-- src
    |-- Makefile.am
    |-- PracticalSocket
    |   |-- Makefile.am
    |   `-- PracticalSocket.cpp
    |-- SecureChat
    |   |-- DiffieHellmanKeyExchange.cpp
    |   |-- Makefile.am
    |   |-- RC4.cpp
    |   |-- SecureChat.cpp
    |   |-- SecureConnection.cpp
    |   `-- Util.cpp
    |-- bigint
    |   |-- BigInteger.cpp
    |   |-- BigIntegerAlgorithms.cpp
    |   |-- BigIntegerUtils.cpp
    |   |-- BigUnsigned.cpp
    |   |-- BigUnsignedInABase.cpp
    |   `-- Makefile.am
    |-- client_main.cpp
    |-- server_main.cpp
    `-- ting
        |-- Makefile.am
        `-- ting.cpp

```

I use autoscan to generate the configure.in and made some modification:
```
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.61)
AC_INIT(csci968-asst1, 0.1)
AC_CONFIG_SRCDIR([src/server_main.cpp])
AC_CONFIG_HEADER([include/config.h])
AM_INIT_AUTOMAKE(csci968-asst1, 0.1)

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_RANLIB

# Checks for libraries.

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADERS([arpa/inet.h netdb.h netinet/in.h string.h sys/socket.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_CONST
AC_C_INLINE
AC_TYPE_SIZE_T
AC_HEADER_TIME
AC_C_VOLATILE

# Checks for library functions.
AC_FUNC_SELECT_ARGTYPES
AC_CHECK_FUNCS([gethostbyname inet_ntoa memset select socket strerror])

AC_CONFIG_FILES([Makefile
	src/Makefile
	src/bigint/Makefile
	src/PracticalSocket/Makefile
	src/ting/Makefile
	src/SecureChat/Makefile])
AC_OUTPUT
```

I wrote several Makefile.am for each part in the project.

**_src/Makefile.am_**
```
bin_PROGRAMS = client host
client_SOURCES = client_main.cpp
host_SOURCES = server_main.cpp
INCLUDES = -I../include

LDADD = $(top_builddir)/src/bigint/libbigint.a \
	$(top_builddir)/src/PracticalSocket/libPracticalSocket.a \
	$(top_builddir)/src/ting/libting.a \
	$(top_builddir)/src/SecureChat/libSecureChat.a

SUBDIRS = bigint PracticalSocket ting SecureChat

```

**_src/bigint/Makefile.am_**
```
lib_LIBRARIES = libbigint.a
libbigint_a_SOURCES = BigIntegerAlgorithms.cpp	\
	BigInteger.cpp	\
	BigIntegerUtils.cpp	\
	BigUnsigned.cpp	\
	BigUnsignedInABase.cpp
INCLUDES = -I../../include
```

**_src/PracticalSocket/Makefile.am_**
```
lib_LIBRARIES = libPracticalSocket.a
libPracticalSocket_a_SOURCES = PracticalSocket.cpp
INCLUDES = -I../../include
```

**_src/ting/Makefile.am_**
```
lib_LIBRARIES = libting.a
libting_a_SOURCES = ting.cpp
INCLUDES = -I../../include

```

**_src/SecureChat/Makefile.am_**
```
lib_LIBRARIES = libSecureChat.a
libSecureChat_a_SOURCES = DiffieHellmanKeyExchange.cpp \
	RC4.cpp	\
	SecureChat.cpp	\
	SecureConnection.cpp	\
	Util.cpp
INCLUDES = -I../../include
```

Then I use commmand ```
aclocal && autoconf && autoheader && automake -a && ./configure
``` to do the configuration. And following is the output:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for working volatile... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for gethostbyname... yes
checking for inet_ntoa... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strerror... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/bigint/Makefile
config.status: creating src/PracticalSocket/Makefile
config.status: creating src/ting/Makefile
config.status: creating src/SecureChat/Makefile
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: executing depfiles commands

```

Everything looks fine. However, during the 'make', I got the 'undefined reference' error. 

```
tao@wombat:/tmp/tao/asst1$ make clean && make
Making clean in src
make[1]: Entering directory `/tmp/tao/asst1/src'
Making clean in SecureChat
make[2]: Entering directory `/tmp/tao/asst1/src/SecureChat'
test -z "libSecureChat.a" || rm -f libSecureChat.a
rm -f *.o
make[2]: Leaving directory `/tmp/tao/asst1/src/SecureChat'
Making clean in ting
make[2]: Entering directory `/tmp/tao/asst1/src/ting'
test -z "libting.a" || rm -f libting.a
rm -f *.o
make[2]: Leaving directory `/tmp/tao/asst1/src/ting'
Making clean in PracticalSocket
make[2]: Entering directory `/tmp/tao/asst1/src/PracticalSocket'
test -z "libPracticalSocket.a" || rm -f libPracticalSocket.a
rm -f *.o
make[2]: Leaving directory `/tmp/tao/asst1/src/PracticalSocket'
Making clean in bigint
make[2]: Entering directory `/tmp/tao/asst1/src/bigint'
test -z "libbigint.a" || rm -f libbigint.a
rm -f *.o
make[2]: Leaving directory `/tmp/tao/asst1/src/bigint'
Making clean in .
make[2]: Entering directory `/tmp/tao/asst1/src'
test -z "client host" || rm -f client host
rm -f *.o
make[2]: Leaving directory `/tmp/tao/asst1/src'
make[1]: Leaving directory `/tmp/tao/asst1/src'
Making clean in .
make[1]: Entering directory `/tmp/tao/asst1'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/tmp/tao/asst1'
Making all in src
make[1]: Entering directory `/tmp/tao/asst1/src'
Making all in bigint
make[2]: Entering directory `/tmp/tao/asst1/src/bigint'
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT BigIntegerAlgorithms.o -MD -MP -MF .deps/BigIntegerAlgorithms.Tpo -c -o BigIntegerAlgorithms.o BigIntegerAlgorithms.cpp
mv -f .deps/BigIntegerAlgorithms.Tpo .deps/BigIntegerAlgorithms.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT BigInteger.o -MD -MP -MF .deps/BigInteger.Tpo -c -o BigInteger.o BigInteger.cpp
mv -f .deps/BigInteger.Tpo .deps/BigInteger.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT BigIntegerUtils.o -MD -MP -MF .deps/BigIntegerUtils.Tpo -c -o BigIntegerUtils.o BigIntegerUtils.cpp
mv -f .deps/BigIntegerUtils.Tpo .deps/BigIntegerUtils.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT BigUnsigned.o -MD -MP -MF .deps/BigUnsigned.Tpo -c -o BigUnsigned.o BigUnsigned.cpp
mv -f .deps/BigUnsigned.Tpo .deps/BigUnsigned.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT BigUnsignedInABase.o -MD -MP -MF .deps/BigUnsignedInABase.Tpo -c -o BigUnsignedInABase.o BigUnsignedInABase.cpp
mv -f .deps/BigUnsignedInABase.Tpo .deps/BigUnsignedInABase.Po
rm -f libbigint.a
ar cru libbigint.a BigIntegerAlgorithms.o BigInteger.o BigIntegerUtils.o BigUnsigned.o BigUnsignedInABase.o 
ranlib libbigint.a
make[2]: Leaving directory `/tmp/tao/asst1/src/bigint'
Making all in PracticalSocket
make[2]: Entering directory `/tmp/tao/asst1/src/PracticalSocket'
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT PracticalSocket.o -MD -MP -MF .deps/PracticalSocket.Tpo -c -o PracticalSocket.o PracticalSocket.cpp
mv -f .deps/PracticalSocket.Tpo .deps/PracticalSocket.Po
rm -f libPracticalSocket.a
ar cru libPracticalSocket.a PracticalSocket.o 
ranlib libPracticalSocket.a
make[2]: Leaving directory `/tmp/tao/asst1/src/PracticalSocket'
Making all in ting
make[2]: Entering directory `/tmp/tao/asst1/src/ting'
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT ting.o -MD -MP -MF .deps/ting.Tpo -c -o ting.o ting.cpp
mv -f .deps/ting.Tpo .deps/ting.Po
rm -f libting.a
ar cru libting.a ting.o 
ranlib libting.a
make[2]: Leaving directory `/tmp/tao/asst1/src/ting'
Making all in SecureChat
make[2]: Entering directory `/tmp/tao/asst1/src/SecureChat'
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT DiffieHellmanKeyExchange.o -MD -MP -MF .deps/DiffieHellmanKeyExchange.Tpo -c -o DiffieHellmanKeyExchange.o DiffieHellmanKeyExchange.cpp
mv -f .deps/DiffieHellmanKeyExchange.Tpo .deps/DiffieHellmanKeyExchange.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT RC4.o -MD -MP -MF .deps/RC4.Tpo -c -o RC4.o RC4.cpp
mv -f .deps/RC4.Tpo .deps/RC4.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT SecureChat.o -MD -MP -MF .deps/SecureChat.Tpo -c -o SecureChat.o SecureChat.cpp
mv -f .deps/SecureChat.Tpo .deps/SecureChat.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT SecureConnection.o -MD -MP -MF .deps/SecureConnection.Tpo -c -o SecureConnection.o SecureConnection.cpp
mv -f .deps/SecureConnection.Tpo .deps/SecureConnection.Po
g++ -DHAVE_CONFIG_H -I. -I../../include -I../../include    -g -O2 -MT Util.o -MD -MP -MF .deps/Util.Tpo -c -o Util.o Util.cpp
mv -f .deps/Util.Tpo .deps/Util.Po
rm -f libSecureChat.a
ar cru libSecureChat.a DiffieHellmanKeyExchange.o RC4.o SecureChat.o SecureConnection.o Util.o 
ranlib libSecureChat.a
make[2]: Leaving directory `/tmp/tao/asst1/src/SecureChat'
make[2]: Entering directory `/tmp/tao/asst1/src'
g++ -DHAVE_CONFIG_H -I. -I../include -I../include    -g -O2 -MT client_main.o -MD -MP -MF .deps/client_main.Tpo -c -o client_main.o client_main.cpp
mv -f .deps/client_main.Tpo .deps/client_main.Po
g++  -g -O2   -o client client_main.o ../src/bigint/libbigint.a ../src/PracticalSocket/libPracticalSocket.a ../src/ting/libting.a ../src/SecureChat/libSecureChat.a 
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `SecureChat::Connect()':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:125: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, BigUnsigned const&)'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:125: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, BigUnsigned const&)'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:127: undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, BigUnsigned const&)'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:131: [COLOR="Red"]undefined reference[/COLOR] to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, BigUnsigned const&)'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:140: [COLOR="Red"]undefined reference[/COLOR] to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, BigUnsigned const&)'
../src/SecureChat/libSecureChat.a(SecureChat.o):/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:143: more undefined references to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, BigUnsigned const&)' follow
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `SecureChat::Chat(bool)':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:70: undefined reference to `ting::Mutex::Mutex()'
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `SecureChatListener':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:17: undefined reference to `ting::Thread::Thread()'
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `SecureChat::Chat(bool)':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:72: undefined reference to `ting::Thread::Start(unsigned int)'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:85: undefined reference to `ting::Mutex::Lock()'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:87: undefined reference to `ting::Mutex::Unlock()'
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `~SecureChatListener':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:13: undefined reference to `ting::Thread::~Thread()'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:13: undefined reference to `ting::Thread::~Thread()'
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `SecureChatListener':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:18: undefined reference to `ting::Thread::~Thread()'
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `~SecureChatListener':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:13: undefined reference to `ting::Thread::~Thread()'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:13: undefined reference to `ting::Thread::~Thread()'
../src/SecureChat/libSecureChat.a(SecureChat.o): In function `SecureChatListener::Run()':
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:26: undefined reference to `ting::Mutex::Lock()'
/tmp/tao/asst1/src/SecureChat/SecureChat.cpp:28: undefined reference to `ting::Mutex::Unlock()'
../src/SecureChat/libSecureChat.a(SecureChat.o):(.rodata._ZTI18SecureChatListener[typeinfo for SecureChatListener]+0x8): undefined reference to `typeinfo for ting::Thread'
collect2: ld returned 1 exit status
make[2]: *** [client] Error 1
make[2]: Leaving directory `/tmp/tao/asst1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/tao/asst1/src'
make: *** [all-recursive] Error 1

```

It looks like linking problem, since every lib*.a or *.o compiled without error, however, the error happened during the final linking step.

And I found the 'undefined reference' is most likely happened for one of my library call another my library, that is one library depends on another.

Please help me to figure out the problem. Is any of my Makefile.am wrong?

Thanks.

---

