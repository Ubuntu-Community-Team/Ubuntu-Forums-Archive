---
title: "problem in compiling qtstalker from source"
date: 2015-01-04
forum: Packaging and Compiling Programs
---

### Post by Jaladhi_R_Trivedi on 2015-01-04
can anyone help me with compiling qtstalker?
i followed the installation guide and installed build-essential, libdb6.0-dev,libqt3-mt-dev,qt3-dev-tools.
i also installed berkley database(db-6.1.19) and compiled it.
i also installed ta-lib from debian package.
now i unpacked the qtstalker sourcefile moved it to usr/local/src
   and gave command ./configure
following is the output

jaladhi@jaladhi-Compaq-510:/usr/local/src/qtstalker-0.36$ ./configure
Building Makefile...
Done
Creating national language files in i18n...
Done
Compiling existing translations...
Done
You may now 'make && make install'
jaladhi@jaladhi-Compaq-510:/usr/local/src/qtstalker-0.36$ make
cd lib && make -f Makefile
make[1]: Entering directory `/usr/local/src/qtstalker-0.36/lib'
g++ -c -pipe -g -ffast-math -Wall -W -O0 -D_REENTRANT -fPIC  -DQT_NO_COMPAT -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I/usr/local/include/ta-lib -I../../../../include/qt3 -o IndicatorPlugin.o IndicatorPlugin.cpp
In file included from IndicatorPlugin.cpp:23:0:
TALIB.h:23:21: fatal error: ta_libc.h: No such file or directory
 #include "ta_libc.h"
                     ^
compilation terminated.
make[1]: *** [IndicatorPlugin.o] Error 1
make[1]: Leaving directory `/usr/local/src/qtstalker-0.36/lib'
make: *** [sub-lib] Error 2
jaladhi@jaladhi-Compaq-510:/usr/local/src/qtstalker-0.36$ 



can any please guide me where i am going wrong and how to sort it out?

---

### Post by steeldriver on 2015-01-04
These look like some pretty old (unmaintained) projects - in particular I would be suspicious of the "ta-lib from debian package" that you found. I suggest you purge that (dpkg --purge *package_name*) and then configure / make / make install ta-lib from the source tarball [http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz](http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz)

If you configure it to install in /usr/local 

```

~/src/ta-lib$ ./configure --prefix=/usr/local

```

then the qtstalker ./configure should find ta_libc.h in /usr/local/include/ta-lib/

**Also please note that a pre-built version of qtstalker may be available from the repository --> [http://ubuntuforums.org/showthread.php?t=2107684](http://ubuntuforums.org/showthread.php?t=2107684)**

---

### Post by oldos2er on 2015-01-04
Moved to Packaging & Compiling Programs.

---

### Post by Yellow Pasque on 2015-01-05
Did you install the ta-lib-**dev** package? That would have the .h file in it

---

### Post by Jaladhi_R_Trivedi on 2015-01-07
Thanks for your concerns friends though I was not able to compile the qtstalker from source I did install qtstalker finally.

---

### Post by goog64 on 2015-01-19
> **Jaladhi_R_Trivedi said:**
> .............. I did install qtstalker finally.

Can you **please** tell me how you did it?? I've been trying on and off for over a year to install qtstalker!!
(Note: I am a very inexperienced Linux user.)

---

### Post by schragge on 2015-01-20
*qtstalker* [was removed]("https://bugs.debian.org/604583") from Debian (and thus from Ubuntu) as part of transition from Qt3 to Qt4. It's still present in *precise* (Ubuntu 12.04 LTS) repository, however. If you have Ubuntu 12.04  you can install *qtstalker* from the repository just as any other software there. Otherwise, in order to install it you'll need to compile Qt3 libraries first.

---

### Post by Jaladhi_R_Trivedi on 2015-01-23
this is what I did
first add the following lines in /etc/apt/source.list using the following command
gksudo gedit /etc/apt/source.list
this will open the file, at the end of the file add foll[COLOR=#000000][SIZE=2][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif]owing [/FONT][/SIZE][/COLOR]lines[COLOR=#000000][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][SIZE=2]
deb     [/SIZE][/FONT][/COLOR][[COLOR=#22229c][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][SIZE=2]http://www.zwets.com/debs[/SIZE][/FONT][/COLOR]]("http://www.zwets.com/debs")[COLOR=#000000][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][SIZE=2]    unstable/[/SIZE][/FONT][/COLOR]     
 [COLOR=#000000][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][SIZE=2]deb-src [/SIZE][/FONT][/COLOR][[COLOR=#22229c][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][SIZE=2]http://www.zwets.com/debs[/SIZE][/FONT][/COLOR]]("http://www.zwets.com/debs")[COLOR=#000000][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][SIZE=2]    unstable/[/SIZE][/FONT][/COLOR]  

    then save the file
    after this you will be able to see qtstalker 0.36 in your synaptic package manager and also ta-lib search for them and install them by selecting.

these requirements should be fulfilled before installing qtstalker

[LIST]
[*][Qt]("http://www.trolltech.com/") development library.     At least Qt 3.3.* version. Qt 4 not yet supported.
[*][Berkeley DB]("http://www.sleepycat.com/") database.     At least db-4.1 version. FreeBSD users are required to use the 4.3 version.
[*][TA-Lib]("http://ta-lib.org/") Technical Analysis Library.     At least ta-lib-0.3.0 version. See below.
[/LIST]
  install these packages before through synaptic manager
    

[LIST]
[*]**build-essential** (meta package for compiler etc.)
[*]**libdb4.4-dev** (for Berkely) ( I installed db-6.1.19)
[*]**qt3-dev-tools** (for qmake)
[*]**libqt3-mt-dev**
[*]install all the necessary packages which are asked through synaptic manager I had to install some packages from package.ubuntu.com
[*]i also installed libtool and automake with sudo apt-get install libtool automake
[*]After all this I typed this command in the terminal
[/LIST]
                     sudo apt-get update [COLOR=#000000][FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][SIZE=2]
                          sudo apt-get install qtstalker libqtstalker0 qtstalker-quote-plugins build-essential
  these got me qtstalker installed I hope this works for you as well[/SIZE][/FONT][/COLOR]    [h=4][/h]

---

### Post by Jaladhi_R_Trivedi on 2015-01-23
the version of qtstalker in precise is if I am not wrong is 0.32

---

