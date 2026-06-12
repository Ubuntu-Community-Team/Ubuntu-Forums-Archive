---
title: "HOWTO: Installing Intel C++ Compiler 10 on Ubuntu 7.04"
date: 2007-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by szr4321 on 2007-06-06
Unfortunately, the Intel C++ Compiler 10 is not officially supported on Ubuntu 7.04 and the install script didn't work for me.

There's also an [official Intel site]("http://www.intel.com/support/performancetools/sb/CS-025939.htm") describing the installation on Ubuntu 7.04.

*Update*: Nuverde posted that the script worked for him after installing the rpm package:
```

sudo apt-get install rpm

```

He also needed to set
```

export LANG=C

```

You might also need to install 32-bit libraries for the 64-bit version, see below.

If this does not work for you, try the manual install:

I've tried this on an 32-bit architecture. I'll assume that you've already downloaded the correct archive for your architecture from the Intel website.

In the code below, I've used an non-commercial license file. Please adjust all the filenames as necessary. This only installs the compiler. Probably, a similar approach works for the debugger as well, but I didn't try.

First make sure you have the GNU C++ Compiler installed:
```
sudo apt-get install build-essential
```
From the [Intel Compiler Forums](http://softwarecommunity.intel.com/isn/Community/en-US/forums/permalink/30235699/30235702/ShowThread.aspx#30235702): If you are using the 64-bit cce compiler, you will need working installations of both 32- and 64-bit g++.  For starters, both
```
g++ -v -print-search-dirs
``` and ```
g++ -m32 -v -print-search-dirs
```
should work, and give versions in the supported range.

Extract the archive:
```
tar xfzv l_cc_p_10.0.023_ia32.tar.gz
```
We need to convert the RPM to a debian package using alien:
```

sudo apt-get install alien
cd l_cc_p_10.0.023_ia32/data
sudo alien -cv intel-icc100023-10.0.023-1.i386.rpm

```
We can now install the debian package:
```
sudo dpkg -i intel-icc100023_10.0.023-2_i386.deb
```
Now we need to copy our license file to the appropriate directory:
```

sudo mkdir -p /opt/intel/licenses
sudo cp /your/license/path/NCOM_L_CMP_CPP_NB96-WLC77F6B.lic /opt/intel/licenses

```
Finally, we need to adjust some strings in the executable scripts:
```

cd  /opt/intel/cc/10.0.023/bin
sudo perl -pi -w -e 's/!\/bin\/sh/!\/bin\/bash/g;' *.sh icc icpc
sudo perl -pi -w -e 's/<INSTALLDIR>/\/opt\/intel\/cc\/10.0.023/g;' *.sh icc icpc

```
For the **64-bit version** the last substitution looks slightly different (thanks, silasgreenback) because of the different installation path:
```

sudo perl -pi -w -e 's/<INSTALLDIR>/\/opt\/intel\/cce\/10.0.023/g;' *.sh icc icpc

```
silasgreenback also noted: You will need to do the same on the debugger if you install it, in particular the files "idb" and "idbvars.sh".

To run the **64-bit version** version you will also need to install the 32-bit libstdc++ packages (thanks, silasgreenback and sundeep):
```

sudo apt-get install ia32-libs lib32stdc++6 libstdc++5

```
To have the compiler directories in the path environment variable, execute
```
. ./iccvars.sh
```
Now, try
```
icc --version
```
You should see some output like
```
icc (ICC) 10.0 20070426
```
If you get the error
```

icc: error #10001: could not find directory in which g++ resides

```
you might have to set your LC_ALL environment variable (thanks, xilef):
```

export LC_ALL=C

```
Finally, if you want to have the compiler in the path all the time, append to your ~/.bashrc
```
source /opt/intel/cc/10.0.023/bin/iccvars.sh
```

To uninstall, simply select the appropriate intel package in synaptic.

Use this guide at your own risk. However, please post if you can enhance this Howto.

---

### Post by madmetal on 2007-06-07
just one question..  its the new compiler with multi-core optimisation?

---

### Post by szr4321 on 2007-06-07
> **madmetal said:**
> just one question..  its the new compiler with multi-core optimisation?
Yes, exactly. You can read more about the new features [here]("http://www.intel.com/cd/software/products/asmo-na/eng/compilers/clin/277618.htm#new").

---

### Post by xilef on 2007-06-09
I followed your HOWTO but I had this error while running *icc --version:*

```

icc: error #10001: could not find directory in which g++ resides

```

---

### Post by szr4321 on 2007-06-11
> **xilef said:**
> I followed your HOWTO but I had this error while running *icc --version:*

```

icc: error #10001: could not find directory in which g++ resides

```
Have you installed the g++ compiler? You might want to try the following:
```
sudo apt-get install build-essential
```

---

### Post by silasgreenback on 2007-06-12
I had to change things slightly when installing the x86-64 version of the compiler.

Follow instructions as above, but change search and replace code to:

sudo perl -pi -w -e 's/\/bin\/sh/\/bin\/bash/g;' *.sh
sudo perl -pi -w -e 's/\/bin\/sh/\/bin\/bash/g;' icc
sudo perl -pi -w -e 's/\/bin\/sh/\/bin\/bash/g;' icpc

sudo perl -pi -w -e 's/<INSTALLDIR>/\/opt\/intel\/cce\/10.0.023/g;' *.sh
sudo perl -pi -w -e 's/<INSTALLDIR>/\/opt\/intel\/cce\/10.0.023/g;' icc
sudo perl -pi -w -e 's/<INSTALLDIR>/\/opt\/intel\/cce\/10.0.023/g;' icpc

Note the extra 'e' in the path in the 64-bit version. Also note that search and replace on all the files as in the original post appeared to corrupt my binaries. You will need to do the same on the debugger if you install it, in particular the files "idb" and "idbvars.sh".

To run the x86-64 version you will also need to install the 32-bit libstdc++ packages, I installed:

'lib32stdc++6'
'libstdc++5'

although the latter is probably not necessary. If you don't install these you get an error like:
"ipcpbin: No such file or directory"

when you try to run the binary.

Thanks go to people on the Intel forum for helping me solve this last problem.

---

### Post by sundeep on 2007-06-13
will the same procedure work for intel fortran 10 compiler on ubuntu feisty x86_64, 
 or what modifications have to be done

---

### Post by silasgreenback on 2007-06-14
You will probably need to change all instances of "cce" in the search and replace string for whatever the Fortran compiler's name is abbreviated to, "ffe"?

Of course, the names of the scripts on which to do the search and replace will also be different.

---

### Post by jhollett66 on 2007-06-14
Hate to be too much of a dummy, but could you elaborate on the fortran compiler installation(64bit)

sorry

---

### Post by jhollett66 on 2007-06-14
I install the debian package, then I perform the perl substitutions on the files: *.sh, ifort, and ifortbin.  When i try the version step this is what I get

/opt/intel/fce/10.0.023/bin/ifort: line 40: /opt/intel/fce/10.0.023/bin/ifortbin: No such file or directory
/opt/intel/fce/10.0.023/bin/ifort: line 40: /opt/intel/fce/10.0.023/bin/ifortbin: Success

what does it mean?

---

### Post by jhollett66 on 2007-06-14
Thanks, forget it, I installed those libraries and just ran the perl sub on *.sh and ifort

Thanks

---

### Post by meatpan on 2007-06-14
A great guide for a great compiler.   Unfortunately, I cannot use the intel compiler unless I pay a fee, since I am employed in academia and would be using this at work.  Here is an FAQ regarding the extremely restrictive license: [http://www.intel.com/cd/software/products/asmo-na/eng/219692.htm](http://www.intel.com/cd/software/products/asmo-na/eng/219692.htm)

---

### Post by jhollett66 on 2007-06-16
I thought everything had installed correctly, but after following the previous instructions(for ubuntu 64bit) I get the following error when compiling code.

/opt/intel/fce/10.0.023/bin/fortcom: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ifort: error #10257: Fatal error in /opt/intel/fce/10.0.023/bin/fortcom, terminated by 0x7f

any ideas?

---

### Post by sundeep on 2007-06-16
had the same problem

solved by installing ia32-libs by the following command

sudo apt-get install ia32-libs

---

### Post by jhollett66 on 2007-06-16
That did it.  Thanks very much for the tip, I should email you a beer.

When I compile my code I get a message "column count incorrect".  It may be something for another forum but do you know what this means?

Also how do I get rid of having to put ./ in front of executables?

Thanks

---

### Post by szr4321 on 2007-06-17
> **silasgreenback said:**
> I had to change things slightly when installing the x86-64 version of the compiler. [...]Thanks a lot for posting! I've updated the HowTo.

---

### Post by szr4321 on 2007-06-17
> **sundeep said:**
> had the same problem

solved by installing ia32-libs by the following command

sudo apt-get install ia32-libs
Thanks! I've added this as well.

---

### Post by szr4321 on 2007-06-17
> **jhollett66 said:**
> Also how do I get rid of having to put ./ in front of executables?You need to adjust your PATH environment variable to contain your current working directory:```
export PATH="${PATH}:"
```
(the colon followed by no directory is treated as the current working directory.)

---

### Post by Nuverde on 2007-06-18
SHORT VERSION:  standard install script mostly worked for me with no changed if I installed 'rpm' using apt first.

Just thought I would chime in with my experience.  I am running Kubuntu 7.04 64-bit on an Intel CPU.  I had already installed the 32bit Swiftfox and plugins using Automatix, so the ia32 libs were already installed.  (I assume this is where they got installed).  

Anyway, I downloaded the intel64 version of the compiler since I am just working with code for myself and don't need to target 32 bit platforms right now.  I installed the 'rpm' package using apt.  I then just ran the install script as root.  I did get a warning about Ubuntu not being a supported distro.  I also got warnings about it not finding 32 bit versions (I think) of libstdc++, libgcc and glibc.  But I just plugged along with the install.  After sourcing the iccvars.sh script, I tried to compile a simple 'hello world' but got an error...

Catastrophic error: could not set locale "" to allow processing of multibyte characters

Well, I had seen this before with other versions of the compiler, so I just added this to my .bashrc...

export LANG=C

Now if I 'icc test.c' it works great.  Also, 'icc -O3 test.c' works.  BUT 'icc -fast test.c' works, but when you run the new binary, I get an error like this...

Fatal Error: This program was not built to run on the processor in your system.
The allowed processors are: Intel(R) Core(TM) Duo processors and compatible Intel processors with supplemental Streaming SIMD Extensions 3 (SSSE3) instruction support.

So, I was able to use the standard install script by just adding a package with apt and adding a line to my .bashrc.  Of course, lets see what happens when I try to compile a real program.

---

### Post by szr4321 on 2007-06-18
> **Nuverde said:**
> standard install script mostly worked for me with no changed if I installed 'rpm' using apt first.

Thanks for posting! I will include this in the HowTo.
> **Nuverde said:**
> 
Now if I 'icc test.c' it works great.  Also, 'icc -O3 test.c' works.  BUT 'icc -fast test.c' works, but when you run the new binary, I get an error like this...

Fatal Error: This program was not built to run on the processor in your system.
The allowed processors are: Intel(R) Core(TM) Duo processors and compatible Intel processors with supplemental Streaming SIMD Extensions 3 (SSSE3) instruction support.

That's because "-fast" currently enables "-xT -O3 -ipo -no-prec-div -static". And "-xT" means to generate specialized code to run exclusively on Intel(R) Core(TM)2 Duo processors, Intel(R) Core(TM)2 Quad processors, and Intel(R) Xeon(R) processors with SSSE3. For more info, try
```

icc --help | less

```

---

### Post by Nuverde on 2007-06-18
> **szr4321 said:**
> Thanks for posting! I will include this in the HowTo.

That's because "-fast" currently enables "-xT -O3 -ipo -no-prec-div -static". And "-xT" means to generate specialized code to run exclusively on Intel(R) Core(TM)2 Duo processors, Intel(R) Core(TM)2 Quad processors, and Intel(R) Xeon(R) processors with SSSE3. For more info, try
```

icc --help | less

```

Ah... this must be a change from the 9.1 compilers... -fast worked for me fine before on the same system.   I have a dual core 930D... but not a Core Duo.

Thanks!

---

### Post by nikki on 2007-06-18
I interestingly enough got an error right at build-essential

> sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages


---

### Post by szr4321 on 2007-06-18
> **nikki said:**
> I interestingly enough got an error right at build-essential
It seems that some of your packages are broken. You might want to try
```
apt-get --fix-broken install
```

---

### Post by xilef on 2007-06-20
I did everything in thhis howTo and have the same error

```

felix@felix-laptop:/opt/intel/cc/10.0.023/bin$ icc --version
icc: error #10001: could not find directory in which g++ resides

```

Yes I have g++ installed:

```
felix@felix-laptop:/opt/intel/cc/10.0.023/bin$ g++ --version
g++ (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright © 2006 Free Software Foundation, Inc.
Ce logiciel est libre; voir les sources pour les conditions de copie.  Il n'y a PAS
GARANTIE; ni implicite pour le MARCHANDAGE ou pour un BUT PARTICULIER.
```

I also have build-essential and such since I develop on this computer since a long time.

Any clues of why I got this error ? Here's my icc script:

```

#!/bin/bash

if [ -z "${INTEL_LICENSE_FILE}" ]
then
 INTEL_LICENSE_FILE="/opt/intel/cc/10.0.023/licenses:/opt/intel/licenses:${HOME}/intel/licenses:/Users/Shared/Library/Application Support/Intel/Licenses";
else
 INTEL_LICENSE_FILE="${INTEL_LICENSE_FILE}:/opt/intel/cc/10.0.023/licenses:/opt/intel/licenses:${HOME}/intel/licenses:/Users/Shared/Library/Application Support/Intel/Licenses";
fi
export INTEL_LICENSE_FILE;

if [ -z "${LD_LIBRARY_PATH}" ]
then 
 LD_LIBRARY_PATH="/opt/intel/cc/10.0.023/lib";
else
 LD_LIBRARY_PATH="/opt/intel/cc/10.0.023/lib:${LD_LIBRARY_PATH}";
fi
export LD_LIBRARY_PATH;

# DYLD_LIBRARY_PATH is used on MAC OS
if [ -z "${DYLD_LIBRARY_PATH}" ]
then 
 DYLD_LIBRARY_PATH="/opt/intel/cc/10.0.023/lib";
else
 DYLD_LIBRARY_PATH="/opt/intel/cc/10.0.023/lib:${DYLD_LIBRARY_PATH}";
fi
export DYLD_LIBRARY_PATH;

if [ -z "${PATH}" ]
then
 PATH="/opt/intel/cc/10.0.023/bin";
else
 PATH="/opt/intel/cc/10.0.023/bin:${PATH}";
fi
export PATH;

export -n IA32ROOT; unset IA32ROOT;

#if [ $# != 0 ]
#then
# exec -a "/opt/intel/cc/10.0.023/bin/icc" /opt/intel/cc/10.0.023/bin/iccbin "$@";
#else
# exec -a "/opt/intel/cc/10.0.023/bin/icc" /opt/intel/cc/10.0.023/bin/iccbin;
#fi
exec -a "/opt/intel/cc/10.0.023/bin/icc" /opt/intel/cc/10.0.023/bin/iccbin "$@";

```

---

### Post by nikki on 2007-06-20
> **szr4321 said:**
> It seems that some of your packages are broken. You might want to try
```
apt-get --fix-broken install
```

That fixed it =)

Edit: Figured it out.

---

### Post by szr4321 on 2007-06-21
> **xilef said:**
> I did everything in thhis howTo and have the same error
```

felix@felix-laptop:/opt/intel/cc/10.0.023/bin$ icc --version
icc: error #10001: could not find directory in which g++ resides

```
Yes I have g++ installed: [...]
I've found a post on the Intel forums that might be related: [http://softwarecommunity.intel.com/isn/Community/en-US/forums/permalink/30235699/30235699/ShowThread.aspx#30235699](http://softwarecommunity.intel.com/isn/Community/en-US/forums/permalink/30235699/30235699/ShowThread.aspx#30235699)
However, to me it seems you're trying to install the 32-bit version, right?

Does
```
g++ -v -print-search-dirs
```
and
```
g++ -m32 -v -print-search-dirs
```
return reasonable output?

There's also [this](http://www.intel.com/support/performancetools/sb/CS-025939.htm) document describing the installation on Ubuntu 7.04.

---

### Post by xilef on 2007-06-21
Thank you for your help. Setting the env. var. LC_ALL to C fixed my problem. Here's the trick:

```

export LC_ALL=C
icc --version

```

Now it gives me:

```

felix@felix-laptop:~$ icc --version
icc (ICC) 10.0 20070426
Copyright (C) 1985-2007 Intel Corporation.  All rights reserved.

```

:D

---

### Post by szr4321 on 2007-06-21
> **xilef said:**
> Thank you for your help. Setting the env. var. LC_ALL to C fixed my problem. Here's the trick:
```

export LC_ALL=C

```

Thanks! I've updated the HowTo.

---

