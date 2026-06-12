---
title: "C Compiler confusion"
date: 2005-03-10
forum: Programming Talk
---

### Post by Bad2theBone on 2005-03-10
Is cpp the same as g++???

I tried to configure hplip and was getting:

configure: error: C++ preprocessor "/lib/cpp" fails sanity check.

I found that /lib/cpp was symlinked to /usr/bin/cpp-3.3, changing that to /usr/bin/cpp-2.95 allowed configure to run all the way with what I thought was error free. 

Then when I ran make I got:

Making all in prnt/hpijs
make[1]: Entering directory `/home/scott/Downloads/hplip-0.8.8/prnt/hpijs'
source='hpijs.cpp' object='hpijs.o' libtool=no \
DEPDIR=.deps depmode=none /bin/sh ./../../depcomp \
g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"hpijs\" -DVERSION=\"2.0.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_MALLOC_H=1 -DHAVE_SYSLOG_H=1 -DHAVE_UNISTD_H=1 -DVERSION=\"2.0.2\" -DHAVE_STRTOD=1 -DHAVE_STRTOL=1 -DHAVE_LIBM=1  -I. -I.     -O2 -Wall -DAPDK_LITTLE_ENDIAN -DAPDK_DJ660 -DAPDK_DJ6xx -DAPDK_DJ6xxPhoto -DAPDK_DJ8xx -DAPDK_DJ9xx -DAPDK_DJ9xxVIP -DAPDK_DJ630 -DAPDK_APOLLO2XXX -DAPDK_APOLLO21XX -DAPDK_APOLLO2560 -DAPDK_DJ600 -DAPDK_DJ350 -DAPDK_DJ8x5 -DAPDK_PSP100 -DAPDK_AUTODUPLEX -DAPDK_HIGH_RES_MODES -DAPDK_LJMONO -DAPDK_DJ540 -DAPDK_DJ850 -DAPDK_DJ890 -DAPDK_DJ3320 -DAPDK_LJCOLOR -DAPDK_DJGENERICVIP -DAPDK_BUFFER_SEND -DAPDK_LDL_COMPRESS -DAPDK_EXTENDED_MEDIASIZE -DAPDK_MLC_PRINTER -DAPDK_DJ3600 -DAPDK_LINUX -DAPDK_AUTO_INCLUDE -c -o hpijs.o hpijs.cpp
./../../depcomp: line 504: exec: g++: not found
make[1]: *** [hpijs.o] Error 127
make[1]: Leaving directory `/home/scott/Downloads/hplip-0.8.8/prnt/hpijs'
make: *** [all-recursive] Error 1

What now??? ](*,) 

TIA

---

### Post by bored2k on 2005-03-10
[QUOTE=Bad2theBone]Is cpp the same as g++???

I tried to configure hplip and was getting:

configure: error: C++ preprocessor "/lib/cpp" fails sanity check.

I found that /lib/cpp was symlinked to /usr/bin/cpp-3.3, changing that to /usr/bin/cpp-2.95 allowed configure to run all the way with what I thought was error free. 

Then when I ran make I got:

Making all in prnt/hpijs
make[1]: Entering directory `/home/scott/Downloads/hplip-0.8.8/prnt/hpijs'
source='hpijs.cpp' object='hpijs.o' libtool=no \
DEPDIR=.deps depmode=none /bin/sh ./../../depcomp \
g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"hpijs\" -DVERSION=\"2.0.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_MALLOC_H=1 -DHAVE_SYSLOG_H=1 -DHAVE_UNISTD_H=1 -DVERSION=\"2.0.2\" -DHAVE_STRTOD=1 -DHAVE_STRTOL=1 -DHAVE_LIBM=1  -I. -I.     -O2 -Wall -DAPDK_LITTLE_ENDIAN -DAPDK_DJ660 -DAPDK_DJ6xx -DAPDK_DJ6xxPhoto -DAPDK_DJ8xx -DAPDK_DJ9xx -DAPDK_DJ9xxVIP -DAPDK_DJ630 -DAPDK_APOLLO2XXX -DAPDK_APOLLO21XX -DAPDK_APOLLO2560 -DAPDK_DJ600 -DAPDK_DJ350 -DAPDK_DJ8x5 -DAPDK_PSP100 -DAPDK_AUTODUPLEX -DAPDK_HIGH_RES_MODES -DAPDK_LJMONO -DAPDK_DJ540 -DAPDK_DJ850 -DAPDK_DJ890 -DAPDK_DJ3320 -DAPDK_LJCOLOR -DAPDK_DJGENERICVIP -DAPDK_BUFFER_SEND -DAPDK_LDL_COMPRESS -DAPDK_EXTENDED_MEDIASIZE -DAPDK_MLC_PRINTER -DAPDK_DJ3600 -DAPDK_LINUX -DAPDK_AUTO_INCLUDE -c -o hpijs.o hpijs.cpp
./../../depcomp: line 504: exec: g++: not found
make[1]: *** [hpijs.o] Error 127
make[1]: Leaving directory `/home/scott/Downloads/hplip-0.8.8/prnt/hpijs'
make: *** [all-recursive] Error 1

What now??? ](*,) 

TIA[/QUOTE]
 configure: error: C++ preprocessor "/lib/cpp" fails sanity check.

Try apt-get gcc cpp g++

---

### Post by tennisplaya05 on 2006-08-21
was having the same prob. but that seemed to work. Thanks bored2k

---

