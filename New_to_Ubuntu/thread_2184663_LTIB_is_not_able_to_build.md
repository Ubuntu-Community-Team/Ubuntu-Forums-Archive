---
title: "LTIB is not able to build"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by K.F.Lee on 2013-10-30
Hi,

Am a new user of Linux. 

Have installed the Ubuntu 12.04 LTS and is up and running.

Have followed below instruction and downloaded the LTIB 

$ cvs -z3 -d:pserver:anonymous@cvs.savannah.nongnu.org:/sources/ltib co -P ltib

Have changed the directory to ltib and execute the ./ltib to build the platform, however enountered below errors. 

Need and appreciate an advice where have gone and what I should do to get the platform build ? Thanks !

$ cd ltib
$ ./ltib

Don't have HTTP::Request::Common
Don't have LWP::UserAgent
Cannot test proxies, or remote file availability without both
HTTP::Request::Common and LWP::UserAgent
sh: 2: g++: not found
sh: 1: tclsh: not found

ltib cannot be run because one or more of the host packages needed to run it
are either missing, failing, out of date or not in ltib's standard path.
Current the PATH environment is set to: 
/opt/ltib/usr/bin:/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/X11R6/bin

Please correct this problem (e.g. install/upgrade these packages on your host).
If you have your own utilities in non-standard paths, please add an entry
into the .ltibrc file for example:

%path_std
/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/X11R6/bin:/my/own/exes

Package                Minimum ver   Installed info
-------                -----------   ---------------
libstdc++              0             not installed or error
gcc-c++                2.96          not installed or error
zlib-devel             0             not installed or error
rpm                    0             not installed or error
rpm-build              0             not installed or error
ncurses-devel          0             not installed or error
m4                     0             not installed or error
bison                  0             not installed or error
tcl                    0             not installed or error

Died at ./ltib line 1509.
traceback:
 main::host_checks:1509
  main:562


Started: Wed Oct 30 15:10:20 2013
Ended:   Wed Oct 30 15:10:20 2013
Elapsed: 0 seconds

VERSION          : 13.2.1
CVS_VERSION      : $Revision: 1.93 $ (Savannah)
PLATFORM         : 
GNUTARCH         : 
TOOLCHAIN        : 
TOOLCHAIN_CFLAGS : 


Build Failed

Exiting on error or interrupt

Regards,
Kim Lee

---

