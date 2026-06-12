---
title: "Building unity from source"
date: 2011-09-03
forum: Packaging and Compiling Programs
---

### Post by snip3r8 on 2011-09-03
Im trying to build unity from source,when i run
```

cmake .. -DCMAKE_INSTALL_PREFIX=/opt/unity

```

i get

```
WARNING:
"FindCompiz.cmake" file not found in cmake module directories.
It should be installed to allow building of external compiz packages.
Call "sudo make findcompiz_install" to install it.

```

the instructions are as follows

```

• Build Compiz GLib
  
  This is taken from http://wiki.ubuntu.com/Unity/InstallationGuideFromSource and
  was originally authored by Sam:

  core:

    git clone git://git.compiz.org/users/dbo/compiz-with-glib-mainloop
    cd compiz-with-glib-mainloop
    mkdir build
    cd build
    cmake .. -DCMAKE_INSTALL_PREFIX=/opt/unity  #this is the instruction im currently trying to follow
    make
    sudo make findcompiz_install
    sudo make install

  exporting paths:

    export PKG_CONFIG_PATH=/opt/unity/lib/pkgconfig:${PKG_CONFIG_PATH}
    export LD_LIBRARY_PATH=/opt/unity/lib:${LD_LIBRARY_PATH}
    export LD_RUN_PATH=/opt/unity/lib:${LD_RUN_PATH}

  libcompizconfig:

    git clone git://git.compiz.org/compiz/compizconfig/libcompizconfig
    cd libcompizconfig
    mkdir build
    cd build
    cmake .. -DCMAKE_INSTALL_PREFIX=/opt/unity
    make
    sudo make install

  compizconfig-python:

    git clone git://git.compiz.org/compiz/compizconfig/compizconfig-python
    cd compizconfig-python
    python setup.py install --prefix=/opt/unity

  ccsm:

    git clone git://git.compiz.org/compiz/compizconfig/ccsm
    cd ccsm
    python setup.py install --prefix=/opt/unity

  plugins-main:

    git clone git://git.compiz.org/compiz/plugins-main
    cd plugins-main
    git submodule init
    git pull origin master
    git submodule update
    mkdir build
    cd build
    cmake .. -DCMAKE_INSTALL_PREFIX=/opt/unity
    make
    sudo make install

  plugins-extra:

    git clone git://git.compiz.org/compiz/plugins-extra
    cd plugins-extra
    git submodule init
    git pull origin master
    git submodule update
    mkdir build
    cd build
    cmake .. -DCMAKE_INSTALL_PREFIX=/opt/unity
    make
    sudo make install


• Build Nux

  bzr branch lp:nux
  cd nux
  ./autogen.sh --disable-documentation --prefix=/opt/unity
  make
  sudo make install


• Build Unity

  bzr branch lp:unity
  cd unity
  mkdir build; cd build
  cmake .. -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=package -DCMAKE_INSTALL_PREFIX=/opt/unity
  make
  sudo make install



```

---

### Post by cariboo on 2011-09-04
This is definitely not an Absolute Beginner question. Moved.

---

### Post by snip3r8 on 2011-09-10
Bump

---

### Post by SevenMachines on 2011-09-10
Does (still in the build sub-directory),
```
$ rm CMakeCache.txt
$ sudo make findcompiz_install
$ cmake .. -DCMAKE_INSTALL_PREFIX=/opt/unity
```not work?

---

### Post by zemikit on 2011-12-26
Hi.

I try to build unity from trunk, but have this problems:

zemik@zemik-laptop:~/workspace/unity/build$ cmake .. -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=local -DCMAKE_INSTALL_PREFIX=/opt/unity
-- checking for modules 'compiz;nux-2.0 >= 2.0.0;libbamf3;dee-1.0;gio-2.0;gio-unix-2.0;dbusmenu-glib-0.4;x11;libstartup-notification-1.0;gthread-2.0;indicator3-0.4;atk;unity-misc >= 0.4.0;gconf-2.0;libutouch-geis;gtk+-3.0 >= 3.1;sigc++-2.0;json-glib-1.0;libnotify;gnome-desktop-3.0;gdu;unity>=4.99.0'
--   package 'unity>=4.99.0' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:266 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:320 (_pkg_check_modules_internal)
  tests/CMakeLists.txt:19 (pkg_check_modules)


-- checking for modules 'glib-2.0;gio-2.0;dee-1.0;sigc++-2.0;nux-core-2.0;gdk-pixbuf-2.0;unity'
--   package 'unity' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:266 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:320 (_pkg_check_modules_internal)
  UnityCore/CMakeLists.txt:2 (pkg_check_modules)


-- checking for modules 'compiz;nux-2.0 >= 2.0.0;libbamf3;dee-1.0;gio-2.0;gio-unix-2.0;dbusmenu-glib-0.4;x11;libstartup-notification-1.0;gthread-2.0;indicator3-0.4;atk;unity-misc >= 0.4.0;gconf-2.0;libutouch-geis;gtk+-3.0 >= 3.1;sigc++-2.0;json-glib-1.0;libnotify;gnome-desktop-3.0;gdu;unity>=4.0.0'
--   package 'unity>=4.0.0' not found
CMake Error at /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:266 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPkgConfig.cmake:320 (_pkg_check_modules_internal)
  standalone-clients/CMakeLists.txt:12 (pkg_check_modules)


-- GSettings schemas will be installed into /usr/share/glib-2.0/schemas/
-- Configuring incomplete, errors occurred!


How I can solve that?

---

### Post by zemikit on 2011-12-26
sudo apt-get build-dep unity :)

---

