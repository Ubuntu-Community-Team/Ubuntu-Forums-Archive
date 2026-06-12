---
title: "Cross-Compiling from 64-bit to 32-bit with SDL"
date: 2006-08-22
forum: Programming Talk
---

### Post by Randomskk on 2006-08-22
Hey all.
I'm tying to setup my 64bit Breezy box to allow me to compile for both 64 and 32bit Linux builds, and windows, using SDL.
I've managed to get compiling for windows working fine with mingw, and compiling for 64bit linux also works, but I'm stuck getting SDL and 32bit to work.

I can do "g++ -m32 <code>.cpp" and it works fine, presumably making a 32-bit executable (I can run both this and a normal one on my 64bit install, but I can also run both on a 32bit install, so I guess the programs are not complex enough for 32/64bit to have a difference).

However, doing "g++ -m32 -lSDL <code using SDL>.cpp" doesn't work, throwing up errors about skipping incompatible SDL libs and then not finding SDL.
The same app, by the way, compiles fine for windows and linux.

I'm guessing I need to get the 32bit SDL libs, and somehow tell the compiler to use them, but I'm not sure of 1) how to get the libs (the SDL site only supplies a .rpm and a deb package, and I doubt either would install on a 64bit system, and if they did they'd probably overwrite my current install) and 2) how to tell it to use the libs.

So, in short:
1) How can I get a set of 32bit SDL libs?
2) How can I tell g++ to use these to make a 32bit program?


Thanks for any help!

---

### Post by Lee_is_alive on 2008-06-29
Hi,

Did you find a solution? I'm about to install Wolfenstein - Enemy Territory, but for this I will need to have the latest 32bit SDL libraries. (running on AMD 64).. And just as you I'm not feeling to confident in just installing these libraries.

thanks in advance for you reply ;-)

Cheers,

Lee

---

### Post by newton64 on 2010-02-21
Well, it's probably rather late for a reply, but in case someone comes across this eventually...

I had the same problem as Randomskk. Another site suggested downloading the "ia32-libs" package, but that this still didn't work. That's because the 32-bit SDL libraries use a slightly different name.

When compiling normally with the 64-bit libraries, you use:
-lSDL

When compiling for 32-bit architectures (using -m32), you should use:
-lSDL-1.2

...and so on for the other SDL libraries (_image, _mixer, _ttf, &c). Obviously, your mileage may vary, and in another four years the advice may be moot, but just be sure to check the exact names of your 32-bit libraries, within /usr/lib32.

```
ls -l /usr/lib32/libSDL*
```

---

### Post by jdb2 on 2010-11-13
> **newton64 said:**
> Well, it's probably rather late for a reply, but in case someone comes across this eventually...

I had the same problem as Randomskk. Another site suggested downloading the "ia32-libs" package, but that this still didn't work. That's because the 32-bit SDL libraries use a slightly different name.

When compiling normally with the 64-bit libraries, you use:
-lSDL

When compiling for 32-bit architectures (using -m32), you should use:
-lSDL-1.2

...and so on for the other SDL libraries (_image, _mixer, _ttf, &c). Obviously, your mileage may vary, and in another four years the advice may be moot, but just be sure to check the exact names of your 32-bit libraries, within /usr/lib32.

```
ls -l /usr/lib32/libSDL*
```

Actually, this is not quite true. If you use gcc/g++ with the --sysroot= option you can change the default library directories that ld searches when it gets a "-l" argument.

First, you need to create a new directory, in your home directory most likely, say sysroots, then create a sub-directory usr and within that  create symlinks include and lib, where include points to /usr/include and lib points to /usr/lib32 respectfully. 

Then you would use gcc/g++ -m32 --sysroot=~/sysroots .

After that there is no need to change library include names. With these options you can use -lSDL or any other "-l" option without any modification.


jdb2

---

### Post by mrobert on 2011-05-23
I can confirm that Newton64's solution still works on Eclipse Galileo / Ubuntu 11.04 

However, I still get an issue:

> /usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make: *** [HackerEvolutionDuality] Error 1

---

### Post by jdb2 on 2011-05-23
> **mrobert said:**
> I can confirm that Newton64's solution still works on Eclipse Galileo / Ubuntu 11.04 

However, I still get an issue:

Are you using GNU GCC/G++ multilib?

jdb2

---

### Post by mrobert on 2011-05-23
> 
sudo apt-get install g++-multilib


solved my issue.

---

