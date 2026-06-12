---
title: "[SOLVED] Compiling terragear"
date: 2008-05-26
forum: Programming Talk
---

### Post by MDSmith2 on 2008-05-26
Hello.
I'm in a bit of a jam here compiling terragear (the part of flightgear that makes the terrain) and wondering if anyone could help.
Everything  configured ok ```
michael@mdsmiths:~/Desktop/terra/TerraGear-0.9.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for glib-config... yes
checking for gts-config... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for extra include and lib directories...
   + found /usr/X11R6/lib
   + found /usr/X11R6/bin
checking for X... libraries , headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for library containing inet_addr... none required
checking for library containing socket... none required
checking for library containing main... none required
checking for library containing cos... -lm
checking for library containing XCreateWindow... -lX11
checking for library containing XShmCreateImage... -lXext
checking for library containing XGetExtensionVersion... -lXi
checking for library containing IceOpenConnection... -lICE
checking for library containing SmcOpenConnection... -lSM
checking for library containing XtMalloc... -lXt
checking for library containing XmuLookupStandardColormap... no
checking for library containing glNewList... -lGL
checking for library containing gluLookAt... -lGLU
checking for library containing glutGetModifiers... -lglut
checking for ulInit in -lplibul... yes
checking how to run the C++ preprocessor... g++ -E
checking plib/pu.h usability... yes
checking plib/pu.h presence... yes
checking for plib/pu.h... yes
checking nurbs++/nurbsS.h usability... yes
checking nurbs++/nurbsS.h presence... yes
checking for nurbs++/nurbsS.h... yes
checking gts.h usability... yes
checking gts.h presence... yes
checking for gts.h... yes
checking gpc.h usability... yes
checking gpc.h presence... yes
checking for gpc.h... yes
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for sys/stat.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking for unistd.h... (cached) yes
checking for windows.h... (cached) no
checking winbase.h usability... no
checking winbase.h presence... no
checking for winbase.h... no
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking simgear/version.h usability... yes
checking simgear/version.h presence... yes
checking for simgear/version.h... yes
checking for proper simgear version... 0.3.6 or greater... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for socklen_t... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for ftime... yes
checking for gettimeofday... yes
checking for timegm... yes
checking for memcpy... yes
checking for bcopy... yes
checking for mktime... yes
checking for strstr... yes
checking for rand... yes
checking for random... yes
checking for setitimer... yes
checking for getitimer... yes
checking for signal... yes
checking for GetLocalTime... no
checking for rint... yes
checking for getrusage... yes
configure: creating ./config.status
config.status: creating VERSION
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/Include/Makefile
config.status: creating src/Airports/Makefile
config.status: creating src/Airports/GenAirports/Makefile
config.status: creating src/Airports/Utils/Makefile
config.status: creating src/BuildTiles/Makefile
config.status: creating src/BuildTiles/Clipper/Makefile
config.status: creating src/BuildTiles/GenOutput/Makefile
config.status: creating src/BuildTiles/Match/Makefile
config.status: creating src/BuildTiles/Triangulate/Makefile
config.status: creating src/BuildTiles/Main/Makefile
config.status: creating src/BuildTiles/Osgb36/Makefile
config.status: creating src/BuildTiles/Parallel/Makefile
config.status: creating src/Lib/Makefile
config.status: creating src/Lib/Array/Makefile
config.status: creating src/Lib/DEM/Makefile
config.status: creating src/Lib/e00/Makefile
config.status: creating src/Lib/Geometry/Makefile
config.status: creating src/Lib/HGT/Makefile
config.status: creating src/Lib/landcover/Makefile
config.status: creating src/Lib/Optimize/Makefile
config.status: creating src/Lib/Output/Makefile
config.status: creating src/Lib/Polygon/Makefile
config.status: creating src/Lib/poly2tri/Makefile
config.status: creating src/Lib/shapelib/Makefile
config.status: creating src/Lib/TriangleJRS/Makefile
config.status: creating src/Lib/vpf/Makefile
config.status: creating src/Prep/Makefile
config.status: creating src/Prep/ArrayFit/Makefile
config.status: creating src/Prep/DemChop/Makefile
config.status: creating src/Prep/DemInfo/Makefile
config.status: creating src/Prep/DemRaw2ascii/Makefile
config.status: creating src/Prep/E00Lines/Makefile
config.status: creating src/Prep/GSHHS/Makefile
config.status: creating src/Prep/MergerClipper/Makefile
config.status: creating src/Prep/Photo/Makefile
config.status: creating src/Prep/ShapeFile/Makefile
config.status: creating src/Prep/TGVPF/Makefile
config.status: creating src/Prep/Terra/Makefile
config.status: creating src/Prep/TerraFit/Makefile
config.status: creating src/Prep/Tower/Makefile
config.status: creating src/Prep/UserDef/Makefile
config.status: creating src/Utils/Makefile
config.status: creating src/Utils/cdrom/Makefile
config.status: creating src/Utils/download-map/Makefile
config.status: creating src/Include/config.h
config.status: src/Include/config.h is unchanged
config.status: executing depfiles commands

Configure Summary
=================
Prefix: /usr/local
Debug messages: yes
michael@mdsmiths:~/Desktop/terra/TerraGear-0.9.5$ 

```
but when i try to make it i keep getting this```
michael@mdsmiths:~/Desktop/terra/TerraGear-0.9.5$ make
Making all in src
make[1]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src'
Making all in Include
make[2]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Include'
make  all-am
make[3]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Include'
make[3]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Include'
make[2]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Include'
Making all in Lib
make[2]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Lib'
Making all in Array
make[3]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Lib/Array'
g++  -g -O2  -L/usr/X11R6/lib -o testarray  testarray.o ../../../src/Lib/Array/libArray.a -lsgbucket -lsgmath -lsgmisc -lsgdebug -lsgxml -L/usr/lib -lgts -lglib-2.0 -lm -L/usr/lib -lglib -lz  -lm 
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::reinit()'
/usr/lib/libsgxml.so: undefined reference to `vtable for sg_location'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::is_suspended() const'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::bind()'
/usr/lib/libsgxml.so: undefined reference to `sg_io_exception::~sg_io_exception()'
/usr/lib/libsgxml.so: undefined reference to `typeinfo for sg_io_exception'
/usr/lib/libsgxml.so: undefined reference to `typeinfo for sg_throwable'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::~SGSubsystem()'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::suspend()'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::suspend(bool)'
/usr/lib/libsgxml.so: undefined reference to `sg_location::~sg_location()'
/usr/lib/libsgmisc.so: undefined reference to `SGPropertyNode::getDoubleValue() const'
/usr/lib/libsgmisc.so: undefined reference to `SGPropertyNode::setDoubleValue(double)'
/usr/lib/libsgxml.so: undefined reference to `vtable for sg_io_exception'
/usr/lib/libsgxml.so: undefined reference to `vtable for sg_throwable'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::postinit()'
/usr/lib/libsgxml.so: undefined reference to `sg_location::sg_location(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, int)'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::resume()'
/usr/lib/libsgxml.so: undefined reference to `sg_exception::~sg_exception()'
/usr/lib/libsgmisc.so: undefined reference to `typeinfo for SGSubsystem'
/usr/lib/libsgxml.so: undefined reference to `sg_io_exception::sg_io_exception(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, sg_location const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::unbind()'
collect2: ld returned 1 exit status
make[3]: *** [testarray] Error 1
make[3]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Lib/Array'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src/Lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.5/src'
make: *** [all-recursive] Error 1
michael@mdsmiths:~/Desktop/terra/TerraGear-0.9.5$ 
```
Please any help or ideas that could help would be appreaceated.

---

### Post by tamoneya on 2008-05-26
you have build-essential installed?  This is the most common problem with make.  Install it like this:
```
sudo apt-get install build-essential
```

---

### Post by MDSmith2 on 2008-05-26
> **tamoneya said:**
> you have build-essential installed?  This is the most common problem with make.  Install it like this:
```
sudo apt-get install build-essential
```
I do build-essential and all dependencies (unless there one ./configures not telling me about and its out to make me mad:))

---

### Post by cubeist on 2008-05-26
Even though ./configure doesn't show it, it looks like you are missing libsgxml, or the version you have is out of date for the new terragear.

If my memory serves me, libsgxml and other libsg's are part of the simgear package.  So to install the latest terragear you may have to install the latest simgear first.

For curiosity sake why do you need the latest terragear?

Edit - Just noticed that the latest simgear libs are 1.0.0 version (which come with simgear in gutsy/hardy) so you may have to build simgear from cvs...

---

### Post by MDSmith2 on 2008-05-26
I have simgear0 and simgeardev both 0.3.10-2 and actually have a slight older version of terragear.
The reason i want terragear is so i can put a custom airport (that just happens to be named after me:)).
If you have build terragear before can you tell me how you did it?

---

### Post by MDSmith2 on 2008-05-26
i tryed 0.9.8 this time and get the following: ```
michael@mdsmiths:~/Desktop/terra/TerraGear-0.9.8$ make
Making all in src
make[1]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src'
Making all in Include
make[2]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Include'
make  all-am
make[3]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Include'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Include'
make[2]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Include'
Making all in Lib
make[2]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Lib'
Making all in Array
make[3]: Entering directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Lib/Array'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../../src/Include -I../../../src  -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include -I/usr/include/glib-1.2 -I/usr/lib/glib/include  -g -O2 -MT array.o -MD -MP -MF ".deps/array.Tpo" -c -o array.o array.cxx; \
    then mv -f ".deps/array.Tpo" ".deps/array.Po"; else rm -f ".deps/array.Tpo"; exit 1; fi
rm -f libArray.a
ar cru libArray.a array.o 
ranlib libArray.a
if g++ -DHAVE_CONFIG_H -I. -I. -I../../../src/Include -I../../../src  -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include -I/usr/include/glib-1.2 -I/usr/lib/glib/include  -g -O2 -MT testarray.o -MD -MP -MF ".deps/testarray.Tpo" -c -o testarray.o testarray.cxx; \
    then mv -f ".deps/testarray.Tpo" ".deps/testarray.Po"; else rm -f ".deps/testarray.Tpo"; exit 1; fi
g++  -g -O2  -L/usr/X11R6/lib -o testarray  testarray.o ../../../src/Lib/Array/libArray.a -lsgbucket -lsgmath -lsgmisc -lsgdebug -lsgxml -L/usr/lib -lgts -lglib-2.0 -lm -L/usr/lib -lglib -lz  -lm 
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::reinit()'
/usr/lib/libsgxml.so: undefined reference to `vtable for sg_location'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::is_suspended() const'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::bind()'
/usr/lib/libsgxml.so: undefined reference to `sg_io_exception::~sg_io_exception()'
/usr/lib/libsgxml.so: undefined reference to `typeinfo for sg_io_exception'
/usr/lib/libsgxml.so: undefined reference to `typeinfo for sg_throwable'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::~SGSubsystem()'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::suspend()'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::suspend(bool)'
/usr/lib/libsgxml.so: undefined reference to `sg_location::~sg_location()'
/usr/lib/libsgmisc.so: undefined reference to `SGPropertyNode::getDoubleValue() const'
/usr/lib/libsgmisc.so: undefined reference to `SGPropertyNode::setDoubleValue(double)'
/usr/lib/libsgxml.so: undefined reference to `vtable for sg_io_exception'
/usr/lib/libsgxml.so: undefined reference to `vtable for sg_throwable'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::postinit()'
/usr/lib/libsgxml.so: undefined reference to `sg_location::sg_location(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, int)'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::resume()'
/usr/lib/libsgxml.so: undefined reference to `sg_exception::~sg_exception()'
/usr/lib/libsgmisc.so: undefined reference to `typeinfo for SGSubsystem'
/usr/lib/libsgxml.so: undefined reference to `sg_io_exception::sg_io_exception(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, sg_location const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/lib/libsgmisc.so: undefined reference to `SGSubsystem::unbind()'
collect2: ld returned 1 exit status
make[3]: *** [testarray] Error 1
make[3]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Lib/Array'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src'
make: *** [all-recursive] Error 1
```
now i am going to try to build simgear over and see if that helps.

---

### Post by MDSmith2 on 2008-05-26
Ok this time i build simgear myself instead of using a deb and got past the above error message but now when i try to make terragear i get this ```
if g++ -DHAVE_CONFIG_H -I. -I. -I../../../src/Include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include -I/usr/include/glib-1.2 -I/usr/lib/glib/include  -g -O2 -MT library.o -MD -MP -MF ".deps/library.Tpo" -c -o library.o library.cxx; \
    then mv -f ".deps/library.Tpo" ".deps/library.Po"; else rm -f ".deps/library.Tpo"; exit 1; fi
In file included from library.cxx:8:
coverage.hxx:54: error: extra qualification ‘VpfCoverage::’ on member ‘VpfCoverage’
make[3]: *** [library.o] Error 1
make[3]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Lib/vpf'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src/Lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/michael/Desktop/terra/TerraGear-0.9.8/src'
make: *** [all-recursive] Error 1

```
Any ideas?

---

### Post by MDSmith2 on 2008-05-26
I Got It!!!
First i removed the VpfCoverage:: from line 54 of coverage.hxx then i changed private to public on line 146 from database.hxx
Thanks for you help!

---

### Post by cubeist on 2008-05-26
> **MDSmith2 said:**
> I Got It!!!
First i removed the VpfCoverage:: from line 54 of coverage.hxx then i changed private to public on line 146 from database.hxx
Thanks for you help!

Good work, I'll bookmark this for the nextime I build terragear... Happy flying!

---

### Post by MDSmith2 on 2008-05-26
> **cubeist said:**
> Good work, I'll bookmark this for the nextime I build terragear... Happy flying!
Same to you.
:)

---

