---
title: "Building a program executable that will run on windows"
date: 2013-12-13
forum: Programming Talk
---

### Post by ccutlip on 2013-12-13
Hi, I made a game with SDL in ubuntu, it runs fine and everything i have a makefile with a run executable. Is there anyway i can make an executable so that i can install the game on my windows OS and run it. Porting it manually to windows would be painful, and the c++ code will run on windows just as it does ubuntu, so i would think there would be a way to make an exe that would run on windows?

Thanks.

---

### Post by oldos2er on 2013-12-13
Moved to Programming Talk.

---

### Post by ju2wheels on 2013-12-14
Its called cross compiling, you will need to setup a cross compiling environment (essentially mingw and sdl libs).

Something like what described here will probably close to what you want: [http://odamex.net/wiki/Cross_compiling_for_Windows_using_MinGW](http://odamex.net/wiki/Cross_compiling_for_Windows_using_MinGW)

---

### Post by ccutlip on 2013-12-15
Ah that looks like it would work, thanks ill try that. I tried bringing it over to windows manually, almost was able to do it but couldnt get expat libraries in my code blocks compiler, ill try this.

---

### Post by ccutlip on 2013-12-19
How do i run this command from your link?

mv SDL-1.2.13/bin/sdl-config SDL-1.2.13/bin/sdl-config.bak
cat SDL-1.2.13/bin/sdl-config.bak | \
    sed 's/\/Users\/hercules\/tmp\/SDL-1.2.13/\/usr\/i586-mingw32msvc/' \
    > SDL-1.2.13/bin/sdl-config
chmod +x SDL-1.2.13/bin/sdl-config

Copy paste doesnt work, and i have no idea what command specifically does as to break it down line by line to input it so it will work?

Its saying the sdl-config.bak isnt a directory, and its saying for sed that unkown option to `s', i never typed the ` char.

---

