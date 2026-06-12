---
title: "newbie programming issue"
date: 2007-02-03
forum: Programming Talk
---

### Post by Robotuner on 2007-02-03
Hi, I'm trying to install a package to adjust my video monitor.  It is the 855resolution package from

[http://perso.orange.fr/apoirier/](http://perso.orange.fr/apoirier/)

When I try to make the package, I get the following, that make me believe something is not correct on my system:

robotuner@Dell700m:~/Desktop/855resolution$ make
cc -Wall -I`pwd` -DVERSION='"0.4"' -DPLUGINS='plugin1,plugin2,plugin3' -DREF_PLUGINS='&plugin1,&plugin2,&plugin3'    -c -o 855resolution.o 855resolution.c
855resolution.c:14:19: error: stdio.h: No such file or directory
855resolution.c:15:20: error: stdlib.h: No such file or directory
855resolution.c:16:20: error: string.h: No such file or directory
855resolution.c:17:20: error: unistd.h: No such file or directory
855resolution.c:18:20: error: sys/io.h: No such file or directory
855resolution.c: In function ‘find_modes’:
855resolution.c:31: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:31: error: (Each undeclared identifier is reported only once
855resolution.c:31: error: for each function it appears in.)
855resolution.c:42: warning: control reaches end of non-void function
855resolution.c: In function ‘find_resolution’:
855resolution.c:53: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:54: warning: control reaches end of non-void function
855resolution.c: In function ‘list_modes’:
855resolution.c:63: warning: implicit declaration of function ‘printf’
855resolution.c:63: warning: incompatible implicit declaration of built-in function ‘printf’
855resolution.c: In function ‘parse_args’:
855resolution.c:79: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:81: warning: implicit declaration of function ‘strlen’
855resolution.c:81: warning: incompatible implicit declaration of built-in function ‘strlen’
855resolution.c:99: warning: implicit declaration of function ‘atoi’
855resolution.c:101: warning: implicit declaration of function ‘fprintf’
855resolution.c:101: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:101: error: ‘stderr’ undeclared (first use in this function)
855resolution.c:122: warning: implicit declaration of function ‘strtol’
855resolution.c: In function ‘usage’:
855resolution.c:130: warning: incompatible implicit declaration of built-in function ‘printf’
855resolution.c: In function ‘main’:
855resolution.c:140: error: ‘NULL’ undeclared (first use in this function)
855resolution.c:147: warning: incompatible implicit declaration of built-in function ‘printf’
855resolution.c:160: warning: implicit declaration of function ‘iopl’
855resolution.c:161: warning: implicit declaration of function ‘perror’
855resolution.c:172: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:172: error: ‘stderr’ undeclared (first use in this function)
855resolution.c:181: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:190: warning: incompatible implicit declaration of built-in function ‘fprintf’
855resolution.c:195: warning: implicit declaration of function ‘putchar’
855resolution.c:206: warning: incompatible implicit declaration of built-in function ‘fprintf’

can someone tell me how to fix it?

Thanks

---

### Post by Wybiral on 2007-02-03
Have you used the command "sudo apt-get install build-essential" yet?

It will install a bunch of stuff you need to compile C/C++ (like libraries/headers)

---

### Post by Robotuner on 2007-02-03
thank you, that enabled me to compile the package!

---

### Post by lnostdal on 2007-02-03
hm .. you should always check the ubuntu repositories before you spend time compiling and installing general versions of stuff .. it will most likely save you from a lot of troubles

i tried:
```
sudo aptitude search 855
```

855resolution shows up, so you might want to install that:

```
sudo aptitude install 855resolution
```

(if you _know_ you need the version of the package compiled from source instead of the one in the ubuntu repositories it would be nice if you stated this .. :))

---

