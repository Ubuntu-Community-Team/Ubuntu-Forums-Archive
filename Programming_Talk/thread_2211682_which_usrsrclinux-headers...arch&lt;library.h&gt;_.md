---
title: "which /usr/src/linux-headers.../arch/&lt;?library.h&gt; should i use, CodeBlocks"
date: 2014-03-17
forum: Programming Talk
---

### Post by axoloti on 2014-03-17
I am a new GCC user, using Code Blocks, on Lubuntu, Dell P4 pentium, and I am an experienced C programmer.
I am starting a new C project from existing code and need advice on the path to the correct library for my program given my Lubuntu installation.
My Lubuntu installation includes include libraries for many different hardware and OS instillation dates. I am guessing i need the x86 (32-bit processor) directory resulting in the following total path:  "/usr/src/linux-headers-3.11.0-18/arch/x86" but there is also the "/usr/src/linux-headers-3.11.0-18-generic/arch/x86" path as well. To add confusion, a search on a specific library returns the same library in many unrelated locations. 

So, please advise:
1) which library path should i use?
2) is there a PATH variable which automatically defines the correct path for my installation?
3) does Code Blocks have the ability to automatically select the correct library path?

I know that i can use the ./configure script on downloaded source code, then command line compile, but my intent is to understand and rebuild the code using an IDE. I have done a Ubuntu forum search, but am not experienced enough to answer my question. I intend to upgrade my code to the latest system libraries, and the downloaded configure script may specify paths to old or modified libraries.

Thanks, axoloti

---

### Post by steeldriver on 2014-03-17
Hello and welcome to the forums

What kind of project are you working on? afaik unless you are building a kernel / kernel modules you should not need any of the /usr/src/linux-headers-xxx files, just the headers and libraries in the regular 'standard' paths (/usr/include, /usr/lib and so on). These should be found by the gcc/g++ compilers using their default built-in search paths regardless of the IDE you are using.

If you *are* building kernel components then you may be able to use the uname utility to expand to the *current *kernel header path e.g.

```
$ ls -d /usr/src/linux-headers-`uname -r`
/usr/src/linux-headers-3.2.0-57-generic-pae

```

---

### Post by axoloti on 2014-03-17
I am interested in embedded networking systems. I have extensive SW on eZ80 using Zilog Acclaim IDE. I have decided to migrate my project to Linux using my code which operates in user space independent of the functionality of kernal mode networking. In other words, two networking systems, one in the ubuntu system unmodified, the other in user space with my code. This involves adding a intel pro 1000 networking card to my system operating as an application, totally independently from the kernal code.

FYI, reference "http://sourceforge.net/projects/e1000/"   contains the base NIC code, I have my own networking stack.

The Code Blocks GCC IDE preprocess failed to find "#include <linux/delay.h>", I searched from root, the entire drive and found lots of matching entries, but the latest one with an actual file size was aparently stored from a recient Ubuntu update in the above cited file path, dated 2/18/2014. I am not sure this one is the best choice, but it could be a start. So, again, the question is what are the "best practices" in Linux software development when so many identically named include files of different sizes and dates exist. Also don't forget links to files. How does one insure conformity. How does one benefit from Ubuntu future distributions and updates which may be best served by kernal module code updates. Also this may allow automatic instalation on other platforms since the library routines used (on re-compile) would follow the instalation. Fundimentally, I do not intend to modify kernel code as required by this forum.

Thanks for the fast reply
axoloti

---

### Post by xb12x2 on 2014-03-17
try running  

$ gcc -v -E -

On my computer the last few lines of the output are:

#include <...> search starts here:
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include

---

### Post by axoloti on 2014-03-17
On my system i get the following, but no header for "delay.h". Of course i can build my own or hunt it down elsewhere.

<code>
Using built-in specs.
COLLECT_GCC=gcc
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.8.1-10ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-i386/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-i386 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-i386 --with-arch-directory=i386 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-targets=all --enable-multiarch --disable-werror --with-arch-32=i686 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu9) 
COLLECT_GCC_OPTIONS='-v' '-E' '-mtune=generic' '-march=i686'
 /usr/lib/gcc/i686-linux-gnu/4.8/cc1 -E -quiet -v -imultiarch i386-linux-gnu - -mtune=generic -march=i686 -fstack-protector -Wformat -Wformat-security
ignoring nonexistent directory "/usr/local/include/i386-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i686-linux-gnu/4.8/../../../../i686-linux-gnu/include"
#include "..." search starts here:
#include ... search starts here:
 /usr/lib/gcc/i686-linux-gnu/4.8/include[COLOR=#ff0000] (linkable .o ilbraries)[/COLOR]
 /usr/local/include[COLOR=#ff0000] (no files)[/COLOR]
 /usr/lib/gcc/i686-linux-gnu/4.8/include-fixed [COLOR=#ff0000](limits.h, README, syslimits.h)[/COLOR]
 /usr/include/i386-linux-gnu[COLOR=#ff0000] (here are the header files, but no "delay.h" as defined in the downloaded code)[/COLOR]
 /usr/include [COLOR=#ff0000](again, more header files, but no delay.h[/COLOR]
End of search list.
</code>

Note that the file "header.h" is only an example. The actual question is how does one go about selecting paths for different headers given that identical header file names occure in multiple file locations with different sizes and time stamps.

---

### Post by axoloti on 2014-03-17
It looks like i also need an example of using <code>

---

### Post by axoloti on 2014-03-18
All of the above comments were very useful, (thanks) I also found a very good description of the UNIX Filesystem Hierarchy Standard at URL [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/). This specification fully answers my post.

---

