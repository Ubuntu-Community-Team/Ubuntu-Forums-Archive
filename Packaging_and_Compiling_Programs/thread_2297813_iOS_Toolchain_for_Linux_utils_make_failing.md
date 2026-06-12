---
title: "iOS Toolchain for Linux utils make failing"
date: 2015-10-06
forum: Packaging and Compiling Programs
---

### Post by spbach1234 on 2015-10-06
I am trying to build this iOS toolchain: code.google.com/p/ios-toolchain-based-on-clang-for-linux
and I get to step four and type make and I get the error below:

```
In file included from /usr/lib/llvm-3.6/include/clang/Frontend/CompilerInstance.h:17:0,
                 from getLocalizedStringFromFile.cpp:21:
/usr/lib/llvm-3.6/include/clang/Frontend/Utils.h:64:6: note: in passing argument 3 of ‘void clang::InitializePreprocessor(clang::Preprocessor&, const clang::PreprocessorOptions&, const clang::FrontendOptions&)’
 void InitializePreprocessor(Preprocessor &PP,
      ^
getLocalizedStringFromFile.cpp:188:19: error: ‘class clang::SourceManager’ has no member named ‘createMainFileID’
     sourceManager.createMainFileID(pFile);
                   ^
Makefile:471: recipe for target 'ios_genLocalization-getLocalizedStringFromFile.o' failed
make[2]: *** [ios_genLocalization-getLocalizedStringFromFile.o] Error 1
make[2]: Leaving directory '/home/sam/iostoolchain/iphonesdk-utils-2.0/genLocalization2'
Makefile:404: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/sam/iostoolchain/iphonesdk-utils-2.0'
Makefile:335: recipe for target 'all' failed
make: *** [all] Error 2



```

```
My configure output is:

sam@SamUbuntuLaptop:~/iostoolchain/iphonesdk-utils-2.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether UID '1000' is supported by ustar format... yes
checking whether GID '1000' is supported by ustar format... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
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
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
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
checking whether to build static libraries... no
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
checking for int16_t... yes
checking for int32_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint8_t... yes
checking for uid_t in sys/types.h... yes
checking for unistd.h... (cached) yes
checking for working chown... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for memset... yes
checking for strdup... yes
checking for strrchr... yes
checking for strtoul... yes
checking for crc32 in -lz... yes
checking for png_create_read_struct in -lpng... yes
checking for pow in -lm... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XML... yes
checking for llvm-config... true
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libhelper/Makefile
config.status: creating libplutil/Makefile
config.status: creating ldid/Makefile
config.status: creating clangwrapper/Makefile
config.status: creating plutil/Makefile
config.status: creating createProject/Makefile
config.status: creating createProject/templates/Makefile
config.status: creating genLocalization2/Makefile
config.status: creating pngcrush/Makefile
config.status: creating xcbuild/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
sam@SamUbuntuLaptop:~/iostoolchain/iphonesdk-utils-2.0$ 
```

Thanks

---

### Post by Vitor_Braga on 2015-10-12
I had this problem and found you while Googling for a solution. Here's what I did. Open the Makefile and remove the genLocalization2 project from the SUBDIRS vars. It should look like this:

SUBDIRS = libplutil libhelper ldid clangwrapper createProject plutil pngcrush xcbuild

This will remove the genLocalization2 project from the build - it seems to be breaking the build due to a change in the clang API. I think I'm going to fix it up (next weekend?), if I do, I'll post it in my github ("vbraga").

---

