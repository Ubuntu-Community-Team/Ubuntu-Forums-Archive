---
title: "LLTD: Failed in compiling an lld2d executable"
date: 2009-03-25
forum: Packaging and Compiling Programs
---

### Post by GraysonPeddie on 2009-03-25
For anyone in the know: LLTD = Link Layer Topology Discovery

I try to compile under 2.6.27-11-server and I've already installed the headers and build-essential.

Here's the error:

```
../src/state.c: In function 'state_process_packet':
../src/state.c:177: error: 'UNIT_MAX' underclared (first use in this function)
../src/state.c:177: error: (Each undeclared identifier is reported only once
../src/state.c:177: error: for each function it appears in.)
make: *** [state.o] Error 1
```

#include <linux/if.h> is already in /usr/include/wireless.h file, but it still won't work. I think it will only work with Debian Lenny, but I don't know what version of the kernel Lenny has.

The reason why I want to compile the sample code under Linux is I want to get my Ubuntu Server 8.10 to show up under Vista Network Map.

For anyone who's interested, here's the link:
[http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny](http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny)

I'm stuck in Compile and Install section; like I said, linux/if.h has already been included in linux/wireless.h.

---

### Post by Draconis Rex on 2009-08-29
The fix for this issue is quite straight forward. Microsoft has omitted a header file from the source file that gives the error. Use your favorite text editor to modify the .../Sample Code/src/state.c file. Insert a line reading "#include <limits.h>" after the line reading "#include <assert.h>". Return to the .../Sample Code/native-linux directory and issue the make command. The image should now build successfully. Follow the rest of the instructions to complete the installation.

---

### Post by Draconis Rex on 2009-08-29
In case you're uncomfortable with editing source files I've created a patch for this issue. Download the attached patch file to your computer. Change directories to the .../Sample Code/src directory. Copy the patch file from where ever you saved it to the src directory. Issue the following commands:
[INDENT]patch <state.patch.txt
cd ../native-linux
make
[/INDENT]

---

### Post by GraysonPeddie on 2009-11-06
Boy, it's been a long time since I haven't replied to that thread. But oh well.

I'll check into it.

EDIT: It works!

---

