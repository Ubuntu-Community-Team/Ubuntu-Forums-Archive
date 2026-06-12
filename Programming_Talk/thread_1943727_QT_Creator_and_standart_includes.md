---
title: "QT Creator and standart includes"
date: 2012-03-20
forum: Programming Talk
---

### Post by CynicRus on 2012-03-20
Good day, gentelmens. I have some problem with a qt creator. I add to project file (*pro) - 
```

QMAKE_CFLAGS = -I/usr/include/
QMAKE_CXXFLAGS = -I/usr/include/

```
I add to code - #include <time.h> - include finded, this normal. But if i want include sys/socket.h, types.h - ```

 p, li { white-space: pre-wrap; }  [COLOR=#be1414]./CCafe/ccafe.cpp:6:36: fatal error: sys/types.h: no such file or directory[/COLOR]

```, i trying add full path to header, but
```

[COLOR=#be1414]./CCafe/ccafe.cpp:6:36: fatal error: usr/include/sys/types.h: no such file or directory[/COLOR]

```
How i can add standart includes to QT creator in ubuntu?

qt creator 2.2.1 and ubuntu 11.10
 p, li { white-space: pre-wrap; }

---

### Post by Zugzwang on 2012-03-20
> **CynicRus said:**
> Good day, gentelmens. I have some problem with a qt creator. I add to project file (*pro) - 
```

QMAKE_CFLAGS = -I/usr/include/
QMAKE_CXXFLAGS = -I/usr/include/

```


Remove these lines from your project file: "/usr/include" is a default include directory and shall never be explicitly mentioned.

> **CynicRus said:**
> 
I add to code - #include <time.h> - include finded, this normal. But if i want include sys/socket.h, types.h - ```

 p, li { white-space: pre-wrap; }  [COLOR=#be1414]./CCafe/ccafe.cpp:6:36: fatal error: sys/types.h: no such file or directory[/COLOR]

```


My guess is that you want to use header files from the package "libc6-dev", but you didn't install the package. Did you also check that you have the Ubuntu package "build-essential" installed?

---

### Post by CynicRus on 2012-03-20
Yep, installed. If i compile with g++ - all ok. If i remove lines from projecy file: time.h - file not found, but qt includes is founded.

---

### Post by Zugzwang on 2012-03-20
Let's try the following: Can you copy & paste your complete .pro project file here? Perhaps there is some other problem with your project file. Also, please copy & paste the output of running "make" from the terminal. It will show us how g++ is called, and help in identifying the root cause of your problem.

---

### Post by CynicRus on 2012-03-21
.pro
```

#-------------------------------------------------
#
# Project created by QtCreator 2012-03-19T12:46:48
#
#-------------------------------------------------

QT       += core gui

TARGET = CCafe
TEMPLATE = app


SOURCES += main.cpp\
        ccafewnd.cpp \
    stations.cpp \
    ccafe.cpp
LIBS += -lsqlite3
QMAKE_CFLAGS = -I/usr/include/
QMAKE_CXXFLAGS = -I/usr/include/

HEADERS  += ccafewnd.h \
    stations.h \
    ccafe.h \
    ccafe_struct.h

FORMS    += ccafewnd.ui
```
Make:
```
  p, li { white-space: pre-wrap; }  [COLOR=#3c3c3c]g++ -c -I/usr/include/ -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I../CCafe -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I../CCafe -I. -o ccafe.o ../CCafe/ccafe.cpp[/COLOR]

```

---

### Post by Zugzwang on 2012-03-21
Can you copy & paste the results of "cpp -v < /dev/null" here? There might be something wrong with your installation - your project file seems to be quite normal, and so does the compilation command.

Running "cpp -v < /dev/null" will tell you in which directories the preprocessor looks by default when trying to include files.

---

### Post by CynicRus on 2012-03-21
```

cynic@ndc:~$ cpp -v < /dev/null
&#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1102;&#1090;&#1089;&#1103; &#1074;&#1085;&#1091;&#1090;&#1088;&#1077;&#1085;&#1085;&#1080;&#1077; &#1089;&#1087;&#1077;&#1094;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1080;.
COLLECT_GCC=cpp
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6.1/lto-wrapper
&#1062;&#1077;&#1083;&#1077;&#1074;&#1072;&#1103; &#1072;&#1088;&#1093;&#1080;&#1090;&#1077;&#1082;&#1090;&#1091;&#1088;&#1072;: i686-linux-gnu
&#1055;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088;&#1099; &#1082;&#1086;&#1085;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1080;: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
&#1052;&#1086;&#1076;&#1077;&#1083;&#1100; &#1084;&#1085;&#1086;&#1075;&#1086;&#1087;&#1086;&#1090;&#1086;&#1095;&#1085;&#1086;&#1089;&#1090;&#1080;: posix
gcc &#1074;&#1077;&#1088;&#1089;&#1080;&#1103; 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
COLLECT_GCC_OPTIONS='-E' '-v' '-mtune=generic' '-march=i686'
 /usr/lib/gcc/i686-linux-gnu/4.6.1/cc1 -E -quiet -v -imultilib . -imultiarch i386-linux-gnu - -mtune=generic -march=i686 -fstack-protector
&#1085;&#1077;&#1089;&#1091;&#1097;&#1077;&#1089;&#1090;&#1074;&#1091;&#1102;&#1097;&#1080;&#1081; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; "/usr/local/include/i386-linux-gnu" &#1087;&#1088;&#1086;&#1080;&#1075;&#1085;&#1086;&#1088;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;
&#1085;&#1077;&#1089;&#1091;&#1097;&#1077;&#1089;&#1090;&#1074;&#1091;&#1102;&#1097;&#1080;&#1081; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; "/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../../i686-linux-gnu/include" &#1087;&#1088;&#1086;&#1080;&#1075;&#1085;&#1086;&#1088;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;
&#1087;&#1086;&#1088;&#1103;&#1076;&#1086;&#1082; &#1087;&#1086;&#1080;&#1089;&#1082;&#1072; &#1076;&#1083;&#1103; #include "...":
&#1087;&#1086;&#1088;&#1103;&#1076;&#1086;&#1082; &#1087;&#1086;&#1080;&#1089;&#1082;&#1072; &#1076;&#1083;&#1103; #include <...>:
 /usr/lib/gcc/i686-linux-gnu/4.6.1/include
 /usr/local/include
 /usr/lib/gcc/i686-linux-gnu/4.6.1/include-fixed
 /usr/include/i386-linux-gnu
 /usr/include
&#1050;&#1086;&#1085;&#1077;&#1094; &#1089;&#1087;&#1080;&#1089;&#1082;&#1072; &#1087;&#1086;&#1080;&#1089;&#1082;&#1072;.
# 1 "<stdin>"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "<stdin>"
COMPILER_PATH=/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/:/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/i686-linux-gnu/4.6.1/:/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/:/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../../lib/:/lib/i386-linux-gnu/:/lib/../lib/:/usr/lib/i386-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-E' '-v' '-mtune=generic' '-march=i686'


```

---

### Post by Zugzwang on 2012-03-21
@OP: The result of "cpp -v" looks perfectly fine. Note that "/usr/include" is already in the include paths of the c++ preprocessor.

I probably can't help you here. However, please double-check that "/usr/include/sys/types.h" is actually present on your system and that the error is actually the first one in your error list. 

If you want to try using absolute pathnames to the include files a try (which is not recommended, however), do not forget the leading "/", as you did in the first post. This can be seen from your error message: "./CCafe/ccafe.cpp:6:36: fatal error: usr/include/sys/types.h: no such file or directory" - There is no "/" in front of "usr" in this message.

---

