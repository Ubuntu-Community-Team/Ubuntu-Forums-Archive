---
title: "RAIDexpress 133 driver compile"
date: 2006-09-30
forum: Packaging and Compiling Programs
---

### Post by rustybutt on 2006-09-30
I built up a RAID file server some months ago in Breezy.  I picked up a great deal on a used server case with a 1.8 Ghz board, a CD-ROM, two 60 G drives and 1/2 G of memory for a whopping $125.  Not bad.  I added in a Promise 100 IDE card and four 250 G hard drives I picked up from Unity Electronics for $80 each.  I then configured three of the four 250 G drives in a RAID 5 array, with the remaining 250 G drive as a hot spare.  The two 60 G drives I configured as a RAID 1 mirror to be used as my boot drive.

So for under $500, I had a 500 G RAID 5 file server for my own use!

Cool...  Until...

For some reason I don't yet understand, one channel of the Promise 100 card decided to stop working.  Fortunately for me, it was the channel that had the host spare drive, so I only lost it and one of the RAID 5 drives, so the remaining two drives are still there, with my data, but running in degraded mode.

I went into fdisk and could see that the drives on the 2nd channel were still functioning.  I checked mdadm and one drive was marked as being bad.  So just used 

mdadm --grow 

to add it back in and like it's supposed to, the RAID software started to resync the array back together.

Cool...  until the damn Promise card locked up and the whole machine came to screeching halt.  Damn...

So I tried a Promise 133 card.  Same thing.  Then I found the same issue in a RAID 1 array with a Promise card on another machine.  Looks like resyncing with Promise cards are a bad idea.

So I scored a RAIDexpress 133 IDE controller card.  I pop it in and there's no driver under Ubuntu  Bleah...  But that's not so bad since RAIDexpress included the source to compile a new driver for the 2.6.x kernel.  Which is great except that I'm not a programmer.  I'm a sysadmin who knows enough to hack and thrash, but I'm really pretty clueless with stuff like this.

The source directory consists of three files:


-rw-rw-rw-  1 root root 152203 2004-05-11 14:46 iteraid.c
-rw-rw-rw-  1 root root  46296 2004-05-11 10:09 iteraid.h
-rw-rw-rw-  1 root root    296 2004-04-07 15:55 Makefile

The problem arises in that make barfs when I run it.  I put the source in a directory at:

/usr/src/raidexpress/driver/src/2.6.x

The Makefile consists of:<br>
==================================================================


root@nfs2:/usr/src/raidexpress/driver/src/2.6.x# cat Makefile<br>
KERNEL_SRC = /usr/src/linux-2.6.1

EXTRA_FLAGS += -I.

EXTRA_FLAGS += -Wno-cast-qual -Wno-strict-prototypes

obj-m += iteraid.o

iteraid-obj := iteraid.o

modules:
        $(MAKE) -C $(KERNEL_SRC) SUBDIRS=$(PWD) modules

clean:
        rm -rf iteraid.o iteraid.ko iteraid.mod.o iteraid.mod.c *~


=======================================================================

I'm pretty clueless here, sorry to say.  But then that's what this forum is for, is it not?  Clueless chumps like me.

So what do I do to get this thing to compile?

Rustybutt

---

### Post by po0f on 2006-09-30
rustybutt,

What's the error you are getting from make?  And the lines after 'modules:' and 'clean:' should be tabbed in the Makefile, maybe this is the problem?

---

### Post by rustybutt on 2006-09-30
Here's what happens when I run "make":

===========================================================================

root@nfs2:/usr/src/raidexpress/driver/src/2.6.x# make
make -C /usr/src/linux-2.6.1 SUBDIRS=/usr/src/raidexpress/driver/src/2.6.x modul
es
make: *** /usr/src/linux-2.6.1: No such file or directory.  Stop.
make: *** [modules] Error 2
root@nfs2:/usr/src/raidexpress/driver/src/2.6.x# more Makefile
KERNEL_SRC = /usr/src/linux-2.6.1

EXTRA_FLAGS += -I.

EXTRA_FLAGS += -Wno-cast-qual -Wno-strict-prototypes

obj-m += iteraid.o

iteraid-obj := iteraid.o

modules:
        $(MAKE) -C $(KERNEL_SRC) SUBDIRS=$(PWD) modules

clean:
        rm -rf iteraid.o iteraid.ko iteraid.mod.o iteraid.mod.c *~

---

### Post by po0f on 2006-09-30
rustybutt,

