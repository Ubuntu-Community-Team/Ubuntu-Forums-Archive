---
title: "Intel C++ Compiler, installation failed"
date: 2006-05-20
forum: Programming Talk
---

### Post by peter_kk on 2006-05-20
Hi,

I was trying to install Intel C++ Compiler 9.0, but it displayes me Installation failed at the end...

I have login to root account, i have unpack tar file with icc, i have run ./install.sh

i have type 1, i have type 1 and i have type my license number.

Later i got this:

```

Checking RPM version ...

Checking Dependencies ...
Checking Kernel and glibc dependencies ...

install_cc.sh can't identify your machine type, glibc, or kernel.

This product is supported for use with the following combinations   :

    Machine Type                Kernel  glibc

1.  IA-32/EM64T                 2.4.x   2.2.5
    IA-32/EM64T                 2.4.x   2.2.4
    IA-32/EM64T                 2.4.x   2.2.93
    IA-32/EM64T                 2.4.x   2.3.2
    IA-32/EM64T                 2.6.x   2.3.x
    IA-32/EM64T                 2.6.x   2.4.x

x.  Exit

If you would you like to perform an unsupported install of this product, enter the number corresponding to the platform most similar to yours. Otherwise, enter "x" to exit   :    

```

I'm typing 1 to continue. Btw: My PC is 32bit Intel Centrino 1.6MHz and my operating system is the latest kubuntu beta 2, and uname -r = 2.6.15-23-386

After that i'm typing the Typical Install (i have try also Custom Install but this also don't work)

Later i'm asked for agree the license terms and conditions.

Later i'm choosing the installation paths (i'm choosing the defaults)

Instantly after that...

```

--------------------------------------------------------------------------------
Substitute Headers for Intel(R) C++ Compiler for 32-bit applications, Version 9.0
Installing...
Installation successful.
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
Intel(R) C++ Compiler for 32-bit applications, Version 9.0
Installing...
Installation failed.
--------------------------------------------------------------------------------


```

Btw:I don't see any log files in the unpacked folder.

Could anyone help me?

Greets&Thanks
Peter_K

---

### Post by cgjones on 2006-05-20
I believe that IA-32 refers to the Intel Itanium 32 bit processor, and EM64T refers to Intel's 64 bit processor. So in either case, I would assume that your processor isn't supported. Did they have a version that matched your processor?

---

### Post by Virak on 2006-05-20
[quote=cgjones]I believe that IA-32 refers to the Intel Itanium 32 bit processor, and EM64T refers to Intel's 64 bit processor. So in either case, I would assume that your processor isn't supported. Did they have a version that matched your processor?[/quote]IA-32 is another name for the x86 architecture.

---

### Post by cgjones on 2006-05-21
[QUOTE=Virak]IA-32 is another name for the x86 architecture.[/QUOTE]

Dang, I must of been thinking of the IA-64.

---

### Post by peter_kk on 2006-05-21
ok, ok, so who can help me?

---

### Post by hod139 on 2006-05-24
Maybe the user interface is bad.  Have you tried entering 5 instead of 1?  I am thinking that you have the following setup:
```
 Machine Type         Kernel       glibc
  IA-32/EM64T          2.6.x         2.3.x
``` 
which would correspond to number 5 is the menu enumeration continued.

---

