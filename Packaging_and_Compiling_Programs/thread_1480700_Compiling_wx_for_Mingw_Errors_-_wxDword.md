---
title: "Compiling wx for Mingw Errors - wxDword"
date: 2010-05-11
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-05-11
I currently have wxWidgets 2.8.10 compiled and installed for mingw, which works wonderfully.  But I recently wanted to recompile it with some different options:
```
$ ./configure --enable-unicode --with-msw --disable-shared --disable-threads --prefix=/usr/i586-mingw32msvc
```

Everything goes well with the configure, but when I try to do make:
```
/home/user/Desktop/wxWidgets-2.8.11/bk-deps gcc -c -o wxregex_regcomp.o -D__WXMSW__   -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -I/home/user/Desktop/wxWidgets-2.8.11/lib/wx/include/msw-unicode-release-static-2.8 -I./include -Wall -Wundef -O2 -fno-strict-aliasing ./src/regex/regcomp.c
In file included from ./include/wx/platform.h:293,
                 from ./include/wx/defs.h:21,
                 from ./src/regex/regcustom.h:39,
                 from ./src/regex/regguts.h:38,
                 from ./src/regex/regcomp.c:33:
./include/wx/chkconf.h:1817:9: error: #error "wxClipboard requires wxDataObject"
In file included from ./src/regex/regcustom.h:39,
                 from ./src/regex/regguts.h:38,
                 from ./src/regex/regcomp.c:33:
./include/wx/defs.h:771:10: error: #error "Unsupported Windows version"
In file included from ./src/regex/regcustom.h:39,
                 from ./src/regex/regguts.h:38,
                 from ./src/regex/regcomp.c:33:
./include/wx/defs.h:824: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;wxDword&#8217;
make: *** [wxregex_regcomp.o] Error 1
```

I can't figure it out, I have tried to compile both versions 2.8.11 and 2.8.10.  The last time that I compiled and installed it was a probably a year ago.  I don't know why it isn't working now.  It says "unsupported windows version", is that because I am using --with-msw?

---

### Post by dodle on 2010-05-11
I realized what I was doing wrong, I wasn't cross-compiling.  I needed to add the following two options to the configure command:
```
--host=i586-mingw32msvc --build=i686-linux
```

---

