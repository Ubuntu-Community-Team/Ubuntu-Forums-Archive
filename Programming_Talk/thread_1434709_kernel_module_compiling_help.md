---
title: "kernel module compiling help"
date: 2010-03-20
forum: Programming Talk
---

### Post by jjoshau on 2010-03-20
i've written a loadable module myMod.c, and am having issues with the makefile.
i'm running ubuntu 9.10 with kernel 2.6.31-20-generic

here is my Makefile
```

obj&#8722;m	:= myMod.o

KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

all:
	$(MAKE) &#8722;C $(KDIR) M=$(PWD) modules

clean:
	$(MAKE) &#8722;C $(KDIR) M=$(PWD) clean
```

i've tried multiple variations of this all with similar output:

# make
make &#8722;C /lib/modules/2.6.31-20-generic/build M=/home/joshua/Documents/10spring/cs4540/asgn3 modules
make[1]: Entering directory `/home/joshua/Documents/10spring/cs4540/asgn3'
make[1]: *** No rule to make target `&#8722;C'.  Stop.
make[1]: Leaving directory `/home/joshua/Documents/10spring/cs4540/asgn3'
make: *** [all] Error 2

when manually typing the command in the shell i get:

# make -C /lib/modules/2.6.31-20-generic/build M=/home/joshua/Documents/10spring/cs4540/asgn3
make: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'

things seem close, just confused as to why when running the makefile it enters the current directory and then doesn't seem to understand the make command. i've also a sym-link from /lib/modules/2.6.31-20-generic/build to /usr/src/linux-headers-2.6.31-20-generic

i can't seem to wrap my head around what's wrong.

---

### Post by dwhitney67 on 2010-03-20
I tried your Makefile, I got the same issue.  I found two workarounds; there might be others:

Option 1:
```

KDIR := /lib/modules/$(shell uname -r)/build
...
all:
        $(MAKE) --directory=$(KDIR) M=$(PWD) modules
...

```

Option 2:
```

all:
        $(MAKE) -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

```

Repeat the same for the 'clean' rule.

P.S.  The alias for PWD, that you defined, is superfluous.  On every *nix system I have every worked with, PWD has always defined within the shell environment.

---

### Post by jjoshau on 2010-03-20
> **dwhitney67 said:**
> 
Option 1:
```

KDIR := /lib/modules/$(shell uname -r)/build
...
all:
        $(MAKE) --directory=$(KDIR) -M=$(PWD) modules
...

```

Repeat the same for the 'clean' rule.

P.S.  The alias for PWD, that you defined, is superfluous.  On every *nix system I have every worked with, PWD has always defined within the shell environment.

that worked! thank you much, now i can continue setting up/debugging this beast.. onto the kernel/bounds.c error. 
thanks for the PWD info, i did try without my declaration and it worked, but including it seemed failsafe. thanks again

---

### Post by jjoshau on 2010-03-20
alright, so i am at another stand still.
my code is in mymod.c and here is the current Makefile:

```
obj&#8722;m := mymod.o

KDIR := /lib/modules/$(shell uname -r)/build

all:
	$(MAKE) --directory=$(KDIR) M=$(PWD) modules

clean:
	$(MAKE) --directory=$(KDIR) M=$(PWD) clean

```

now when i run make i get:

# make
make --directory=/lib/modules/2.6.32.3phase2/build M=/home/joshua/Documents/10spring/cs4540/asgn3 modules
make[1]: Entering directory `/usr/src/linux-2.6.32.3'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-2.6.32.3'

i've got to be looking past some mundane detail.. any thoughts?
i've two kernels and have the same results on both

---

### Post by dwhitney67 on 2010-03-21
You are using a later version of the kernel than I have available on my patched Ubuntu 9.10 system (I have linux-headers-2.6.31-20-generic).

Either you are running a newer distro, but without the Linux source code (ie. headers) properly installed, or you are just experiencing a bout of bad luck.  Either way, there isn't much I can do to help.

Perhaps someone else will chime in.

