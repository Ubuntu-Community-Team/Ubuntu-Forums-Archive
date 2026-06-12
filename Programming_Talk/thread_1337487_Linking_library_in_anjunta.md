---
title: "Linking library in anjunta"
date: 2009-11-25
forum: Programming Talk
---

### Post by kizofilax on 2009-11-25
Hello all

I am writing a program that uses libreries here

/usr/src/linux-headers-2.6.28-16/include/net/bluetooth

Im programming this in anjunta, I already added that path to the source directories on the debug tab but I still get the file not found error

My program starts like this


#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/socket.h>
#include <bluetooth.h>
#include <hci.h>
#include <hci_lib.h>

The last 3 files are the ones i cannot get to work

Thanks

---

### Post by MadCow108 on 2009-11-25
you must tell the compiler/linker where to find the files
you do that by right clicking on your build target (in project sidebar) -> properties -> advanced
-I for include files (in bluetooth case: -I/usr/src/linux-headers-2.6.28-16/include/net/bluetooth)
-L for library path -l for library name (without lib and extension)

if your libraries are tracked by pkg-config you can add the package to the project properties dialog. Then pkg-config will fill in the flags.

---

