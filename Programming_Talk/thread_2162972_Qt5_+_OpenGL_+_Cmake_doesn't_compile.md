---
title: "Qt5 + OpenGL + Cmake doesn't compile"
date: 2013-07-16
forum: Programming Talk
---

### Post by bird1500 on 2013-07-16
I'd like to use Qt5 to do OpenGL but I wanna use CMake instead of qmake to compile it cause I know it already, but a simple example with Qt5+OpenGL doesn't compile (all files attached):
```

Linking CXX executable app
CMakeFiles/app.dir/main.cpp.o:(.data.rel.ro._ZTI14TriangleWindow[_ZTI14TriangleWindow]+0x10): undefined reference to `typeinfo for OpenGLWindow'
CMakeFiles/app.dir/main.cpp.o:(.data.rel.ro._ZTV14TriangleWindow[_ZTV14TriangleWindow]+0x10): undefined reference to `OpenGLWindow::metaObject() const'
CMakeFiles/app.dir/main.cpp.o:(.data.rel.ro._ZTV14TriangleWindow[_ZTV14TriangleWindow]+0x18): undefined reference to `OpenGLWindow::qt_metacast(char const*)'
CMakeFiles/app.dir/main.cpp.o:(.data.rel.ro._ZTV14TriangleWindow[_ZTV14TriangleWindow]+0x20): undefined reference to `OpenGLWindow::qt_metacall(QMetaObject::Call, int, void**)'
CMakeFiles/app.dir/openglwindow.cpp.o: In function `OpenGLWindow::OpenGLWindow(QWindow*)':
openglwindow.cpp:(.text+0x1a): undefined reference to `vtable for OpenGLWindow'
CMakeFiles/app.dir/openglwindow.cpp.o: In function `OpenGLWindow::~OpenGLWindow()':
openglwindow.cpp:(.text+0x81): undefined reference to `vtable for OpenGLWindow'
collect2: error: ld returned 1 exit status
make[2]: *** [app] Error 1
make[1]: *** [CMakeFiles/app.dir/all] Error 2
make: *** [all] Error 2

```

Anyone knows if it's me, cmake or qt5 to blame?

I got Ubuntu 13.04 amd64, nvidia proprietary driver.

---

### Post by bird1500 on 2013-07-16
Basically it boils down to [having to handle the "moc" thingy]("http://qt.developpez.com/doc/5.0-snapshot/cmake-manual/")  and qt5 specific stuff, for a simple GL hello world example cmake should look like this:

```

cmake_minimum_required(VERSION 2.8.8)
project(App)

#disable -rdynamic
SET(CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS "")
SET(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")

# Find includes in corresponding build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)
# Instruct CMake to run moc automatically when needed.
set(CMAKE_AUTOMOC ON)

add_definitions(-O2 -D_FILE_OFFSET_BITS=64 -fPIC) 

find_package(PkgConfig)

find_package(Qt5Core)
find_package(Qt5Widgets)
find_package(Qt5Gui)
find_package(Qt5OpenGL)

add_executable(app
    main.cpp
    window.cpp window.h
    glwidget.cpp glwidget.h
    qtlogo.h qtlogo.cpp
    )

qt5_use_modules(app Core Gui Widgets OpenGL)
target_link_libraries(app GL)

```

And the warning when you run the compiled app "QBackingStore::flush() called with non-exposed window, behavior is undefined" apparently has been fixed in qt 5.1
Imo too much hassle.

---

