---
title: "Linking binary data using mingw-w64 for 32 bit Windows executable"
date: 2015-07-30
forum: Packaging and Compiling Programs
---

### Post by Andrej_Balkonski on 2015-07-30
Post-edit: I see now that this post would better suit "Programming Talk". Feel free to move it there[COLOR=#4E4E4E].[/COLOR]

I'm trying to link custom binary data into a Windows 32 bit executable using MinGW-w64 tools (i686-w64-mingw32-*).


I'm doing this on a 64 bit Ubuntu (well, Kubuntu actually). Details:


$ lsb_release -a[INDENT]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty[/INDENT]


$ uname -a[INDENT]Linux themachine 3.13.0-57-generic #95-Ubuntu SMP Fri Jun 19 09:28:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux[/INDENT]


Package manager says that mingw-w64 package is of version 3.1.0-1,
I'm using[INDENT]i686-w64-mingw32-g++ (from package g++-mingw-w64-i686 of version 4.8.2-10ubuntu2+12)
    i686-w64-mingw32-ld, i686-w64-mingw32-objcopy, i686-w64-mingw32-objdump (from package binutils-mingw-w64-i686 of version 2.23.52.20130620-1ubuntu1+3build1)[/INDENT]


Now, I can do 64 bit version like this:


1. blink.cpp: program to dump contents of linked-in binary data.[INDENT]#include <iostream>


    using namespace std;


    extern char _binary_foo_bar_start[];
    extern char _binary_foo_bar_end[];
    //extern int  _binary_foo_bar_size;


    int main(void)
    {
        [/INDENT]
[INDENT=2]cout << "address of start: " << &_binary_foo_bar_start << endl;
        cout << "address of end  : " << &_binary_foo_bar_end   << endl;
        //cout << "size            : " << &_binary_foo_bar_size  << endl;


        for (char* p = _binary_foo_bar_start; p != _binary_foo_bar_end; ++p) {
            [/INDENT]
[INDENT=3]cout << *p;[/INDENT]
[INDENT=2]        }
        cout << endl;


        return 0;[/INDENT]
[INDENT]    }[/INDENT]


2. foo.bar: binary data file, in this case a simple text file, containing the following line:[INDENT]My own custom binary data.[/INDENT]


3. makefile:[INDENT]NAME = blink
    INSERT_NAME = foo.bar
    CC = x86_64-w64-mingw32-g++
    LD = x86_64-w64-mingw32-ld
    OBJDUMP = x86_64-w64-mingw32-objdump


    CFLAGS = -static


    #Supported emulations: elf_x86_64 elf32_x86_64 elf_i386 i386linux elf_l1om elf_k1om i386pep i386pe
    #LDFLAGS = -static -mi386pep
    LDFLAGS = -static


    all : link


    link : convert compile
        [/INDENT]
[INDENT=2]$(CC) $(CFLAGS) -o $(NAME).exe $(NAME).o $(INSERT_NAME).o[/INDENT]
[INDENT]

    compile :
        [/INDENT]
[INDENT=2]$(CC) $(CFLAGS) -o $(NAME).o -c $(NAME).cpp[/INDENT]
[INDENT]

    convert :
        [/INDENT]
[INDENT=2]$(LD) $(LDFLAGS) -r -b binary -o $(INSERT_NAME).o $(INSERT_NAME)
    #    file $(INSERT_NAME).o
    #    $(OBJDUMP) -stT $(INSERT_NAME).o[/INDENT]
[INDENT]

    clean :
        [/INDENT]
[INDENT=2]rm -f $(NAME).o
        rm -f $(NAME).exe
        rm -f $(INSERT_NAME).o
[/INDENT]

"make clean all" produces blink.exe which, when executed on 64 bit Windows dumps "My own custom binary data." (without the quotes, of course) as expected.


Now, producing 32 bit application should be no more than replacing the x86_64-* versions with i686-* ones and perhaps inserting a few -32 or -m32 flags, right? Wrong! I can't seem to make it work.


The 32 bit makefile I'm using is a mess, but I'm including it nevertheless, thinking that it might make some sense regarding what I'm trying to do:[INDENT]NAME = blink
    INSERT_NAME = foo.bar


    CC = i686-w64-mingw32-g++
    LD = i686-w64-mingw32-ld
    OBJCOPY = i686-w64-mingw32-objcopy
    OBJDUMP = i686-w64-mingw32-objdump


    #CFLAGS = -m32 -static -fvisibility-ms-compat -Wl,-m32
    CFLAGS = -m32 -static


    #LDFLAGS = -mi386pe
    LDFLAGS = -static -y _binary_foo_bar_start -y _binary_foo_bar_end -y _binary_foo_bar_size -r -b binary


    OBJCOPYFLAGS = -static -B i386 -I binary -O pei-i386


    all : link


    link : convert compile
    [/INDENT]
[INDENT=2]#    $(CC) -v $(CFLAGS) -o $(NAME).exe $(NAME).o $(INSERT_NAME).o
    #    $(CC) $(CFLAGS) -o $(NAME).exe $(NAME).o $(INSERT_NAME).o
        $(CC) -v $(CFLAGS) -o $(NAME).exe $(NAME).o $(INSERT_NAME).o[/INDENT]
[INDENT]

    compile :
    [/INDENT]
[INDENT=2]#    $(CC) -v $(CFLAGS) -o $(NAME).o -c $(NAME).cpp
        $(CC) $(CFLAGS) -o $(NAME).o -c $(NAME).cpp[/INDENT]
[INDENT]

    convert :
    [/INDENT]
[INDENT=2]#    $(LD) $(LDFLAGS) -r -b binary -o $(INSERT_NAME).o $(INSERT_NAME)
    #    $(LD) $(LDFLAGS) -o $(INSERT_NAME).o $(INSERT_NAME)


    #    file $(INSERT_NAME).o
    # foo.bar.o: Targa image data - Map 3 x
    # Targa image data?!? WTF?!?


    #    $(OBJDUMP) -stT $(INSERT_NAME).o


    #    $(OBJCOPY) -B i386 -I binary -O pei-i386 $(INSERT_NAME) $(INSERT_NAME).o
    # This objcopy produces .o file, for which file says: "foo.bar.o: PE Unknown PE signature 0x642e (Unknown subsystem 0x0) Intel 80386 (stripped to external PDB), for MS Windows"
    # But linking then says
    # i686-w64-mingw32-g++  -o blink.exe blink.o foo.bar.o
    # blink.o:blink.cpp: (.text+0x12): undefined reference to `_binary_foo_bar_start'
    # blink.o:blink.cpp: (.text+0x26): undefined reference to `_binary_foo_bar_end'
    # blink.o:blink.cpp: (.text+0x3a): undefined reference to `_binary_foo_bar_size'
    # blink.o:blink.cpp: (.text+0x4e): undefined reference to `_binary_foo_bar_start'
    # blink.o:blink.cpp: (.text+0x6f): undefined reference to `_binary_foo_bar_end'
    # collect2: error: ld returned 1 exit status
    # make: *** [link] Error 1
    #
    # Strangelly enough though, "i686-w64-mingw32-objdump -stT foo.bar.o" says:
    # foo.bar.o:     file format pei-i386
    #
    # i686-w64-mingw32-objdump: foo.bar.o: not a dynamic object
    # SYMBOL TABLE:
    # [  0](sec  1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x00000000 _binary_foo_bar_start
    # [  1](sec  1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x0000000d _binary_foo_bar_end
    # [  2](sec -1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x0000000d _binary_foo_bar_size
    #
    #
    # DYNAMIC SYMBOL TABLE:
    # no symbols
    #
    #
    # Contents of section .data:
    #  0000 42696e61 72792064 6174612e 0a        Binary data..
    # So, those symbols actually do exist! WTF?!?


    #    $(OBJCOPY) -v -B i386 -I binary -O pei-i386 $(INSERT_NAME) $(INSERT_NAME).o
    #    $(OBJCOPY) -static -B i386 -I binary -O pei-i386 $(INSERT_NAME) $(INSERT_NAME).o
        $(OBJCOPY) -v $(OBJCOPYFLAGS) $(INSERT_NAME) $(INSERT_NAME).o
    #    file $(INSERT_NAME).o
    # foo.bar.o: PE Unknown PE signature 0x642e (Unknown subsystem 0x0) Intel 80386 (stripped to external PDB), for MS Windows
    #    $(OBJDUMP) -stT $(INSERT_NAME).o
    # foo.bar.o:     file format pei-i386
    #
    # i686-w64-mingw32-objdump: foo.bar.o: not a dynamic object
    # DYNAMIC SYMBOL TABLE:
    # no symbols
    #
    #
    # $(OBJDUMP) -stT $(INSERT_NAME).o
    #
    # foo.bar.o:     file format pei-i386
    #
    # i686-w64-mingw32-objdump: foo.bar.o: not a dynamic object
    # SYMBOL TABLE:
    # [  0](sec  1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x00000000 _binary_foo_bar_start
    # [  1](sec  1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x0000001b _binary_foo_bar_end
    # [  2](sec -1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x0000001b _binary_foo_bar_size
    #
    #
    # DYNAMIC SYMBOL TABLE:
    # no symbols
    #
    #
    # Contents of section .data:
    #  0000 4d79206f 776e2063 7573746f 6d206269  My own custom bi
    #  0010 6e617279 20646174 612e0a             nary data..


    # So, in fact, those symbols ARE THERE! Why doesn't g++ find them then?!?[/INDENT]
[INDENT]

    clean :
        [/INDENT]
[INDENT=2]rm -f $(NAME).o
        rm -f $(NAME).exe
        rm -f $(INSERT_NAME).o[/INDENT]


At first I was trying to use i686-w64-mingw32-ld (analogous to 64 bit version x86_64-w64-mingw32-ld), but the file it produces is somewhat strange: file foo.bar.o says that it's a "Targa image data - Map 3 x"!?! As I couldn't find the right flags for i686-w64-mingw32-ld, I switched to i686-w64-mingw32-objcopy. In this case:


file foo.bar.o says[INDENT]PE Unknown PE signature 0x642e (Unknown subsystem 0x0) Intel 80386 (stripped to external PDB), for MS Windows[/INDENT]

and

i686-w64-mingw32-objdump -stT foo.bar.o says[INDENT]foo.bar.o:     file format pei-i386


i686-w64-mingw32-objdump: foo.bar.o: not a dynamic object
SYMBOL TABLE:
[  0](sec  1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x00000000 _binary_foo_bar_start
[  1](sec  1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x0000001b _binary_foo_bar_end
[  2](sec -1)(fl 0x00)(ty   0)(scl   2) (nx 0) 0x0000001b _binary_foo_bar_size




DYNAMIC SYMBOL TABLE:
no symbols




Contents of section .data:
 0000 4d79206f 776e2063 7573746f 6d206269  My own custom bi
 0010 6e617279 20646174 612e0a             nary data..


[/INDENT]
Note: the _binary_foo_bar_* symbols are clearly there.

But then the final i686-w64-mingw32-g++ -v -m32 -static -o blink.exe blink.o foo.bar.o says[INDENT]

Using built-in specs.
COLLECT_GCC=i686-w64-mingw32-g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-w64-mingw32/4.8/lto-wrapper
Target: i686-w64-mingw32
Configured with: ../../src/configure --build=x86_64-linux-gnu --prefix=/usr --includedir='/usr/include' --mandir='/usr/share/man' --infodir='/usr/share/info' --sysconfdir=/etc --localstatedir=/var --libexecdir='/usr/lib/gcc-mingw-w64' --disable-maintainer-mode --disable-dependency-tracking --prefix=/usr --enable-shared --enable-static --disable-multilib --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --libdir=/usr/lib --enable-libstdcxx-time=yes --with-tune=generic --enable-version-specific-runtime-libs --enable-threads=posix --enable-fully-dynamic-string --enable-sjlj-exceptions --enable-libgomp --enable-languages=c,c++,fortran,objc,obj-c++ --enable-lto --with-plugin-ld --target=i686-w64-mingw32 --with-gxx-include-dir=/usr/include/c++/4.8 --with-as=/usr/bin/i686-w64-mingw32-as --with-ld=/usr/bin/i686-w64-mingw32-ld
Thread model: posix
gcc version 4.8.2 (GCC)
COMPILER_PATH=/usr/lib/gcc/i686-w64-mingw32/4.8/:/usr/lib/gcc/i686-w64-mingw32/4.8/:/usr/lib/gcc/i686-w64-mingw32/:/usr/lib/gcc/i686-w64-mingw32/4.8/:/usr/lib/gcc/i686-w64-mingw32/
LIBRARY_PATH=/usr/lib/gcc/i686-w64-mingw32/4.8/:/usr/lib/gcc/i686-w64-mingw32/4.8/../../../../i686-w64-mingw32/lib/../lib/:/usr/lib/gcc/i686-w64-mingw32/4.8/../../../../i686-w64-mingw32/lib/
COLLECT_GCC_OPTIONS='-v' '-m32' '-static' '-o' 'blink.exe' '-mtune=generic' '-march=pentiumpro'
 /usr/lib/gcc/i686-w64-mingw32/4.8/collect2 -m i386pe -Bstatic -o blink.exe /usr/lib/gcc/i686-w64-mingw32/4.8/../../../../i686-w64-mingw32/lib/../lib/crt2.o /usr/lib/gcc/i686-w64-mingw32/4.8/crtbegin.o -L/usr/lib/gcc/i686-w64-mingw32/4.8 -L/usr/lib/gcc/i686-w64-mingw32/4.8/../../../../i686-w64-mingw32/lib/../lib -L/usr/lib/gcc/i686-w64-mingw32/4.8/../../../../i686-w64-mingw32/lib blink.o foo.bar.o -lstdc++ -lmingw32 -lgcc -lgcc_eh -lmoldname -lmingwex -lmsvcrt -lpthread -ladvapi32 -lshell32 -luser32 -lkernel32 -lmingw32 -lgcc -lgcc_eh -lmoldname -lmingwex -lmsvcrt /usr/lib/gcc/i686-w64-mingw32/4.8/crtend.o
blink.o:blink.cpp: (.text+0x2d): undefined reference to `_binary_foo_bar_start'
blink.o:blink.cpp: (.text+0x63): undefined reference to `_binary_foo_bar_end'
blink.o:blink.cpp: (.text+0x85): undefined reference to `_binary_foo_bar_start'
blink.o:blink.cpp: (.text+0xab): undefined reference to `_binary_foo_bar_end'
/usr/bin/i686-w64-mingw32-ld: blink.o: bad reloc address 0x0 in section `.ctors'
collect2: error: ld returned 1 exit status
make: *** [link] Error 1[/INDENT]


The two "points of interest" I'm looking at are the block where it says that there are undefined references to the _binary_foo_bar_* symbols, which is conflicting with what objdump said (explained above).


The second, and perhaps more important, is "Configured with: ../../src/configure --build=x86_64-linux-gnu". But, as "--target=i686-w64-mingw32" and "--with-ld=/usr/bin/i686-w64-mingw32-ld", I don't think this has anything to do with the target file, but rather with the host machine.


If anybody could shed some light on all this, I'd be most grateful.

---

