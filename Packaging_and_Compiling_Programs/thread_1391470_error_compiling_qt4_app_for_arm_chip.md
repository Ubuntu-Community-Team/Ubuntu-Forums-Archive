---
title: "error compiling qt4 app for arm chip"
date: 2010-01-26
forum: Packaging and Compiling Programs
---

### Post by KyferEz on 2010-01-26
I am attempting to follow a guide to cross compile a qt4 app for an arm based board. 

Mostly, everything was going Ok, until I got to this error, and now I'm really stuck.

The error is:
```

user@user-desktop:~/project$ source source-me.txt
Setting up dev env for Ångström
Altered environment for OE Development
user@user-desktop:~/project/build$ bitbake lcdslider
NOTE: Handling BitBake files: - (7983/7983) [100 %]
NOTE: Parsing finished. 7346 cached, 312 parsed, 325 skipped, 0 masked.
NOTE: Resolving any missing task queue dependencies
NOTE: Runtime target 'qt4-embedded-gles' is unbuildable, removing...
Missing or unbuildable dependency chain was: ['qt4-embedded-gles', 'virtual/egl']
ERROR: '[]' RDEPENDS/RRECOMMENDS or otherwise requires the runtime entity 'virtual/egl' but it wasn't found in any PACKAGE or RPROVIDES variables
NOTE: Runtime target 'virtual/egl' is unbuildable, removing...
Missing or unbuildable dependency chain was: ['virtual/egl']
NOTE: Preparing runqueue
NOTE: Executing runqueue
NOTE: Running task 1471 of 2099 (ID: 5, /home/user/project/openembedded/recipes/lcdslider/lcdslider.bb, do_configure)
ERROR: function do_configure failed
ERROR: log data follows (/media/320gb-2/project/build/tmp/work/armv4t-angstrom-linux-gnueabi/lcdslider-1.0-r0/temp/log.do_configure.16959)
| Qt QTGUI library not found.
| Qt QTCORE library not found.
| CMake Error at /media/320gb-2/project/build/tmp/staging/i686-linux/usr/share/cmake-2.6/Modules/FindQt4.cmake:1080 (FILE):
|   file Internal CMake error when trying to open file:
|   /media/320gb-2/project/build/tmp/work/armv4t-angstrom-linux-gnueabi/lcdslider-1.0-r0/lcdslider/images.qrc
|   for reading.
| Call Stack (most recent call first):
|   CMakeLists.txt:19 (QT4_ADD_RESOURCES)
| 
| 
| -- Configuring incomplete, errors occurred!
NOTE: Task failed: /media/320gb-2/project/build/tmp/work/armv4t-angstrom-linux-gnueabi/lcdslider-1.0-r0/temp/log.do_configure.16959
ERROR: TaskFailed event exception, aborting
ERROR: Build of /home/user/project/openembedded/recipes/lcdslider/lcdslider.bb do_configure failed
ERROR: Task 5 (/home/user/project/openembedded/recipes/lcdslider/lcdslider.bb, do_configure) failed
NOTE: Tasks Summary: Attempted 1470 tasks of which 1470 didn't need to be rerun and 1 failed.
ERROR: '/home/user/project/openembedded/recipes/lcdslider/lcdslider.bb' failed

```

I went into package manager and have all repositories checked except sources. Then in the quicksearch I typed libqt4 and installed everything there except:
libqt4-sql-psql
libqt4-sql-sqlite2
libqt4-webkit-dbg
libqt4-xmlpatterns-dbg
libqt4-ruby1.8-dev and -examples
uim-qt

And I still get the qt4 core not found error.

I am using bitbake, following this tutorial: [http://www.developmentboard.net/index.php/article/Creating+Qt4+project+with+bitbake+for+Mini2440V2](http://www.developmentboard.net/index.php/article/Creating+Qt4+project+with+bitbake+for+Mini2440V2)

I can successfully do bitbake qt4-embedded
however bitbake lcdslider fails with the above error. Please help!

---

### Post by KyferEz on 2010-01-26
Well, I fixed part of the error, so now it finds QT4:

```
CMake is using a file called FindQt4.cmake to look for Qt4 libraries, while
it would work with the qt4×11 of Qt, Qt4-embedded produce libraries that
end with an E, making it inefficient only because of that missing E.
Since the problem has been corrected in a more recent version of cmake,
another cleaner solution is to download the last version of the
FindQt4.cmake file here and to replace yours. This will also work if you
have a native cmake (as long as your version is recent enough to handle
stuff in that .cmake file).

Otherwise, you can change add the E manually (dirty). If you use a cmake
from OE (ie you didn’t ASSUME cmake-native in your local.conf), just edit
the file
/path/to/your/build/tmp-folder/staging/i686-linux/usr/share/cmake-2.6/Modules/FindQt4.cmake

Line 696, add ${QT_MODULE}E, it should now look like this:

NAMES ${QT_MODULE} ${QT_MODULE}4 ${QT_MODULE}E
```



But still not working yet:
```

NOTE: Running task 1471 of 2099 (ID: 5,
/home/user/project/openembedded/recipes/lcdslider/lcdslider.bb,
do_configure)
ERROR: function do_configure failed
ERROR: log data follows
(/media/320gb-2/project/build/tmp/work/armv4t-angstrom-linux-gnueabi/lcdslider-1.0-r0/temp/log.do_configure.17589)
| -- Found Qt-Version 4.6.0
| CMake Error at
/media/320gb-2/project/build/tmp/staging/i686-linux/usr/share/cmake-2.6/Modules/
FindQt4.cmake:1080
(FILE):
|   file Internal CMake error when trying to open file:
|  
/media/320gb-2/project/build/tmp/work/armv4t-angstrom-linux-gnueabi/lcdslider-1.
0-r0/lcdslider/images.qrc
|   for reading.
| Call Stack (most recent call first):
|   CMakeLists.txt:19 (QT4_ADD_RESOURCES)
| 
| 
| -- Configuring incomplete, errors occurred!
NOTE: Task failed:
/media/320gb-2/project/build/tmp/work/armv4t-angstrom-linux-gnueabi/lcdslider-1.
0-r0/temp/log.do_configure.17589
ERROR: TaskFailed event exception, aborting
ERROR: Build of
/home/user/project/openembedded/recipes/lcdslider/lcdslider.bb do_configure
failed
ERROR: Task 5
(/home/user/project/openembedded/recipes/lcdslider/lcdslider.bb,
do_configure) failed
NOTE: Tasks Summary: Attempted 1470 tasks of which 1470 didn't need to be
rerun and 1 failed.
ERROR: '/home/user/project/openembedded/recipes/lcdslider/lcdslider.bb'
failed

```

What is going on here? I've checked for the file below and it doesn't exist. I'm not sure what it is or where it's supposed to come from.
/media/320gb-2/project/build/tmp/work/armv4t-angstrom-linux-gnueabi/lcdslider-1.0-r0/lcdslider/images.qrc

Thanks for any help!!

---

