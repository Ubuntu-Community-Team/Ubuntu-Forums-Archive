---
title: "Xerces Ubuntu Powerpc KDevelop Build Help"
date: 2009-11-12
forum: Programming Talk
---

### Post by jcraig on 2009-11-12
[FONT=Times New Roman][SIZE=2]I am trying to build xerces 3.0.1 with a power pc build in the KDevelop enviroment and I have been unsuccessful so far.  I am a nubbie to linux.  When I try to link to the xerces-c-3.0.1.so, I get the following error:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]/opt/eldk41/usr/bin/../lib/gcc/powerpc-linux/4.0.0/../../../../powerpc-linux/bin/ld: skipping incompatible ../../../xerces-c-3.0.1/lib/A5/libxerces-c-3.0.so when searching for -lxerces-c-3.0[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=2]/opt/eldk41/usr/bin/../lib/gcc/powerpc-linux/4.0.0/../../../../powerpc-linux/bin/ld: cannot find -lxerces-c-3.0
[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]I believe that it is trying to find the library, but it is configured incorrectly.  The build is configured at 32bit, which is what I need. When I build with ./configure only, it builds fine, but I receive the error above.  When I try to build xerces with the following parameters ./configure CFLAGS="-arch ppc" CXXFLAGS="-arch ppc" I get this error:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]configure: error: C++ compiler cannot create executables
See `config.log' for more details.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]
I have attached the config log if you would like to look at it.  I am stuck right now so any suggestions or ideas would be helpful.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=2]Thanks[/SIZE][/FONT]

---

### Post by Zugzwang on 2009-11-13
> **jcraig said:**
> When I build with ./configure only, it builds fine, but I receive the error above.  
What do you mean by that? Taking into accound that this "cannot find ..."-error is a building (i.e., linking) error, I'm not sure what you mean.

You say that "the build is configured at 32-bit". So you use the "-m32" switch? I'm not sure, but this shouldn't be necessary for PowerPC builds. It might even tell the compiler to compile for the Intel x86 platform.

Also, you wrote that you are trying to build xerces-3.0.1, but you are linking against it at the same time. You might want to consider re-writing your question. And finally: What does kdevelop have to do with the whole stuff? Always try to build from the terminal until the building process worked for the first time. Then you can switch to the IDE.

---

### Post by jcraig on 2009-11-16
I am building xerces on a Intel x86 machine targeting a hardware powerpc platform.  I am including xerces in my application.  I need to configure the shared library file for the powerpc.  I am using KDevelop to build my application and I am linking the xerces shared library in my makefile.

---

### Post by Zugzwang on 2009-11-17
> **jcraig said:**
> I am building xerces on a Intel x86 machine targeting a hardware powerpc platform.  I am including xerces in my application.  I need to configure the shared library file for the powerpc.  I am using KDevelop to build my application and I am linking the xerces shared library in my makefile.

Hmm, this is tricky. I don't know the official way to do that, but I would suggest extracting the library files from the powerpc package for xerxes into some directory and tell the linker to look into that directory. However, I must admit that I have no clue how to do that in conjunction with the autotools.

---

### Post by jcraig on 2009-11-17
I found that I could download the debian package with a powerpc build from this website [https://launchpad.net/ubuntu/+source/xerces-c/3.0.1-1/+build/978213](https://launchpad.net/ubuntu/+source/xerces-c/3.0.1-1/+build/978213).  I could invoke a build by using the command dpkg-cross -a powerpc -A -b <package name>.deb.  Each time it would say it couldn't install the package because of a dependency, so I would find the dependency, which was based on another dependency.  I ran into the problem, I can't install libgcc1 because it has a dependency of libc6.  I can't install libc6 because it has a dependency of libgcc1.  I believe that this is my last dependency to install to get the entire package to work, but I haven't found a way around the dependency issue.

---

### Post by jcraig on 2009-11-17
This is the website https:// launchpad.net/ubuntu/+source/xerces-c/3.0.1-1/+build/978213

---

