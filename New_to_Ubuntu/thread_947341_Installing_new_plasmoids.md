---
title: "Installing new plasmoids"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by browny254 on 2008-10-14
Hi, Im trying to install some plasmoids using the following instructions

    * tar -xvf plasmoid.tar.gz
    * cd plasmoid
    * mkdir build
    * cd build
    * cmake -DCMAKE_INSTALL_PREFIX=`kde4-config –prefix` ..
    * make
    * sudo make install OR su -c “make install”

but i cant get past the cmake/make step, this is what i get

```
$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config –prefix` ..
kde4-config: Unexpected argument '–prefix'.
kde4-config: Use --help to get a list of available command line options.
-- Found Qt-Version 4.4.1 (using /usr/bin/qmake)
-- Found X11: /usr/lib/libX11.so
-- Found Automoc4: /usr/bin/automoc4
-- Found Perl: /usr/bin/perl
-- Found KDE 4.1 include dir: /usr/lib/kde4/include
-- Found KDE 4.1 library dir: /usr/lib/kde4/lib
-- Found KDE4 kconfig_compiler preprocessor: /usr/lib/kde4/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
CMake Error at /usr/lib/kde4/share/kde4/apps/cmake/modules/FindPackageHandleStandardArgs.cmake:53 (MESSAGE):
  Could not find REQUIRED package Plasma
Call Stack (most recent call first):
  /usr/lib/kde4/share/kde4/apps/cmake/modules/FindPlasma.cmake:30 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:7 (find_package)


-- Configuring done
```
```
$ make
make: *** No targets specified and no makefile found.  Stop.

```


anyone know what im doing wrong or dont have installed?

---

### Post by browny254 on 2008-10-14
ok i found I didnt have libplasma-dev installed, but now im getting another error and have no idea on this one...

```
$ make                
[  6%] Generating ui_pluginwidgetbase.h                                         
Generating iconmanager.moc                                                      
Generating popupdialog.moc                                                      
Generating resizedialog.moc                                                     
Generating quickaccess.moc                                                      
Generating button.moc                                                           
Generating itemview.moc                                                         
Generating settings.moc                                                         
Generating pluginwidget.moc                                                              
Generating dirmodel.moc                                                                  
Generating moc_label.cpp                                                                 
Generating moc_pluginmodel.cpp                                                           
[ 13%] Generating ui_quickaccessConfig.h
Scanning dependencies of target plasma_applet_quickaccess
[ 20%] Building CXX object CMakeFiles/plasma_applet_quickaccess.dir/plasma_applet_quickaccess_automoc.o
[ 26%] Building CXX object CMakeFiles/plasma_applet_quickaccess.dir/quickaccess.o
/home/andrew/Programs/Plasmoids/quickaccess-0.7.1/quickaccess.cpp:34:29: error: konq_operations.h:No such file or directory
/home/andrew/Programs/Plasmoids/quickaccess-0.7.1/quickaccess.cpp: In member function &#8216;virtual void QuickAccess::dropEvent(QGraphicsSceneDragDropEvent*)&#8217;:
/home/andrew/Programs/Plasmoids/quickaccess-0.7.1/quickaccess.cpp:276: error: &#8216;KonqOperations&#8217; hasnot been declared
make[2]: *** [CMakeFiles/plasma_applet_quickaccess.dir/quickaccess.o] Error 1
make[1]: *** [CMakeFiles/plasma_applet_quickaccess.dir/all] Error 2
make: *** [all] Error 2
```

---

### Post by Farmer of Bricks on 2009-01-03
Have you tried installing the build-essential package?
```

sudo apt-get install build-essential

```
installing it might help with compiling plasmoids.

---

### Post by Azathoth_ on 2010-10-30
```
sudo apt-get install libkonq5-dev
```

---

