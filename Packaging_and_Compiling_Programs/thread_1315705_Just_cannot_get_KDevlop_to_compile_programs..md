---
title: "Just cannot get KDevlop to compile programs."
date: 2009-11-05
forum: Packaging and Compiling Programs
---

### Post by Swerve1000 on 2009-11-05
Hi,

After having trouble trying to install KDevelop on Ubuntu version 9.04 due to it having libtool version 2.2.4 instead of the required version of 1.5.X.X, I installed version 8.0.4.3LTS.

However, after then installing KDevelop through Synaptic (including the dependencies it said were required) I still fail to be able to compile the basic 'Hello World' program. When I attempt to build I receive the following prompt:

> 
There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?


To which I select 'Yes'. But despite this I receive the following error:

> 
cd '/home/a/helloworldtest2' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/a/helloworldtest2/debug' && cd '/home/a/helloworldtest2/debug' && CXXFLAGS="-O0 -g3" "/home/a/helloworldtest2/configure" --enable-debug=full && cd '/home/a/helloworldtest2/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***


After looking for a solution, common suggestion is the following:

> 
You need to have aclocal (automake, autoconf and libtool) installed.


But upon running the following commands in the Terminal to see if they are installed:

> 
apt-cache showpkg automake
apt-cache showpkg autoconf
apt-cache showpkg libtool


I am lead to believe that I have the following versions installed:

> 
automake Versions: 1:1.10.1-2
autoconf Versions: 2.61-4 
libtool Versions: 1.5.26-1ubuntu1


But alas, I am still unable to compile programs. 

If anyone has any ideas I'd be really grateful if they could suggest them because I need to get this installed for a college class and so far it's been a total fail.

Thanks very much.

---

### Post by SevenMachines on 2009-11-05
Apologies if this is a silly question, but Versions in apt-cache showpkg does not mean that the package is installed, are you sure they're really installed?

$sudo apt-get install automake autoconf libtool
will make sure

$sudo apt-get install apt-show-version

$apt-show-versions automake autoconf libtool
autoconf/lucid uptodate 2.64-1ubuntu1
automake/lucid uptodate 1:1.11-1
libtool/lucid uptodate 2.2.6a-4

---

### Post by Swerve1000 on 2009-11-05
Hi there SevenMachines :)

No that wasn't a silly question at all! I thought it did!

I ran the
> 
$sudo apt-get install automake autoconf libtool


and it did show they weren't installed!

Here is what was shown in the Terminal:

> 
a@a-desktop:~$ sudo apt-get install automake autoconf libtool
[sudo] password for a: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic linux-headers-2.6.24-24
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autotools-dev libc6 libc6-dev libc6-i686 linux-libc-dev m4
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc glibc-doc
  manpages-dev gcj gfortran fortran95-compiler libtool-doc
Recommended packages:
  automaken libltdl3-dev
The following NEW packages will be installed
  autoconf automake autotools-dev libc6-dev libtool linux-libc-dev m4
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 7 newly installed, 0 to remove and 8 not upgraded.
Need to get 11.2MB of archives.
After this operation, 22.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y


So that seemed to work well and when I made a new Hello world program, it got much further this time:

> 
cd '/home/a/helloworldtest3' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/a/helloworldtest3/debug' && cd '/home/a/helloworldtest3/debug' && CXXFLAGS="-O0 -g3" "/home/a/helloworldtest3/configure" --enable-debug=full && cd '/home/a/helloworldtest3/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
aclocal
autoheader
automake
autoconf
installing -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
*** Exited with status: 77 ***


I really worried about messing up another installation, but what would you suggest I do now?

Some commands I have tried:

> 
a@a-desktop:~$ which gcc
/usr/bin/gcc
a@a-desktop:~$ 


> 
a@a-desktop:~$ which g++
a@a-desktop:~$ 



> 

a@a-desktop:~$ sudo apt-get install build-essential
[sudo] password for a: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-24-generic linux-headers-2.6.24-24
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libstdc++6-4.2-dev libtimedate-perl patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.2 libstdc++6-4.2-dev libtimedate-perl
  patch
0 upgraded, 7 newly installed, 0 to remove and 8 not upgraded.
Need to get 4664kB of archives.
After this operation, 17.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 


> 
a@a-desktop:~$ apt-show-versions automake autoconf libtool
autoconf/hardy uptodate 2.61-4
automake/hardy uptodate 1:1.10.1-2
libtool/hardy uptodate 1.5.26-1ubuntu1
a@a-desktop:~$ 



Do any of those commands help showing what the issue maybe? Should I install 'build-essential' do you think?

I REALLY am most grateful for this help.

---

### Post by SevenMachines on 2009-11-05
yes, build-essential is, well... essential! mainly because it brings in libc6-dev, which is 'the key' development library if you want to start compiling things.

---

### Post by Swerve1000 on 2009-11-05
It works!!!!!!!!

Thank you ever so much SevenMachines for helping me out. 

I need to get this working for a class and most of the class was having this problem as well, so I'm sure all of them would like to pass on their thanks as well.

massiveThumbsUp.jpg

:)


//--------------

Note to self:

Had to also install Konsole, using:

> sudo apt-get install konsole

The program's output can then be viewed in the Application window.

---

### Post by SevenMachines on 2009-11-05
just to add, you'll probably want to install g++ as well

---

### Post by SevenMachines on 2009-11-05
glad to hear it works :) happy compiling!

---

### Post by Swerve1000 on 2009-11-05
Thanks buddy! :)

---

