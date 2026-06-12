---
title: "xml-xalan-c make errors in Ubuntu 9.04"
date: 2009-10-26
forum: Packaging and Compiling Programs
---

### Post by edo1080 on 2009-10-26
I'm new in this forum and trying to compile xml-xalan c++ on Ubuntu 9.04 ; I've installed gcc 4.4.2; I get no errors when launching 'make', but I've got the following error when launching 'make tests' 
 
```

make -C Tests tests
make[1]: ingresso nella directory «/home/edoardo/Librerie/xml-xalan/c/Tests»
mkdir -p ../lib
mkdir -p ../bin
g++ -O2 -DNDEBUG     -fno-elide-constructors -Wall -fPIC -DLINUX -D_REENTRANT -DXALAN_INMEM_MSG_LOADER -c -I/home/edoardo/Librerie/xml-xalan/c/src -I/home/edoardo/Librerie/xml-xalan/c/include -I../nls/include -I/home/edoardo/Librerie/xerces-c-3.0.1/src/ -I/home/edoardo/Librerie/xerces-c-3.0.1/include/xercesc -I/home/edoardo/Librerie/xerces-c-3.0.1/include/  -o ../obj/conf.o /home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp
In file included from /usr/local/lib/gcc/i686-pc-linux-gnu/4.4.2/../../../../include/c++/4.4.2/backward/strstream:46,
                 from /home/edoardo/Librerie/xml-xalan/c/src/xalanc/Harness/XalanFileUtility.hpp:30,
                 from /home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp:61:
/usr/local/lib/gcc/i686-pc-linux-gnu/4.4.2/../../../../include/c++/4.4.2/backward/backward_warning.h:28:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated.
/home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp: In function &#8216;int main(int, char**)&#8217;:
/home/edoardo/Librerie/xml-xalan/c/Tests/Conf/conf.cpp:507: error: no matching function for call to &#8216;xercesc_3_0::XMLPlatformUtils::Initialize(const char [], int, int, xalanc_1_10::XalanDiagnosticMemoryManager*, bool)&#8217;
/home/edoardo/Librerie/xerces-c-3.0.1/src/xercesc/util/PlatformUtils.hpp:173: note: candidates are: static void xercesc_3_0::XMLPlatformUtils::Initialize(const char*, const char*, xercesc_3_0::PanicHandler*, xercesc_3_0::MemoryManager*)
/home/edoardo/Librerie/xerces-c-3.0.1/src/xercesc/util/PlatformUtils.hpp:227: note:                 static void xercesc_3_0::XMLPlatformUtils::Initialize(XMLSize_t, XMLSize_t, XMLSize_t, const char*, const char*, xercesc_3_0::PanicHandler*, xercesc_3_0::MemoryManager*)
make[1]: *** [../obj/conf.o] Errore 1
make[1]: uscita dalla directory «/home/edoardo/Librerie/xml-xalan/c/Tests»
make: *** [tests] Errore 2

```
 
 
 
Is there any solution? Thanks.

---

### Post by edo1080 on 2009-11-01
I installed Ubuntu 9.10 but I keep having the same error;

this is the code of conf.cpp in last lines just before 507

```
int theResult = 0;

    try
    {
        XALAN_USING_XERCES(XMLPlatformUtils)
        XALAN_USING_XERCES(XMLUni)

        XalanMemoryManagerDefault       theGlobalMemoryManager;
        XalanDiagnosticMemoryManager    theDiagnosticMemoryManager(theGlobalMemoryManager, true, &cerr);
        XalanMemoryManagerDefault       theTestingMemoryManager;

        // Call the static initializers for xerces and xalan, and create a transformer
        //
        XMLPlatformUtils::Initialize(
            XMLUni::fgXercescDefaultLocale,
            0,
            0,
            &theDiagnosticMemoryManager,
            true);

        XalanTransformer::initialize(theDiagnosticMemoryManager);

        theDiagnosticMemoryManager.lock();

        {
            theResult = runTests(argc, argv, theTestingMemoryManager);
        }

        theDiagnosticMemoryManager.unlock();

        XalanTransformer::terminate();

        XMLPlatformUtils::Terminate();

        XalanTransformer::ICUCleanUp();
    }
    catch(...)
    {
        cerr << "Initialization failed!" << endl << endl;

        theResult = -1;
    }

    return theResult;
}
```

