---
title: "Qt4 Errors...."
date: 2009-01-24
forum: Programming Talk
---

### Post by qbox on 2009-01-24
Hi.
I try to compile this code in Qt4

main.cpp
```
#include "main.h"
#include <QtGui>
#include <QApplication>
#include <QtNetwork/QTcpSocket>
#include <QtNetwork/QTcpServer>

class ClientSocket : public QSocket{
	Q_OBJECT
public:
	ClientSocket( int sock, QObject *parent=0, const char *name=0 ) : QSocket( parent, name ){
		line = 0;
		connect( this, SIGNAL(readyRead()), SLOT(readClient()) );
		connect( this, SIGNAL(connectionClosed()), SLOT(deleteLater()) );
		setSocket( sock );
	}

	~ClientSocket(){}
signals:
	void logText( const QString& );

private:
	int line;
};

appwindow::appwindow(QWidget *parent)
{
    setupUi(this);
}

int main(int argc, char *argv[]){
	QApplication mainserv(argc, argv);
	
	appwindow *dialog = new appwindow;
	
	dialog->show();
	return mainserv.exec();
}
```

main.h
```
#ifndef __MAIN_H__
#define __MAIN_H__
#include "ui_window.h"

class appwindow : public QWidget, private Ui::windowDLG
{
	Q_OBJECT
	
	public:
		appwindow(QWidget *parent=0);
};

#endif // __MAIN_H__
```

and here is the errors :)

```
Build (make)...
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o src/main.cpp
src/main.cpp:7: error: expected class-name before &#8216;{&#8217; token
src/main.cpp: In constructor &#8216;ClientSocket::ClientSocket(int, QObject*, const char*)&#8217;:
src/main.cpp:10: error: class &#8216;ClientSocket&#8217; does not have any field named &#8216;QSocket&#8217;
src/main.cpp:12: error: &#8216;connect&#8217; was not declared in this scope
src/main.cpp:14: error: &#8216;setSocket&#8217; was not declared in this scope
src/main.cpp: At global scope:
src/main.cpp:25: warning: unused parameter &#8216;parent&#8217;
make: *** [main.o] Error 1
---------------------- Build finished with 4 error(s) and 1 warning(s) ----------------------
```

The code is probably written for Qt3 and I want to translate to Qt4
any idea?

SORRY.... A Find solution. Thank you any way ;)

---

