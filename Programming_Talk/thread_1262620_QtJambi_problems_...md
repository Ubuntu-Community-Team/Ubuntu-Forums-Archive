---
title: "QtJambi problems .."
date: 2009-09-10
forum: Programming Talk
---

### Post by armageddon08 on 2009-09-10
I'm trying to compile this program:
```
class HelloWorld
{
	public static void main(String args[])
	{
  		QApplication.initialize(args);
  		QPushButton hello = new QPushButton("Hello World!");
  		hello.resize(120, 40);
  		hello.setWindowTitle("Hello World");
  		hello.show();
  		QApplication.exec();
	}
}


```
On compiling I'm getting this result:
```

&#9484;&#9472;[armageddon @ dragonzden]
&#9492;&#9472;[~/Programming/Qt]> javac HelloWorld.java
HelloWorld.java:5: cannot find symbol
symbol  : variable QApplication
location: class HelloWorld
                QApplication.initialize(args);
                ^
HelloWorld.java:6: cannot find symbol
symbol  : class QPushButton
location: class HelloWorld
                QPushButton hello = new QPushButton("Hello World!");
                ^
HelloWorld.java:6: cannot find symbol
symbol  : class QPushButton
location: class HelloWorld
                QPushButton hello = new QPushButton("Hello World!");
                                        ^
HelloWorld.java:10: cannot find symbol
symbol  : variable QApplication
location: class HelloWorld
                QApplication.exec();
                ^
4 errors

```
I need some help please.

---

### Post by armageddon08 on 2009-09-10
Okay, so I found out that I had to import the gui package. So I added 
```
import com.trolltech.qt.gui.*;
```
to my code. Now I'm getting an extra error:
```

&#9484;&#9472;[armageddon @ dragonzden]
&#9492;&#9472;[~/Programming/Qt]> javac HelloWorld.java
HelloWorld.java:1: package com.trolltech.qt.gui does not exist
import com.trolltech.qt.gui.*;
^
HelloWorld.java:6: cannot find symbol
symbol  : variable QApplication
location: class HelloWorld
                QApplication.initialize(args);
                ^
HelloWorld.java:7: cannot find symbol
symbol  : class QPushButton
location: class HelloWorld
                QPushButton hello = new QPushButton("Hello World!");
                ^
HelloWorld.java:7: cannot find symbol
symbol  : class QPushButton
location: class HelloWorld
                QPushButton hello = new QPushButton("Hello World!");
                                        ^
HelloWorld.java:11: cannot find symbol
symbol  : variable QApplication
location: class HelloWorld
                QApplication.exec();
                ^
5 errors


```
Can anybody tell me what I'm doing wrong and point me towards the right direction.:confused:

---

### Post by Shin_Gouki2501 on 2009-09-10
1. read up classpath in java
or
2. use a IDE and add the QT lib to your classpath ( buildpath) or such

---

