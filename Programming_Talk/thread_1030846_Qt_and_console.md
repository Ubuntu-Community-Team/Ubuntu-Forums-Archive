---
title: "Qt and console"
date: 2009-01-04
forum: Programming Talk
---

### Post by qbox on 2009-01-04
Hi
Im new in Qt. I just start to learn and for exercise I want to make little program who will give me some information. So I know how to get that information in the console. But I dont know how to show that information in Qt window.
Lets say that ifconfig give me information about network interfaces on the computer. How can I send "ifconfig" command to console and take back results in Qt?

Thank you :)

---

### Post by dwhitney67 on 2009-01-04
Use the system() library call and write the results of 'ifconfig' to a file, then open the file and read it.

Alternatively, you can use a popen() to run your command and then read the results as if you were reading a file.

For example:
[php]
std::string cmd("/sbin/ifconfig eth0");
FILE* pfd = popen(cmd.c_str(), "r");

if (pfd)
{
  while (!feof(pfd))
  {
    char buf[1024] = {0};

    if (fgets(buf, sizeof(buf), pfd) > 0)
    {
      std::cout << "buf = " << buf;    // a newline is already present
    }
  }
  pclose(pfd);
}
[/php]

As for displaying the data in a Qt dialog box, well that is beyond the scope of my knowledge (by choice!).  I dabbled with Qt over a year ago (required for the job), but I thought it was a poor library chock full of macros that did injustice to the C++ syntax.

---

### Post by jinksys on 2009-01-04
Use QProcess.

