---
title: "Connect to output from QProcess? (Qt4)"
date: 2007-06-22
forum: Programming Talk
---

### Post by Kimm on 2007-06-22
I'm trying to execute an application from another application (made using Qt4), using QProcess, and then tie into the output of the executed process and display it in a QTextEdit. This is how I am doing it (I'll try to post all relevant code, all of it is a bit much :))

mainwindowimpl.h:
```

#ifndef MAINWINDOWIMPL_H
#define MAINWINDOWIMPL_H

#include "ui_mainwindow.h"
#include <QProcess>

class MainWindowImpl : public QMainWindow, public Ui::MainWindow
{
	Q_OBJECT
	public:
		MainWindowImpl( QWidget * parent = 0, Qt::WFlags f = 0 );
	private slots:
		void Start();
		void Output();
};

#endif

```

mainwindowimpl.cpp:
```

#include "mainwindowimpl.h"
#include <QtGui>

QProcess *app = new QProcess();

MainWindowImpl::MainWindowImpl(QWidget *parent, Qt::WFlags f) : QMainWindow(parent, f)
{
	setupUi(this);
	
	connect(app, SIGNAL(readyReadStandardOutput()), this, SLOT(Output()));
	
	connect(BtnStart, SIGNAL(clicked()), this, SLOT(Start()));
}

void MainWindowImpl::Start()
{
	QString xterm = "thunar";
	QStringList arguments;
	
	arguments<<"/home/kim/";
	
	app->start(xterm, arguments);
}

void MainWindowImpl::Output()
{
	OutText->setText(app->readAllStandardOutput());
}

```

Now, I can see in the terminal I launch my application from that Thunar prints something about D-Bus to the terminal, but nothing happens with my QTextEdit.

Ideas anyone? I'm kind of a novice with Qt and I've been googling to find an answer for quite a while :)

---

