---
title: "Problems linking during cross-compilation with MinGW"
date: 2010-05-24
forum: Programming Talk
---

### Post by TheUnwiseman on 2010-05-24
Hello Ubuntu forum.  I'm very new at Allegro, but I managed to make my first game, Pong, in C using Allegro 4.2.2 on my Ubuntu 9.04 computer. You can find the project, along with source code, at [http://sourceforge.net/projects/mvppong](http://sourceforge.net/projects/mvppong).  But not all of my friends use Linux!  I wanted to make a Windows executable file for my friends with a Microsoft inclination.  So I found out about MinGW and did a sudo apt-get install for it.  I've tried compiling it, but I can't manage to get MinGW to link the Allegro library files properly.

I try this command:
```
i586-mingw32msvc-gcc -v `allegro-config --cflags --libs` pong.c
```

And this is what spits back out:
```
Using built-in specs.
Target: i586-mingw32msvc
Configured with: /build/buildd/mingw32-4.2.1.dfsg/build_dir/src/gcc-4.2.1-2-dfsg/configure -v --prefix=/usr --target=i586-mingw32msvc --enable-languages=c,c++ --enable-threads --enable-sjlj-exceptions --disable-multilib --enable-version-specific-runtime-libs
Thread model: win32
gcc version 4.2.1-sjlj (mingw32-2)
 /usr/libexec/gcc/i586-mingw32msvc/4.2.1-sjlj/cc1 -quiet -v -I/usr/include pong.c -quiet -dumpbase pong.c -mtune=pentium -auxbase pong -version -o /tmp/ccfFt3qh.s
ignoring nonexistent directory "/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/sys-include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include
 /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/include
 /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include
End of search list.
GNU C version 4.2.1-sjlj (mingw32-2) (i586-mingw32msvc)
	compiled by GNU C version 4.2.3 20071210 (prerelease) (Ubuntu 4.2.2-4ubuntu2).
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9f7339889766358351a8c487565f111d
 /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/as -o /tmp/cciRbuSz.o /tmp/ccfFt3qh.s
 /usr/libexec/gcc/i586-mingw32msvc/4.2.1-sjlj/collect2 -Bdynamic /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/lib/crt2.o /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/crtbegin.o -L/usr/lib -L/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj -L/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj -L/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/lib -Bsymbolic-functions -lalleg-4.2.2 /tmp/cciRbuSz.o -lmingw32 -lgcc -lmoldname -lmingwex -lmsvcrt -luser32 -lkernel32 -ladvapi32 -lshell32 -lmingw32 -lgcc -lmoldname -lmingwex -lmsvcrt /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/crtend.o
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/bin/ld: cannot find -lalleg-4.2.2
collect2: ld returned 1 exit status
```

Note that I only have files pong.c and pong.h in my program altogether.  I have no problem compiling this with gcc normally.  Any help figuring this out would be appreciated.

==================================================

I originally posted the above in the Absolute Beginners forum and they referred me over here.  What I've tried after that was downloading and unzipping allegro-mingw-4.2.2 from the Allegro website and manually moving over all the .dll, include, and lib files to /usr/i586-mingw32mvsc/ (in their appropriate folders).  I no longer need the --cflags argument for allegro-config, but I still get the error message that -lalleg-4.2.2 is not found.

---

### Post by dwhitney67 on 2010-05-24
EDIT:  Nevermind my previous question.

Where is liballeg-4.2.2.so (or possibly .a) located at?  You will need to specify the location using the -L option.

---

### Post by TheUnwiseman on 2010-05-24
liballeg.a and liballeg-4.2.2.so (a link to liballeg-4.2) are located in /usr/lib.  Note that `allegro-config --libs` echos:
```
-L/usr/lib -Wl,-Bsystem-functions -lalleg-4.2.2
```
So I am indeed specifying with -L.

---

### Post by dwhitney67 on 2010-05-24
Please verify that you do indeed have a liballeg-4.2.2.so file in /usr/lib.

EDIT: I'm tired... and I'm not reading good.  It appears you already have verified the library's existence.  Was this library compiled with MinGW?

---

### Post by TheUnwiseman on 2010-05-24
> **TheUnwiseman said:**
> liballeg.a and liballeg-4.2.2.so (a link to liballeg-4.2) are located in /usr/lib.

Indeed, I do have liballeg-4.2.2.so located in /usr/lib.

Also, I said it wrong originally, it is a link to the file liballeg.so.4.2, not liballeg-4.2

---

### Post by TheUnwiseman on 2010-05-24
> **dwhitney67 said:**
> Was this library compiled with MinGW?

No.  But I did download the mingw binaries from Allegro's website and copied them over into my /usr/i586.../ directory.

---

### Post by TheUnwiseman on 2010-05-25
Bumpitty bump bump.

---

### Post by TheUnwiseman on 2010-05-25
Bumping again, hoping for more help.

---

### Post by dodle on 2010-05-25
You will probably have to do something like this:
```
i586-mingw32msvc-gcc -v `/usr/i586-mingw32msvc/bin/allegro-config --cflags --libs` pong.c
```
Because MinGW's bin folder is not located in PATH.  Or you can create a symbolic link:
```
sudo ln -fs /usr/i586-mingw32msvc/bin/allegro-config /usr/bin/mingw-allegro-config
```
Then do:
```
i586-mingw32msvc-gcc -v `mingw-allegro-config --cflags --libs` pong.c
```
Hope that helps.

**Edit:** If you're still having problems, you can try adding the mingw's lib and include directories to the command:
```
i586-mingw32msvc-gcc -v `/usr/i586-mingw32msvc/bin/allegro-config --cflags --libs` -I/usr/i586-mingw32msvc/include -L/usr/i586-mingw32msvc/lib pong.c
```

---

### Post by TheUnwiseman on 2010-05-26
I don't have an allegro-config command in any mingw folder.

---

### Post by dodle on 2010-05-26
I was able to compile some of [ these tutorials](http://www.loomsoft.net/resources/alltut/alltut_index.htm) with this command:
```
i586-mingw32msvc-g++ lesson1.cpp -lalleg -o lesson1.exe
```

You need to link to allegro's libraries with [color=red]-lalleg[/color].  Note that the allegro dlls need to placed either in the executables directory or wine's system32 directory (or anywhere else in wine's PATH) for the app to run.  Also, don't expect these to run very well on wine.  Do you have a Windows machine to test the executables before you send them to your friends?

---

### Post by TheUnwiseman on 2010-05-26
I'm still not able to compile.  I'm not sure how you got an allegro-config in the /usr/i586-mingw32msvc/bin directory.

---

### Post by dodle on 2010-05-26
> **TheUnwiseman said:**
> I'm still not able to compile.  I'm not sure how you got an allegro-config in the /usr/i586-mingw32msvc/bin directory.

No, I was wrong about that.  There is no allegro-config for MinGW, you simply link to it with [color=red]-lalleg[/color] as long as allegro's libraries are in your compiler's path.  If you extracted the lib and include folders from the allegro archive into /usr/i586-mingw32msvc, you should be able to compile it.  That's all I did, then used the command:

On Ubuntu with MinGW:
```
i586-mingw32msvc-g++ lesson1.cpp -lalleg -o lesson1.exe
```

On Windows with MinGW:
```
g++ lesson1.cpp -lalleg -o lesson1.exe
```

---

### Post by TheUnwiseman on 2010-05-26
Ah, ok!  Just using -lalleg and not -lalleg-4.2.2 caused it to link properly.  Thank you very much!

---

