---
title: "HOWTO: Compile Sheepshaver from source."
date: 2008-01-17
forum: Outdated Tutorials &amp; Tips
---

### Post by SOULRiDER on 2008-01-17
***[SIZE="5"]INFO:[/SIZE]***
> SheepShaver is an open source PowerPC Apple Macintosh emulator originally designed for BeOS and Linux. The name is a play on ShapeShifter, a Macintosh II emulator (made obsolete by Basilisk II), which is in turn not to be confused with a third-party preference pane for Mac OS X with the same name. The SheepShaver (and ShapeShifter) project was originally conceived and programmed by Christian Bauer. However, the main developer behind SheepShaver, as of late, has been Gwenolé Beauchesne.

SheepShaver was originally commercial software when first released in 1998, but after the demise of Be Inc., the maker of BeOS, it became open source in 2002. It can be run on both PowerPC and x86 systems; however, it runs more slowly on an x86 system than on a PowerPC system.

It has also been ported to Microsoft Windows. Ports to the Mac OS X PowerPC and Intel versions have also been released. A complete install for Intel Macs can be found here.

It is capable of running Mac OS 7.5.2 through 9.0.4 (though it needs the image of an Old World ROM to run Mac OS 8.1 or below), and can be run inside a window so that the user can run classic Mac OS applications and BeOS or Linux or Windows applications at the same time.

Although SheepShaver does have Ethernet support and CD-quality sound output, SheepShaver does not emulate a memory management unit, as is the case with Basilisk II, and thus cannot run later versions of Mac OS 9 or any version of Mac OS X, which is best emulated by PearPC. At the present, SheepShaver's developers do not have plans to add MMU emulation, since it would hinder the performance of the emulator.

Homepage: [http://gwenole.beauchesne.info/en/projects/sheepshaver](http://gwenole.beauchesne.info/en/projects/sheepshaver)


***[SIZE="5"]STEP 1 - GET THE BASIC COMPILE TOOLS[/SIZE]***
First you'll need to have the basic tools for compiling the program. We're going to install build-essential and autoconf.
```
sudo aptitude install build-essential autoconf
```
If you want to create a Debian package, you can also install checkinstall. A Debian package will allow the easy removal of the program from your system.
```
sudo aptitude install checkinstall
```


***[SIZE="5"]STEP 2 - INSTALL NEEDED LIBRARIES[/SIZE]***
In order to compile Sheepshaver you will need to have these packages installed: libx11-dev libesd0-dev libgtk2.0-dev libgtk1.2-dev.
To install the needed packages use this command:
```
sudo aptitude install libx11-dev libesd0-dev libgtk2.0-dev libgtk1.2-dev.
```


***[SIZE="5"]STEP 3 - DOWNLOAD AND PREPARE THE SOURCE[/SIZE]***
Go to the projects homepage and download the latest source. As of January 17 2008, this is the latest source: [http://gwenole.beauchesne.info/projects/sheepshaver/files/SheepShaver-2.3-0.20060514.1.tar.bz2](http://gwenole.beauchesne.info/projects/sheepshaver/files/SheepShaver-2.3-0.20060514.1.tar.bz2)
 
Once its downloaded unpack it and open a terminal in the src/Unix directory of the unpacked source.


***[SIZE="5"]STEP 4 - COMPILE SHEEPSHAVER[/SIZE]***
Now that you're in the src/Unix directory, its time to start compiling.
To begin configuring type:
```
./autogen.sh
```
followed by
```
make
```


***[SIZE="5"]STEP 5 - INSTALL SHEEPSHAVER[/SIZE]***
Here you can either choose to install or install using a Debian package.
If you simply want to install, do the usual
```
sudo make install
```
If you want to make a Debian package and have installed checkinstall, you can do
```
sudo checkinstall
``` remember to make sure you filled the different fields with the proper information.


***[SIZE="5"]STEP 6 - RUNNING SHEEPSHAVER[/SIZE]***
Use this command to run Sheepshaver
```
SheepShaver
```

I Hope you found this tutorial a bit useful. Good luck!!


***[SIZE="5"]OTHER INFO[/SIZE]***

***[SIZE="4"]UNINSTALLING[/SIZE]***
If you created a Debian package and if you correctly set it's name, you can uninstall the package with this command
```
sudo aptitude remove sheepshaver
```

***[SIZE="4"]DEBIAN PACKAGE[/SIZE]***
I am also attaching a Debian package I made, its working but its missing the dependencies field. If somebody creates a Debian package with all the correct information please post it.
The package should depend only on libesd0, libgtk2.0-common and libgtk1.2-common

---

### Post by Cabalist on 2008-02-22
This is great!  Just what I was looking for.  :)  I think that you should add the instructions on how to do this from CVS also as the has been updated since those  old source releases...

Would you have any information on installing OS9 from an iso? Or is there a better way to install OS9 on linux?  Thanks in advance.  :)

---

### Post by SOULRiDER on 2008-02-25
> **Cabalist said:**
> This is great!  Just what I was looking for.  :)  I think that you should add the instructions on how to do this from CVS also as the has been updated since those  old source releases...

Would you have any information on installing OS9 from an iso? Or is there a better way to install OS9 on linux?  Thanks in advance.  :)

I'm updating the post as we speak, I don't know how to install OS9, I've never even ran sheepshaver, i just made the guide because some people didn't know how to compile.

---

### Post by quanumphaze on 2008-06-25
autogen.sh seems to be having trouble when it calls the configure script:

```
$ ./autogen.sh 
 + Running aclocal: aclocal: couldn't open directory `m4': No such file or directory
done.
 + Running autoheader: done.
 + Running autoconf: done.
 + Running 'configure ':
   ** If you wish to pass arguments to ./configure, please
   ** specify them on the command line.