P.S.  Maybe posting your mymod.c source code might help.

P.S. #2:  For some strange reason, I am no longer able to duplicate the original problem that you posted; the following Makefile works fine:
```

obj-m := mymod.o

KDIR  := /lib/modules/$(shell uname -r)/build

all:
        $(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
        $(MAKE) -C $(KDIR) M=$(PWD) clean

```

Ah.. I found the issue; it is with the dash-symbols that you used in your original posting.  They are incorrect; in fact I do not know what they are.  But a single dash-symbol (ie. the key between keys '0' and '=') are needed.

---

### Post by jjoshau on 2010-03-21
haha, yeah it is strange, i've noticed that the -C flag works properly now for me to (strange it seemed to be a dash issue). 
bad luck seems the case, this shouldn't be so difficult.

2.6.31-20-generic is the other kernel i've been attempting with, the newer one is one i compiled for a project.
thank you for your repeated assistance

---

### Post by jjoshau on 2010-03-21
i suppose i'll post a bit more information

i only assume i have everything set up properly.

here is my /lib/modules for my current kernel:

joshua@jjoshau:/lib/modules$ uname -r
2.6.31-20-generic
joshua@jjoshau:/lib/modules/2.6.31-20-generic$ ls -l
total 3404
lrwxrwxrwx  1 root root     28 2010-03-21 01:22 build -> /usr/src/linux-source-2.6.31
drwxr-xr-x  2 root root   4096 2010-03-19 18:29 initrd
drwxr-xr-x 10 root root   4096 2010-03-05 10:00 kernel
drwxr-xr-x  7 root root   4096 2010-03-19 18:35 linux-headers-2.6.31-20-generic
-rw-r--r--  1 root root 550766 2010-03-19 18:29 modules.alias
-rw-r--r--  1 root root 530732 2010-03-19 18:29 modules.alias.bin
-rw-r--r--  1 root root     69 2010-03-19 18:29 modules.ccwmap
-rw-r--r--  1 root root 238048 2010-03-19 18:29 modules.dep
-rw-r--r--  1 root root 350815 2010-03-19 18:29 modules.dep.bin
-rw-r--r--  1 root root   1405 2010-03-19 18:29 modules.ieee1394map
-rw-r--r--  1 root root    218 2010-03-19 18:29 modules.inputmap
-rw-r--r--  1 root root   7825 2010-03-19 18:29 modules.isapnpmap
-rw-r--r--  1 root root     74 2010-03-19 18:29 modules.ofmap
-rw-r--r--  1 root root  92924 2010-03-12 01:46 modules.order
-rw-r--r--  1 root root 364281 2010-03-19 18:29 modules.pcimap
-rw-r--r--  1 root root   1345 2010-03-19 18:29 modules.seriomap
-rw-r--r--  1 root root 204083 2010-03-19 18:29 modules.symbols
-rw-r--r--  1 root root 263979 2010-03-19 18:29 modules.symbols.bin
-rw-r--r--  1 root root 834418 2010-03-19 18:29 modules.usbmap


and here is running the make...

god dammit, just ran a hello.c example i found and it compiled fine... must be my source code
now i feel like an idiot

---

### Post by dwhitney67 on 2010-03-21
The directory that 'build' is pointing to looks suspect.  I have the following on my system:
```

$ uname -r
2.6.31-20-generic
$ cd /lib/modules/`uname -r`
$ ls -l
total 3552
lrwxrwxrwx  1 root root     40 2010-03-06 13:35 build -> /usr/src/linux-headers-2.6.31-20-generic
drwxr-xr-x  2 root root   4096 2010-03-17 08:00 initrd
drwxr-xr-x 10 root root   4096 2010-03-06 13:34 kernel
-rw-r--r--  1 root root 563054 2010-03-17 08:01 modules.alias
...

```

---

### Post by jjoshau on 2010-03-21
my god, it was the '-' in obj-m... fml. i'm really curious where that character came from and why it was throughout my file.
thanks again, all seems to be well now.

---

