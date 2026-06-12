---
title: "checkinstall faild"
date: 2015-07-31
forum: Packaging and Compiling Programs
---

### Post by shidrang on 2015-07-31
Hi
I try to use checkinstall  to make a deb file from libdnet source code, but it always faild! I got libnet from github and below is my command. (I run all the from with root privileges)
./configure
make
checkinstall 

after it faild, I remove all file and redownload source and use this:
auto-apt run ./configure
make
checkinstall

but it in both way I got this error :
*** Warning: The package name "%{name}" does not start with
*** Warning: an alphanumetic character. dpkg might not like that so I prefixed
*** Warning: it with a number 0.
.
.
.
.

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: y

<log file>
dpkg-deb: error: parsing file '/var/tmp/tmp.VYIdTAwvnq/package/DEBIAN/control' near line 7 package '0--name-':
error in 'Version' field string '-%{release}': invalid character in revision number

any one can help me?
thanks

---

### Post by ron998 on 2015-08-10
...

---

