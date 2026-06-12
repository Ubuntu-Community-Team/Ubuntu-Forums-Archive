---
title: "Basic question about proper directory to place source-compiled program in before make"
date: 2008-08-25
forum: Packaging and Compiling Programs
---

### Post by seaworthy4life on 2008-08-25
Or should I say basic question about cmake process.

From what I can tell, /usr/ is where all of the user applications go.  This is what I have to work with.  

I have this tarred file.

/home/justin/Desktop/lmms-0.4.0-beta2.tar.bz2

If I unzip it, I get this directory.

/home/justin/Desktop/LMMS/lmms-0.4.0-beta2

When I look at the install file, this is what I see.  Cmake 2.6.0 is installed ahead of schedule and all of the dependencies are installed.

> Building LMMS got quite simple since 0.4.0 as everything is managed
by cmake now. Therefore make sure you have CMake (>= 2.6.0 recommended) and
then run


mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install


This way an out-of-tree build is performed. You can also run "cmake ." directly
in the root of source-tree although this is not recommended. When performing an
out-of-tree build after there's already an in-tree build, make sure to run
"make distclean" before running cmake inside build-directory.

After running cmake (the 3rd command above) you can see a summary of things
that are going to be built into LMMS or built as plugins. Install the
according libraries and development files if a certain feature is not enabled.
Then remove CMakeCache.txt and run cmake again.


Should I move the lmms-0.4.0-beta2 dir under /usr/ , then go to /usr/lmms-0.4.0-beta2/ and then do the following, as it says?

mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install

---

### Post by seaworthy4life on 2008-08-25
What I don't understand is this part about the 'out-of-tree build", and how "running cmake in the root of source-tree is not recommended".  That's what it looks like if I run cmake in the lmms directory.  How do you run cmake (from any specific directory?) and apply it to the lmms unzipped directory?  I'm so close!

cmake /usr/lmms-0.4.0-beta2 ?????

---

### Post by seaworthy4life on 2008-08-26
Here are the contents of what will be /usr/lmms-0.4.0-beta2/

/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/build
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/buildtools
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/cmake
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/data
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/include
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/plugins
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/src
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/AUTHORS
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/build_mingw32
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/ChangeLog
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/CMakeLists.txt
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/configure
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/COPYING
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/INSTALL
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/lmms.1
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/lmms.rc.in
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/lmms.spec.in
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/lmmsconfig.h.in
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/README
/home/justin/Desktop/LMMS/lmms-0.4.0-beta2/TODO

---

### Post by seaworthy4life on 2008-08-26
This is what I am thinking, after reading more about cmake.  I move /home/justin/Desktop/LMMS/lmms-0.4.0-beta2/ to /usr/lmms-0.4.0-beta2/.  

mkdir build     
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install

It's saying that with a preferred out-of-source build, I should mkdir a different name than lmms-0.4.0-beta2, so the new subdir will be "build".  cd build will change directory to new build dir.  cmake ../ -DCMAKE_INSTALL_PREFIX=/usr from within build dir, then it does its thing whatever all that is.  Then type make, enter, and sudo make install, enter.  

Tis a bit out of my league.

---

### Post by WW on 2008-08-27
No, don't do any of that in /usr.

You can leave it where you had it, in /home/justin/Desktop/LMMS/lmms-0.4.0-beta2/.  Then run the commands as suggested, from that directory (i.e. first cd to /home/justin/Desktop/LMMS/lmms-0.4.0-beta2/).  It is the option **-DCMAKE_INSTALL_PREFIX=/usr** that tells where the installed program should be put.  Nothing is actually copied there until you run **sudo make install**, which is why that command must be run with sudo.  By the way, I recommend **/usr/local** instead of **/usr**.  It is generally a good idea to reserve **/usr** for files installed via .deb packages. 

E.g.:
```

cd /home/justin/Desktop/LMMS/lmms-0.4.0-beta2/
mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr/local
make
sudo make install

```

---

