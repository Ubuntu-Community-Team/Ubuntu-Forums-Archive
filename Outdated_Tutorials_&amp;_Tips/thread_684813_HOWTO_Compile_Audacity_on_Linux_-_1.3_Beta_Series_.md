---
title: "HOWTO: Compile Audacity on Linux - 1.3 Beta Series on Ubuntu Gutsy"
date: 2008-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by ArtInvent on 2008-02-01
This will tell you how to install Audacity 1.3.4 onto Gutsy using the source code. You will be able to leave a previously installed version of Audacity on your system and still use that when desired. It should also help you compile the next version of Audacity when it is released.  Compiling is generally not for noobs, and not generally recommended if an up-to-date package is available. You should at least know what a repo is and know your way around the command line a bit. If you're up for a little challenge, however, dive in.

This HowTo may seem long winded but the actual steps taken are actually pretty easy. I just wanted to give a little in the way of theory for each step and not just issue a bunch of blind commands. This can be helpful if you run into trouble.

[SIZE="2"]BACKGROUND[/SIZE]

Audacity is a phenomenal piece of audio editing software with a peculiar development quirk. There are two lines of the software and have been for some time: the 1.2 'stable' series and the 1.3 'beta' series. The 1.3 series is by far the more capable, has been around for over two years, yet the developers insist on calling it 'beta' software and they never seem to release it as the real deal, even though it seems perfectly stable and refined for most of that time IMO.

On top of that, and perhaps because of it, the latest release of the 1.3 series is seldom available as a normal install package from repos, and even finding a .deb package for the latest Ubuntu is not possible. This version lag has been a constant problem ever since I've been using Audacity.

Next, if you settle for the older release and install an 8-month old version from the repos, it may not be compiled with all the options like mp3 and flac import and export.

In that light, I decided to try and shed my distaste of compiling from source and give it a go. It worked well and really wasn't that difficult and I have a fully-functional Audacity 1.3.4 on Gutsy with all the optional bells and whistles I need for the first time. Moreover, when the next 'beta' (sigh) is released, I will probably be well prepared to compile that post haste as well. 

Since I found a few scattered tips and tutorials on how to do this, I thought I would start a thread here that aims to be as complete as possible. 

Also note that these instructions likely work for any apt or Debian based distro. Also, I would appreciate it if people would correct any mistakes and add helpful bits, I can aim to edit the top post so others don't have to troll the whole thread for corrected instructions.

[SIZE="2"]1. INSTALL DEPENDENCIES[/SIZE]

99% of failed compiles are due to not having the right dependency packages installed. In order to compile, we need a number of runtime and development packages of the correct version. These run the gamut from user interface widgets to audio hardware enablers to codec libraries. It's quite a number of packages if you want full functionality, but when finished, much of it can be removed easily enough as Audacity doesn't need it all to actually run.

Make sure Universe and Multiverse repos are enabled, these should contain all the necessary packages.

First of all, if you've never tried to compile anything, you will need to install the Gnu C Compiler and some other stuff. The easiest way to do this is to install **build-essential** which should suffice.
```
sudo apt-get install build-essential
```

There is a way to have Ubuntu look for the required dependencies for a particular package and install them automatically. 

```
$ sudo apt-get build-dep audacity
```

A alternate way way is to get all the dependencies for Audacity is to just fire a shotgun at the whole thing from the command line using the code below. I have tried to list here all the dependencies I have found as a reference. If the above build-dep seems to work, you can forgo the following command. Don't worry if you already have some of these packages, the install routine will only install those you don't have already. 

```
$ sudo apt-get install cdbs gettext libasound2-dev libjack-dev libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers libtwolame0 libtwolame-dev libgtk-dev libwxgtk-dev twolame libasound2-dev libjack0.100.0-dev portaudio19-dev libgtk2.0-dev libsndfile libsndfile-dev libsamplerate libsamplerate0-dev libsoundtouch libsoundtouch-dev 
```

One of these two methods (or even both) should install all the packages. After this is finished GO BACK and read the output. If ANYTHING failed to install you must track it down and find it. There is no reason to proceed with the compile if a package is not present, it will waste lots of time. If the install routine can't find certain packages, you will have to make sure you have enough official or 3rd party repos enabled and track these down. I repeat: compiles fail because you don't have all the dependencies. 

[SIZE="2"]2. DOWNLOAD AUDACITY SOURCE CODE [/SIZE]

We want the latest officially released beta and not the CVS builds. The Audacity Linux source code is usually found here:

[B][URL="http://audacity.sourceforge.net/download/beta_source"]
http://audacity.sourceforge.net/download/beta_source[/URL][/B]

This can be downloaded as a compressed tarball in the tar.bz2 format. You will save this to your home folder and uncompress the archive. (I used Archive Manager.) You will end up with a folder called, which in my case is, "/audacity-src-1.3.4-beta".

[SIZE="2"]3. CONFIGURE[/SIZE]

Now we are ready to start the compile process. At the command line, change to the directory you just created, for instance -

```
$ cd ~/audacity-src-1.3.4-beta
```

Now we will start the lengthy configure. It's at this point that we will tell the compile to enable certain useful things like the ability to directly export and import FLAC, Ogg, MP3, MP2, ID3 tag writing that actually writes the tags, etc. Options are explained exhaustively if you run the command "./configure --help" but it's a little too much info for most mortals. Below is a pretty complete command you can run without trying to figure all this out for yourself. This step on my machine took about 3 minutes. 

