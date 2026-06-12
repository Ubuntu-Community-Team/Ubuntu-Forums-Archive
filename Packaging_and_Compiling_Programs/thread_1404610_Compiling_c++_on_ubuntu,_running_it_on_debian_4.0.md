---
title: "Compiling c++ on ubuntu, running it on debian 4.0"
date: 2010-02-11
forum: Packaging and Compiling Programs
---

### Post by jmp971 on 2010-02-11
Hi,

I recently installed Ubuntu 9.10.
I compiled my current c++ program using Code::Blocks. My program is supposed to run on a Debian etch box (I cannot upgrade this machine). The program makes use of boost and mysql++.

As expected, the libraries linked with the program under ubuntu are more recent than the ones available on the Debian box. Here is the output when I try to run the application on Debian.

./app: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by ./FWServer)
./app: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./app)
./app: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by ./app)

All those libraries are installed on the Debian box but the version is not matched.

What would be my best approach to get the program to work on Debian?


Here is what I could think of up until now:

a) Compiling the sources on the target system
The setup of the project is relatively complex and I have no GUI on the Debian machine. It could still work out though, I assume. Maybe I could set up a virtual system inside ubuntu to run debian so I could run X?

b) Including the libraries with the application and setting LD_LIBRARY_PATH on application launch to only link to the specific libraries.
I assume that this would not work right away with the low level c libraries and their dependencies?

c) Statically linking the libraries
Probably this is not a good idea for these low-level libraries either?

d) Installing an older version of gcc on ubuntu alongside the current version

Finally, here is the objdump for the directly required libraries.

:~# objdump -x ./app | grep -i needed
  NEEDED      librt.so.1
  NEEDED      libmysqlclient_r.so.15
  NEEDED      libmysqlpp.so.3
  NEEDED      libstdc++.so.6
  NEEDED      libm.so.6
  NEEDED      libgcc_s.so.1
  NEEDED      libc.so.6
  NEEDED      libpthread.so.0

Any directions which road I should try would be greatly appreciated.

jmp

---

### Post by SevenMachines on 2010-02-12
hi there. I think there are a few good ways to do this kind of thing

1. set up a vm - there are a number of choices, generally i use virtualbox because its easy! but there are better choices of vm for doing builds i'm told :) Generally i use vm's if i need to actually test something on a running system rather than doing builds

2. set up a chroot - you can have any number of chroot for different distributions, versions, and set-ups where you can build your deb and test it out too. the only problem is the chroot's are not 'clean' environments, ie, you could have set up an environment on which your package builds but find it doesnt build in other environments

3. set up pbuilder - pbuilder is purely a build tool, if you use pbuilder-dist you can have any amount of 'clean' environments to build in, hardy, lucid, sid, whatever. To me this is the default environment build tool, building in this clean environment will test the build, and all your package dependencies too. 

In practice I build on pbuilder and test if i need to on a vm, although there are plenty of people who use clean environment vm's to build.

---

### Post by jmp971 on 2010-02-12
Thanks! I will have a look at pbuilder.

I also thought that I could use something like premake [http://premake.sourceforge.net/](http://premake.sourceforge.net/)

This way I could build my sources quickly on the platform where I would need it.
Did anybody try this?

---

