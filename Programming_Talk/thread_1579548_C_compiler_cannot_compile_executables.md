---
title: "C compiler cannot compile executables"
date: 2010-09-22
forum: Programming Talk
---

### Post by eholz1 on 2010-09-22
Hello All,
I have search in vain for an answer to this one (for about 3 days).
I am trying to compile ImageMagick.  I am unable to run ./configure on the source download for this.  Actually the c compiler will not compile anything!  This is an extraction from the config.log.
************************************************
configure: error: C compiler cannot create executables
See `config.log' for more details
ewh@ewhubuntu:/utilities/ImageMagick/ImageMagick-6.6.4-2$ vim config.log
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9)
configure:4415: $? = 0
configure:4404: gcc -V >&5
gcc: '-V' option must have argument
configure:4415: $? = 1
configure:4404: gcc -qversion >&5
gcc: unrecognized option '-qversion'
gcc: no input files
configure:4415: $? = 1
configure:4435: checking whether the C compiler works
configure:4457: gcc    conftest.c  >&5
/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.20 internal error, aborting at ../../bfd/elflink.c line 8664 in elf_link_output_extsym

/usr/bin/ld: Please report this bug.

collect2: ld returned 1 exit status
configure:4461: $? = 1
configure:4499: result: no
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "ImageMagick"
| #define PACKAGE_TARNAME "ImageMagick"
| #define PACKAGE_VERSION "6.6.4"
| #define PACKAGE_STRING "ImageMagick 6.6.4"
| #define PACKAGE_BUGREPORT "http://www.imagemagick.org"


************************************************

any ideas on what I am missing?
this is a pentium III processor, 600 mb memory

thanks,

eric

---

### Post by lloyd_b on 2010-09-22
In a terminal window, "sudo apt-get install build-essential".  This will ensure that you have *all* the required pieces for a complete build system.  Once you've done that, try the ./configure again.

Lloyd B.

---

### Post by Iowan on 2010-09-22
Moved to Programming Talk.

---

### Post by eholz1 on 2010-09-22
Hello Lloyd_b,

I will try this.

Thanks,

eholz1

---

### Post by eholz1 on 2010-09-22
Thanks for moving this to "Programming Talk"  I will
remember to use this forum for future question 
with "programming" , etc.

eholz1

---

### Post by eholz1 on 2010-09-23
Hello Lloyd and others,
The build-essential program is on my system.
I tried building another program (MagickWandForPHP)
and get the same error.  Below is part of the config.log

I alwasy get this error after running phpize, and then the ./configure command.

*********************************************************
cc: unrecognized option '-qversion'
cc: no input files
configure:2923: $? = 1
configure:2945: checking for C compiler default output file name
configure:2967: cc    conftest.c  >&5
/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.20 internal error, aborting at ../.
./bfd/elflink.c line 8664 in elf_link_output_extsym

/usr/bin/ld: Please report this bug.

collect2: ld returned 1 exit status
configure:2971: $? = 1
configure:3008: result:
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| /* end confdefs.h.  */

**********************************************************
Let me know if I need to attach the entire log.

eholz1

---

### Post by spjackson on 2010-09-23
There's something odd going on here. Does cc work? Does gcc work?

Edit a new file mytest.c and insert the following.
```

#include <stdio.h>

int main()
{
  puts("It works!");
  return 0;
}

```Now compile, link and run:
```

$ cc -o mytest mytest.c
$ ./mytest
It works!
$ gcc -o mytest mytest.c
$ ./mytest
It works!

```Whether that works or not, what's the output of the following?
```

$ which -a cc
$ which -a gcc

```What platform are you on?
```

$ uname -a

