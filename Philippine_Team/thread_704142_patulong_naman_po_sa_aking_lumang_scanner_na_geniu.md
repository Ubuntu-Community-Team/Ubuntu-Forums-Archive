---
title: "patulong naman po sa aking lumang scanner na genius vividpro II"
date: 2008-02-22
forum: Philippine Team
---

### Post by papichulo on 2008-02-22
magandang araw!

nagdownload po ako ng SANE para sa scanner ko, kaso po nagkakaroon cya ng error kapag compile na.

**"configure:2590: error: C compiler cannot create executables"**

bakit kaya??
may kulang ba sa ubuntu ko??

ito yung config.log nya:

> 
configure:2058: checking build system type
configure:2076: result: i686-pc-linux-gnulibc1
configure:2098: checking host system type
configure:2113: result: i686-pc-linux-gnulibc1
configure:2197: checking for gcc
configure:2224: result: gcc
configure:2462: checking for C compiler version
configure:2469: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2472: $? = 0
configure:2479: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2482: $? = 0
configure:2489: gcc -V >&5
gcc: '-V' option must have argument
configure:2492: $? = 1
configure:2515: checking for C compiler default output file name
configure:2542: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2545: $? = 1
configure:2583: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "sane-backends"
| #define PACKAGE_TARNAME "sane-backends"
| #define PACKAGE_VERSION "1.0.19"
| #define PACKAGE_STRING "sane-backends 1.0.19"
| #define PACKAGE_BUGREPORT "sane-devel@lists.alioth.debian.org"
| #define PACKAGE "sane-backends"
| #define VERSION "1.0.19"
| #define SANE_DLL_V_MAJOR 1
| #define SANE_DLL_V_MINOR 0
| #define SANE_DLL_V_BUILD 19
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2590: error: C compiler cannot create executables
See `config.log' for more details.


maraming salamat, sana matulungan nyo ako.

:)

---

### Post by loell on 2008-02-22
may xsane naman sa repository,

may dahilan ba para e-compile mo from source? ;)

---

### Post by dodimar on 2008-02-22
tama si sir lloel, meron sa repository.. mas madali..

yung error na nareceive mo is due to some libs (yata) or some components of the compiler na hindi naka-install... mas mahirap ayusin yun kesa mag-install using the repo...

---

### Post by ragadanga63 on 2008-02-23
Dats right!!  Just start Synaptic and search for SANE and XSANE (graphical front end ng SANE).

---

### Post by papichulo on 2008-02-25
nagawa ko na po siyang i-compile sa papamagitan nito:

> sudo apt-get install build-essential

wala na po error!

meron na rin naman **xsane** na naka-install sa system.

sinubukan ko rin install yung **sane**.

> apt-get install sane

ngunit ito pa rin ang lumalabas sa kanya.

sa xsane:

> 
no device available

possible reasons:
1) there is really no device that is supported by SANE
2) supported device are busy
3) the permissions for the device file do not allow you to use it - try as root
4) the backend is not loaded by SANE (man sane-dll)
5) the backend is not configured correct (man sane-"backendname")
6) possibly there is more than one SANE version installed



paano ko po ba malalaman ang # 4,5,6 ??

sinubukan ko rin ang:
> sane-find-scanner tool

>  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # SANE has been built without libusb support. This may be a reason
  # for not detecting USB scanners. Read README for more details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.



> [b]# Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.[/b]

eh paano kaya iyon? nasa parallel port yung scanner ko!

sana naman ay mabigyan kasagutan ang aking mga katanungan.

maraming salamat.

---

### Post by loell on 2008-02-25
try this


```
sudo apt-get install libsane-extras
```


then run xsane again, see if it can now detect your scanner.

---

### Post by papichulo on 2008-02-26
frustrated na ako dito...

nalalagas na ata ang buhok ko sa bunbunan...

hanggang ngayon hindi ko pa mapagana ang yung **"genius colorpage vivid pro II"** na scanner.

ayon pala doon sa website na ito:

> [http://geniusvp2.sourceforge.net/supported.shtml](http://geniusvp2.sourceforge.net/supported.shtml)

hindi supported ang model number ko... wahhhhh....

kelangan ko raw pumunta dito:

> [http://home2.swipnet.se/~w-25069/pxscan.html](http://home2.swipnet.se/~w-25069/pxscan.html)

na pinapapunta naman ako dito:

> [http://primax.sourceforge.net/](http://primax.sourceforge.net/)

na kelangan ko raw itong mga ito:

> [http://px-backend.sourceforge.net/](http://px-backend.sourceforge.net/)

na sinubukan ko gamit ang mga ito:

> [http://px-backend.sourceforge.net/install.html](http://px-backend.sourceforge.net/install.html)

Requirements

    * a working C compiler and the make tool
    * the primaxscan sources
    * the libieee1284 library and header files
    * for the SANE driver the SANE header files



wow...

maraming kulang...maraming kulang...

ano bah...

bumili na lang kaya ako ng bagong scanner...

pero hindi..wala pera ang opisina namin...kaya nga ubuntu yung naka install eh...

:( :( :(

---

### Post by papichulo on 2008-02-26
pero maraming salamat na rin kay master loell sana ay huwag kang magsawang tulungan ang isang tulad ko na shonga...kaya sana ay lubos-lubosin mo na rin ang pagtulong....pakihanap naman ang sulusyon oh..hehehehe....

yung canon na pixma ip1000 printer..ayaw din gumana...pero ibang usapan na iyon.

---

### Post by daxumaming on 2008-04-12
[https://help.ubuntu.com/community/GeniusColorpageVivid4X](https://help.ubuntu.com/community/GeniusColorpageVivid4X)

Same steps, just look for _your scanners'_ .fw firmware/driver file which can usually be found on the installer cd.

---

### Post by papichulo on 2009-07-12
july 2009 na hindi pa rin supported yung genius scanner ko. hus.. :(

---

### Post by Script Warlock on 2009-07-12
nagawa ko na yan dati sa 7.04 may na-import akong parang firmware ata yun medyo nakalimutan ko lang kung paano kc bago na scanner ko. try ko rin hanap yung notes ko baka rin makatulong....

ah yan pala guide tama sabi dax.....

---

### Post by daxumaming on 2009-07-13
> **papichulo said:**
> july 2009 na hindi pa rin supported yung genius scanner ko. hus.. :(

er... the hardest part is copying the proprietary firmware since you'll have to hunt it down. I  don't believe it's unsupported 'coz if it is, it won't work even with the firmware.

---

