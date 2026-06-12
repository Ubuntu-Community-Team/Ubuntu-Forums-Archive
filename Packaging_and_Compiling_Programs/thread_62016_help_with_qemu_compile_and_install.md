---
title: "help with qemu compile and install"
date: 2005-09-03
forum: Packaging and Compiling Programs
---

### Post by thieves.honor on 2005-09-03
I have followed the directions from the qemu howto and am having problems with the ./configure.  when i run ./configure here is my output:

big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/thieveshonor/Downloads/qemu-0.7.1
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu
gprof enabled     no
static build      no
SDL support       no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /lib/modules/2.6.10-5-386/build
kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.
root@ubuntu:~/Downloads/qemu-0.7.1#

any suggestions or help would be great.

---

### Post by tageiru on 2005-09-06
QEMU needs something to draw the display on (if you are not planning to use it without a display, then append --disable-gfx-check to the configure line). You probably need SDL (Cocoa is only used in Mac OS X)

Install libsdl-dev to use SDL output and re-run the configure script.

---

