---
title: "Qt program make error"
date: 2012-06-25
forum: Programming Talk
---

### Post by pellyhawk on 2012-06-25
I have a c/c++ program and want to build with qt. My qt is located in /usr/local/Trolltech/Qt-4.7.3-pc. After conduct command:
```
qmake -project
qmake
make
```

I got these result:
```
ian@mike-desktop:/mnt/hgfs/VBox_Shared/SeaTools$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o downloaddialog.o downloaddialog.cpp
downloaddialog.cpp:2:21: error: QtNetwork: No such file or directory
In file included from downloaddialog.cpp:4:
downloaddialog.h:6:22: error: QTcpSocket: No such file or directory
In file included from downloaddialog.cpp:4:
downloaddialog.h:49: error: ‘QAbstractSocket’ has not been declared
downloaddialog.h:49: error: expected ‘,’ or ‘...’ before ‘socketError’
downloaddialog.h:50: error: ‘QAbstractSocket’ has not been declared
downloaddialog.h:50: error: expected ‘,’ or ‘...’ before ‘socketState’
downloaddialog.h:80: error: ISO C++ forbids declaration of ‘QTcpSocket’ with no type
downloaddialog.h:80: error: expected ‘;’ before ‘*’ token
downloaddialog.cpp: In constructor ‘DownloadDialog::DownloadDialog(QWidget*)’:
downloaddialog.cpp:29: error: ‘tcpClient’ was not declared in this scope
downloaddialog.cpp:29: error: expected type-specifier before ‘QTcpSocket’
downloaddialog.cpp:29: error: expected ‘;’ before ‘QTcpSocket’
downloaddialog.cpp: In member function ‘void DownloadDialog::on_btStopTransfer_clicked()’:
downloaddialog.cpp:426: error: ‘tcpClient’ was not declared in this scope
downloaddialog.cpp: In member function ‘void DownloadDialog::on_btQuit_clicked()’:
downloaddialog.cpp:436: error: ‘tcpClient’ was not declared in this scope
downloaddialog.cpp: In member function ‘void DownloadDialog::startDownloadFiles()’:
downloaddialog.cpp:509: error: ‘tcpClient’ was not declared in this scope
downloaddialog.cpp:510: error: ‘QHostAddress’ was not declared in this scope
downloaddialog.cpp: At global scope:
downloaddialog.cpp:583: error: variable or field ‘onSocketStateChanged’ declared void
downloaddialog.cpp:583: error: ‘QAbstractSocket’ has not been declared
myclient.h:126: warning: ‘SyncChar’ defined but not used
make: *** [downloaddialog.o] Error 1

```

I conduct:
```
find / -name QtNetwork
```
and got many results, some of which are permission denied

I conduct:
```
find / -name access_log 2>/dev/null QtNetwork
```
and got```
find: paths must precede expression: QtNetwork
```(Is this command line [COLOR="red"]not right[/COLOR]?)

More importantly,QAbstractSocket cannot be find in /usr/local/Trolltech/Qt-4.7.3-pc/include, While ```
ian@mike-desktop:/usr/local/Trolltech/Qt-4.7.3-pc/include$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/Trolltech/Qt-4.7.3-pc/include
ian@mike-desktop:/usr/local/Trolltech/Qt-4.7.3-pc/include$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/Trolltech/Qt-4.7.3-pc/include: No such file or directory
ian@mike-desktop:/usr/local/Trolltech/Qt-4.7.3-pc/include$
ian@mike-desktop:/usr/local/Trolltech/Qt-4.7.3-pc/include$ ls -al
total 180
drwxr-xr-x 21 root root  4096 2012-06-25 23:35 .
drwxr-xr-x 13 root root  4096 2012-06-26 01:31 ..
drwxr-xr-x  2 root root 36864 2012-06-26 01:31 Qt
drwxr-xr-x  2 root root 12288 2012-06-26 01:30 Qt3Support
drwxr-xr-x  2 root root 20480 2012-06-26 01:28 QtCore
drwxr-xr-x  2 root root  4096 2012-06-26 01:30 QtDeclarative
drwxr-xr-x  2 root root  4096 2012-06-26 01:31 QtDesigner
drwxr-xr-x  2 root root 36864 2012-06-26 01:30 QtGui
drwxr-xr-x  2 root root  4096 2012-06-26 01:31 QtHelp
drwxr-xr-x  2 root root  4096 2012-06-26 01:30 QtMultimedia
drwxr-xr-x  2 root root  4096 2012-06-26 01:29 QtNetwork
drwxr-xr-x  2 root root  4096 2012-06-26 01:30 QtOpenGL
drwxr-xr-x  2 root root  4096 2012-06-26 01:30 QtScript
drwxr-xr-x  2 root root  4096 2012-06-26 01:31 QtScriptTools
drwxr-xr-x  2 root root  4096 2012-06-26 01:29 QtSql
drwxr-xr-x  2 root root  4096 2012-06-26 01:30 QtSvg
drwxr-xr-x  2 root root  4096 2012-06-26 01:29 QtTest
drwxr-xr-x  2 root root  4096 2012-06-26 01:31 QtUiTools
drwxr-xr-x  2 root root  4096 2012-06-26 01:31 QtWebKit
drwxr-xr-x  2 root root  4096 2012-06-26 01:28 QtXml
drwxr-xr-x  2 root root  4096 2012-06-26 01:30 QtXmlPatterns

```

