---
title: "audiere problems"
date: 2010-05-06
forum: Programming Talk
---

### Post by Nebelhom on 2010-05-06
sorry for double posting. didn't know how to move the thread from a different section (which I think was the wrong one... I am actually not sure where to post this), but I am desperate for an answer on this one. So I just reopened the thread in this forum. Thanks for the help:

-----------

Hi folks,

different python module for playing audio similar problem. This time pyAudiere (sorry for sounding a little bored by this, but I had not much success of late)

Ok, I am trying to install [Audiere]("http://audiere.sourceforge.net/home.php") which doesnt work.

I download the dependencies (libaudiere), then I extract the tarball download from their website.

then I followed a procedure from [this website]("http://sphere.sourceforge.net/flik/files/linux.txt") because that was the only one I could find (documentation is a little sparse in that compartment unfortunately)

from the terminal I write

```
./configure
```

which works fine

then I try

```
make
```

which gives me this error

```
nebelhom@nebelhom-desktop:~/audiere-1.9.4$ make
make  all-recursive
make[1]: Entering directory `/home/nebelhom/audiere-1.9.4'
Making all in doc
make[2]: Entering directory `/home/nebelhom/audiere-1.9.4/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/nebelhom/audiere-1.9.4/doc'
Making all in src
make[2]: Entering directory `/home/nebelhom/audiere-1.9.4/src'
Making all in mpaudec
make[3]: Entering directory `/home/nebelhom/audiere-1.9.4/src/mpaudec'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/nebelhom/audiere-1.9.4/src/mpaudec'
make[3]: Entering directory `/home/nebelhom/audiere-1.9.4/src'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"audiere\" -DVERSION=\"1.9.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DNO_FLAC=1 -DHAVE_CLOCK_GETTIME=1 -DSTDC_HEADERS=1 -DHAVE_OSS=1 -DNO_SPEEX=1  -I. -I.     -g -O2 -Wall -Wno-non-virtual-dtor -MT midi_null.lo -MD -MP -MF ".deps/midi_null.Tpo" -c -o midi_null.lo midi_null.cpp; \
	then mv -f ".deps/midi_null.Tpo" ".deps/midi_null.Plo"; else rm -f ".deps/midi_null.Tpo"; exit 1; fi
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"audiere\" -DVERSION=\"1.9.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DNO_FLAC=1 -DHAVE_CLOCK_GETTIME=1 -DSTDC_HEADERS=1 -DHAVE_OSS=1 -DNO_SPEEX=1 -I. -I. -g -O2 -Wall -Wno-non-virtual-dtor -MT midi_null.lo -MD -MP -MF .deps/midi_null.Tpo -c midi_null.cpp  -fPIC -DPIC -o .libs/midi_null.o
In file included from midi_null.cpp:1:
audiere.h: In function 'void audiere::SplitString(std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&, const char*, char)':
audiere.h:1148: error: 'strchr' was not declared in this scope
audiere.h: In function 'void audiere::GetSupportedFileFormats(std::vector<audiere::FileFormatDesc, std::allocator<audiere::FileFormatDesc> >&)':
audiere.h:1177: error: 'strchr' was not declared in this scope
audiere.h: In function 'void audiere::EnumerateCDDevices(std::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&)':
audiere.h:1535: error: 'strlen' was not declared in this scope
make[3]: *** [midi_null.lo] Error 1
make[3]: Leaving directory `/home/nebelhom/audiere-1.9.4/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nebelhom/audiere-1.9.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nebelhom/audiere-1.9.4'
make: *** [all] Error 2

```

If anyone of you has any idea what this could mean and knows a fix, I would be very grateful. it is driving me insane, that I cannot install any of these modules (PyMedia was before). they are not in synaptic so I am a bit at a loss and I have hardly any experience with installations from source... ;(

---