```
$  ./configure --with-libvorbis --with-libflac --with-libid3tag --with-soundtouch
```

This should spit out a lot of messages, but if you get 'error' messages at the end, it failed probably because Step 1 didn't succeed in getting you all the dependencies. You will have to hunt these down by using the error messages which pretty much always indicate pretty clearly which package it couldn't find etc. After tracking these down and installing, you can run this command in the same directory over again until no errors appear. 

[SIZE="2"]4. MAKE[/SIZE]

The make command may also take 5 minutes or so, as this is the actual compile. Stare at the screen if you like watching grass grow. This will probably spit out a lot of 'warning' gobbledygook, but this should be okay. You just don't want any errors.

```
$ make 
```

[SIZE="2"]5. MAKE INSTALL [/SIZE]

The final step is to install the compiled program so it can be run. Now, you can either do this command as 'sudo' in which case it will install across the board to all users. Or you can leave out the 'sudo' and just install it in your home directory which is what I did. If you choose the latter, you will be able to leave the previous Audacity version on your computer that were installed from repos. You can use the same .audacity folder with all of your preferences etc and choose which version you want to run. I simply made a menu launcher with the location of my special compile folder, and now I can run either version. (There are alternate ways to achieve similar things, this is simply the way I chose.)

```
$ make install 
```

I actually got an error message at the end of this, but it only pertained to installing the program in /usr/bin/install which would make it a system wide program. Again, using 'sudo' in front of the command would make this go away. Trying to clarify the difference: without using 'sudo' in this step, if you just run the command 'audacity' from any directory except this one, you will be running the previous install of Audacity if you have one, not this compile, which is what I wanted. In my case I can either run the repo version 1.3.3 or this compile 1.3.4. You could also probably run the 1.2.x series from repos if you want without affecting this compile at all. In this way you can have any number of Audacity versions resident on your box and even compile different options for the same version in different directories. I'm boring you now so I'll stop.

[SIZE="2"]6. RUN[/SIZE]

Finished. Now there will be an 'audacity' file sitting in your folder. Double click on this or, _within the folder_ at the CLI, run the 'audacity' command. Test the program especially the import and export of various filetypes to make sure you have it all right. 

Make a shortcut, or menu item in the 'Sound and Video' section, for more convenience, making sure to specify the exact folder location.

[SIZE="2"]7. ADDITIONAL STUFF[/SIZE]

Now, if you want to use additional plugins like effects, beyond the 20 or so stock effects included in Audacity itself, which most of us do, you will need to install these separately. There are hundreds of these available. Most for Linux are in the LADSPA format and install easily system wide for any enabled audio program. The easiest way to find what's available is to open Synaptic and search for LADSPA. For instance: caps, cmt, ubuntustudio-audio-plugins, tap-plugins, swh-plugins. 

[SIZE="2"]8. CLEAN UP UNNECESSARY PACKAGES (optional)[/SIZE]

Since you may have downloaded a bunch of development packages in Step 1 that are likely useless now that the compile is finished, you can easily purge these since they should not be registered as dependencies for any runtime package. Make sure you test and run the program for quite a while to make sure it's as it should be. You can always hold off on this step indefinitely.

 If you want to conserve disk space do this. If disk space is less important and you want to be able to compile the next version of Audacity whenever that is issued, you can just leave it as is. Of course, new versions of Audacity may use newer versions of many of these packages like the WX widgets stuff so be aware.

The command to purge your system of the specific unnecessary dev packages is below.

```
$ sudo apt-get remove --purge libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libwxbase2.6-dev libwxgtk2.6-dev libtwolame-dev libgtk-dev libwxgtk-dev portaudio19-dev libgtk2.0-dev 
```

[SIZE="2"]9. MAKING A .DEB PACKAGE -?[/SIZE]

It all certainly begs the question of a .deb package. This would be the really intelligent thing to do, so that this could be sent to the good folks at GetDeb or even to a more official Ubuntu or third party repo. Why this is never done until 6 months after the latest version, I don't know. As a packaging noob I attempted to make my own .deb package using checkinstall. It resulted in a very small file that can't possibly be right. I have a bit to learn if I'm to become a package maintainer. If someone who knows the ins and outs of making .deb packages better than I would like to investigate and propose a solution, this would be very nice. Then only one of us would have to go through the above rigamarole, and the rest of us could just download a .deb or use Synaptic which is how the whole Ubuntu thing is meant to work.

[SIZE="2"]10. OTHER TUTORIALS[/SIZE]

I used two other web pages primarily and this HowTo is a synthesis and update of these efforts by others, thanks to their respective authors. 

