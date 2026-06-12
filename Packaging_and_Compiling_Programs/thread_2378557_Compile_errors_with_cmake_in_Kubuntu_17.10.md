---
title: "Compile errors with cmake in Kubuntu 17.10"
date: 2017-11-24
forum: Packaging and Compiling Programs
---

### Post by AwaitingUserInput on 2017-11-24
I have never compiled software before, but I've read a couple tutorials and now have run into this error. Some searching on the error's text really didn't turn up anything useful.

The program I'm trying to compile is SoundKonverter, available here: [https://github.com/dfaust/soundkonverter](https://github.com/dfaust/soundkonverter)

```
.../soundkonverter-master/src/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
-- No qmake Qt5 binary found. Can't check QT_INSTALL_PREFIX
-- Looking for __GLIBC__
-- Looking for __GLIBC__ - found
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_DATE_TIME
-- Performing Test HAVE_DATE_TIME - Success
CMake Error at CMakeLists.txt:33 (find_package):
  By not providing "FindQt5.cmake" in CMAKE_MODULE_PATH this project has
  asked CMake to find a package configuration file provided by "Qt5", but
  CMake did not find one.

  Could not find a package configuration file provided by "Qt5" with any of
  the following names:

    Qt5Config.cmake
    qt5-config.cmake

  Add the installation prefix of "Qt5" to CMAKE_PREFIX_PATH or set "Qt5_DIR"
  to a directory containing one of the above files.  If "Qt5" provides a
  separate development package or SDK, be sure it has been installed.


-- Configuring incomplete, errors occurred!
See also "/home/xxxxx/Compiled/soundkonverter-master/src/build/CMakeFiles/CMakeOutput.log". 

```

---

### Post by Yellow Pasque on 2017-11-24
[https://launchpad.net/~dominik-stadler/+archive/ubuntu/dsta-artful-ppa](https://launchpad.net/~dominik-stadler/+archive/ubuntu/dsta-artful-ppa)

EDIT: Actually, the build failed in that PPA. Sorry.

---

### Post by ubname on 2017-11-24
In "src" dir you find an INSTALL file, the first source for info you should look to compile,

you can use make install without sudo and install somewhere in your home dir to 
avoid messing with you system

```
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kde-config --prefix` ..
make
make install
```

---

### Post by slickymaster on 2017-11-24
*Thread moved to **Packaging and Compiling Programs**.*

---

### Post by Yellow Pasque on 2017-11-24
```
sudo apt-get install intltool libcdparanoia-dev libkcddb-dev qtbase5-dev extra-cmake-modules libtag1-dev
```
^That should get you started and past the error you quoted. Unfortunately, the documentation on their wiki is a bit old and doesn't give a good list of the -dev packages needed for the newer KDE5 version. I'll play with it a bit and see if I can give you any other tips.

---

### Post by mc4man on 2017-11-24
The build in ppa didn't 'fail' per se , it has a dependency wait on a non existent packagename (was renamed to libkf5cddb-dev for 17.10
That build is for sk 2.2.2 which should be ok in 17.10
If trying to build a 3.x version one may need to look at some of the Team Kubuntu ppa's for updated files

---

### Post by Yellow Pasque on 2017-11-24
This should help too:
```
sudo apt-get install libkf5cddb-dev libphonon4qt5-dev libkf5widgetsaddons-dev libkf5kdelibs4support-dev libkf5configwidgets-dev libkf5config-dev libkf5solid-dev libkf5kio-dev libkf5xmlgui-dev libkf5i18n-dev python-six python-scour
```

---

### Post by AwaitingUserInput on 2017-11-24
> **Temüjin said:**
> This should help too:
```
sudo apt-get install libkf5cddb-dev libphonon4qt5-dev libkf5widgetsaddons-dev libkf5kdelibs4support-dev libkf5configwidgets-dev libkf5config-dev libkf5solid-dev libkf5kio-dev libkf5xmlgui-dev libkf5i18n-dev python-six python-scour
```

Thank you. So it looks like I had missing libraries and dependencies, which this is adding to my system? After I get this one compiled, I want to compile the latest version of Gimp. I started with SoundKonverter first because it looked like the easier one. I'm just trying to understand generally what the problem was with the installation, and how you knew how to fix it. I have not installed those packages next, will do so later today and report back if it works.

---

### Post by Yellow Pasque on 2017-11-24
> So it looks like I had missing libraries and dependencies, which this is adding to my system?
Yes. I tried to build it and it spit out a bunch of errors about missing components. So the fix is finding the corresponding packages (usually ending with '-dev'). Synaptic is very useful in this regard.

---

