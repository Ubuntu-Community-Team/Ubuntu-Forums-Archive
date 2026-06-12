---
title: "nagging stdio.h problems"
date: 2010-07-19
forum: Programming Talk
---

### Post by dbmolester on 2010-07-19
Hi experts,

I have your standard, posted all over the web, "stdio.h file not found" problem when tying to compile from source using gcc.  

The standard solution offered is to install build-essential and libc6-dev, which I do have:

```

aptitude search libc6-dev build-essential
i A build-essential                                                  - informational list of build-essential packages                            
i A libc6-dev                                                        - GNU C Library: Development Libraries and Header Files                     
i A libc6-dev-i386                                                   - GNU C Library: 32bit development libraries for AMD64     

```I am still getting the same file not found problem.

I can find the stdio.h file in ```
/usr/include/c++/4.2/tr1/stdio.h
```but gcc doesn't look in tr1/

here's an example:
```

cat test1.cpp
#include <stdio.h>
g++ -c -isystem /usr/include test1.cpp 
test1.cpp:1:19: error: stdio.h: No such file or directory

```now if I changed my program to use <tr1/stdio.h>:
```

cat test2.cpp
#include <tr1/stdio.h>
g++ -c -isystem /usr/include test2.cpp 
In file included from /usr/include/c++/4.2/x86_64-linux-gnu/bits/c++config.h:41,
                 from /usr/include/c++/4.2/tr1/cstdio:37,
                 from /usr/include/c++/4.2/tr1/stdio.h:37,
                 from test2.cpp:1:
/usr/include/c++/4.2/x86_64-linux-gnu/bits/os_defines.h:44:22: error: features.h: No such file or directory
In file included from /usr/include/c++/4.2/tr1/cstdio:38,
                 from /usr/include/c++/4.2/tr1/stdio.h:37,
                 from test2.cpp:1:
/usr/include/c++/4.2/cstdio:53:19: error: stdio.h: No such file or directory
In file included from /usr/include/c++/4.2/tr1/cstdio:38,
                 from /usr/include/c++/4.2/tr1/stdio.h:37,
                 from test2.cpp:1:

...

```so it finds stdio.h at first, but when other header files refer to stdio again they don't include the tr1/, and it is missed.

by the way, features.h can be found at 
```

/usr/src/linux-headers-2.6.24-28/include/xen/features.h
/usr/src/linux-headers-2.6.24-28/include/xen/interface/features.h

```which is not used as well.

This is very frustrating, and I'm not sure how to solve this problem.  

I'm running Ubuntu Hardy 8.04 LTS on x86_64

---

### Post by Bachstelze on 2010-07-19
Package libc6-dev has file /usr/include/stdio.h. If you have the package installed but the file is not present, it means it was removed somehow. Try reinstalling the package:

```
sudo apt-get install --reinstall libc6-dev
```

---

### Post by trent.josephsen on 2010-07-19
If you're using C++, you should #include <cstdio>, not <stdio.h>.  If you're using C, you should use gcc and not g++.

---

### Post by dbmolester on 2010-07-19
> **Bachstelze said:**
> Package libc6-dev has file /usr/include/stdio.h. If you have the package installed but the file is not present, it means it was removed somehow. Try reinstalling the package:

```
sudo apt-get install --reinstall libc6-dev
```

Hi Bachstelze,

Thank you very much for your help.  The reinstall fixed my problem -- the stdio.h I now get in ```
/usr/include
``` is very much different from the one I've been looking at in ```
/usr/include/c++/4.2/tr1/stdio.h
```.

In any case, your solution fixed my problem.  Thank you.

---

### Post by johnl on 2010-07-19
Files in the **tr1** directory are part of the upcoming (proposed) C++ standard.  You shouldn't be using these files unless you know what you're doing.  You would need to enable this functionality with the "--std=c++0x" argument.

---