[http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/]("http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/")
[http://ubuntuforums.org/showthread.php?t=419358]("http://ubuntuforums.org/showthread.php?t=419358")

[SIZE="2"]11. FEEDBACK[/SIZE]

I may have made mistakes in the above. I tried a few permutations and did some steps more than once, so this is a reconstruction of steps I took. If others would like to try this HowTo and test it, please leave some feedback if it worked or if I omitted a package or made a typo or my theory is just plain wrong.

AUDACIOUS!

---

### Post by 1GENNADIY1 on 2008-02-02
Helo!
I try to compile, but didn't have luck. This is bash:
```
cd audacity-src-1.3.4-beta
gennadiy@alla:~/Desktop/audacity-src-1.3.4-beta$ ./configure --with-libvorbis --with-libflac --with-libid3tag --with-soundtouch
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
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
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
gennadiy@alla:~/Desktop/audacity-src-1.3.4-beta$ ./configure --with-libvorbis --with-libflac --with-libid3tag
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
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
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
gennadiy@alla:~/Desktop/audacity-src-1.3.4-beta$ 

```
This is config.log:
```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure --with-libvorbis --with-libflac --with-libid3tag

## --------- ##
## Platform. ##
## --------- ##

hostname = alla
uname -m = i686
uname -r = 2.6.22-14-generic
uname -s = Linux
uname -v = #1 SMP Tue Dec 18 08:02:57 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1866: checking for gcc
configure:1882: found /usr/bin/gcc
configure:1893: result: gcc
configure:2131: checking for C compiler version
configure:2138: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2141: $? = 0
configure:2148: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2151: $? = 0
configure:2158: gcc -V >&5
gcc: '-V' option must have argument
configure:2161: $? = 1
configure:2184: checking for C compiler default output file name
configure:2211: gcc    conftest.c  >&5
configure:2214: $? = 0
configure:2252: result: a.out
configure:2269: checking whether the C compiler works
configure:2279: ./a.out
configure:2282: $? = 0
configure:2299: result: yes
configure:2306: checking whether we are cross compiling
configure:2308: result: no
configure:2311: checking for suffix of executables
configure:2318: gcc -o conftest    conftest.c  >&5
configure:2321: $? = 0
configure:2345: result: 
configure:2351: checking for suffix of object files
configure:2377: gcc -c   conftest.c >&5
configure:2380: $? = 0
configure:2403: result: o
configure:2407: checking whether we are using the GNU C compiler
configure:2436: gcc -c   conftest.c >&5
configure:2442: $? = 0
configure:2459: result: yes
configure:2464: checking whether gcc accepts -g
configure:2494: gcc -c -g  conftest.c >&5
configure:2500: $? = 0
configure:2599: result: yes
configure:2616: checking for gcc option to accept ISO C89
configure:2690: gcc  -c -g -O2  conftest.c >&5
configure:2696: $? = 0
configure:2719: result: none needed
configure:2743: checking how to run the C preprocessor
configure:2783: gcc -E  conftest.c
configure:2789: $? = 0
configure:2820: gcc -E  conftest.c
conftest.c:8:28: error: ac_nonexistent.h: No such file or directory
configure:2826: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:2859: result: gcc -E
configure:2888: gcc -E  conftest.c
configure:2894: $? = 0
configure:2925: gcc -E  conftest.c
conftest.c:8:28: error: ac_nonexistent.h: No such file or directory
configure:2931: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:2969: checking for grep that handles long lines and -e
configure:3043: result: /bin/grep
configure:3048: checking for egrep
configure:3126: result: /bin/grep -E
configure:3132: checking whether gcc needs -traditional
configure:3174: result: no
configure:3245: checking for g++
configure:3275: result: no
configure:3245: checking for c++
configure:3275: result: no
configure:3245: checking for gpp
configure:3275: result: no
configure:3245: checking for aCC
configure:3275: result: no
configure:3245: checking for CC
configure:3275: result: no
configure:3245: checking for cxx
configure:3275: result: no
configure:3245: checking for cc++
configure:3275: result: no
configure:3245: checking for cl.exe
configure:3275: result: no
configure:3245: checking for FCC
configure:3275: result: no
configure:3245: checking for KCC
configure:3275: result: no
configure:3245: checking for RCC
configure:3275: result: no
configure:3245: checking for xlC_r
configure:3275: result: no
configure:3245: checking for xlC
configure:3275: result: no
configure:3303: checking for C++ compiler version
configure:3310: g++ --version >&5
./configure: line 3311: g++: command not found
configure:3313: $? = 127
configure:3320: g++ -v >&5
./configure: line 3321: g++: command not found
configure:3323: $? = 127
configure:3330: g++ -V >&5
./configure: line 3331: g++: command not found
configure:3333: $? = 127
configure:3336: checking whether we are using the GNU C++ compiler
configure:3365: g++ -c   conftest.cpp >&5
./configure: line 3366: g++: command not found
configure:3371: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| #ifndef __GNUC__
|        choke me
| #endif
| 
|   ;
|   return 0;
| }
configure:3388: result: no
configure:3393: checking whether g++ accepts -g
configure:3423: g++ -c -g  conftest.cpp >&5
./configure: line 3424: g++: command not found
configure:3429: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3461: g++ -c   conftest.cpp >&5
./configure: line 3462: g++: command not found
configure:3467: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3500: g++ -c -g  conftest.cpp >&5
./configure: line 3501: g++: command not found
configure:3506: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3528: result: no
configure:3556: checking how to run the C++ preprocessor
configure:3592: g++ -E  conftest.cpp
./configure: line 3593: g++: command not found
configure:3598: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:3592: g++ -E  conftest.cpp
./configure: line 3593: g++: command not found
configure:3598: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:3592: /lib/cpp  conftest.cpp
cpp: error trying to exec 'cc1plus': execvp: No such file or directory
configure:3598: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:3592: /lib/cpp  conftest.cpp
cpp: error trying to exec 'cc1plus': execvp: No such file or directory
configure:3598: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:3668: result: /lib/cpp
configure:3697: /lib/cpp  conftest.cpp
cpp: error trying to exec 'cc1plus': execvp: No such file or directory
configure:3703: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:3697: /lib/cpp  conftest.cpp
cpp: error trying to exec 'cc1plus': execvp: No such file or directory
configure:3703: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:3765: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=no
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_JACK_CFLAGS_set=
ac_cv_env_JACK_CFLAGS_value=
ac_cv_env_JACK_LIBS_set=
ac_cv_env_JACK_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBMAD_CFLAGS_set=
ac_cv_env_LIBMAD_CFLAGS_value=
ac_cv_env_LIBMAD_LIBS_set=
ac_cv_env_LIBMAD_LIBS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_LIBTWOLAME_CFLAGS_set=
ac_cv_env_LIBTWOLAME_CFLAGS_value=
ac_cv_env_LIBTWOLAME_LIBS_set=
ac_cv_env_LIBTWOLAME_LIBS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_SAMPLERATE_CFLAGS_set=
ac_cv_env_SAMPLERATE_CFLAGS_value=
ac_cv_env_SAMPLERATE_LIBS_set=
ac_cv_env_SAMPLERATE_LIBS_value=
ac_cv_env_SNDFILE_CFLAGS_set=
ac_cv_env_SNDFILE_CFLAGS_value=
ac_cv_env_SNDFILE_LIBS_set=
ac_cv_env_SNDFILE_LIBS_value=
ac_cv_env_SOUNDTOUCH_CFLAGS_set=
ac_cv_env_SOUNDTOUCH_CFLAGS_value=
ac_cv_env_SOUNDTOUCH_LIBS_set=
ac_cv_env_SOUNDTOUCH_LIBS_value=
ac_cv_env_VAMP_CFLAGS_set=
ac_cv_env_VAMP_CFLAGS_value=
ac_cv_env_VAMP_LIBS_set=
ac_cv_env_VAMP_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_objext=o
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_GREP=/bin/grep
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_CXXCPP=/lib/cpp
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_cxx_g=no
ac_cv_prog_gcc_traditional=no

## ----------------- ##
## Output variables. ##
## ----------------- ##

AFTERBUILD=''
AUDACITY_NAME=''
BUILDLIBS=''
CC='gcc'
CDEPEND=''
CFLAGS='-g -O2'
CONFIGHEADER=''
CPP='gcc -E'
CPPFLAGS=''
CXX='g++'
CXXCPP='/lib/cpp'
CXXFLAGS=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
EXEEXT=''
EXTRAINSTALLTARGETS=''
EXTRAOBJS=''
EXTRATARGETS=''
EXTRAUNINSTALLTARGETS=''
GREP='/bin/grep'
INSTALL_DATA=''
INSTALL_PREFIX=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
JACK_CFLAGS=''
JACK_LIBS=''
LDFLAGS=''
LIBMAD_CFLAGS=''
LIBMAD_LIBS=''
LIBOBJS=''
LIBS=''
LIBTWOLAME_CFLAGS=''
LIBTWOLAME_LIBS=''
LOCAL_LIBS=''
LTLIBOBJS=''
OBJEXT='o'
OPTOBJS=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PKG_CONFIG=''
PRECOMP_CFLAGS=''
SAMPLERATE_CFLAGS=''
SAMPLERATE_LIBS=''
SHELL='/bin/bash'
SNDFILE_CFLAGS=''
SNDFILE_LIBS=''
SOUNDTOUCH_CFLAGS=''
SOUNDTOUCH_LIBS=''
VAMP_CFLAGS=''
VAMP_LIBS=''
WX_CONFIG=''
ac_ct_CC='gcc'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build=''
build_alias=''
build_cpu=''
build_os=''
build_vendor=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host=''
host_alias=''
host_cpu=''
host_os=''
host_vendor=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
subdirs=''
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""

configure: exit 1
```
Thanks!
Gena

---

### Post by ArtInvent on 2008-02-02
> checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.


This would indicate that you may no have** cpp** installed. I checked and this is on my machine. I would think that this would be part of the package **build-essential**, but it may not be. 

Speaking of which, also make sure you have installed** build-essential** - which is pretty essential and has a bunch of packages for compiling. 

```
$ sudo apt-get install build-essential cpp
```

Should solve this though it may be redundant. I should probably have this as Step 1, so I've edited the top post with this info.

---

### Post by 1GENNADIY1 on 2008-02-04
Helo!
Here bash:
```
gennadiy@alla:~/audacity-src-1.3.4-beta$ ./configure --with-libvorbis --with-libflac --with-libid3tag --with-soundtouch
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
configure: Determining what libraries are available in this tree and on the system
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SNDFILE... no
configure: Libsndfile libraries are NOT available as system libraries
checking for ./lib-src/libsndfile/src/sndfile.h.in... no
configure: libsndfile libraries are NOT available in this source tree
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for XML_ParserCreate in -lexpat... yes
checking expat.h usability... yes
checking expat.h presence... yes
checking for expat.h... yes
configure: Expat libraries are available as system libraries
checking for ./lib-src/expat/xmlparse/xmlparse.h... yes
configure: Expat libraries are available in the local tree
checking for SAMPLERATE... no
configure: Libsamplerate libraries are NOT available as system libraries
checking for ./lib-src/libsamplerate/src/samplerate.h... no
configure: libsamplerate libraries are NOT available in the local tree
checking for ./lib-src/libresample/include/libresample.h... yes
configure: libresample libraries are available in the local tree
checking for vorbis_bitrate_addblock in -lvorbisfile... yes
checking vorbis/vorbisfile.h usability... yes
checking vorbis/vorbisfile.h presence... yes
checking for vorbis/vorbisfile.h... yes
configure: Vorbis libraries are available as system libraries
checking for ./lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for ./lib-src/libogg/include/ogg/ogg.h... no
configure: Vorbis libraries are NOT available in this source tree
checking for LIBMAD... yes
checking for mad_decoder_init in -lmad... yes
configure: libmad libraries are available as system libraries
checking for ./lib-src/libmad/frame.h... no
configure: libmad libraries are NOT available in the local tree
checking for FLAC__stream_decoder_new in -lFLAC... yes
checking FLAC/format.h usability... yes
checking FLAC/format.h presence... yes
checking for FLAC/format.h... yes
configure: FLAC libraries are available as system libraries
checking for ./lib-src/libflac/include/FLAC/format.h... no
checking for ./lib-src/libflac/include/FLAC++/decoder.h... no
configure: FLAC libraries are NOT available in this source tree
checking for id3_file_open in -lid3tag... yes
checking id3tag.h usability... yes
checking id3tag.h presence... yes
checking for id3tag.h... yes
configure: Libid3tag libraries are available as system libraries
checking for ./lib-src/libid3tag/frame.h... no
configure: libid3tag libraries are NOT available in the local tree
checking for SOUNDTOUCH... no
configure: Libsoundtouch libraries are NOT available as system libraries
checking for ./lib-src/soundtouch/include/SoundTouch.h... no
configure: libsoundtouch libraries are NOT available in the local tree
checking for ./lib-src/libnyquist/nyx/nyx.h... yes
configure: nyquist libraries are available in the local tree
checking for VAMP... no
configure: Vamp libraries are NOT available as system libraries
checking for ./lib-src/libvamp/vamp-sdk/hostext/PluginLoader.h... yes
configure: Vamp libraries are available in the local tree
checking for LIBTWOLAME... yes
configure: Libtwolame library available as system library
checking for ./lib-src/twolame/libtwolame/twolame.h... no
configure: libtwolame library is NOT available in the local tree
configure: Figuring out what libraries to enable
configure: Using SYSTEM libraries for LIBVORBIS
configure: Using SYSTEM libraries for LIBMAD
configure: disabling LIBSNDFILE
configure: Using SYSTEM libraries for LIBFLAC
configure: Using SYSTEM libraries for LIBID3TAG
configure: disabling LIBSAMPLERATE
configure: Using LOCAL libraries for LIBRESAMPLE
configure: disabling LIBSOUNDTOUCH
configure: Using LOCAL libraries for LIBNYQUIST
configure: Using LOCAL libraries for LIBVAMP
configure: Using SYSTEM libraries for LIBEXPAT
configure: Using SYSTEM libraries for LIBTWOLAME
configure: error: Audacity requires libsndfile to be enabled
gennadiy@alla:~/audacity-src-1.3.4-beta$ 


```

I cann't English. I beg your pardon.
Cheers!
Gena

---

### Post by ArtInvent on 2008-02-04
You are almost there.

Three packages need to be added as you can see from the three 'disable' messages. I should have, and will, add these three packages to the mass apt-get install line of the top post. You can add these three by (it should be obvious by now) - 

```
sudo apt-get install libsndfile libsamplerate libsoundtouch 
```

It should also be obvious by now that the 'error' and the 'disable' messages of a configure command output probably point to missing packages that you will want to go back and install. (The alternative is to eliminate the **--with** part of the command that refers to these configure options being included.)

---

### Post by 1GENNADIY1 on 2008-02-05
Helo!
I try newly , but without success. Here is bash:
```

................
configure: error: Audacity requires libsndfile to be enabled

```
```
gennadiy@alla:~/audacity-src-1.3.4-beta$ dpkg -l | grep libsndfile
ii  libsndfile1                                1.0.17-4                             Library for reading/writing audio files

```
Thanks!
Gena

---

### Post by rocky5051 on 2008-02-05
Well I gave this a whirl, and everything went smooth until this error came up...

```
checking for wx-config... no
configure: error: "Could not find wx-config: is wxWidgets installed? is wx-config in your path?"
```

:confused:

I'm a noob at this myself so any explanation would be appreciated. :)

Thank you.

---

### Post by ArtInvent on 2008-02-06
@Gena -
my similar grep indicates **libsndfile-dev** is also installed. This must be a dependency as well. I will add it to the list. Install and retry.

@Rocky5051

I got the same error in an earlier attempt. wxWidgets are needed to build the icons and user interface menus etc.  You have to make sure that everything to do with wx version 2.6 is installed including -dev packages. They are listed in the long package install command in the top post. Look for everything that starts with **libwxbase....** and **libwxgtk... **and make sure it's all installed. Also** wx2.6headers** and** wx-common**. The most informative way is to open Synaptic and scroll all the way down and see what's got a green box. If it's not on the list at all as being available to install, you may not have the right repo enabled. I believe it's all in the Universe and Multiverse repos, so make sure you have these enabled in Synaptic | Setting | Repositories. "Reload" after enabling any repo. This would be one reason if you tried and failed in installing some packages when running the long install command.

---

### Post by rocky5051 on 2008-02-06
Okay. Well actually after posting that I researched into what wxWidgets was...and then when I went into Adept (I have Kubuntu 7.10...not that it makes any difference) and was totally confused by what I needed...so now that I know I'll make sure I get that all.

Thanks again.

---

### Post by ArtInvent on 2008-02-08
I added to the dependencies list on the above post. Also added perhaps a better way to automatically check for and install all the required dependencies. This is the command **apt-get build-dep [package]** and supposedly it will should be able to find out exactly what's needed and lacking on your system . See top post.

---

### Post by CyberDean on 2008-04-04
I have just compiled my first Linux program and my first in almost 40 years.  Yes, it has been awhile since I have been programming.  Your "HowTo" on compiling Audacity 1.3 Beta was very helpful and complete, a big Thanks to you.  I will be using Audacity as my selected digital recording program at church, and I feel it will serve us greatly.

Much THANKS.

I do have a question about Audacity that you might be able to shine some light on.  After starting Audacity, I tried to get into the "Help" file, tried to download from the internet, but could not get the download started.  Any hints, or is this having to do with it being a "Beta"?

I have used other programs similar in windows and I need some help learning Audacity.  Any other place I can find an Audacity "HowTo" use file or thread?

Thanks again for all your help.

---

### Post by ArtInvent on 2008-04-04
Forty years? I would guess your compiling skills might be a little rusty :)

