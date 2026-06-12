---
title: "Breezy: Compiling qemu - SDL problems"
date: 2005-10-19
forum: Packaging and Compiling Programs
---

### Post by gobfrey on 2005-10-19
Hi

  I'm following the instructions on:
[http://ubuntuforums.org/showthread.php?t=39513](http://ubuntuforums.org/showthread.php?t=39513)

Before you read the following, please be aware that SDL is installed:

$ sudo apt-get install libsdl1.2-dev
Password:
Reading package lists... Done
Building dependency tree... Done
libsdl1.2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And when I run ./configure I get:

$ ./configure
big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/adam/Desktop/qemu-0.7.2
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
kernel sources    /usr/src/linux-headers-2.6.12-9-386
kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.


What's the problem?

Some help would be appreciated.

---

### Post by samjam on 2005-10-27
[QUOTE=gobfrey]Hi

  I'm following the instructions on:
[http://ubuntuforums.org/showthread.php?t=39513](http://ubuntuforums.org/showthread.php?t=39513)

Before you read the following, please be aware that SDL is installed:

$ sudo apt-get install libsdl1.2-dev

[/QUOTE]

How about:
```

apt-get install libsdl-dev

```

I fail further on with:
```

gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -mpreferred-stack-boundary=2 -falign-functions=0 -fno-gcse -fno-reorder-blocks -fno-optimize-sibling-calls -I. -I/root/debs/qemu/qemu-0.7.2/target-i386 -I/root/debs/qemu/qemu-0.7.2 -I/root/debs/qemu/qemu-0.7.2/linux-user -I/root/debs/qemu/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/root/debs/qemu/qemu-0.7.2/fpu -I/root/debs/qemu/qemu-0.7.2/slirp -c -o op.o /root/debs/qemu/qemu-0.7.2/target-i386/op.c
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h: In function 'op_pshufw_mmx':
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:574: error: unable to find a register to spill in class 'GENERAL_REGS'
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:574: error: this is the insn:
(insn:HI 18 17 19 0 /root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:569 (set (strict_low_part (subreg:HI (reg/v:DI 63 [ r ]) 0))
        (mem/s/j:HI (plus:SI (mult:SI (reg:SI 64)
                    (const_int 2 [0x2]))
                (reg/v/f:SI 59 [ s ])) [0 <variable>._w S2 A16])) 52 {*movstricthi_1} (insn_list:REG_DEP_TRUE 16 (insn_list:REG_DEP_TRUE 12 (insn_list:REG_DEP_TRUE 53 (nil))))
    (expr_list:REG_DEAD (reg:SI 64)
        (nil)))
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:574: confused by earlier errors, bailing out
make[1]: *** [op.o] Error 1
make[1]: Leaving directory `/root/debs/qemu/qemu-0.7.2/i386-user'
make: *** [all] Error 1

```
which I guess is just as likely to be gcc4 errors as anything else.

Sam

---

### Post by us3rQUE on 2005-10-27
[QUOTE=gobfrey]Hi

  I'm following the instructions on:
[http://ubuntuforums.org/showthread.php?t=39513](http://ubuntuforums.org/showthread.php?t=39513)

Before you read the following, please be aware that SDL is installed:

$ sudo apt-get install libsdl1.2-dev
Password:
Reading package lists... Done
Building dependency tree... Done
libsdl1.2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And when I run ./configure I get:

$ ./configure
big/little test failed
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/adam/Desktop/qemu-0.7.2
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
kernel sources    /usr/src/linux-headers-2.6.12-9-386
kbuild type       2.6
ERROR: QEMU requires SDL or Cocoa for graphical output
To build QEMU with graphical output configure with --disable-gfx-check
Note that this will disable all output from the virtual graphics card.


What's the problem?

Some help would be appreciated.[/QUOTE]


Previously had gcc-3.4 installed, after installing gcc-3.3 
 

I tried this: 
Now tell qemu to use gcc-3.3

 .```

 ./configure --cc=gcc-3.3 
.
```

It finally seemed to detect SDL

 .```

./configure --cc=gcc-3.3
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/us3rQUE/Documents/Software/Emulation/qemu-0.7.2
C compiler        gcc-3.3
Host C compiler   gcc
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.12-9-386
kbuild type       2.6
.
```

---

### Post by us3rQUE on 2005-10-27
Also make sure you have build-essentials.
.```

sudo apt-get install build-essentials
.
```

---

### Post by us3rQUE on 2005-10-27
samjam your correct about gcc4

Ok so I got the same errors "samjam"
.```

gcc -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -mpreferred-stack-boundary=2 -falign-functions=0 -fno-gcse -fno-reorder-blocks -fno-optimize-sibling-calls -I. -I/root/debs/qemu/qemu-0.7.2/target-i386 -I/root/debs/qemu/qemu-0.7.2 -I/root/debs/qemu/qemu-0.7.2/linux-user -I/root/debs/qemu/qemu-0.7.2/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/root/debs/qemu/qemu-0.7.2/fpu -I/root/debs/qemu/qemu-0.7.2/slirp -c -o op.o /root/debs/qemu/qemu-0.7.2/target-i386/op.c
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h: In function 'op_pshufw_mmx':
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:574: error: unable to find a register to spill in class 'GENERAL_REGS'
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:574: error: this is the insn:
(insn:HI 18 17 19 0 /root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:569 (set (strict_low_part (subreg:HI (reg/v:DI 63 [ r ]) 0))
        (mem/s/j:HI (plus:SI (mult:SI (reg:SI 64)
                    (const_int 2 [0x2]))
                (reg/v/f:SI 59 [ s ])) [0 <variable>._w S2 A16])) 52 {*movstricthi_1} (insn_list:REG_DEP_TRUE 16 (insn_list:REG_DEP_TRUE 12 (insn_list:REG_DEP_TRUE 53 (nil))))
    (expr_list:REG_DEAD (reg:SI 64)
        (nil)))
/root/debs/qemu/qemu-0.7.2/target-i386/ops_sse.h:574: confused by earlier errors, bailing out
make[1]: *** [op.o] Error 1
make[1]: Leaving directory `/root/debs/qemu/qemu-0.7.2/i386-user'
make: *** [all] Error 1
.
```


also found this: [http://www.raditha.com/blog/archives/000790.html](http://www.raditha.com/blog/archives/000790.html)

so I did the following:
 (BTW - I tried find a easier way to do the following w/o success. - please post if U know how :confused: )

make sure you already have: gcc-3.3 

sudo cp /usr/bin/gcc gcc-xyz
sudo cp /usr/bin/gcc-3.3 gcc

Then when back to my Qemu install & run 

make

And finally it compiles w/o any errors.

and undo my compiler switchup 

sudo cp /usr/bin/gcc-xyz gcc

DONE.

---

### Post by tuxboy on 2005-10-30
us3rQUE, an easier way of what you were asking might be to pass the '--cc=gcc-3.3' option to the ./configure script before running make. I tried that and it worked for me.

---

### Post by samjam on 2005-10-31
[QUOTE=tuxboy]us3rQUE, an easier way of what you were asking might be to pass the '--cc=gcc-3.3' option to the ./configure script before running make. I tried that and it worked for me.[/QUOTE]

Top tip, workedfor me.

I also edited kqemu/install.sh(I thihnk) and commented out the depmod -a

Then I was able to successfully use "checkinstall" tool to install it as a dpkg

---

### Post by aesux on 2005-11-01
[QUOTE=us3rQUE]samjam your correct about gcc4


make sure you already have: gcc-3.3 

sudo cp /usr/bin/gcc gcc-xyz
sudo cp /usr/bin/gcc-3.3 gcc

Then when back to my Qemu install & run 

DONE.[/QUOTE]

gcc on Ubuntu Breezy is a symlink, so I have had to change that 

sudo ln -sf gcc-3.3 gcc

Then i compile with no errors :p 

In my case, using configure parameters does not work. I don't know why :confused: 

Aesux

---

### Post by andrew_d_mackenzie on 2005-12-22
I have the same problem as original posting (using Ubunto Breezy).

I have tried all the suggested fixes without success.

I am new to Ubunto (and Linux) and very rusty on Unix. But after investigation my suspicion is that the compiler is not finding the <SDL.h> header files. 

Is there anything special to do after using Synaptic to install the libsdl* before trying to build?

Thanks

---

