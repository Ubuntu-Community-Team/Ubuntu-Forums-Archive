---
title: "gcc 4.4 (any subversion) in Ubuntu 9.04?"
date: 2009-12-07
forum: Packaging and Compiling Programs
---

### Post by butsam on 2009-12-07
I currently have Ubuntu 2009-April (9.04) installed, and I looked in the repository for gcc 4.4 and did not see it there.

When I grabbed the Binary, I got lost in some of the techno-speak for what to do.

So, my first question is whether there is a prepackaged install in Synaptic yet for gcc 4.4? (Perhaps I just need to add a repository?)

If not, I need to get gfortran 4.4 working on my machine, which is a 64-bit machine. I got the appropriate binaries, but it is not clear to me what to do with them, and the instructions I found seemed out-of-date (referring to gcc-trunk, which was not in the tar file I retrieved). When I try running gfortran to actually compile a program I get a shared library error, so I am doing something wrong.

So, how do you go about getting gcc 4.4 installed on Ubuntu 9.04?

Thanks,

Sam

---

### Post by MadCow108 on 2009-12-07
the easiest would be to install karmic (9.10)
it has gcc 4.4.1 in its main repo

this ppa has 4.4.2 in it
[https://launchpad.net/~ubuntu-toolchain-r/+archive/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/test)
but it may have negative effects on your system stability because it also updates the libraries

---

### Post by snowpine on 2009-12-07
Hi ButSam, gcc 4.4 is not in Ubuntu 9.04 because it came out in April 2009, therefore there was no time to test it for inclusion in 9.04.

For the average Ubuntu user, the easiest way to have the latest applications is to use the current Ubuntu release (currently 9.10).

Motivated users can of course install newer versions of apps into an older version of Ubuntu (at their own risk), for example: [http://gcc.gnu.org/install/index.html](http://gcc.gnu.org/install/index.html)

---

### Post by alexkaz on 2010-01-02
SOLUTIONS for GNU-GCC and GNU-G++ INSTALL: 
SOLUTIONS for GCC and G++ test script hello.c and hello.cpp. 

Thank you for everyone's assitance over some pretty naive errors (guess that's the only way to learn something new). 

A suggestion for Ubuntu is to add the simple instructions to a download and install common software posting, for specific software, i.e. GCC. 

Here are the solutions to be shared: 

1. My installation of GCC and G++ were chaotic because I coudn't get the ./configure command to work as provided by the GNU GCC Homepage that provides instructions. 
Fortunately, the Ubuntu Software Center makes downloading the software and installing it easier than the GNU Homepage Instructions. Also the Synaptic Package Manager simplifies finding  and verifying the correct package versions for the 'build'. 

Summary:  Just use the Ubuntu SW Ctr to download and install, then the Synaptic Mgr for finding the most current upgrades and explanations for the file functions. 


2. The gcc and g++ would not find the gcc or g++ file until a symbolic link was created between the folder with code and the gcc-4.4.2 folder. 

Also the failing to code the differences between hello.c and hello.cpp prevented their compilation. .c uses #include "stdio.h" and .cpp uses #include <iostream> for
printf("hello\n"); //.c version and using namespace std cout << 'hello\n'; //.cpp version.

---

