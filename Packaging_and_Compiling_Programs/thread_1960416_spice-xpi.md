---
title: "spice-xpi"
date: 2012-04-17
forum: Packaging and Compiling Programs
---

### Post by bruijnea on 2012-04-17
I want to compile the spice-xpi-2.7 package([http://spice-space.org/download.html](http://spice-space.org/download.html)), but when i do this i have the following error:

# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether gcc and cc understand -c and -o together... yes
checking for x86 or x86-64 platform... 64 bit
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LOG4CPP... yes
checking for XUL... no
configure: error: Package requirements (libxul-embedding >= 1.9 nspr >= 4.7.1) were not met:

No package 'libxul-embedding' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

What can i do to configure, make, make install spice-xpi

---

### Post by oldos2er on 2012-04-17
Moved to Packaging and Compiling Programs.

---

### Post by speedoops on 2012-09-26
I found xulrunner-1.9.2 here: [https://launchpad.net/ubuntu/lucid/+source/xulrunner-1.9.2/1.9.2.2+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/xulrunner-1.9.2/1.9.2.2+nobinonly-0ubuntu1) , somewhere say can use xulrunner instead libxul-dev, but I don't know how to use this. Anyone can help?

---

### Post by mgiammarco on 2012-10-15
> **speedoops said:**
> I found xulrunner-1.9.2 here: [https://launchpad.net/ubuntu/lucid/+source/xulrunner-1.9.2/1.9.2.2+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/xulrunner-1.9.2/1.9.2.2+nobinonly-0ubuntu1) , somewhere say can use xulrunner instead libxul-dev, but I don't know how to use this. Anyone can help?

I have tried  also with xulrunner 2.0 but the source does not compile correctly.

I have found a ppa but it crashes.

Please give us a spice xpi that works. It is ridicolous that is it all open source but spice for ovirt is usable only on fedora.

---

### Post by speedoops on 2012-10-18
My Solution:

# 1. libxul-embedding

# [https://launchpad.net/ubuntu/natty/i386/xulrunner-1.9.2/1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1](https://launchpad.net/ubuntu/natty/i386/xulrunner-1.9.2/1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1)
wget [http://launchpadlibrarian.net/96607586/xulrunner-1.9.2_1.9.2.28%2Bbuild1%2Bnobinonly-0ubuntu0.11.04.1_i386.deb](http://launchpadlibrarian.net/96607586/xulrunner-1.9.2_1.9.2.28%2Bbuild1%2Bnobinonly-0ubuntu0.11.04.1_i386.deb)
sudo dpkg -i xulrunner-1.9.2_1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1_i386.deb

sudo apt-get install libdbus-glib-1-dev libnotify-dev libiw-dev

# [https://launchpad.net/ubuntu/natty/i386/xulrunner-1.9.2-dev/1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1](https://launchpad.net/ubuntu/natty/i386/xulrunner-1.9.2-dev/1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1)
# Depends on: libiw-dev libnotify-dev libnspr4-dev libnss3-dev xulrunner-1.9.2 (= 1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1) 
wget [http://launchpadlibrarian.net/96607590/xulrunner-1.9.2-dev_1.9.2.28%2Bbuild1%2Bnobinonly-0ubuntu0.11.04.1_i386.deb](http://launchpadlibrarian.net/96607590/xulrunner-1.9.2-dev_1.9.2.28%2Bbuild1%2Bnobinonly-0ubuntu0.11.04.1_i386.deb)
sudo dpkg -i xulrunner-1.9.2-dev_1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1_i386.deb


# 2. xul-sdk-bin
# find / -name "typelib.py" 2>/dev/null
# [http://code.google.com/p/google-web-toolkit/source/browse/plugin-sdks/gecko-sdks/?r=10842#gecko-sdks%2Fgecko-10.0.0%2Fbin](http://code.google.com/p/google-web-toolkit/source/browse/plugin-sdks/gecko-sdks/?r=10842#gecko-sdks%2Fgecko-10.0.0%2Fbin)

---

### Post by Jaypers on 2013-05-31
Hi,

I am running Ubuntu 13.04 and I got the spice xpi working using the following steps:

1. Install the spice-client package which gives you /usr/bin/spicec 
2. Extract the libnsISpicec.so file from the latest Fedora (FC19) spice-xpi RPM.
3. Placed it in /usr/lib/mozilla/plugins/
4. Restart Firefox.

Worked for me!

---

### Post by tabasko on 2013-07-03
Hi,

Did you use i386 or x86_64 rpm with libnsISpicec.so? I tried your method on 13.04 and with firefox 22, but no luck :(

Thanks!

---

### Post by eaton-james on 2013-09-16
I just wanted to say that these steps worked perfectly for me. I installed spice-client, I downloaded package spice-xpi-2.8-3.fc19.x86_64.rpm (which you can find by using google) and then I placed the file from the plugins directory into the /usr/mozilla/plugins directory, after restarting Firefox, I can now view the console from RHEV/OVIRT.
[TABLE="class: textblack"]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

I am using Xubuntu 13.04, Firefox 23.0

---

### Post by nyshadham on 2013-09-18
The instructions given by [COLOR=#000000]Jaypers worked like a charm for me. Thanks.[/COLOR]

---

### Post by jakommo2 on 2014-01-11
jaypers instructions worked for me too on 12.04.
Thanks

---