Anyone can help me? Thanks.

---

### Post by GeneralZod on 2012-06-25
> **pellyhawk said:**
> I have a c/c++ program and want to build with qt. My qt is located in /usr/local/Trolltech/Qt-4.7.3-pc. 


A strange place to put it - any particular reason why you didn't just install via a package manager ... ?

What is the result of 

```

which qmake

```

?

Edit:

For your find expression, you probably want:

```

find / -name  QtNetwork 2>/dev/null 

```

I'm not sure what the "access_log" bit was for, though ... ?

---

### Post by eotakos on 2012-06-25
Hello, 

I know that if you have a problem you should deal with it and not bypass it... but there are some times that the problem you're having is not the actual target, but some obstacle standing in the way. 

If that is the case and you don't care about doing everything manually, maybe eclipse and this plugin can do it for you  
[http://www.ai3.uni-bayreuth.de/software/eclipsecudaqt/](http://www.ai3.uni-bayreuth.de/software/eclipsecudaqt/)
(eclipse has options for auto-generating makefiles).

I'm not saying it works, because I've used it only for cuda and not QT, but I saw the post and I thought that searching that way may bypass your problems.


eotakos

---

### Post by dwhitney67 on 2012-06-25
> **pellyhawk said:**
> 
Anyone can help me? Thanks.

Why is the path to the Qt header files (/usr/local/Trolltech/Qt-4.7.3-pc/include) set up within your PATH environment variable?  It is not necessary to add paths to PATH that do not contain executable files.

You indicated that you installed Qt at /usr/local/Trolltech/Qt-4.7.3-pc, yet when you use 'make' to build your project, it is referencing files in /usr/include/qt4 and specs from /usr/share/qt4.

I suspect that you are using the incorrect qmake and/or have an incorrect dot-pro file.

---

### Post by hakermania on 2012-06-25
Please consider adding
```
QT += network
```
after 
```
INCLUDEPATH += .
```
in your .pro file which is being generated from the command
```

qmake -project

```
and then try building your code.

---

### Post by pellyhawk on 2012-06-25
> **GeneralZod said:**
> A strange place to put it - any particular reason why you didn't just install via a package manager ... ?

What is the result of 

```

which qmake

```

?

Edit:

For your find expression, you probably want:

```

find / -name  QtNetwork 2>/dev/null 

```

I'm not sure what the "access_log" bit was for, though ... ?

Thank you first.
I install qt at  /usr/local/Trolltech/Qt-4.7.3-pc because I command the following command to install it:
```
./configure -prefix /usr/local/Trolltech/Qt-4.7.3-pc
make
make install
```

I got the following result when running "which qmake"
```
ian@mike-desktop:/mnt/hgfs/VBox_Shared/SeaTools$ which qmake
/usr/bin/qmake

```

The "access_log" related command seems wrong, I got it from a blogs. And I conduct your "find / -name  QtNetwork 2>/dev/null" got many "QtNetwork", thus it should not says "No such file or directory".

---

### Post by pellyhawk on 2012-06-25
> **dwhitney67 said:**
> Why is the path to the Qt header files (/usr/local/Trolltech/Qt-4.7.3-pc/include) set up within your PATH environment variable?  It is not necessary to add paths to PATH that do not contain executable files.

You indicated that you installed Qt at /usr/local/Trolltech/Qt-4.7.3-pc, yet when you use 'make' to build your project, it is referencing files in /usr/include/qt4 and specs from /usr/share/qt4.

I suspect that you are using the incorrect qmake and/or have an incorrect dot-pro file.

I guess you are right. I also realized that I am using incorrect qmake and environment variable. Or I would have already succeed in build my project. 

By the way, why when using "$PATH" I will get "no such file or directory" while "echo $PATH" will not?

I will delete 

Before I installed this qt-everywhere-opensource-src-4.7.3.tar.gz at /usr/local/Trolltech/Qt-4.7.3-pc, I also installed QtSdk-online-linux-x86-v1.2.1.run at /home/mike/QtSdk. I did not find how to uninstall this .run and QtSdk  by google. Can you tell me? &#65288;I also read qt.nokia.com and do not find out the difference between QtSdk and qt-everywhere-opensource-src-4.7.3.tar.gz. It seems they are different qt version and can do the same or similar things&#65289; 

How do you know I am referencing files in /usr/include/qt4 and specs from /usr/share/qt4 when using "make" to build my project?

Thanks.

---

### Post by pellyhawk on 2012-06-25
Hi dwhitney67 and hakermania,

Why you both think my .pro file is incorrect? You know, .pro file is generated by the command "qmake -project" not me.

```
ian@mike-desktop:/mnt/hgfs/VBox_Shared/SeaTools$ cat SeaTools.pro
######################################################################
# Automatically generated by qmake (2.01a) Mon Jun 25 21:44:54 2012
######################################################################

TEMPLATE = app
TARGET = 
DEPENDPATH += . debug include release translations
INCLUDEPATH += . include

# Input
HEADERS += addgrptabledelegate.h \
           calccrcdialog.h \
           cascadetabledelegate.h \
......
......
......

```

---

### Post by dwhitney67 on 2012-06-25
> **pellyhawk said:**
> 
By the way, why when using "$PATH" I will get "no such file or directory" while "echo $PATH" will not?

You cannot execute $PATH; hence the error.  Of course, you can echo its setting.

> **pellyhawk said:**
> 
Before I installed this qt-everywhere-opensource-src-4.7.3.tar.gz at /usr/local/Trolltech/Qt-4.7.3-pc, I also installed QtSdk-online-linux-x86-v1.2.1.run at /home/mike/QtSdk. I did not find how to uninstall this .run and QtSdk  by google. Can you tell me?

Usually the installation makefile has a rule called "uninstall"; perhaps you can try "make uninstall".  Refer to the README file or similar with the Trolltech product you downloaded.

> **pellyhawk said:**
> 
How do you know I am referencing files in /usr/include/qt4 and specs from /usr/share/qt4 when using "make" to build my project?

Quite simple... note the information in the line that you posted earlier:
```

g++ -c ... -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 ...

```

---

### Post by hakermania on 2012-06-25
> **pellyhawk said:**
> Hi dwhitney67 and hakermania,

Why you both think my .pro file is incorrect? You know, .pro file is generated by the command "qmake -project" not me.

```
ian@mike-desktop:/mnt/hgfs/VBox_Shared/SeaTools$ cat SeaTools.pro
######################################################################
# Automatically generated by qmake (2.01a) Mon Jun 25 21:44:54 2012
######################################################################

TEMPLATE = app
TARGET = 
DEPENDPATH += . debug include release translations
INCLUDEPATH += . include

# Input
HEADERS += addgrptabledelegate.h \
           calccrcdialog.h \
           cascadetabledelegate.h \
......
......
......

```

Well, I'm using the network libs in Wallch (see sig) and I had to add Qt += network in my pro file before generating the Makefile using
```

qmake *.pro

```
so, I don't see why you shouldn't :)

