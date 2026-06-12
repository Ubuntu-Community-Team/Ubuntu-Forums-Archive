---
title: "cpp fails sanity check"
date: 2009-07-03
forum: Packaging and Compiling Programs
---

### Post by mslate on 2009-07-03
> C preprocessor "/lib/cpp" fails sanity check


As I try to compile (downloaded) programs from source using the "configure" command, I always run into this error. In my config.log file, there are these abbreviated lines about failing to find the stdio.h header file:

> ...
108 configure:3447: gcc  -c -g -O2  conftest.c >&5
 109 conftest.c:11:19: error: stdio.h: No such file or directory
 110 conftest.c:12:23: error: sys/types.h: No such file or directory
 111 conftest.c:13:22: error: sys/stat.h: No such file or directory
 112 conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
 113 conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
 114 configure:3453: $? = 1
 115 configure: failed program was:
 116 | /* confdefs.h.  */
 117 | #define PACKAGE_NAME ""
...

I am aware that others have posted (multiple times) in forums about this error, but as far as I can tell my gcc compiler exists and doesn't need to be updated. I've run both:

> sudo aptitude install build-essential
sudo aptitude update

What am I missing (or how can I tell if it's missing)?

---

### Post by johnl on 2009-07-03
Hi,

Try making sure that the package 'libc6-dev' is installed.

---

### Post by mslate on 2009-07-03
> burritoman@slaptop:~$ sudo aptitude install libc6-dev
[sudo] password for burritoman:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

burritoman@slaptop:~$ locate libc6
/usr/lib/libapt-inst-libc6.9-6.so.1.1
/usr/lib/libapt-inst-libc6.9-6.so.1.1.0
/usr/lib/libapt-pkg-libc6.9-6.so.4.7   
/usr/lib/libapt-pkg-libc6.9-6.so.4.7.0 
/usr/share/doc/libc6                   
/usr/share/doc/libc6-dev               
/usr/share/doc/libc6-i686              
/usr/share/doc/libc6/BUGS              
/usr/share/doc/libc6/CONFORMANCE.gz    
/usr/share/doc/libc6/ChangeLog.nptl.gz 
/usr/share/doc/libc6/FAQ.gz            
/usr/share/doc/libc6/NAMESPACE         
/usr/share/doc/libc6/NEWS.Debian.gz    
/usr/share/doc/libc6/NEWS.gz           
/usr/share/doc/libc6/NOTES.gz          
/usr/share/doc/libc6/PROJECTS.gz       
/usr/share/doc/libc6/README.Debian.gz  
/usr/share/doc/libc6/README.gz         
/usr/share/doc/libc6/README.hesiod.gz  
/usr/share/doc/libc6/TODO              
/usr/share/doc/libc6/changelog.Debian.gz
/usr/share/doc/libc6/changelog.gz       
/usr/share/doc/libc6/copyright          
/usr/share/doc/libc6/test-results-i486-linux-gnu-libc
/usr/share/doc/libc6-dev/changelog.Debian.gz         
/usr/share/doc/libc6-dev/copyright                   
/usr/share/doc/libc6-i686/changelog.Debian.gz        
/usr/share/doc/libc6-i686/copyright                  
/usr/share/doc/libc6-i686/test-results-i686-linux-i686
/usr/share/lintian/overrides/libc6                    
/usr/share/lintian/overrides/libc6-dev                
/usr/share/lintian/overrides/libc6-i686
/var/lib/dpkg/info/libc6-dev.list
/var/lib/dpkg/info/libc6-dev.md5sums
/var/lib/dpkg/info/libc6-i686.list
/var/lib/dpkg/info/libc6-i686.md5sums
/var/lib/dpkg/info/libc6-i686.postinst
/var/lib/dpkg/info/libc6-i686.postrm
/var/lib/dpkg/info/libc6-i686.shlibs
/var/lib/dpkg/info/libc6.conffiles
/var/lib/dpkg/info/libc6.list
/var/lib/dpkg/info/libc6.md5sums
/var/lib/dpkg/info/libc6.postinst
/var/lib/dpkg/info/libc6.postrm
/var/lib/dpkg/info/libc6.preinst
/var/lib/dpkg/info/libc6.shlibs
/var/lib/dpkg/info/libc6.symbols
/var/lib/dpkg/info/libc6.templates
/var/lib/dpkg/info/libc6.triggers


I believe it's installed A-OK

---

### Post by c0mput3r_n3rD on 2009-07-04
If it says that stdio.h does not exist, then you must make it.  You have to put the file stdio.h into your /usr/include/  directory.  I could even email you the file if you want.

---

### Post by mslate on 2009-07-04
I thought this means I already have it:

> burritoman@slaptop:~$ locate stdio.h
/home/burritoman/tiff-3.8.2/include/stdio.h
/home/burritoman/tiff-3.8.2/include/bits/stdio.h
**/usr/include/c++/4.3/tr1/stdio.h**
/usr/lib/perl/5.10.0/CORE/nostdio.h


I'll message you my email address anyways, and try copying it into /usr/include/

---

### Post by johnl on 2009-07-06
Hi,

libc6-dev provides the files you are missing:

/usr/include/stdio.h
/usr/include/sys/types.h
/usr/include/sys/stat.h

It looks like you have it installed already, but if these files are missing reinstalling could solve the problem:

sudo apt-get install --reinstall libc6-dev

If you are ever missing a file and need to know which package it comes from, you can use dpkg -S:

$ dpkg -S sys/types.h
libc6-dev: /usr/include/sys/types.h
mingw32-runtime: /usr/i586-mingw32msvc/include/sys/types.h

Hope this helps.

---

### Post by mslate on 2009-07-06
Yup, fixes the problem! Thanks John

---

