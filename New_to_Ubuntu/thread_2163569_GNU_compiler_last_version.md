---
title: "GNU compiler last version"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by mohsen12 on 2013-07-18
Hello everyone
I installed the GNU compiler from software center and   version of that is  4.6.3 (g++ --version) but I want use  last version  How I can  update that to (4.8.1)
(The 4 .6.3 does not support  last ISO of C++11)
Tank you:p
[TABLE="class: wikitable"]
[TR]
[TD]ISO/IEC 14882:2011[SUP][[21]]("https://en.wikipedia.org/wiki/C%2B%2B#cite_note-21")[/SUP][/TD]
[TD][C++11]("https://en.wikipedia.org/wiki/C%2B%2B11")[/TD]
[/TR]
[/TABLE]

---

### Post by mc4man on 2013-07-18
You can't update gcc & likely wouldn't want to (more on that below

However you can install newer versions of gcc & use it for compiling, how depends on what you are doing.
Later versions of gcc are available here for precise thru raring
[https://launchpad.net/~ubuntu-toolchain-r/+archive/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/test)

So add the ppa, update your sources & install as you see fit, synaptic is good choice. From cli this would take care of - 
```
sudo apt-get install gcc-4.8 g++-4.8 cpp-4.8
```

As far as system defaults - 
Generally better to leave as is & use gcc-4.8, (or any alt. gcc version),  specifically  when desired.  The system gcc defaults are set from /usr/bin/gcc g++ cpp which if you take a look at are  just links to the system's default gcc binaries. (4.6 in your case.

ex. on 12.04.2+ - the first 2 are the same because gcc links to gcc-4.6
> doug@doug-XPS-M1330:~$ gcc --version
gcc-4.6.real (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

doug@doug-XPS-M1330:~$ gcc-4.6 --version
gcc-4.6.real (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

doug@doug-XPS-M1330:~$ gcc-4.8 --version
gcc-4.8 (Ubuntu 4.8.1-2ubuntu1~12.04) 4.8.1
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

---