---

### Post by pellyhawk on 2012-06-25
> Usually the installation makefile has a rule called "uninstall"; perhaps you can try "make uninstall".  Refer to the README file or similar with the Trolltech product you downloaded.

I mean how to uninstall QtSdk? I install it by "./QtSdk-online-linux-x86-v1.2.1.run" and QtSdk-online-linux-x86-v1.2.1.run is only a .run file. And I also read qt.nokia.com and do not find out the difference between QtSdk and qt-everywhere-opensource-src-4.7.3.tar.gz. It seems they are different qt version and can do the same or similar things


```
Quite simple... note the information in the line that you posted earlier:
[code]
g++ -c ... -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 ...

```[/CODE]
:)But how can I succeed in building my project? uninstall QtSdk, thus "make" will reference the proper path or how to change it and what is the proper path?

Thanks

---

### Post by pellyhawk on 2012-06-25
Maybe I do not clarify my issue very clearly. I installed 2 packages. One is QtSdk-online-linux-x86-v1.2.1.run located at /home/mike/QtSdk, the other is qt-everywhere-opensource-src-4.7.3.tar.gz located at /usr/local/Trolltech/Qt-4.7.3-pc because QtSdk-online-linux-x86-v1.2.1.run includes qt-everywhere-opensource-src-4.7.3.tar.gz. It seems I only need to install one of them, and uninstall the other???

And how to make the command "make" refer the proper path?

Thanks.

---

### Post by pellyhawk on 2012-06-26
Hi all,

I uninstalled QtSdk-online-linux-x86-v1.2.1.run and now my qt-everywhere-opensource-src-4.7.3.tar.gz is installed at /usr/local/Trolltech/Qt-4.7.3-pc.

I added the following at /etc/profile
```
export QTDIR=/usr/local/Trolltech/Qt-4.7.3-pc
export PATH=$QTDIR/bin:$PATH
export MANPATH=$QTDIR/man:$MANPATH
export LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH
```

As hakermania told me, add ```
INCLUDEPATH += .
``` after ```
QT += network
``` in .pro file

```
/usr/local/Trolltech/Qt-4.7.3-pc/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/mike/CodeSourcery/Sourcery_G++_Lite/bin

```

Also:
```
mike@mike-desktop:/mnt/hgfs/VBox_Shared/SeaTools$ which qmake
/usr/local/Trolltech/Qt-4.7.3-pc/bin/qmake

```

Therefore, everything is OK now. But I have no idea that why we should add these environment variables.

Thanks

---

