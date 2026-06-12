---
title: "Too many open files"
date: 2009-06-10
forum: Programming Talk
---

### Post by agilor on 2009-06-10
Too many open files!!!!??

Im am trying to install the MSI (Macro Substitution and Include Tool) for EPICS, but when I try to compile using 'make' it appears:

/home/epics/base-3.14.9/extensions$ make
configure/CONFIG:5: configure/RELEASE: Too many open files
configure/CONFIG:13: configure/CONFIG: Too many open files
configure/CONFIG:17: configure/CONFIG_SITE: Too many open files
configure/RULES_TOP:3: configure/RULES_TOP: Too many open files
make: *** No targets specified and no makefile found.  Stop.

I did tried to see which is the limit of files open in my system:
sudo sysctl -a | grep "fs.file-max"
error: permission denied on key 'kernel.cap-bound'
error: permission denied on key 'kernel.cad_pid'
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
fs.file-max = 302305
error: permission denied on key 'dev.parport.parport0.autoprobe'
error: permission denied on key 'dev.parport.parport0.autoprobe0'
error: permission denied on key 'dev.parport.parport0.autoprobe1'
error: permission denied on key 'dev.parport.parport0.autoprobe2'
error: permission denied on key 'dev.parport.parport0.autoprobe3'

302305 ??? I do not really understand this number and how all this files could be open but anyway increased the fs.file-max to 1000000 with 'sudo sysctl -w fs.file-max=1000000' but I still get the same problem. Any ideas?

---

### Post by dwhitney67 on 2009-06-10
Go to the directory where you typed 'make'.  Do you even have a Makefile in that directory?  This statement suggests that you do not:
```

make: *** No targets specified and no makefile found. Stop.

```

Perhaps you need to run 'configure' first?  Or better yet, peruse the README file or other documentation for notes on the procedure for the proper building and the installation of your product.

---

### Post by alternatealias on 2009-06-10
> **agilor said:**
> Too many open files!!!!??

Im am trying to install the MSI (Macro Substitution and Include Tool) for EPICS, but when I try to compile using 'make' it appears:

/home/epics/base-3.14.9/extensions$ make
configure/CONFIG:5: configure/RELEASE: Too many open files
configure/CONFIG:13: configure/CONFIG: Too many open files
configure/CONFIG:17: configure/CONFIG_SITE: Too many open files
configure/RULES_TOP:3: configure/RULES_TOP: Too many open files
make: *** No targets specified and no makefile found.  Stop.

I did tried to see which is the limit of files open in my system:
sudo sysctl -a | grep "fs.file-max"
error: permission denied on key 'kernel.cap-bound'
error: permission denied on key 'kernel.cad_pid'
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'
fs.file-max = 302305
error: permission denied on key 'dev.parport.parport0.autoprobe'
error: permission denied on key 'dev.parport.parport0.autoprobe0'
error: permission denied on key 'dev.parport.parport0.autoprobe1'
error: permission denied on key 'dev.parport.parport0.autoprobe2'
error: permission denied on key 'dev.parport.parport0.autoprobe3'

302305 ??? I do not really understand this number and how all this files could be open but anyway increased the fs.file-max to 1000000 with 'sudo sysctl -w fs.file-max=1000000' but I still get the same problem. Any ideas?

you might try using `lsof` as root to see what program(s) are using up all your file handles and kill them or something.

My guess is that you have some runaway process (or two) that are leaking file descriptors (i.e. not closing them like they should).

If you've been running Thunderbird for several days in a row, for example, you might try closing it (it seems to leak file descriptors on me and closing Thunderbird usually solves the problem when I run into this - but usually I have to run Thunderbird for a week or more before I run out).

Hope that helps

---

### Post by agilor on 2009-06-10
--There is a Makefile, and also a README file, which only says to unzip and untar the file in the extensions/src/directory

The Makefile only contains this:
--------------------------------
# Makefile,v 1.6 2007/05/18 16:16:49 jba Exp
#
TOP = ../..

