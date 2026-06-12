---
title: "compiling i386 binary on x86_64"
date: 2012-01-16
forum: Packaging and Compiling Programs
---

### Post by neil_1 on 2012-01-16
i've been trying to compile a binary on my amd64 ubuntu
[http://www.goreclan.net/public/ioUrTded.zip](http://www.goreclan.net/public/ioUrTded.zip)

i did
```
[FONT=monospace]
[/FONT]cd /home/neil/ioUrTded/ 
make ARCH=i386

```

but i get this error

```

neil@lappy:~/ioUrTded$ sudo make ARCH=i386
make[1]: Entering directory `/home/neil/ioUrTded'

Building ioquake3 in build/release-linux-i386:
  PLATFORM: linux
  ARCH: i386
  COMPILE_PLATFORM: linux
  COMPILE_ARCH: x86_64
  CC: cc

  CFLAGS:
    -MMD
    -Wall
    -fno-strict-aliasing
    -Wimplicit
    -Wstrict-prototypes
    -pipe
    -DUSE_ICON
    -I/usr/include/SDL
    -D_GNU_SOURCE=1
    -D_REENTRANT
    -DUSE_OPENAL
    -DUSE_CURL
    -DUSE_CURL_DLOPEN
    -m32
    -DUSE_LOCAL_HEADERS
    -DNDEBUG
    -O3
    -march=i586
    -fomit-frame-pointer
    -ffast-math
    -funroll-loops
    -falign-loops=2
    -falign-jumps=2
    -falign-functions=2
    -fstrength-reduce

  Output:
    build/release-linux-i386/ioUrTded.i386

make[2]: Entering directory `/home/neil/ioUrTded'
DED_CC code/server/sv_bot.c
In file included from /usr/include/assert.h:37:0,
                 from code/server/../qcommon/q_shared.h:99,
                 from code/server/server.h:24,
                 from code/server/sv_bot.c:24:
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
compilation terminated.
make[2]: *** [build/release-linux-i386/ded/sv_bot.o] Error 1
make[2]: Leaving directory `/home/neil/ioUrTded'
make[1]: *** [targets] Error 2
make[1]: Leaving directory `/home/neil/ioUrTded'
make: *** [release] Error 2
neil@lappy:~/ioUrTded$ sudo make ARCH=i386
make[1]: Entering directory `/home/neil/ioUrTded'

Building ioquake3 in build/release-linux-i386:
  PLATFORM: linux
  ARCH: i386
  COMPILE_PLATFORM: linux
  COMPILE_ARCH: x86_64
  CC: cc

  CFLAGS:
    -MMD
    -Wall
    -fno-strict-aliasing
    -Wimplicit
    -Wstrict-prototypes
    -pipe
    -DUSE_ICON
    -I/usr/include/SDL
    -D_GNU_SOURCE=1
    -D_REENTRANT
    -DUSE_OPENAL
    -DUSE_CURL
    -DUSE_CURL_DLOPEN
    -m32
    -DUSE_LOCAL_HEADERS
    -DNDEBUG
    -O3
    -march=i586
    -fomit-frame-pointer
    -ffast-math
    -funroll-loops
    -falign-loops=2
    -falign-jumps=2
    -falign-functions=2
    -fstrength-reduce

  Output:
    build/release-linux-i386/ioUrTded.i386

make[2]: Entering directory `/home/neil/ioUrTded'
DED_CC code/server/sv_bot.c
In file included from /usr/include/assert.h:37:0,
                 from code/server/../qcommon/q_shared.h:99,
                 from code/server/server.h:24,
                 from code/server/sv_bot.c:24:
/usr/include/features.h:323:26: fatal error: bits/predefs.h: No such file or directory
compilation terminated.
make[2]: *** [build/release-linux-i386/ded/sv_bot.o] Error 1
make[2]: Leaving directory `/home/neil/ioUrTded'
make[1]: *** [targets] Error 2
make[1]: Leaving directory `/home/neil/ioUrTded'
make: *** [release] Error 2

```

does anyone know whats wrong ?
i do not want it to be an x86_64 binary as it is unstable for a game server.

---

### Post by neil_1 on 2012-01-18
anyone ?

---

### Post by MadCow108 on 2012-01-18
you probably need gcc-multilib installed
you also need all build dependencies for i386 available and installable

its mostly easier to create a i386 chroot on your amd64 machine to cross compile.

the easiest way is pbuilder-dist:
```
pbuilder-dist ubuntu-releasename i386 create
pbuilder-dist  ubuntu-releasename i386 login
> install and build
```

---

### Post by neil_1 on 2012-01-21
how do i do that ? :S
sorry, i'm new to coding :S

---

### Post by neil_1 on 2012-01-27
anyone ?

---

### Post by MadCow108 on 2012-01-28
```
sudo apt-get install ubuntu-dev-tools
pbuilder-dist ubuntu-releasename i386 create
pbuilder-dist ubuntu-releasename i386 login --bindmounts=/some/folder
# build
```

---

### Post by neil_1 on 2012-01-28
> **MadCow108 said:**
> ```
sudo apt-get install ubuntu-dev-tools
pbuilder-dist ubuntu-releasename i386 create
pbuilder-dist ubuntu-releasename i386 login --bindmounts=/some/folder
# build
```
i get this error after executing line 3:

```

neil@lappy:~$ pbuilder-dist oneiric i386 login --bindmounts=/home/neil/i3/
W: /home/neil/.pbuilderrc does not exist
E: Unknown option [--bindmounts=/home/neil/i3/] was specified 

```

edit:
i tried to compile and it did compile w/o executing lines 3,4

---

### Post by MadCow108 on 2012-01-28
pbuilder is a bit picky about the commandline arguments try
```
--bindmounts /home/neil/i3/
```

---

### Post by neil_1 on 2012-05-03
> **MadCow108 said:**
> pbuilder is a bit picky about the commandline arguments try
```
--bindmounts /home/neil/i3/
```
that worked, thanks MadCow!

---

