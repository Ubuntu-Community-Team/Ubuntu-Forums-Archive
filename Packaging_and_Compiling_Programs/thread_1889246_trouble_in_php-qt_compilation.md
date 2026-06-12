---
title: "trouble in php-qt compilation"
date: 2011-12-01
forum: Packaging and Compiling Programs
---

### Post by devashish22 on 2011-12-01
i m using Ubuntu Oneiric and i downloaded the php-qt sources ...

but when i compile i get the error message

```
make
2% Generating smokedata.cpp, x_1.cpp, x_2.cpp, x_3.cpp, x_4.cpp, x_5.cpp, x_6.cpp, x_7.cpp, x_8.cpp, x_9.cpp, x_10.cpp, x_11.cpp, x_12.cpp, x_13.cpp, x_14.cpp, x_15.cpp, x_16.cpp, x_17.cpp, x_18.cpp, x_19.cpp, x_20.cpp
Checking how Qt was built... 
Threshold is set to 10
Number of defines to be tested : 45/78

Found 44 predefined symbols in qglobal.h
Trying to compile and link a small program...             
FAILED : check your configuration.
Failed program was:

        #include <QtGui/qapplication.h>
        int main( int argc, char **argv )
        {
            QApplication foo( argc, argv );
            return 0;
        }
    
Compiled with:
/usr/bin/c++  -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/usr/share/qt4/mkspecs/default -I/usr/include/qt4/Qt -I/usr/include/qt4  -lpthread /usr/lib/i386-linux-gnu/libQtCore.so /usr/lib/i386-linux-gnu/libQtNetwork.so /usr/lib/i386-linux-gnu/libQtSql.so /usr/lib/i386-linux-gnu/libQtXml.so /usr/lib/i386-linux-gnu/libQtGui.so /usr/lib/i386-linux-gnu/libQtUiTools.a /usr/lib/i386-linux-gnu/libQtSvg.so /usr/lib/i386-linux-gnu/libQtOpenGL.so /usr/lib/i386-linux-gnu/libQt3Support.so  -o ./3327-qtguess ./3327-qtguess.cpp
Compiler output:
/tmp/ccmygCLe.o: In function `main':
3327-qtguess.cpp:(.text+0x28): undefined reference to `QApplication::QApplication(int&, char**, int)'
3327-qtguess.cpp:(.text+0x39): undefined reference to `QApplication::~QApplication()'
collect2: ld returned 1 exit status

make[2]: *** [smoke/qt/smokedata.cpp] Error 1
make[1]: *** [smoke/qt/CMakeFiles/smokeqt.dir/all] Error 2
make: *** [all] Error 2

```

---

### Post by SevenMachines on 2011-12-01
> ```
/usr/bin/c++  -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/usr/share/qt4/mkspecs/default -I/usr/include/qt4/Qt -I/usr/include/qt4  -lpthread /usr/lib/i386-linux-gnu/libQtCore.so /usr/lib/i386-linux-gnu/libQtNetwork.so /usr/lib/i386-linux-gnu/libQtSql.so /usr/lib/i386-linux-gnu/libQtXml.so /usr/lib/i386-linux-gnu/libQtGui.so /usr/lib/i386-linux-gnu/libQtUiTools.a /usr/lib/i386-linux-gnu/libQtSvg.so /usr/lib/i386-linux-gnu/libQtOpenGL.so /usr/lib/i386-linux-gnu/libQt3Support.so  -o ./3327-qtguess ./3327-qtguess.cpp
```Libs need to come after the source in this case due to the default --as-needed being passed to the compiler in ubuntu (see many... many threads for more detail :))
In the source directory...

smoke/qt/qtguess.pl.cmake:45
```
 my $ccmd = "$cc $ccflags $allinc $alllib -o $tmp $tmp.cpp";
```needs to be
```
 my $ccmd = "$cc $ccflags $allinc -o $tmp $tmp.cpp $alllib";
```then it will build..
```
$ mkdir build
$ cd build
$ cmake ../
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Found Perl: /usr/bin/perl 
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
.........

$ make
[  2%] Generating smokedata.cpp, x_1.cpp, x_2.cpp, x_3.cpp, x_4.cpp, x_5.cpp, x_6.cpp, x_7.cpp, x_8.cpp, x_9.cpp, x_10.cpp, x_11.cpp, x_12.cpp, x_13.cpp, x_14.cpp, x_15.cpp, x_16.cpp, x_17.cpp, x_18.cpp, x_19.cpp, x_20.cpp
Checking how Qt was built... 
Threshold is set to 10
Number of defines to be tested : 45/78

Found 45 predefined symbols in qglobal.h
Trying to compile and link a small program...             OK
Testing QT_NO_DRAWUTIL                                    *Undefined*
Testing QT_NO_DIAL                                        *Undefined*
Testing QT_NO_SIZEGRIP                                    *Undefined*
Testing QT_NO_WHATSTHIS                                   *Undefined*
Testing QT_NO_LABEL                                       *Undefined*
.......
```well, up to a point....
```
Scanning dependencies of target smokeqt
[  4%] Building CXX object smoke/qt/CMakeFiles/smokeqt.dir/smokedata.o
[  6%] Building CXX object smoke/qt/CMakeFiles/smokeqt.dir/x_1.o
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp: In static member function 'static void x_QAbstractGraphicsShapeItem::x_0(Smoke::Stack)':
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1944:130: error: cannot allocate an object of abstract type 'x_QAbstractGraphicsShapeItem'
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1940:7: note:   because the following virtual functions are pure within 'x_QAbstractGraphicsShapeItem':
/usr/include/qt4/Qt/qgraphicsitem.h:331:20: note:     virtual QRectF QGraphicsItem::boundingRect() const
/usr/include/qt4/Qt/qgraphicsitem.h:352:18: note:     virtual void QGraphicsItem::paint(QPainter*, const QStyleOptionGraphicsItem*, QWidget*)
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp: In static member function 'static void x_QAbstractGraphicsShapeItem::x_1(Smoke::Stack)':
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1951:100: error: cannot allocate an object of abstract type 'x_QAbstractGraphicsShapeItem'
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1940:7: note:   since type 'x_QAbstractGraphicsShapeItem' has pure virtual functions
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp: In static member function 'static void x_QAbstractGraphicsShapeItem::x_2(Smoke::Stack)':
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1958:72: error: cannot allocate an object of abstract type 'x_QAbstractGraphicsShapeItem'
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1940:7: note:   since type 'x_QAbstractGraphicsShapeItem' has pure virtual functions
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp: In static member function 'static void x_QAbstractGraphicsShapeItem::x_9(Smoke::Stack)':
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1995:181: error: cannot allocate an object of abstract type 'x_QAbstractGraphicsShapeItem'
/home/niall/Downloads/phpqt/build/smoke/qt/x_1.cpp:1940:7: note:   since type 'x_QAbstractGraphicsShapeItem' has pure virtual functions
make[2]: *** [smoke/qt/CMakeFiles/smokeqt.dir/x_1.o] Error 1
make[1]: *** [smoke/qt/CMakeFiles/smokeqt.dir/all] Error 2
make: *** [all] Error 2

```Doesn't look like php-qt has seen any work for 4/5 years, don't know if it's been ditched/renamed/replaced or whatever. It's likely to be a bit broken after that sort of time frame though. Better check with some experienced qt-ists and see if theres a better option.

---