[http://audacity.sourceforge.net/help/](http://audacity.sourceforge.net/help/)

has links to the documentation, user manuals, online wiki help site, etc. I think the help within Audacity would be the same as the html help files online.

---

### Post by CyberDean on 2008-04-04
Machine language and micro code was my beginning in programming back in the late 60's and early 70's but that's history now.

I tried to download the "help" file for Audacity after compiling it, but nothing would happen, I don't know if i was doing something wrong or not, I'll look at the link you gave me, Thanks.

Your "HowTo" really works.

I am looking for the "Help" file to be located on the computer due to while the computer is at the church, there is no internet connection, therefore no online HELP.

---

### Post by BandD on 2008-04-17
Thanks for the guide, I found it helpful.  One thing to note however, aptitude couldn't find the packages "libsndfile", "libsamplerate", or "libsoundtouch".

I checked the audacity site and they said (as you also did) that the "-dev" packages are important.  To get aptitude to install all the required packages I had to delete both "libsndfile" and "libsamplerate" from the list (the packages ending in -dev are there, those should stay) and I added a "-dev" to the end of libsoundtouch (so it reads like: libsoundtouch-dev).  Everything worked wonderfully after that!

Thanks a bunch!

---

### Post by ArtInvent on 2008-04-17
BandD - Can't quite figure why you could install the -dev package but couldn't find the non-dev of the same name. Maybe version conflicts? 

You don't absolutely need everything on the list, some are only necessary when compiling with certain options.

Anyway, I edited the top post and added libsoundtouch-dev to the list. I did not delete anything as this seems likely to be an anomaly.

Thanks for the feedback.

---

### Post by BandD on 2008-04-17
Sorry, I guess my post wasn't really clear.  In your long list of depenencies, you have something like this written:

```
 ...libsndfile libsndfile-dev...libsamplerate libsamplerate-dev...libsoundtouch
```

So as you already realized, the packages missing the -dev do not exist.  Because of this, it was casuing aptitude to prematurally end before anything was installed.  The libsoundtouch pakage doens't have a corresponding libsoundtouch-dev package so I added a -dev to the end of that package.

Maybe that is clearer.  You should delete the non-existant packages from your how-to.

Sorry for the confussion.

---

### Post by ArtInvent on 2008-04-17
I've checked and it's kind of odd. I have no libsndfile or the -dev but I do have libsndfile1 and -dev. I have no libsamplerate or -dev but I have libsamplerate0 and -dev.

Not sure what the deal is on those numbering conventions. I think this happens when someone updates a significantly different package. I believe I've used that apt-get intstall in the past with no problems. Usually if there is a version numer like that at the end, apt-get is smart enough to use the up-to-date version of the package. For instance, if I try to remove libsamplerate - which doesn't exist per se - apt-get does this
```
$ sudo apt-get remove libsamplerate-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libsamplerate0-dev instead of libsamplerate-dev
The following packages will be REMOVED:
  libsamplerate0-dev
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 332kB disk space will be freed.
Do you want to continue [Y/n]?
```


Another thing - apt-get will install all the programs it can from a long list like that. It doesn't abort the operation just because it can't find one or more of them. I just tested that to be sure.

---

### Post by drs305 on 2008-04-30
Solved: I got it working. Reinstalled all the dependencies and compiling worked the second time around.

Original entry:

I've been trying to compile 1.3.4 beta for hardy for a couple of hours. Finally found your post and it would have saved me quite a bit of time as I fumbled around installing dependencies ](*,)

Anyway, I can't get past this error when I run ./configure  
Here are the final lines:

```
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: error: cannot find input file: lib-src/Makefile.in

```

I've searched the internet but can't find a solution.

thanks.

Note: The reason for compiling is to enable the tempo feature, which has been left off of the 1.3.4 beta linux version. Supposedly you can get it work if you add soundtouch and complile audacity instead of using the repos.

---

### Post by Mepis_User on 2008-09-15
Much thanks to the OP.  I just compiled Audacity on Mepis 7.9 Beta.  With your help, it was only moderately painful.  
 
:)