[http://doc.trolltech.com/4.4/qprocess.html](http://doc.trolltech.com/4.4/qprocess.html)

---

### Post by qbox on 2009-01-05
> **jinksys said:**
> Use QProcess.

[http://doc.trolltech.com/4.4/qprocess.html](http://doc.trolltech.com/4.4/qprocess.html)

Can you give me a little example? I cant make it work.

---

### Post by qbox on 2009-01-05
I receiving errors on the places I didnt received before. :S this is really weird. I make elementary program with few lines, I copy the lines from program who worked before, and now I have errors... Really weird programing language.....

---

### Post by jinksys on 2009-01-05
> **qbox said:**
> I receiving errors on the places I didnt received before. :S this is really weird. I make elementary program with few lines, I copy the lines from program who worked before, and now I have errors... Really weird programing language.....

Could be a problem with the way you are compiling your sources, perhaps you have old object files laying around.

If you post the code you are having trouble with, we could help you further.

---

### Post by qbox on 2009-01-06
Here is the program
```
#include <qapplication.h>
#include <qpushbutton.h>
#include <qfont.h>

int main( int argc, char **argv )
{
	QApplication a( argc, argv );

	QPushButton quit( "Quit", 0 );
	quit.resize( 75, 30 );
	quit.setFont( QFont( "Times", 18, QFont::Bold ) );

	QObject::connect( &quit, SIGNAL(clicked()), &a, SLOT(quit()) );

	a.setMainWidget( &quit );
	quit.show();
	return a.exec();
}
```
Here is the error
```

Build (make)...
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:15: error: &#8216;class QApplication&#8217; has no member named &#8216;setMainWidget&#8217;
make: *** [main.o] Error 1
---------------------- Build finished with 1 error(s) ----------------------
```
I didnt receive error before on this code.

---

### Post by tseliot on 2009-01-06
[Here]("http://ubuntuforums.org/showthread.php?t=1020779") I tried to help another user who was trying to perform the same task.

---

### Post by Zugzwang on 2009-01-06
> **qbox said:**
> 
I didnt receive error before on this code.

See here: [http://lists.trolltech.com/qt-interest/2005-08/thread00310-0.html](http://lists.trolltech.com/qt-interest/2005-08/thread00310-0.html)

Summary: You are trying to compile code for QT3 with the QT4 libraries. Either change your code to comply to QT4 or link and compile against the QT3 libraries. If you use "qmake", run "qmake-qt3" instead of "qmake-qt4".

---

### Post by qbox on 2009-01-06
To compile in Qt 3 or to upgrade and learn Qt4 :) what is better solution?

---

### Post by Zugzwang on 2009-01-06
> **qbox said:**
> To compile in Qt 3 or to upgrade and learn Qt4 :) what is better solution?

It depends on how much time you will invest into Qt programming in the future. If that's a lot or you definitely need Qt4's new features, switching might be worthwhile. If you'll never use it again, stick with Qt3.

---

### Post by qbox on 2009-01-06
I try this tutorial
[http://sector.ynet.sk/qt4-tutorial/my-first-qt-gui-application.html](http://sector.ynet.sk/qt4-tutorial/my-first-qt-gui-application.html)
and when I try to compile program I get this

qbox@qbox:~/Qt/my_first_qt_app$ qmake
WARNING: Found potential symbol conflict of myqtapp.cpp (myqtapp.cpp) in SOURCES
WARNING: Found potential symbol conflict of myqtapp.h (myqtapp.h) in HEADERS
qbox@qbox:~/Qt/my_first_qt_app$ 

What is wrong with this? Can something start to work?

```
qbox@qbox:~/Qt/my_first_qt_app$ make
Makefile:153: warning: overriding commands for target `moc_myqtapp.cpp'
Makefile:150: warning: ignoring old commands for target `moc_myqtapp.cpp'
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o myqtapp.o myqtapp.cpp
myqtapp.cpp:1:18: error: QtGui: No such file or directory
In file included from myqtapp.cpp:2:
myqtapp.h:4:24: error: ui_myqtapp.h: No such file or directory
In file included from myqtapp.cpp:2:
myqtapp.h:7: error: expected class-name before &#8216;,&#8217; token
myqtapp.h:7: error: &#8216;Ui&#8217; has not been declared
myqtapp.h:7: error: expected `{' before &#8216;myQtAppDLG&#8217;
myqtapp.h:7: error: function definition does not declare parameters
myqtapp.cpp:6: error: expected constructor, destructor, or type conversion before &#8216;(&#8217; token
myqtapp.cpp:18: error: invalid use of incomplete type &#8216;class myQtApp&#8217;
myqtapp.h:7: error: forward declaration of &#8216;class myQtApp&#8217;
myqtapp.cpp:32: error: invalid use of incomplete type &#8216;class myQtApp&#8217;
myqtapp.h:7: error: forward declaration of &#8216;class myQtApp&#8217;
myqtapp.cpp:58: error: invalid use of incomplete type &#8216;class myQtApp&#8217;
myqtapp.h:7: error: forward declaration of &#8216;class myQtApp&#8217;
myqtapp.cpp:64: error: invalid use of incomplete type &#8216;class myQtApp&#8217;
myqtapp.h:7: error: forward declaration of &#8216;class myQtApp&#8217;
make: *** [myqtapp.o] Error 1
qbox@qbox:~/Qt/my_first_qt_app$ 

```

---

### Post by Zugzwang on 2009-01-07
It looks like as if you executed the *old* version of "qmake", so try "qmake-qt4".

Have a look at your include paths and you'll see that immediately.

---

### Post by qbox on 2009-01-07
Thanks thats worked. Why I cant make qmake-qt4 with QDevelot? he still make programs with qmake. And give me alot of errors :S

---

### Post by Zugzwang on 2009-01-07
> **qbox said:**
> Thanks thats worked. Why I cant make qmake-qt4 with QDevelot? he still make programs with qmake. And give me alot of errors :S

So there's "qmake-qt3" and "qmake-qt4". "qmake" refers to the default qmake-version that is installed. You can change the default version by typing:
```

sudo update-alternatives --config qmake

```
in the terminal. You will need to have sudo-rights (always the case in Ubuntu for the first user) and to type your password.

---

### Post by qbox on 2009-01-07
Wow nice work. I have a lot to learn :)

---

### Post by qbox on 2009-01-08
How
```
void ifTer::takeInfo(){
	QProcess myProcess;
	
	myProcess.execute("ifconfig eth0");
}
```

how can I take the output from ifconfig and put it in variable?

---

### Post by dwhitney67 on 2009-01-08
> **qbox said:**
> How
```
void ifTer::takeInfo(){
	QProcess myProcess;
	
	myProcess.execute("ifconfig eth0");
}
```

how can I take the output from ifconfig and put it in variable?

How about Googling for answers??  [http://doc.trolltech.com/4.1/qprocess.html](http://doc.trolltech.com/4.1/qprocess.html)

---

### Post by qbox on 2009-01-08
I googleed the same link but I cant understand the code. There isnt good example.

---