```

---

### Post by eholz1 on 2010-09-23
Hello spjackson,
Thanks for replying.  I have been trying to get this to work!
I have tried to use gcc with simple "hello world" C program,
and get the same problem.  I will try your suggestions in the reply above, and get back to the forum with the info.

Thanks Very Much,

eholz1 (aka eric)

---

### Post by eholz1 on 2010-09-23
Hello,  OK here is a mystery. I may (or may not) have a weird issue.  I will list the info you requested first.

I am using a Pentium III processor - "Coppermine" (old)
600 mb memory.

The kernel:

ewh@ewhubuntu:~$ uname -a
Linux ewhubuntu 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux

ewh@ewhubuntu:~$ **which -a cc**
/usr/bin/cc
ewh@ewhubuntu:~$ **which -a gcc**
/usr/bin/gcc

Here is the weirdness.  I logged on to the system under my username. I used vim to create mytest.c file. I attempted to write this file, and got a message to the effect "this is a read-only file system." This seemed real strange, since I wrote the hello.c program yesterday without any problem.  So, I looked 
at my home dir - for some reason somehow my /home/ewh dir was changed to READ ONLY??!!!  I could not change the permissions on any of the files in my dir, even as root!. I rebooted the system - suspecting some sort of disk issue.  It did pop me into a maintenance prompt.  I had to run fsck manually.  The main disk partition had some problems (inodes, etc).  Once finished, I rebooted. I logged on, and tried it again, this time the file system was not read-only, and I wrote the mytest.c program, and 
then ran cc -o mytest mytest.c.  The compiler coughed with the following error:

***************
/usr/bin/ld: BFD (GNU Binutils for Ubuntu) 2.20 internal error, aborting at ../. 8664 in elf_link_output_extsym

/usr/bin/ld: Please report this bug.

collect2: ld returned 1 exit status
*************

The just for fun I tried it again, this time it compiles and I could run the program!!  I tried the hello.c program as well, and
the first attempt it crashes (same error).  On the second attempt
it compiles and runs.  I give up.

I tried the ImageMagick program as well, and the configure ran for a while, but make fails everytime.

One other thing - I used to be able to update or get packages using apt-get.  Now all I get is error messages like this:

**************************************************
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main python-zope.interface 3.5.2-1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main python-lazr-restfulclient 0.9.3-0ub                       untu3
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main python-oauth 1.0a~svn1124-0ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main python-launchpadlib 1.5.1-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main python-apport 1.9.3-0ubuntu                       4.2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main apport 1.9.3-0ubuntu4.2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main apport-symptoms 0.2
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-pr](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-pr)                       oblem-report_1.9.3-0ubuntu4.2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/simplejson/pytho](http://us.archive.ubuntu.com/ubuntu/pool/main/s/simplejson/pytho)                       n-simplejson_2.0.9-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lazr.uri/python-](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lazr.uri/python-)                       lazr-uri_1.0-0ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-wadllib/p](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-wadllib/p)                       ython-wadllib_1.1.2-0ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-httplib2/](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-httplib2/)                       python-httplib2_0.4.0-0ubuntu2_i386.deb  Could not resolve 'us.archive.ubuntu.co                       m'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptool](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-setuptool)                       s/python-pkg-resources_0.6c9-0ubuntu5_all.deb  Could not resolve 'us.archive.ubu                       ntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/z/zope.interface/p](http://us.archive.ubuntu.com/ubuntu/pool/main/z/zope.interface/p)                       ython-zope.interface_3.5.2-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/lazr.restfulclie](http://us.archive.ubuntu.com/ubuntu/pool/main/l/lazr.restfulclie)                       nt/python-lazr-restfulclient_0.9.3-0ubuntu3_all.deb  Could not resolve 'us.archi                       ve.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-oauth/pyt](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-oauth/pyt)                       hon-oauth_1.0a~svn1124-0ubuntu2_all.deb  Could not resolve 'us.archive.ubuntu.co                       m'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-lau](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-lau)
**************************************************

so I am able to install nothing, no upgrade or update or etc.

I may have a disk problem, so I will start copying my important files to somewhere safe (fstab, interfaces, hosts, apache2, mysql,etc)

If you have any suggestions, I am open!!

eholz1 (eric)

---

### Post by Queue29 on 2010-09-24
> I may have a disk problem, so I will start copying my important files to somewhere safe (fstab, interfaces, hosts, apache2, mysql,etc)

If you have any suggestions, I am open!!

Yea... once you back everything up, buy a new harddrive and do a fresh install (and perhaps upgrade to 10.04 while you're at it).

---

### Post by dwhitney67 on 2010-09-24
> **eholz1 said:**
> 
If you have any suggestions, I am open!!

eholz1 (eric)
I think you are on the right path; wax the machine and reinstall the OS.

---