---

### Post by SevenMachines on 2009-11-04
It looks like xml-xalan is using an out-of-date xerces interface, you could try either getting a newer version of xml-xalan, or an older version of xerces to compile against. judging by the gcc deprecation warning i'm guessing its the newer xml-xalan that you need (and that xerces 3.0 seems to be quite up to date)

---

### Post by edo1080 on 2009-11-04
Thank you for your answer, I'm using the lates versions of both and it doesn't work; I also tested with the older version of xerces 2.7.0 which is the one xalan 1.5.1 is tested with but it gives the same errors.

---

### Post by SevenMachines on 2009-11-04
If you have links to download the source your using I'll have a look and have a look and see if i get the same problem

---

### Post by SevenMachines on 2009-11-04
is the older version of libxalan110 in the repositories not the one you're looking for? Your task would be a lot easier if it was :)

---

### Post by edo1080 on 2009-11-04
Hi, thank you for your interest and the time you are giving me; here's the one I downloaded and am trying to use:
 
[http://mirror.soluzionisis.com/apache/xml/xalan-c/Xalan-C_current-src.zip](http://mirror.soluzionisis.com/apache/xml/xalan-c/Xalan-C_current-src.zip)
 
 
version 1.10 
 
I was using Xml-xalan to build XML-security library but it worked also without xalan, so it's no more a problem if it doesn't work.
 
I need to build all of these libraries to compile the program named:
 
kdm-decrypt in appendix C.4. of the followinf document:
 
 [http://www.dcimovies.com/**DCI_CTP_v1_0**.**pdf]("http://www.dcimovies.com/DCI_CTP_v1_0.pdf")** 
 
 
I succesfully compiled and installed Xerces 3.0.1, Xml-Security 1.5.1, Openssl 1.0.0 Beta 3 and asdcplib 1.4.24 latest stable version [http://www.cinecert.com/asdcplib/asdcplib-1.4.24.tar.gz](http://www.cinecert.com/asdcplib/asdcplib-1.4.24.tar.gz)
 
To tell the truth when building  asdcplib 1.4.24  I had to add this option to ./configure :
 
--with-openssl=/usr/local......
 
because I had an error without this option; if I also add --with-xcerces=.... I have a building error, so I only set  
 
--with-openssl=/usr/local......
 
When the command ./configure --with.... launches it says cheching for Openss.... found but checking for xerces.... no
 
When compiling the kdm-decrypt source I have the following error :
 
```
/usr/local/include/KM_fileio.h:112: error: redefinition of ‘void
Kumu::compile_time_size_checker() [with bool sizecheck = false]’
/usr/local/include/KM_fileio.h:99: error: ‘void
Kumu::compile_time_size_checker() [with bool sizecheck = false]’ previously
declared here

```
 
it's due to asdcplib 1.4.24  but can't untestand what's the problem, can you help me? Thanks

---

### Post by SevenMachines on 2009-11-04
Theres seems to be the same problem with  asdcplib and a solution [here]("http://code.google.com/p/opencinematools/issues/detail?id=13") 
To be honest, i'd try to use repository libraries rather than manually built ones if at all possible, you can end up with a bit of a mess. Unfortunately I'm on 9.10 so I can't really tell what will work for you but

$sudo apt-get install libcrypto++-dev libxerces-c2-dev libxml-security-c-dev

seems to cover the dependencies apart from asdcplib. That built fine on 9.10 then I installed it using checkinstall, i like to let the package manager handle 'make install', its slightly better than doing it manually

apart from changing a couple of header lines in the source from xsec to xercesc (i'll attach the source file), where the new headers are in the packages I have, kdm-decrypt builds and runs fine on 9.10 with

$g++ -o kdm-decrypt kdm-decrypt.cpp  -lxerces-c  -lkumu -lcrypto -lxml-security-c

---

### Post by edo1080 on 2009-11-04
I'm really impressed, in a few lines you solved a problem I have been after for a month. 
 
I'm not so familiar with linux , and so I was thinking I always had to start from source files, build them and install, while using repository, as you suggested, is faster and safer.
 
I really have no words to thank you, I'm going to test myself and report.
Btw I also cleaned my installation and installed 9.10 yesteday.

---

### Post by SevenMachines on 2009-11-04
there are literally 1000's of development packages (the ones ending in -dev) in the repository containing what you need to build against that source, usually any ones you need will be in there already. In general you shouldnt need to build your own ones unless 

* The source hasnt been packaged already and you definitely need it!
* You need a specific version of something that is different from the ones available in the repository

In either case I would generally advise using repository development packages if at all possible

---

### Post by edo1080 on 2009-11-04
I tested but keep having the same errors; just to check my steps, unfortuately I had built and installed prevoiously xerces, xml-security and openssl 1.0.0beta3, could this be the problem ?

I launched

$sudo apt-get install libcrypto++-dev libxerces-c2-dev libxml-security-c-dev

and succesfully installed it all

I guess my error is in ./configue in asdcolib-1.4.24 directory

which ./configure did you lauch, have you added --with-openssl=/usl/local/ssl... and --with-xerces=.....

or simply ./configure?

If I launch ./configure (without all the other stuff) it says no openssl found and no xerces found and when I launch make it gives an error

thanks

---

### Post by SevenMachines on 2009-11-04
using asdcplib-1.4.24, just ./configure, no options, with libssl-dev and libxerces-c2-dev installed. they are installed into /usr/include, which is on the system path so you dont need any options. I have no other ssl or xerces dev files installed so i'm not sure whats going on

---

### Post by SevenMachines on 2009-11-04
you can 'make uninstall' the libraries you built by hand, this is where using checkinstall to run 'make install' when manually installing things can be handy

---

### Post by edo1080 on 2009-11-04
Thank you for this explaination. I'm going to uninstall it all and retry. Thanks again fr your patience.

---

### Post by edo1080 on 2009-11-04
uninstalling and then ./configure and make gives the following for asdcplib-1.4.24:

```
asdcp-test.o: In function `digest_file(char const*)':
/home/edoardo/Librerie/asdcplib-1.4.24/src/asdcp-test.cpp:1772: undefined reference to `SHA1_Init'
/home/edoardo/Librerie/asdcplib-1.4.24/src/asdcp-test.cpp:1789: undefined reference to `SHA1_Update'
/home/edoardo/Librerie/asdcplib-1.4.24/src/asdcp-test.cpp:1797: undefined reference to `SHA1_Final'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_init'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_num_bits'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_exp'
./.libs/libasdcp.so: undefined reference to `AES_set_decrypt_key'
./.libs/libasdcp.so: undefined reference to `AES_encrypt'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_set_word'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_bn2bin'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_CTX_free'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_bin2bn'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_add_word'
./.libs/libasdcp.so: undefined reference to `ERR_get_error'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_CTX_new'
./.libs/libasdcp.so: undefined reference to `ERR_error_string'
./.libs/libasdcp.so: undefined reference to `AES_decrypt'
./.libs/libasdcp.so: undefined reference to `AES_set_encrypt_key'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_add'
/home/edoardo/Librerie/asdcplib-1.4.24/src/.libs/libkumu.so: undefined reference to `BN_div'
collect2: ld returned 1 exit status
make[2]: *** [asdcp-test] Errore 1
make[2]: uscita dalla directory «/home/edoardo/Librerie/asdcplib-1.4.24/src»
make[1]: *** [all] Errore 2
make[1]: uscita dalla directory «/home/edoardo/Librerie/asdcplib-1.4.24/src»
make: *** [all-recursive] Errore 1

```

---

### Post by SevenMachines on 2009-11-04
if you havent already, try with a clean unzip of the asdcplib archive you downloaded. you might also want to run 
$sudo ldconfig
to update the linker since you've removed the local versions you had. if none of that works post your complete config.log and attach make output and i'll try to have a look at it sometime tomorrow

---

### Post by edo1080 on 2009-11-05
Hi, I made a clean install of Ubuntu 9.10 and launched

$sudo apt-get install libcrypto++-dev libxerces-c2-dev libxml-security-c-dev

all is fine now with the ./configure of asdcplib, it finds openssl without any option. It still keeps on missing xerces but I guess it's not a problem since oyu launched it wihtout any option

unfortunately when I complie the modified source of kdm-decrypt, I keep o having the same error

```
In file included from kdm-decrypt.cpp:12:
/usr/local/include/KM_fileio.h:112: error: redefinition of &#8216;void Kumu::compile_time_size_checker() [with bool sizecheck = false]&#8217;
/usr/local/include/KM_fileio.h:99: error: &#8216;void Kumu::compile_time_size_checker() [with bool sizecheck = false]&#8217; previously declared here
```how did you solve it? Thanks

---

### Post by SevenMachines on 2009-11-05
i didnt have this problem, but from 
/usr/local/include/KM_fileio.h:
we get,
  //
  // READ THIS if your compiler is complaining about a previously declared implementation of
  // compile_time_size_checker(). For example, GCC 4.0.1 looks like this:
  //
  // error: 'void Kumu::compile_time_size_checker() [with bool sizecheck = false]' previously declared here
  //
  // This is happening because the equality being tested below is false. The reason for this 
  // will depend on your OS, but on Linux it is probably because you have not used -D_FILE_OFFSET_BITS=64
  // Adding this magic macro to your CFLAGS will get you going again. If you are on a system that
  // does not support 64-bit files, you can disable this check by using -DKM_SMALL_FILES_OK. You
  // will then of course be limited to file sizes < 4GB.

so i guess you need to try adding either
-D_FILE_OFFSET_BITS=64
or 
-DKM_SMALL_FILES_OK
to your CFLAGS in the Makefile when compiling asdcplib. Sorry, can't test it, that problem didn't crop up here

---

### Post by SevenMachines on 2009-11-05
hmm, i'm guessing that perhaps that should really be CXXFLAGS="-O2 -g -D_FILE_OFFSET_BITS=64" ./configure
and not  CFLAGS

---

### Post by edo1080 on 2009-11-05
I tested replacing the line 

CXXFLAGS= -O2 -g 

in the Makefile with 

CXXFLAGS="-O2 -g -D_FILE_OFFSET_BITS=64" ./configure

there are no " in the source makefile

I also have the following warnings while compiling:




```

KM_log.cpp:147: warning: ignoring return value of 'ssize_t write(int, const void*, size_t)', declared with attribute warn_unused_result


asdcp-test.cpp:1560: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 3 has type ‘size_t’
```


The error remains anyway, of course I always  type  'make clean', but have I to perform make uninstall before a new checkinstall? Thanks

---

### Post by SevenMachines on 2009-11-05
sorry, maybe i didnt put that well, you could either have CXXFLAGS="-O2 -g -D_FILE_OFFSET_BITS=64" in the makefile, or better is to not change the makefile directly but add it when you run configure, ie

$ CXXFLAGS="-O2 -g -D_FILE_OFFSET_BITS=64" ./configure

Any advice I give needs to be double checked, especially after dinner time :)

compile warnings are not errors, its g++ questioning whether you really meant to do that in the code. 

checkinstall generates a pretend debian package, so it uninstalls the old one and installs the new one when you dpkg -i some.deb

---

### Post by edo1080 on 2009-11-05
I'm really sory but after testing a lot of times, also with last suggestion I keep having the same error

I double checked the readme file and I found

> OpenSSL is also required, version 0.9.8k is recommendedif I type $openssl version   I have OpenSSL 0.9.8g 19 Oct 2007

Maybe you have the 0.9.8k ?



> error: 'void Kumu::compile_time_size_checker() [with bool sizecheck = false]' previously declared here
  //
  // This is happening because the equality being tested below is false. The reason for this 
  // will depend on your OS, but on Linux it is probably because you have not used -D_FILE_OFFSET_BITS=64
  // Adding this magic macro to your CFLAGS will get you going again. If you are on a system that
  // does not support 64-bit files, you can disable this check by using -DKM_SMALL_FILES_OK. You
  // will then of course be limited to file sizes < 4GB.This is only the 2ND error, but the 1st one I have is:

```
usr/local/include/KM_fileio.h:112: error: redefinition of ‘void Kumu::compile_time_size_checker() [with bool sizecheck = false]’

```These are the steps I performed:

1)Installed a clean copy of Ubuntu
2) Run the language update and set the language to Italian and install all of the updates found for Ubuntu 9.10
3) $sudo apt-get install g++
4) $sudo apt-get install libcrypto++-dev libxerces-c2-dev libxml-security-c-dev
5) $sudo make uninstall
6) $make clean
7) $ CXXFLAGS="-O2 -g -D_FILE_OFFSET_BITS=64" ./configure in the asdcplib root
8)make
9) sudo checkinstall
10) in teh kdm-decrypt directory $g++ -o kdm-decrypt kdm-decrypt.cpp  -lxerces-c  -lkumu -lcrypto -lxml-security-c

I am realy happy to know you have been able to compile and run the prog,this mean I'm not wasting my time; so I'm doing something wrong with the process, have you done any mroe steps about this? Have you got a different openssl? Thank you , you're giving me precious help

---

### Post by SevenMachines on 2009-11-05
i've the same ssl version, have you tried it with CFLAGS instead of CXXFLAGS? I need to install a ubuntu 32 virtual machine tomorrow for something else anyway so I'll have a look at whats going on with this then or at some point over the weekend. 
just to add, theres no need to reinstall ubuntu to redo these things
redefinition of a function seems a little odd given that i dont get this with the same source. if you just have the one copy of asdcplib installed, you might want to look at doing
$sudo updatedb
$locate asdcplib 
and see if theres more installs than you thought.

---

### Post by edo1080 on 2009-11-05
If I try with CFLAGS instead of CXXFLAGS I have the follwoing error when launching 'make' for the asdcp library

```
./KM_fileio.h:112: error: redefinition of 'void Kumu::compile_time_size_checker() [with bool sizecheck = false]'
./KM_fileio.h:99: error: 'void Kumu::compile_time_size_checker() [with bool sizecheck = false]' previously declared here
make[2]: *** [KM_fileio.lo] Errore 1
make[2]: uscita dalla directory «/home/edoardo/AsDCP/asdcplib-1.4.24/src»
make[1]: *** [all] Errore 2
make[1]: uscita dalla directory «/home/edoardo/AsDCP/asdcplib-1.4.24/src»
make: *** [all-recursive] Errore 1

```

If I manually edit the makefile removing the  -D_FILE_OFFSET_BITS=64 I keep having the error even after a 'make clean' . Only if I re-launch ./configure without any option it builds smoothly. 

No duplicate installations of asdcplib are present; btw I have an Intel core 2 duo T5500 CPU on my notebook and have never been asked to install a 32 or 64 bit version, could it maybe due to a 64bit installation I'm not aware of?

---

### Post by SevenMachines on 2009-11-07
i've just built it on 9.04 32bit and the -D_FILE_OFFSET_BITS=64 option is automatically found and set when i run ./configure so I cant generate the same problem as you have. all i can suggest is that you check that -D_FILE_OFFSET_BITS isnt redefined inside the Makefile when you run 
CXXFLAGS="-g -O2 -D_FILE_OFFSET_BITS=64" ./configure
making sure that its only in CXXFLAGS

You might give the other suggested option a try, limiting you to <4gb files. ie, use the option
-DKM_SMALL_FILES_OK
but this gives me errors so I dont know how that'll go for you

---

### Post by edo1080 on 2009-11-07
I make a clean unzip of asdcplib and if running a ./configure with no option I haven't  -D_FILE_OFFSET_BITS=64 option by default

this is the first portion of the makefile after running the CXXFLAGS="-O2 -g -D_FILE_OFFSET_BITS=64" ./configure in the asdcplib root:

```
pkgdatadir = $(datadir)/asdcplib
pkglibdir = $(libdir)/asdcplib
pkgincludedir = $(includedir)/asdcplib
am__cd = CDPATH="$${ZSH_VERSION+.}$(PATH_SEPARATOR)" && cd
install_sh_DATA = $(install_sh) -c -m 644
install_sh_PROGRAM = $(install_sh) -c
install_sh_SCRIPT = $(install_sh) -c
INSTALL_HEADER = $(INSTALL_DATA)
transform = $(program_transform_name)
NORMAL_INSTALL = :
PRE_INSTALL = :
POST_INSTALL = :
NORMAL_UNINSTALL = :
PRE_UNINSTALL = :
POST_UNINSTALL = :
build_triplet = i686-pc-linux-gnu
host_triplet = i686-pc-linux-gnu
subdir = .
DIST_COMMON = README $(am__configure_deps) $(srcdir)/Makefile.am \
    $(srcdir)/Makefile.in $(top_srcdir)/configure COPYING \
    build-aux/config.guess build-aux/config.sub build-aux/depcomp \
    build-aux/install-sh build-aux/ltmain.sh build-aux/missing
ACLOCAL_M4 = $(top_srcdir)/aclocal.m4
am__aclocal_m4_deps = $(top_srcdir)/m4/ax_lib_expat.m4 \
    $(top_srcdir)/m4/ax_lib_openssl.m4 \
    $(top_srcdir)/m4/ax_lib_xerces.m4 \
    $(top_srcdir)/m4/az_python.m4 $(top_srcdir)/configure.ac
am__configure_deps = $(am__aclocal_m4_deps) $(CONFIGURE_DEPENDENCIES) \
    $(ACLOCAL_M4)
am__CONFIG_DISTCLEAN_FILES = config.status config.cache config.log \
 configure.lineno config.status.lineno
mkinstalldirs = $(install_sh) -d
CONFIG_CLEAN_FILES =
SOURCES =
DIST_SOURCES =
RECURSIVE_TARGETS = all-recursive check-recursive dvi-recursive \
    html-recursive info-recursive install-data-recursive \
    install-dvi-recursive install-exec-recursive \
    install-html-recursive install-info-recursive \
    install-pdf-recursive install-ps-recursive install-recursive \
    installcheck-recursive installdirs-recursive pdf-recursive \
    ps-recursive uninstall-recursive
RECURSIVE_CLEAN_TARGETS = mostlyclean-recursive clean-recursive    \
  distclean-recursive maintainer-clean-recursive
ETAGS = etags
CTAGS = ctags
DIST_SUBDIRS = $(SUBDIRS)
DISTFILES = $(DIST_COMMON) $(DIST_SOURCES) $(TEXINFOS) $(EXTRA_DIST)
distdir = $(PACKAGE)-$(VERSION)
top_distdir = $(distdir)
am__remove_distdir = \
  { test ! -d $(distdir) \
    || { find $(distdir) -type d ! -perm -200 -exec chmod u+w {} ';' \
         && rm -fr $(distdir); }; }
DIST_ARCHIVES = $(distdir).tar.gz
GZIP_ENV = --best
distuninstallcheck_listfiles = find . -type f -print
distcleancheck_listfiles = find . -type f -print
ACLOCAL = ${SHELL} /home/edoardo/AsDCP/asdcplib-1.4.24/build-aux/missing --run aclocal-1.10
AMTAR = ${SHELL} /home/edoardo/AsDCP/asdcplib-1.4.24/build-aux/missing --run tar
AR = ar
AUTOCONF = ${SHELL} /home/edoardo/AsDCP/asdcplib-1.4.24/build-aux/missing --run autoconf
AUTOHEADER = ${SHELL} /home/edoardo/AsDCP/asdcplib-1.4.24/build-aux/missing --run autoheader
AUTOMAKE = ${SHELL} /home/edoardo/AsDCP/asdcplib-1.4.24/build-aux/missing --run automake-1.10
AWK = mawk
CC = gcc
CCDEPMODE = depmode=gcc3
CFLAGS = -g -O2
CPP = gcc -E
CPPFLAGS =  -I/usr/include -DHAVE_SSL=1
CXX = g++
CXXCPP = g++ -E
CXXDEPMODE = depmode=gcc3
CXXFLAGS = -g -O2 -D_FILE_OFFSET_BITS=64
CYGPATH_W = echo
DEFS = -DPACKAGE_NAME=\"asdcplib\" -DPACKAGE_TARNAME=\"asdcplib\" -DPACKAGE_VERSION=\"1.4.24\" -DPACKAGE_STRING=\"asdcplib\ 1.4.24\" -DPACKAGE_BUGREPORT=\"asdcplib@cinecert.com\" -DPACKAGE=\"asdcplib\" -DVERSION=\"1.4.24\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -D_FILE_OFFSET_BITS=64 -DHAVE_LIBPTHREAD=1
DEPDIR = .deps
DSYMUTIL = 
ECHO = echo
ECHO_C = 
ECHO_N = -n
ECHO_T = 
EGREP = /bin/grep -E
EXEEXT = 
EXPAT_CFLAGS = 
EXPAT_LDFLAGS = 
EXPAT_VERSION = 
F77 = 
FFLAGS = 
GREP = /bin/grep
INSTALL = /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = $(install_sh) -c -s
LDFLAGS =  -L/usr/lib -lssl -lcrypto
LIBOBJS = 
LIBS = -lpthread 
LIBTOOL = $(SHELL) $(top_builddir)/libtool
LN_S = ln -s
LTLIBOBJS = 
MAKEINFO = ${SHELL} /home/edoardo/AsDCP/asdcplib-1.4.24/build-aux/missing --run makeinfo
MKDIR_P = /bin/mkdir -p
NMEDIT = 
OBJEXT = o
OPENSSL_CPPFLAGS = -I/usr/include
OPENSSL_LDFLAGS = -L/usr/lib
OPENSSL_LIBS = -lssl -lcrypto
OPENSSL_VERSION = OpenSSL 0.9.8g 19 Oct 2007
PACKAGE = asdcplib
PACKAGE_BUGREPORT = asdcplib@cinecert.com
PACKAGE_NAME = asdcplib
PACKAGE_STRING = asdcplib 1.4.24
PACKAGE_TARNAME = asdcplib
PACKAGE_VERSION = 1.4.24
PATH_SEPARATOR = :
PYTHON = 
PYTHON_CPPFLAGS = 
PYTHON_CSPEC = 
PYTHON_EXECDIR = 
PYTHON_EXECPREFIX = 
PYTHON_LDFLAGS = 
PYTHON_LSPEC = 
PYTHON_PREFIX = 
PYTHON_SHORTVERSION = 
RANLIB = ranlib
SED = /bin/sed
SET_MAKE = 
SHELL = /bin/bash
STRIP = strip
VERSION = 1.4.24
XERCES_CPPFLAGS = 
XERCES_LDFLAGS = 
XERCES_LIBS = 
XERCES_VERSION = 
abs_builddir = /home/edoardo/AsDCP/asdcplib-1.4.24
abs_srcdir = /home/edoardo/AsDCP/asdcplib-1.4.24
abs_top_builddir = /home/edoardo/AsDCP/asdcplib-1.4.24
abs_top_srcdir = /home/edoardo/AsDCP/asdcplib-1.4.24
ac_ct_CC = gcc
ac_ct_CXX = g++
ac_ct_F77 = 
am__include = include
am__leading_dot = .
am__quote = 
am__tar = ${AMTAR} chof - "$$tardir"
am__untar = ${AMTAR} xf -
bindir = ${exec_prefix}/bin
build = i686-pc-linux-gnu
build_alias = 
build_cpu = i686
build_os = linux-gnu
build_vendor = pc
builddir = .
datadir = ${datarootdir}
datarootdir = ${prefix}/share
docdir = ${datarootdir}/doc/${PACKAGE_TARNAME}
dvidir = ${docdir}
exec_prefix = ${prefix}
host = i686-pc-linux-gnu
host_alias = 
host_cpu = i686
host_os = linux-gnu
host_vendor = pc
htmldir = ${docdir}
includedir = ${prefix}/include
infodir = ${datarootdir}/info
install_sh = $(SHELL) /home/edoardo/AsDCP/asdcplib-1.4.24/build-aux/install-sh
libdir = ${exec_prefix}/lib
libexecdir = ${exec_prefix}/libexec
localedir = ${datarootdir}/locale
localstatedir = ${prefix}/var
mandir = ${datarootdir}/man
mkdir_p = /bin/mkdir -p
oldincludedir = /usr/include
pdfdir = ${docdir}
prefix = /usr/local
program_transform_name = s,x,x,
psdir = ${docdir}
sbindir = ${exec_prefix}/sbin
sharedstatedir = ${prefix}/com
srcdir = .
sysconfdir = ${prefix}/etc
target_alias = 
top_build_prefix = 
top_builddir = .
top_srcdir = .
SUBDIRS = src win32
ACLOCAL_AMFLAGS = -I m4
all: all-recursive
```Would it be different if I had a 64bit install of Ubuntu? I can do it easily but I don't know if I have a 32 or 64 bit install, how can I check? Thanks

---

### Post by SevenMachines on 2009-11-07
just to check, does asdcplib build fine with the makefile as shown? i forget where we are, is it a build problem with kdm-decrypt thats holding you back.
changing to 64 bit wouldnt make any difference i'd think, works fine in 32 bit too

---

### Post by edo1080 on 2009-11-07
Yes, of course, asdcplib always builds and installs fine, the problem is only with the kdm-decrypt compilation, the error is given when running 

g++ -o kdm-decrypt kdm-decrypt.cpp -lxerces-c -lkumu -lcrypto -lxml-security-c


I have always the same error whatever I add to the asdcplib makefile. It doesn't matter if I have -D_FILE_OFFSET_BITS=64 option in the makefile, the error is always the same.

```
n file included from kdm-decrypt.cpp:12:
/usr/local/include/KM_fileio.h:112: error: redefinition of &#8216;void Kumu::compile_time_size_checker() [with bool sizecheck = false]&#8217;
/usr/local/include/KM_fileio.h:99: error: &#8216;void Kumu::compile_time_size_checker() [with bool sizecheck = false]&#8217; previously declared here
```Since asdcplib compiles smoothly with ot without  -D_FILE_OFFSET_BITS=64 option, is it better to add it or to launch ./configure instead of CXXFLAGS="-O2 -g -D_FILE_OFFSET_BITS=64" ./configure ? Please note I'm now using Ubuntu 9.10 even if when I started this thread I was using the 9.04. Thanks

---

### Post by SevenMachines on 2009-11-07
sorry, i should have paid more attention and thought about it 2 pages ago, i think i got distracted by not having 32bit at the time. offset bits is added when compiling kdm-decrypt on 32 bit, on 64 bit this isnt needed

$g++ -D_FILE_OFFSET_BITS=64 -o kdm-decrypt kdm-decrypt.cpp  -lxerces-c  -lkumu -lcrypto -lxml-security-c

---

### Post by SevenMachines on 2009-11-07
note-to-self: I must pay more attention next time, it saves everybody time and will stop me posting useless advice :)

---

### Post by edo1080 on 2009-11-07
Wonderful!!!!!! It really works to me!!!! You helped me a lot, I finally have been able to compile it. I've no words to thank you.

---

### Post by SevenMachines on 2009-11-07
i can only apologise for not giving the right advice sooner, just got thrown due to -D_FILE_OFFSET_BITS=64 not being needed to compile kdm-decrypt in 64 bits so confused myself into thinking it was an asdcplib problem you had. glad its working for you though :)

---

### Post by edo1080 on 2009-11-07
No problem for this; please don't worry;  you've been really helpful. I'm no so much into Unbuntu and it could also have been my fault to ask the question in proper way.

---