---

### Post by no_angst on 2010-03-19
Thanks ArtInvent!  Still works in 9.10, so bumping the thread for other users.  (I was needing the FLAC functionality).

---

### Post by EllyBilateralCI on 2010-07-24
> **ArtInvent said:**
> This will tell you how to install Audacity 1.3.4 onto Gutsy using the source code. You will be able to leave a previously installed version of Audacity on your system and still use that when desired. It should also help you compile the next version of Audacity when it is released.  Compiling is generally not for noobs, and not generally recommended if an up-to-date package is available. You should at least know what a repo is and know your way around the command line a bit. If you're up for a little challenge, however, dive in.

This HowTo may seem long winded but the actual steps taken are actually pretty easy. I just wanted to give a little in the way of theory for each step and not just issue a bunch of blind commands. This can be helpful if you run into trouble.

[SIZE=2]BACKGROUND[/SIZE]

Audacity is a phenomenal piece of audio editing software with a peculiar development quirk. There are two lines of the software and have been for some time: the 1.2 'stable' series and the 1.3 'beta' series. The 1.3 series is by far the more capable, has been around for over two years, yet the developers insist on calling it 'beta' software and they never seem to release it as the real deal, even though it seems perfectly stable and refined for most of that time IMO.

On top of that, and perhaps because of it, the latest release of the 1.3 series is seldom available as a normal install package from repos, and even finding a .deb package for the latest Ubuntu is not possible. This version lag has been a constant problem ever since I've been using Audacity.