include $(TOP)/configure/CONFIG

PROD_HOST = msi
HTMLS = msi.html

msi_SRCS = msi.c
PROD_LIBS += Com
---------------------------------
I closed the firefox and nothing improved. Then I reboot the system and also the same.

I used the command 'lsof' after rebooting and this is what appears....

COMMAND    PID       USER   FD      TYPE     DEVICE     SIZE    NODE NAME
init         1       root  cwd   unknown                             /proc/1/cwd (readlink: Permission denied)
init         1       root  rtd   unknown                             /proc/1/root (readlink: Permission denied)
.............. many lines .............
lsof      6567       gtruser  mem       REG        8,5  1364388 4138000 /lib/tls/i686/cmov/libc-2.7.so
lsof      6567       gtruser  mem       REG        8,5    25700 5710345 /usr/lib/gconv/gconv-modules.cache
lsof      6567       gtruser  mem       REG        8,5   109152 4120588 /lib/ld-2.7.so
lsof      6567       gtruser    4r     FIFO        0,5            21969 pipe
lsof      6567       gtruser    7w     FIFO        0,5            21970 pipe

---

### Post by dwhitney67 on 2009-06-10
> **agilor said:**
> --There is a Makefile, and also a README file, which only says to unzip and untar the file in the extensions/src/directory

The Makefile only contains this:
--------------------------------
# Makefile,v 1.6 2007/05/18 16:16:49 jba Exp
#
TOP = ../..

include $(TOP)/configure/CONFIG

PROD_HOST = msi
HTMLS = msi.html

msi_SRCS = msi.c
PROD_LIBS += Com
---------------------------------
I closed the firefox and nothing improved. Then I reboot the system and also the same.

I used the command 'lsof' after rebooting and this is what appears....

Yes, you have a lot of open files on your system... but was it really necessary to post them here on the forum?

The Makefile you posted above is incomplete, unless it can find at least one "rule".  Are you sure there is not more to the package that you are working with?  The Makefile wants to include a file called CONFIG that resides two-directories above the Makefile, in a directory called configure.

If you do not have this directory, then I would say that you have an incomplete package.

---

### Post by agilor on 2009-06-11
I did the right procedure to install the program and the "too many open files" message dissapeard.

How to  **install MSI for EPICS**. 
I summarize what I did to install it:
Since MSI (Macro Substitution and Include Tool) is an extension of EPICS, first I had to install the so called "extensions top" (download from [http://www.aps.anl.gov/epics/extensions/msi/index.php](http://www.aps.anl.gov/epics/extensions/msi/index.php)) file:extensionsTop_20070703.tar.gz

Go to the epics directory (I assume something like /home/epics) and
tar -zxvf extensionsTop_20070703.tar.gz

This creates the directory "extensions" which includes many subdirectories and files. Then

emacs /home/epics/extensions/configure/RELEASE

define the variables EPICS_BASE and EPICS_EXTENSIONS to the correct value. Ie:
EPICS_BASE=/home/epics/base-3.14.9/
EPICS_EXTENSIONS=/home/epics/extensions

 /home/epics/extensions/configure$ make

Download MSI file:msi1-5.tar.gz from the link above. You can use:
wget -N [http://www.aps.anl.gov/epics/downloa.../msi1-5.tar.gz]("http://www.aps.anl.gov/epics/download/extensions/msi1-5.tar.gz")
tar -zxvf msi1-5.tar.gz
It creates a directory called msi1-5, which you have to move to
 /home/epics**/**extensions/src/

emacs /home/epics**/**extensions/src/Makefile
and modify in the Makefile the EXTENSION_MSI variable to the name of the directory msi:
EXTENSION_MSI = msi1-5

/home/epics/extensions/src$ make

Thats it!
now, just to check that it works:
cd /home/epics/extensions/bin/linux-x86
msi --help

----------------------
Thanks a lot to everybody for your help

---