I was using [this](http://www.ubuntuforums.org/showthread.php?t=164040&highlight=xbox+360+controller) guide on how to compile a driver for the Xbox 360 controller without having the kernel source installed.  Try changing your -C argument to point to /lib/modules/`uname -r`/build instead and see if that works.

---

### Post by rustybutt on 2006-10-01
Another friend who's a Redhat developer suggested using:

/lib/modules/`uname -r`/build 

But that directory doesn't exist

Just for grins, I put that into the Makefile.  I'm pretty clueless really and I figured it wouldn't hurt anything.  And sure enough, this barfs as well:

root@nfs2:/usr/src/raidexpress/driver/src/2.6.x# make
make -C /lib/modules/`uname -r`/build/ SUBDIRS=/usr/src/raidexpress/driver/src/2.6.x modules
make: *** /lib/modules/2.6.12-10-386/build/: No such file or directory.  Stop.
make: *** [modules] Error 2





Are the necessary supporting source files installed with the standard Ubuntu release, or are there more packages I need to pull down?

---

### Post by po0f on 2006-10-01
rustybutt,

Install either linux-headers or kernel-headers, I forget which one actually resolved the dependency for me.  Make sure you install the version of those packages that corresponds with what kernel you have running.

[EDIT]

These are the contents of the Makefile I used to compile the controller driver:
```

obj-m := xpad.o

KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS = -I$(shell pwd)

all:
    $(MAKE) modules -C $(KDIR) SUBDIRS="$(shell pwd)
```

The driver consisted of one source and one header file, as in your case.  Try this Makefile, changing the necessary variables.  After installing linux-headers.  I just confirmed that it was this package that had to be installed.  In my case, linux-headers-2.6.15-27-686.  Hope this helps.

[EDIT2]

You do know which directory under /lib/modules/`uname -r` that you have to copy the driver to, correct?

---

### Post by rustybutt on 2006-10-01
I did as you suggested and loaded in two packages I didn't have before:

linux-headers-2.6.12-10 
linux-headers-2.6.12-10-386 

And Presto!  The /lib/modules/`uname -r`/build directory appeared!

Good.

But then things still aren't completing, and this time I think it's an Ubuntu issue.  As part of the build process, it seems as though something is trying to determine what version of gcc is being run and it's barfing on that.  For some reason it's bitching about 

gcc-3.4: command not found

I don't know if it's looking for gcc-3.4, or if this is a gcc complaint.  When I do a "gcc -v" I get:

root@nfs2:/usr/src/linux-headers-2.6.12-10-386/scripts# gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)



Here's the current status of when I try to run "make".

Oh, and no, I don't know what/where to do what/with the driver after the compile is done.  It's going to be a .o file, right?  Do I need to put it somewhere specific and then reference it in 

/etc/modules

======================================================================



root@nfs2:/usr/src/raidexpress/driver/src/2.6.x# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/raidexpress/driver/src/2.6.x modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/raidexpress/driver/src/2.6.x/iteraid.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/usr/src/raidexpress/driver/src/2.6.x/iteraid.o] Error 127
make[1]: *** [_module_/usr/src/raidexpress/driver/src/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2

---

### Post by po0f on 2006-10-01
rustybutt,

You have to compile kernel modules with the version of gcc that built the kernel.  Try installing gcc-3.4 as well and see if that helps the make process.

Yes, you will have to find out what directory to put the driver .o file in.  And yes, after that you can load it via /etc/modules.

Googled real quick and found that you'll probably have to install it in /lib/modules/`uname -r`/kernel/drivers/scsi.  Run this command in the directory with the kernel module:
```
# install -c iteraid.o /lib/modules/`uname-r`/kernel/drivers/scsi
```

[Reference](http://www.syba.com/us/bin/ite/it8212/it8212_manual.pdf).

---

### Post by rustybutt on 2006-10-01
I installed gcc-3.4 and that made a big difference.  The thing actually began to compile.  Now I've got C language issues (I think).  Bleah...

I've attached a zip file with the driver source code and the output of the compile.  I'm totally lost on this one.  There are complaints about parse errors, but I don't see anything that obvious in the code.

You suggest that I'll need to put the driver in:

# install -c iteraid.o /lib/modules/`uname-r`/kernel/drivers/scsi

This device is an IDE controller.  Shouldn't it be put in:

# install -c iteraid.o /lib/modules/`uname-r`/kernel/drivers/ide

---

### Post by rustybutt on 2006-10-01
Also as an FYI, here's a listing of the kernel and header packages on the system in case you see that something might be missing:

root@nfs2:~# dpkg -l | egrep 'headers|kernel'
ii  comerr-dev                             2.1-1.38-2ubuntu1                  common error description library - headers a
ii  iptables                               1.3.1-2ubuntu1.1                   Linux kernel 2.4+ iptables administration to
ii  kernel-package                         9.001ubuntu5                       A utility for building Linux kernel related 
ii  libcompfaceg1                          1989.11.11-24ubuntu1               Compress/decompress images for mailheaders, 
ii  linux-386                              2.6.12.16.1                        Complete Linux kernel on 386.
ii  linux-headers-2.6.12-10                2.6.12-10.40                       Header files related to Linux kernel version
ii  linux-headers-2.6.12-10-386            2.6.12-10.40                       Linux kernel headers 2.6.12 on 386
ii  linux-headers-386                      2.6.12.16.1                        Linux kernel headers on 386
ii  linux-image-2.6.12-10-386              2.6.12-10.36                       Linux kernel image for version 2.6.12 on 386
ii  linux-image-2.6.12-9-386               2.6.12-9.23                        Linux kernel image for version 2.6.12 on 386
ii  linux-image-386                        2.6.12.16.1                        Linux kernel image on 386.
ii  linux-kernel-headers                   2.6.11.2-0ubuntu13                 Linux Kernel Headers for development
ii  linux-source-2.6.12                    2.6.12-10.40                       Linux kernel source for version 2.6.12 with 
ii  module-init-tools                      3.2-pre7-0ubuntu4                  tools for managing Linux kernel modules
ii  nfs-kernel-server                      1.0.7-3ubuntu1                     Kernel NFS server support
ii  nvidia-kernel-common                   1.0.7667+1                         NVIDIA binary kernel module common files

---

### Post by po0f on 2006-10-02
rustybutt,

In the source file, at the very top with all the includes, change the line that says```
#include "hosts.h"
``` to ```
#include <scsi/scsi_host.h>
```

Better yet, try this file instead: [click](http://dufo.tugraz.at/~prokop/grml-kernel/2.6.17-patches/4150_iteraid.patch).

This is a patch file, but it looks like the complete source so you don't have to patch!  But you will have to find a way to remove the +'s at the beginning of each file.  Download that file and save it as iteraid.c.new.  Do you like Python?  I do.  Try this script to remove the +'s:
```
#!/usr/bin/python

import sys

def main():
    try:
        fd = open("iteraid.c.new")
        lines = fd.readlines()
        fd.close()
    except IOError:
        sys.exit("Error reading file")

    for line in lines:
        line.lstrip("+")
        print line

if __name__ == "__main__":
    main()
```

Save that as whatever.py (or whatever you want to save it as ;) ) in the directory with the sources, and run this from a terminal:
```
# mv iteraid.c iteraid.c.old
# python whatever.py > iteraid.c
```

Note that you'll still have to remove the first four lines of the new file.  That's off the top of my head, and I haven't tested it since I'm on my Windows box atm, but I don't see a problem with it.  If that doesn't work, post back and I'll fix it.

---

### Post by rustybutt on 2006-10-02
I tried both of the fixes you suggested.  I tried changing hosts.h to <scsi/scsi_hosts.h> as well as using your source code.   I also had to alter the line which reads "scsi.h" to <scsi/scsi.h>, which I had to do in both the original source and the source you gave to me.

Making those changes removed the complaints about those files not being found.  Progress!

But all the complaints about iteraid.h remain.  Parse errors and such.  Since you pulled down that zip file, you have a copy of the iteraid.h file.  While I'm not a C coder, I do know enough C and such to look in a file and see obvious typos and the like.  The error messages begins complaining with:

/usr/src/raidexpress/driver/src/2.6.x/iteraid.h:945: error: parse error before "Scsi_Cmnd"


I go to that line and I see that it's part of a typedef struct block, and I don't see any obvious typos, or missing semi-colons.  I'm not competent to do more than that.  Any suggestions?

Russ

---

### Post by rustybutt on 2006-10-02
I showed this to a buddy of mine and he suggested that the supplied driver from RAIDexpress is for a different version of the Linux kernel and has different kernel data structures. 

You provided me with a new iteraid.c file, but not a new iteraid.h file.  Have you got an iteraid.h file to go along with the iteraid.c file?

---

### Post by po0f on 2006-10-02
rustybutt,

No sorry, it was just something I found while googling.  I read somewhere that the driver supplied by the manufacturer is for kernel-2.4.*.  I read somewhere else that in >kernel-2.6.12 they have a driver for it.  I also read somewhere else that you might have to use the -ac branch of the kernel to get it.

I just downloaded 2.6.18's source and looked through it.  It appears there is a driver for your card, it821x, under drivers/ide/pci.  Have you ever compiled your own kernel before?  ;)  If you have trouble, post back, I can walk you through it.

---

### Post by rustybutt on 2006-10-02
Nope.  I've never compiled a kernel before.  So if the newest kernel has the driver in it, then that's a great solution!  Your help is enormously appreciated.

---

### Post by po0f on 2006-10-02
rustybutt,

I'm sorry it took so long to come to this conclusion.  I had thought about suggesting it earlier (didn't know it had the driver, was just going to suggest), and it looks like it was the right answer.  Anyway...

Like I said, if you have problems compiling you kernel, drop me a line, PM or here.

---

### Post by rustybutt on 2006-10-02
You suggest possibly moving to the 2.6.18 kernel.  Is it possible that the driver might be contained in the 2.6.15 kernel which is stock with Dapper Drake?  Would simply upgrading to Dapper fix my problem?

---

### Post by po0f on 2006-10-02
rustybutt,

That is very likely.  I was wondering why you weren't getting the latest packages for your kernel.  (You'll have to excuse me, I'm coming from Gentoo.  As soon as a package is released, they chuck it into the Gentoo repository, called the Portage tree, and that's the latest version.  If you upgrade, you're always bleeding-edge current.  Causes some frustration every now and then.  It's also why I have more than a little experience compiling kernels, but I digress.)

I retract my previous suggestion and change it to upgrade to Dapper.  Just ran a 'locate it821x' and got several hits, one of them being it821x.ko, so as soon as you upgrade, you'll be golden.  :)

---

### Post by rustybutt on 2006-10-02
Yeah.  I'm with you on that.  I have a dapper desktop and checked the kernel, which is 2.6.15.  I pulled down the source from kernel.org and the 8216 stuff seems to be there, so I'm already running an apt-get dist-upgrade (after updating /etc/apt/sources.list).  Hopefully that'll do the trick.

Man, you've been golden!  You've scored major good karma points here!  I'll let you know how it goes.

---

### Post by po0f on 2006-10-02
rustybutt,

I just hope it works for you.  At this point, I have a certain amount of emotional investment in this undertaking of your's, and am eagerly waiting a successful outcome (even if I have to compile a kernel for you myself!).  :)

---

### Post by rustybutt on 2006-10-03
I finished the upgrade to Dapper.  uname -r shows the 2.6.15 kernel.  Unfortunately the RAIDexpress card still seems to have issues.  With the card installed and no drives connected to it, the machine boots up.  But connect a drive to the card and the machine hangs on driver loading.  One time I managed to get it to boot and when I did an fdisk on the drive, fdisk just gave some errors.

I'm going to try booting the machine off of a Dapper install CD and see how that goes, but I'm not hopeful.  I may have to look for another IDE card.  This is taking too much time.

Is there an IDE card you'd recommend?  The Promise cards don't work as software RAID cards.  That's why I'm in this mess.

---

### Post by po0f on 2006-10-03
rustybutt,

Are you concerned with the performance of the drive?  Try turning DMA off for it.  Read somewhere that DMA may be the culprit.  Google knows all, but is not very specific.  ;)  I think you can pass an option to the kernel to turn off DMA, and I think the only way to do it would be to turn off DMA for all drives, then turn it back on for the onboard IDE interfaces:
```
ide=nodma ide0=dma ide1=dma
```

If that doesn't work, just use the ide=nodma option, and after your computer is booted, reactivate DMA for the onboard IDE interfaces with hdparm:
```
# hdparm -d1 /dev/hd{a,b,c,d}
```

And no, I can't recommend an IDE card.  I don't have a use for anything more than what my 120 gigger can hold.

---

### Post by rustybutt on 2006-10-04
I'm about to head out of town for a 4 day trip to Yosemite.  No computing.  The wife won't allow it.  Probably no wireless access at the campsite anyway.  I've ordered up an Adaptec card which will be waiting for me on my return.  Between that and turning off DMA, which might make the Promise card actually function, something's goign to have to work.

I'll check in sometime Sunday or Monday.

---

### Post by rustybutt on 2006-10-11
Just thought I'd let you know that the Adaptec ASH-1233 card seems to work just fine and all of the drives show up.  That's the good news.  What seems to be rather funky news is that mdadm from Breezy  seems to barf for a RAID 5 array, but is OK for RAID 1.  My data is still there on just the 2 drives in degraded mode, so what I'm going to do is to copy it off to another spare drive and just rebuild the whole bloody machine.  

My data is still there and that's what really counts.  You've been a big help man!  Thanks a bunch!

---