### Post by peter_kk on 2006-05-24
Unfortunately options 5 & 6 dont work :( Install.sh is saying me instantly "Incorrect option"

---

### Post by hod139 on 2006-05-24
Have you installed the build-essential package?  I think intel's compiler depends on some of that stuff.

---

### Post by alin.elena on 2006-05-30
Hi,

I am afraid that I have to join your club.
I was not able to install intel compilers on my ubuntu 6.0.6 LTS box.
If I follow this post [http://ubuntuforums.org/showthread.php?t=89571](http://ubuntuforums.org/showthread.php?t=89571)
I finish in the same point as mentioned above.
There is another post [http://www.ubuntuforums.org/archive/index.php/t-149579.html](http://www.ubuntuforums.org/archive/index.php/t-149579.html).
The result is more or less the same ./make9 the script suggested finishes with unexpected end.

Any idea how to install it?


Alin

---

### Post by alin.elena on 2006-05-30
Hi

first i suppose that you have the *.lic files.
i have created /opt/intel/licenses and I have copied the *.lic files there.

then 

```
tar xvf l_cc_c_9.0.031.tar.gz
```
went to 
```
cd l_cc_c_9.0.031
```
then
```

sudo alien -k intel-icc9-9.0-031.i386.rpm
sudo alien -k intel-iidb9-9.0-036.i386.rpm
sudo alien -k intel-isubh9-9.0-031.i386.rpm

```
the instalation bit
```

sudo dpkg -i intel-*.deb

```
now we are alomst done with C\C++, and idb

now  C/C++

in /opt/intel/cc/9.0/bin
I edited icc icpc and iccvars.sh
be sure that INTEL_LICENSE_FILE points to /opt/intel/licenses (remove the <INSTALLDIR>/licenses  bit)
a license part in my case looks like

```

if [ -z "${INTEL_LICENSE_FILE}" ]
then
        INTEL_LICENSE_FILE="/opt/intel/licenses:${HOME}/intel/licenses"; export INTEL_LICENSE_FILE
else
        INTEL_LICENSE_FILE="${INTEL_LICENSE_FILE}:/opt/intel/licenses:${HOME}/intel/licenses"; export INTEL_LICENSE_FILE
fi

```

for the rest I have replaced <INSTALLDIR> with /opt/intel/cc/9.0

now the debugger
```

cd /opt/intel/idb/9.0/bin
```
I changed idbvars.sh to look like
```
#! /bin/sh

if [ -z "${PATH}" ]
then
    PATH="/opt/intel/idb/9.0/bin"; export PATH
else
    PATH="/opt/intel/idb/9.0/bin:$PATH"; export PATH
fi

if [ -z "${MANPATH}" ]
then
    MANPATH="/opt/intel/idb/9.0/man":$(manpath); export MANPATH
else
    MANPATH="/opt/intel/idb/9.0/man:${MANPATH}"; export MANPATH
fi

```

the idb should look like
```

#!/bin/bash
#
# Script to run the correct installed idb executable, depending on the
# platform.  This allows the user to simply type "idb" at command line
# regardless of platform.
#

MACHINE=`uname -m`
DIR=`dirname ${0}`

# If the machine is not Itanium(R), then it must be a variation on the 32 bit
# machine.
#
if [[ ${MACHINE} == "ia64" ]]; then
        IDB=${DIR}/eidb
else
    if [[ ${MACHINE} == "x86_64" && -e ${DIR}/idb-e ]]; then
        IDB=${DIR}/idb-e
    else
        if [[ ${MACHINE} == "i686" ]]; then
            export IDB_SAVE_LD_LIBRARY_PATH=${LD_LIBRARY_PATH}
            export IDB_SAVE_DYLD_LIBRARY_PATH=${DYLD_LIBRARY_PATH}
            export IDB_SAVE_DYLD_FRAMEWORK_PATH=${DYLD_FRAMEWORK_PATH}
            export IDB_SAVE_DYLD_ROOT_PATH=${DYLD_ROOT_PATH}
            export IDB_SAVE_DYLD_FALLBACK_LIBRARY_PATH=${DYLD_FALLBACK_LIBRARY_PATH}
            export IDB_SAVE_DYLD_FALLBACK_FRAMEWORK_PATH=${DYLD_FALLBACK_FRAMEWORK_PATH}
            export IDB_SAVE_DYLD_PATHS_ROOT=${DYLD_PATHS_ROOT}
            export IDB_SAVE_DYLD_IMAGE_SUFFIX=${DYLD_IMAGE_SUFFIX}
            export IDB_SAVE_DYLD_INSERT_LIBARIES=${DYLD_INSERT_LIBARIES}
        fi
        IDB=${DIR}/iidb
    fi
fi

if [[ -e ${IDB} ]]; then
    exec ${IDB} "$@"
else
    echo "Unable to find idb (${IDB})"
fi


```

probably the most important bit is

```

sudo ln -s /usr/lib/libXft.so.2 /usr/lib/libXft.so.1

```

for fortran compiler
the idea is more or less the same
```
tar xvf  l_fc_c_9.0.032.tar.gz
cd l_fc_c_9.0.032
sudo alien -k intel-ifort9-9.0-032.i386.rpm
sudo dpkg -i intel-*.deb

```

now you should have the fortran installed in /opt/intel/fc/9.0

i have changed ifortvars.sh like that
the INTEL_LICENSE_FILE part to look like

```


if [ -z "$INTEL_LICENSE_FILE" ]
then
 INTEL_LICENSE_FILE="/opt/intel/licenses";
else
 INTEL_LICENSE_FILE="$INTEL_LICENSE_FILE:/opt/intel/licenses";
fi
export INTEL_LICENSE_FILE;

```

in the rest of the file I have changed <INSTALLDIR> to /opt/intel/fc/9.0

I did the same with ifort file.

last bit

in my home directory I added this lines to .bashrc
```

#intel stuff
source /opt/intel/cc/9.0/bin/iccvars.sh
source /opt/intel/fc/9.0/bin/ifortvars.sh
source /opt/intel/idb/9.0/bin/idbvars.sh

```

Hope that helps,

Alin

---

### Post by peter_kk on 2006-06-01
Thanks for your help! Now ICC works fine on my PC :)

---

### Post by Omni-Vi on 2006-06-21
Hi All,
originally this post concernd the Intel Fortran Compiler, but it works for C++ Compiler as well. You will figure it out :-)

I had the same problem of not being able to install Intel Fortran Compiler under Dapper. The error was
...
install_fc.sh can't identify your machine type, glibc, or kernel.
...

Some of you had the same problem.
Solution:
The installation script install_fc.sh tries to determine the GLIBC version  within the function GET_SYSTEM_REQUIREMENTS () {...} with the following statement (lines 1506-1510):
```

if [ "$RPM_NOT_FOUND" = 0 ] ; then
  GLIBC="$(rpm -qa | egrep -e 'glibc-2\.2\.4' -e 'glibc-2\.2\.5' -e 'glibc-2\.2\.93' -e 'glibc-2\.3' -e 'glibc-2\.4' 2> /dev/null )"
else
  GLIBC="$(ls /lib/libc-* | grep -e '[.]so' | sed s@'\(.*\)\(\.so.*\)'@'\1'@g)"
fi

```
Now the thing is, if you are using Debian/Ubuntu and you have alien, you also have rpm. BUT the rpm database that holds a list of all installed packages under eg. SUSE is empty under Ubuntu, since it is not used.
Therefore, the GLIBC variable is left empty (rpm -qa gives back nothing). The second call (ls /lib/libc-...) should be used but is not since rpm is installed.

Okay, what do we do about it?
First of all, you can not uninstall rpm for alien depends on it. What we can do though, is to change the install_fc.sh script so that it does not use rpm. This is simple. Just go to line 226 in install_fc.sh (the IS_RPM_PRESENT () {} function) and look for
```
RPM_NOT_FOUND=$?
```.
Change it to
```
RPM_NOT_FOUND=1
```
and install.sh should work just fine. No need to convert any package by hand, the installer will do that for you.

I would be happy to hear if this works for you, I hope it will :D 
Ciao

Ps: The line numbers are for the Intel Fortran 9.1 Compiler. You might have to adapt them for 9.0 or C Compiler. Thats why I gave you the function names as well.

---

### Post by tom-tag on 2006-07-11
Thanks Omni-Vi!

That worked perfectly!

---

### Post by dsokus on 2006-07-27
Thanks, it's just worked for me too. :D

---

### Post by flightcrank on 2006-07-27
why not use the gnu compiler collection ?

---

### Post by dbw on 2006-07-27
For the first guy who started this thread - I just installed intel's fortran compiler, and I get the same list.  I think that you were going too deep, i.e., there are actually only two options on that list:

1: various architectures
x: cancel

The default script will only work if you have installed rpm, though.  Otherwise, check out [this link]("http://colt.projectgamma.com/intel/ixc-debian.html").

wrt flightcrank, some people find that intel's compilers produce faster code, especially if you are using an intel processor (i.e. compiler optimized for the processor)  I am using intel's fortran compiler because the support for fortran 90 & 95 is still pretty weak in the GNU world.

---

### Post by Vincosmo on 2006-08-03
there's no such trick for the Math Kernel Library under Dapper Drake

any idea how to get it working?

```

Where do you want to extract temporary files to? Specify directory starting with '/' [ /tmp/mkl ] :
Extracting...               ########################################################################################  [ 99%]

Extracting...               ######################################################################################### [100%]
ERROR: unable to find command 'rpm'.
Please add the location to the above commands to your PATH and re-run the script
Press Enter to continue.
Warning: It seems installation failed
Deleting temporary files...


```
:(

---

### Post by csc14us on 2006-08-16
> **flightcrank said:**
> why not use the gnu compiler collection ?

Because Intel's Fortran 90/95 compiler is extremely powerful in terms of runtime performance through its optimization technology.  And Intel Fortran, unlike gfortran, is basically fully debugged and provides all the features of the language necessary to compile and run legacy code.

---

### Post by dbw on 2006-08-22
@Vincosmo:
 do youhave "rpm" installed?  how about "alien"?

---

### Post by mwindham on 2006-08-22
I was able to install intel c++ on 6.0.6, but it complains that g++ not found. I am new to Ubuntu, and I used the sys-something to install gcc 3.4, 4.0, ... and now g++-3.4 and g++-4.0 are both on the system, and Nautilus does not seem to let me create links like it would on Fedora, and I anyway, I hope someone would suggest a good way to fix this without resorting to my usual suspect methods...

Thanks

---

### Post by cokhavim on 2006-08-29
thanks Omni-Vi!  that worked for me!

---

### Post by junglepeanut on 2006-09-02
Sometimes intels is faster sometimes it is not, I see different results many times for different problems. High memory, absoft seems to do best, multiple (greater than 4) processors intel is good, single processor varies widely between programs between gfortran intel, etc etc. Although on powerpc arch, I dont have a code yet that is running or compiling faster than gfortran on a 1vs1 or 2vs2 or 3vs3 etc single/multiple processor comparison. 

Things may be very different for your type of programming, as you always need the right tool for the job. Just trying to state one is not always better than another.

---

### Post by accsvv on 2006-09-27
> **junglepeanut said:**
> Sometimes intels is faster sometimes it is not, I see different results many times for different problems. High memory, absoft seems to do best, multiple (greater than 4) processors intel is good, single processor varies widely between programs between gfortran intel, etc etc. Although on powerpc arch, I dont have a code yet that is running or compiling faster than gfortran on a 1vs1 or 2vs2 or 3vs3 etc single/multiple processor comparison. 

Things may be very different for your type of programming, as you always need the right tool for the job. Just trying to state one is not always better than another.

Hi, I have intel Fortran 9.0 installation problem in Linux SuSe too. The error message comes out like this:
--------------------------------------------
Intel(R) Fortran Compiler for 32-bit applications, Version 9.0
Installing...
error reading header from package
cpio: premature end of archive
error reading header from package
cpio: premature end of archive
Installation Failed.
---------------------------------------------
Thanks!!:confused:

---

### Post by gcordoba on 2007-02-23
I got the wrong idea to update from dapper to edgy. Now I have an ugly screen, no fonts for emacs and ifort not longer works; 

gcordoba@xterm2:~$ ifort
export: 27: Illegal option -n
gcordoba@xterm2:~$ 

It seems to me that ifort is lost in the a jungle new library places.
Please, any idea?
Gustavo

---

### Post by gcordoba on 2007-02-24
I fixed the problem by following an advice for edgy install:
change in ifort and ifortvars.sh:
 #!/bin/sh

to

#!/bin/bash

Sorry for the cross-posting
Gustavo

---

### Post by OvelhaNegra on 2007-02-25
Alin.Elena,

Thanks for your post! It really have helped me a lot!

Have you ever tried intel fortran with ubuntu edgy 6.10? It seems that the instalation procedures that work fine with 6.06 has some tricky problems in 6.10...

Thanks once again!
ON

---

### Post by OvelhaNegra on 2007-02-25
[QUOTE=alin.elena;1069768]

Alin.Elena,

Thanks for your post! It really have helped me a lot!

Have you ever tried intel fortran with ubuntu edgy 6.10? It seems that the instalation procedures that work fine with 6.06 has some tricky problems in 6.10...

Thanks once again!
ON

---

### Post by gcordoba on 2007-02-25
Hi,
I installed ifort 9.0 in Dapper some months ago. Last week I took the very risky desition to update to edgy and I discover that ifort was not longer available ("invalid input option -n").
I change those lines in the files and it works in full (including the parallel option).

Maybe ifort 9.1 could be a bit better, but for me 9.0 is ok. (some times to be so brave is not a good advise...).
Best regards,
Gustavo

---

### Post by gcordoba on 2007-02-25
sorry, edgy 6.10, of course.
Gustavo

---

### Post by tuxfanben on 2007-03-28
I think that your problem is that the install requires rpm and is not using "--nodeps" so that it quietly fails because it thinks that there are a bunch of failed dependencies.  For example if I try to install the intel-icc91047-9.1.047-1.i386.rpm by hand, I get:

error: Failed dependencies:
        ld-linux.so.2 is needed by intel-icc91047-9.1.047-1.i386
        libc.so.6 is needed by intel-icc91047-9.1.047-1.i386
        libdl.so.2 is needed by intel-icc91047-9.1.047-1.i386
        libm.so.6 is needed by intel-icc91047-9.1.047-1.i386
        libpthread.so.0 is needed by intel-icc91047-9.1.047-1.i386
        libc.so.6(GLIBC_2.0) is needed by intel-icc91047-9.1.047-1.i386
        libc.so.6(GLIBC_2.1) is needed by intel-icc91047-9.1.047-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by intel-icc91047-9.1.047-1.i386
        libc.so.6(GLIBC_2.2) is needed by intel-icc91047-9.1.047-1.i386
        libdl.so.2(GLIBC_2.0) is needed by intel-icc91047-9.1.047-1.i386
        libdl.so.2(GLIBC_2.1) is needed by intel-icc91047-9.1.047-1.i386
        libpthread.so.0(GLIBC_2.0) is needed by intel-icc91047-9.1.047-1.i386
        libpthread.so.0(GLIBC_2.1) is needed by intel-icc91047-9.1.047-1.i386
        libpthread.so.0(GLIBC_2.2) is needed by intel-icc91047-9.1.047-1.i386
        libpthread.so.0(GLIBC_2.2.3) is needed by intel-icc91047-9.1.047-1.i386

If I run: rpm -Uvh --nodeps intel-icc91047-9.1.047-1.i386.rpm, the rpm is successfully installed.  Unfortunately, to be installed correctly, you need to use the install.sh script.  To make this work, edit the "install_cc.sh" file located in the "data" directory.  You should change DEFAULTOPTIONS='-U --replacefiles --force' to:
DEFAULTOPTIONS='-U --replacefiles --force --nodeps' (there is only one occurrence of this variable).  Then, run the install.sh script again and everything should work.

---

### Post by kuscsik on 2007-05-19
I wrote a short guide for feisty:

[http://kuscsik.blogspot.com/2007/05/install-intel-icc-on-ubuntu-feisty.html](http://kuscsik.blogspot.com/2007/05/install-intel-icc-on-ubuntu-feisty.html)

this worked for me.

---

### Post by gcordoba on 2007-05-21
Thanks for the tip
Gustavo

---

### Post by Iowan on 2011-01-06
Old thread...

---