Next, if you settle for the older release and install an 8-month old version from the repos, it may not be compiled with all the options like mp3 and flac import and export.

In that light, I decided to try and shed my distaste of compiling from source and give it a go. It worked well and really wasn't that difficult and I have a fully-functional Audacity 1.3.4 on Gutsy with all the optional bells and whistles I need for the first time. Moreover, when the next 'beta' (sigh) is released, I will probably be well prepared to compile that post haste as well. 

Since I found a few scattered tips and tutorials on how to do this, I thought I would start a thread here that aims to be as complete as possible. 

Also note that these instructions likely work for any apt or Debian based distro. Also, I would appreciate it if people would correct any mistakes and add helpful bits, I can aim to edit the top post so others don't have to troll the whole thread for corrected instructions.

[SIZE=2]1. INSTALL DEPENDENCIES[/SIZE]

99% of failed compiles are due to not having the right dependency packages installed. In order to compile, we need a number of runtime and development packages of the correct version. These run the gamut from user interface widgets to audio hardware enablers to codec libraries. It's quite a number of packages if you want full functionality, but when finished, much of it can be removed easily enough as Audacity doesn't need it all to actually run.

Make sure Universe and Multiverse repos are enabled, these should contain all the necessary packages.

First of all, if you've never tried to compile anything, you will need to install the Gnu C Compiler and some other stuff. The easiest way to do this is to install **build-essential** which should suffice.
```
sudo apt-get install build-essential
```There is a way to have Ubuntu look for the required dependencies for a particular package and install them automatically. 