configure: error: cannot run /bin/bash ./config.sub
```

Any clues why it doesn't like /bin/bash?

And where would I find a decent how to (and where to get this Old World ROM thing) once I get it installed?

---

### Post by mfox on 2008-07-28
I've been trying to get SheepShaver installed on Ubuntu Hardy on my PowerBook since Mac-on-Linux doesn't seem to work on the Hardy kernel.  I followed these excellent instructions but ran into trouble in the make stage.  Here is my output:

fox@fox-PowerBook:~/Desktop/SheepShaver-2.3/src/Unix$ make 
gcc -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2   -c Linux/sheepthreads.c -o obj/sheepthreads.o 
Linux/sheepthreads.c:53: error: field &#8216;__sem_lock&#8217; has incomplete type 
Linux/sheepthreads.c:55: error: expected specifier-qualifier-list before &#8216;_pthread_descr&#8217; 
Linux/sheepthreads.c: In function &#8216;fastlock_init&#8217;: 
Linux/sheepthreads.c:190: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:191: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c: In function &#8216;fastlock_try_acquire&#8217;: 
Linux/sheepthreads.c:197: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:198: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:199: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:203: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c: In function &#8216;fastlock_acquire&#8217;: 
Linux/sheepthreads.c:211: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c: In function &#8216;fastlock_release&#8217;: 
Linux/sheepthreads.c:218: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:219: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:219: error: dereferencing pointer to incomplete type 
Linux/sheepthreads.c:219: error: invalid lvalue in asm output 0 
Linux/sheepthreads.c:219: error: memory input 1 is not directly addressable 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_init&#8217;: 
Linux/sheepthreads.c:229: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c:230: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:230: error: &#8216;pthread_mutexattr_t&#8217; has no member named &#8216;__mutexkind&#8217; 
Linux/sheepthreads.c:231: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_count&#8217; 
Linux/sheepthreads.c:232: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_owner&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_destroy&#8217;: 
Linux/sheepthreads.c:243: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:245: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_lock&#8217;: 
Linux/sheepthreads.c:258: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:260: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_trylock&#8217;: 
Linux/sheepthreads.c:274: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:276: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutex_unlock&#8217;: 
Linux/sheepthreads.c:289: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_kind&#8217; 
Linux/sheepthreads.c:291: error: &#8216;pthread_mutex_t&#8217; has no member named &#8216;__m_lock&#8217; 
Linux/sheepthreads.c: In function &#8216;pthread_mutexattr_init&#8217;: 
Linux/sheepthreads.c:305: error: &#8216;pthread_mutexattr_t&#8217; has no member named &#8216;__mutexkind&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_init&#8217;: 
Linux/sheepthreads.c:336: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_destroy&#8217;: 
Linux/sheepthreads.c:351: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:356: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_wait&#8217;: 
Linux/sheepthreads.c:377: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:377: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c: In function &#8216;sem_post&#8217;: 
Linux/sheepthreads.c:400: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:401: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
Linux/sheepthreads.c:401: error: &#8216;sem_t&#8217; has no member named &#8216;__sem_waiting&#8217; 
make: *** [obj/sheepthreads.o] Error 1 

Anyone know what I can do to correct this?

---

### Post by David.a.s93 on 2008-10-27
can someone plz help me with this part

Once its downloaded unpack it and open a terminal in the src/Unix directory of the unpacked source.:confused:

---

### Post by igor_av on 2009-02-22
Hi. I've been trying to compile Sheepshaver from source on Unbuntu 8.10 (i386 and PowerPC) without success. I tried autogen.sh with current gcc and gcc-3.4. When I try to make, I get the following error message : 

> g++ -I../kpx_cpu/include -I../kpx_cpu/src -DUSE_JIT -I../include -I. -I../slirp -DHAVE_CONFIG_H -D_REENTRANT -DDATADIR=\"/usr/local/share/SheepShaver\" -g -O2    -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -c sys_unix.cpp -o obj/sys_unix.o
sys_unix.cpp: In function ‘void* Sys_open(const char*, bool)’:
sys_unix.cpp:582: attention : ignoring return value of ‘ssize_t read(int, void*, size_t)’, declared with attribute warn_unused_result
sys_unix.cpp: In function ‘bool SysIsDiskInserted(void*)’:
sys_unix.cpp:888: error: ‘INT_MAX’ was not declared in this scope
make: *** [obj/sys_unix.o] Error 1


Any idea on what I should do?

---

### Post by woohoo576 on 2009-07-18
******* NEWB ALERT*******
"Once its downloaded unpack it and open a terminal in the src/Unix directory of the unpacked source."


How would I go about doing that?:confused:

---

### Post by rpangrazio on 2009-09-14
There is a system header file called limits.h that defines this. 
To fix it edit sys_unix.cpp

right after "#include <errno.h> add 
#include <limits.h>

That should do it.

---

### Post by rpangrazio on 2009-09-15
> **rpangrazio said:**
> There is a system header file called limits.h that defines this. 
To fix it edit sys_unix.cpp

right after "#include <errno.h> add 
#include <limits.h>

That should do it.

This was in reply to the question about the INT_MAX problem

---

### Post by afrodeity on 2009-11-11
got this during make

```

./configure: line 4410: syntax error near unexpected token `('
./configure: line 4410: `case "(($ac_try" in'

```

When I make the file, it comes out okay, but it won't run after install.


The [http://ubuntuforums.org/attachment.php?attachmentid=56717&d=1200586675](http://ubuntuforums.org/attachment.php?attachmentid=56717&d=1200586675) works on karmic but seg faults and quits when you try to start anything.

---

