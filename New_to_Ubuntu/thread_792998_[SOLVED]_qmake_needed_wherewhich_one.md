---
title: "[SOLVED] qmake needed where/which one?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Fenris_rising on 2008-05-13
hi all
ive downloaded stellarium and am trying to install it.
however im getting one error message that stops it dead.

the error is 'qmake' not found or some such phrase. the
initial command is 'cmake ../..' . cmake is installed
ive searched the repo's for qt and qmake and there are 
stacks of 'qt's. i dont know which one(s) i need to install.
other than that its almost going swimmingly. 

any clues hints or large neon signs saying '[COLOR="Lime"]over here-->[/COLOR]'
would be gratefully appreciated.

---

### Post by Oldsoldier2003 on 2008-05-14
> **Fenris_rising said:**
> hi all
ive downloaded stellarium and am trying to install it.
however im getting one error message that stops it dead.

the error is 'qmake' not found or some such phrase. the
initial command is 'cmake ../..' . cmake is installed
ive searched the repo's for qt and qmake and there are 
stacks of 'qt's. i dont know which one(s) i need to install.
other than that its almost going swimmingly. 

any clues hints or large neon signs saying '[COLOR="Lime"]over here-->[/COLOR]'
would be gratefully appreciated.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```
If after installing build essential you still have problems please post the error output

---

### Post by Fenris_rising on 2008-05-14
hi there
thanks for the reply. i have done as you directed. only 2 files were updated and my build essential is upto date. here is the output of the Cmake command, the QT error is at the bottom.im using the official wiki site about installation. it could be im not understanding any dependancy issues, im a noob so some of it is going over my head.

fenris@lair:~$ cd Desktop
fenris@lair:~/Desktop$ tar zxf stellarium-0.9.1.tar.gz
fenris@lair:~/Desktop$ cd stellarium-0.9.1
fenris@lair:~/Desktop/stellarium-0.9.1$ mkdir -p builds/unix
fenris@lair:~/Desktop/stellarium-0.9.1$ cd builds/unix
fenris@lair:~/Desktop/stellarium-0.9.1/builds/unix$ cmake ../..
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Looking for include files HAVE_UNISTD_H
-- Looking for include files HAVE_UNISTD_H - found
-- Looking for include files HAVE_STRING_H
-- Looking for include files HAVE_STRING_H - found
-- Looking for include files HAVE_BYTESWAP_H
-- Looking for include files HAVE_BYTESWAP_H - found
-- Looking for timegm
-- Looking for timegm - found
-- Looking for mktime
-- Looking for mktime - found
-- Looking for tzset
-- Looking for tzset - found
-- Looking for pow10
-- Looking for pow10 - not found
-- Looking for setlocale
-- Looking for setlocale - found
-- Looking for snprintf
-- Looking for snprintf - found
CMake Error: Qt qmake not found!
-- Configuring done
fenris@lair:~/Desktop/stellarium-0.9.1/builds/unix$

im just looking at the cmake dl site i may need to get the latest version, not sure what i actually have.

---

### Post by Oldsoldier2003 on 2008-05-14
i'm downloading the source now to take a peek

---

### Post by Oldsoldier2003 on 2008-05-14
> **Oldsoldier2003 said:**
> i'm downloading the source now to take a peek
[http://stellarium.org/wiki/index.php/Build_Dependencies](http://stellarium.org/wiki/index.php/Build_Dependencies) suggests to me that you need lib libqt4-dev

---

### Post by Fenris_rising on 2008-05-14
hi all

thanks for your help. ive dl the 2.6 version of cmake. it has a gui option
the error output is the same. i think i may have cocked up when i looked for the qmake files in the synaptic. i have a feeling i typed qtmake. any way i have now searched synaptic for 'qmake' and it has brought up 4 files only, amongst which is the dev file. im installing now. fingers crossed and sorry if it turns out my ineptitude has wasted your time.

ok still no go heres the output of the gui.

Found Qt-Version 4.3.4
No sound support.
Boost version required: . Found: ..
CMake Error at /home/fenris/Documents/cmake-2.6.0-Linux-i386/share/cmake-2.6/Modules/FindBoost.cmake:553 (MESSAGE):
  Couldn't find the Boost libraries and/or include directory, or the version
  found is too old.  Please install the Boost libraries AND development
  packages.  You can set BOOST_ROOT, BOOST_INCLUDEDIR and BOOST_LIBRARYDIR to
  help find Boost.
Call Stack (most recent call first):
  CMakeLists.txt:106 (FIND_PACKAGE)

---

### Post by Oldsoldier2003 on 2008-05-14
No worries! We all have to learn some way or another, and compiling can get a bit tricky. Good luck on the build and let us know if it works out!

---

### Post by Fenris_rising on 2008-05-14
lol cheers see above post, i edited it with the latest error message from the gui output.

---

### Post by Oldsoldier2003 on 2008-05-14
```
sudo apt-get install libboost-dev
```

It looks like this thing has a ton of dependencies :)

---

### Post by Fenris_rising on 2008-05-14
cheers m8
did that. the gui version still screws up so im running through the terminal again. this time its compiling by the looks of it. lots of lines of green text scrolling up. ill let you know how it goes.

---

### Post by Fenris_rising on 2008-05-14
ok thanks for the help all. it works like a charm currently viewing the night sky from my real location and looking out the window its spot on lol.
now heres a shocking admission. ive been snooping around my OS and looking in add/remove...........guess what............<whimpers>........it was already in there as an option! oh well at least i learned from you chaps.

---