```
$ sudo apt-get build-dep audacity
```A alternate way way is to get all the dependencies for Audacity is to just fire a shotgun at the whole thing from the command line using the code below. I have tried to list here all the dependencies I have found as a reference. If the above build-dep seems to work, you can forgo the following command. Don't worry if you already have some of these packages, the install routine will only install those you don't have already. 

```
$ sudo apt-get install cdbs gettext libasound2-dev libjack-dev libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers libtwolame0 libtwolame-dev libgtk-dev libwxgtk-dev twolame libasound2-dev libjack0.100.0-dev portaudio19-dev libgtk2.0-dev libsndfile libsndfile-dev libsamplerate libsamplerate0-dev libsoundtouch libsoundtouch-dev 
```One of these two methods (or even both) should install all the packages. After this is finished GO BACK and read the output. If ANYTHING failed to install you must track it down and find it. There is no reason to proceed with the compile if a package is not present, it will waste lots of time. If the install routine can't find certain packages, you will have to make sure you have enough official or 3rd party repos enabled and track these down. I repeat: compiles fail because you don't have all the dependencies. 

[SIZE=2]2. DOWNLOAD AUDACITY SOURCE CODE [/SIZE]

We want the latest officially released beta and not the CVS builds. The Audacity Linux source code is usually found here:

[B][URL="http://audacity.sourceforge.net/download/beta_source"]
http://audacity.sourceforge.net/download/beta_source[/URL][/B]

This can be downloaded as a compressed tarball in the tar.bz2 format. You will save this to your home folder and uncompress the archive. (I used Archive Manager.) You will end up with a folder called, which in my case is, "/audacity-src-1.3.4-beta".

[SIZE=2]3. CONFIGURE[/SIZE]

Now we are ready to start the compile process. At the command line, change to the directory you just created, for instance -

```
$ cd ~/audacity-src-1.3.4-beta
```Now we will start the lengthy configure. It's at this point that we will tell the compile to enable certain useful things like the ability to directly export and import FLAC, Ogg, MP3, MP2, ID3 tag writing that actually writes the tags, etc. Options are explained exhaustively if you run the command "./configure --help" but it's a little too much info for most mortals. Below is a pretty complete command you can run without trying to figure all this out for yourself. This step on my machine took about 3 minutes. 

