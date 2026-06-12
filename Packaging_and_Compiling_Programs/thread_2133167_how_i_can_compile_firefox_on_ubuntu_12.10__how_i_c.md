---
title: "how i can compile firefox on ubuntu 12.10 ? how i can set optimization for i7"
date: 2013-04-07
forum: Packaging and Compiling Programs
---

### Post by xfcewithmutter on 2013-04-07
i doed it before. i was build optimized firefox builds. i used --march=native option for gcc. i used a lot of .mozconfig options. i digged more. but now i cant remember anything.

now im thinking get ubuntu source of firefox 20 ( "firefox_20.0+build1-0ubuntu1.debian.tar.gz" and  "firefox_20.0+build1.orig.tar.bz2" files )  and not modifyin standart compiling mozconfig options. im only think modify gcc cpu options. march=native -o3 like...

**i need basicaly default ubuntu compiling method for ubuntu source. **:confused:

im not need basicaly cpu optimization tips.  i can modify something.

---

### Post by oldos2er on 2013-04-07
Compiling software isn't an "absolute beginner" task, so I've moved your post to a more appropriate forum, Packaging & Compiling Software.

---

### Post by schragge on 2013-04-07
Just recompiling a package is easy. I'm not sure about changing compiler options. Hopefully, it will honor the environment settings, so try something like
```
CFLAGS='-O3' apt-get -b source firefox
sudo dpkg -i firefox*.deb

``` Otherwise, you will need to modify [debian/rules]("http://www.debian.org/doc/manuals/maint-guide/dreq.en.html#rules").

---

### Post by xfcewithmutter on 2013-04-07
im on dpkg-flags dpkg-* area.

im get firefox build dep. im get firefox source from ubuntu. 

DEB_CFLAGS_SET="-g -O3 -march=core-avx-i -mtune=core-avx-i -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security" DEB_CXXFLAGS_SET="-g -O3 -march=core-avx-i -mtune=core-avx-i -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security" DEB_FFLAGS_SET="-g -O3 -march=core-avx-i -mtune=core-avx-i" dpkg-buildpackage -uc -us -j8

i started compiling but firefox very large. my 3 gb free virtualbox space not enough for this. slow and realy large area compiling.  im not know is it %100 true method.

---

### Post by xfcewithmutter on 2013-04-07
compiler options not activated. i can trace it from terminal screen. 

i can use mozilla default compile method. [https://developer.mozilla.org/en-US/docs/Developer_Guide/Build_Instructions](https://developer.mozilla.org/en-US/docs/Developer_Guide/Build_Instructions) 
i used them before... i can easily set .mozconfig file... i can easily add cflag options like "-O3 match=native mtune=native  or  march=corei7-avx" .....

bu im thinking i can do it in debian/ubuntu way for better compatibility.

---

### Post by xfcewithmutter on 2013-04-07
[TABLE]
[TR]
[TD]gcc[/TD]
[TD]gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1)[/TD]
[TD] -pedantic -Wall -Wpointer-arith -Wdeclaration-after-statement  -Werror=return-type -Wtype-limits -Wempty-body -Wno-unused  -Wno-overlength-strings -Wcast-align -Wno-long-long -fno-strict-aliasing  -ffunction-sections -fdata-sections -pthread -pipe  -DNDEBUG -DTRIMMED  -g -Os -freorder-blocks  -fomit-frame-pointer[/TD]
[/TR]
[TR]
[TD] c++[/TD]
[TD]gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1)[/TD]
[TD] -pedantic -Wall -Wpointer-arith -Woverloaded-virtual  -Werror=return-type -Wtype-limits -Wempty-body -Wno-ctor-dtor-privacy  -Wno-overlength-strings -Wno-invalid-offsetof -Wno-variadic-macros  -Wcast-align -Wno-long-long -fno-exceptions -fno-strict-aliasing  -fno-rtti -ffunction-sections -fdata-sections -fno-exceptions  -std=gnu++0x -pthread -pipe  -DNDEBUG -DTRIMMED -g -Os -freorder-blocks   -fomit-frame-pointer[/TD]
[/TR]
[/TABLE]
 **Configure arguments**

 --host=i686-linux-gnu --prefix=/usr --libexecdir=/usr/lib/firefox  --with-l10n-base=/build/buildd/firefox-20.0+build1/./l10n  --srcdir=/build/buildd/firefox-20.0+build1/. --disable-install-strip  --disable-updater --enable-application=browser  --enable-startup-notification --with-distribution-id=com.ubuntu  --enable-optimize --enable-tests --enable-crashreporter  --with-branding=browser/branding/official --disable-gnomevfs  --enable-gio --enable-update-channel=release --disable-debug  --disable-elf-hack --enable-extensions=default,globalmenu

they are firefox builtf options from "about:buildconfig" 

i can add them to .mozconfig file and can add optimize build option and  use "make" "make install" commands but why i cant use debian ubuntu way?

---

### Post by malteworld on 2013-06-27
There are three main reasons for the firefor build to be long:
[LIST]
[*]It has a huge code base. 
[*]For gcc 4.7, profiling is enabled by default. In this case, everything needs to be compiled twice and the linker stage takes huge amounts of memory (around 6 GiB for me) and may therefore cause heavy swapping. 
[*]Virtual machines aren't exactly the fastest execution environment. Especially memory allocation can be tricky because of the previous point. Just build on the host machine, possibly in a chroot environment. There are build tools to automate the creation of such environments and this is what launchpad does. 
[/LIST]

---