```
$  ./configure --with-libvorbis --with-libflac --with-libid3tag --with-soundtouch
```This should spit out a lot of messages, but if you get 'error' messages at the end, it failed probably because Step 1 didn't succeed in getting you all the dependencies. You will have to hunt these down by using the error messages which pretty much always indicate pretty clearly which package it couldn't find etc. After tracking these down and installing, you can run this command in the same directory over again until no errors appear. 

[SIZE=2]4. MAKE[/SIZE]

The make command may also take 5 minutes or so, as this is the actual compile. Stare at the screen if you like watching grass grow. This will probably spit out a lot of 'warning' gobbledygook, but this should be okay. You just don't want any errors.

```
$ make 
```[SIZE=2]5. MAKE INSTALL [/SIZE]

The final step is to install the compiled program so it can be run. Now, you can either do this command as 'sudo' in which case it will install across the board to all users. Or you can leave out the 'sudo' and just install it in your home directory which is what I did. If you choose the latter, you will be able to leave the previous Audacity version on your computer that were installed from repos. You can use the same .audacity folder with all of your preferences etc and choose which version you want to run. I simply made a menu launcher with the location of my special compile folder, and now I can run either version. (There are alternate ways to achieve similar things, this is simply the way I chose.)

```
$ make install 
```I actually got an error message at the end of this, but it only pertained to installing the program in /usr/bin/install which would make it a system wide program. Again, using 'sudo' in front of the command would make this go away. Trying to clarify the difference: without using 'sudo' in this step, if you just run the command 'audacity' from any directory except this one, you will be running the previous install of Audacity if you have one, not this compile, which is what I wanted. In my case I can either run the repo version 1.3.3 or this compile 1.3.4. You could also probably run the 1.2.x series from repos if you want without affecting this compile at all. In this way you can have any number of Audacity versions resident on your box and even compile different options for the same version in different directories. I'm boring you now so I'll stop.

[SIZE=2]6. RUN[/SIZE]

Finished. Now there will be an 'audacity' file sitting in your folder. Double click on this or, _within the folder_ at the CLI, run the 'audacity' command. Test the program especially the import and export of various filetypes to make sure you have it all right. 

Make a shortcut, or menu item in the 'Sound and Video' section, for more convenience, making sure to specify the exact folder location.

[SIZE=2]7. ADDITIONAL STUFF[/SIZE]

Now, if you want to use additional plugins like effects, beyond the 20 or so stock effects included in Audacity itself, which most of us do, you will need to install these separately. There are hundreds of these available. Most for Linux are in the LADSPA format and install easily system wide for any enabled audio program. The easiest way to find what's available is to open Synaptic and search for LADSPA. For instance: caps, cmt, ubuntustudio-audio-plugins, tap-plugins, swh-plugins. 

[SIZE=2]8. CLEAN UP UNNECESSARY PACKAGES (optional)[/SIZE]

Since you may have downloaded a bunch of development packages in Step 1 that are likely useless now that the compile is finished, you can easily purge these since they should not be registered as dependencies for any runtime package. Make sure you test and run the program for quite a while to make sure it's as it should be. You can always hold off on this step indefinitely.

 If you want to conserve disk space do this. If disk space is less important and you want to be able to compile the next version of Audacity whenever that is issued, you can just leave it as is. Of course, new versions of Audacity may use newer versions of many of these packages like the WX widgets stuff so be aware.

The command to purge your system of the specific unnecessary dev packages is below.

```
$ sudo apt-get remove --purge libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libwxbase2.6-dev libwxgtk2.6-dev libtwolame-dev libgtk-dev libwxgtk-dev portaudio19-dev libgtk2.0-dev 
```[SIZE=2]9. MAKING A .DEB PACKAGE -?[/SIZE]

It all certainly begs the question of a .deb package. This would be the really intelligent thing to do, so that this could be sent to the good folks at GetDeb or even to a more official Ubuntu or third party repo. Why this is never done until 6 months after the latest version, I don't know. As a packaging noob I attempted to make my own .deb package using checkinstall. It resulted in a very small file that can't possibly be right. I have a bit to learn if I'm to become a package maintainer. If someone who knows the ins and outs of making .deb packages better than I would like to investigate and propose a solution, this would be very nice. Then only one of us would have to go through the above rigamarole, and the rest of us could just download a .deb or use Synaptic which is how the whole Ubuntu thing is meant to work.

[SIZE=2]10. OTHER TUTORIALS[/SIZE]

I used two other web pages primarily and this HowTo is a synthesis and update of these efforts by others, thanks to their respective authors. 

[http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/](http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/)
[http://ubuntuforums.org/showthread.php?t=419358](http://ubuntuforums.org/showthread.php?t=419358)

[SIZE=2]11. FEEDBACK[/SIZE]

I may have made mistakes in the above. I tried a few permutations and did some steps more than once, so this is a reconstruction of steps I took. If others would like to try this HowTo and test it, please leave some feedback if it worked or if I omitted a package or made a typo or my theory is just plain wrong.

AUDACIOUS!

I followed steps 1 to 6 and it worked for lucid lynx (10.04 LTS) but the cleaning up of dev modules didn't work for me.....I used synaptic manager for this.

Many thanks as the latest audacity from lucid lynx wouldn't install which I tried from the Software Download centre!

---

