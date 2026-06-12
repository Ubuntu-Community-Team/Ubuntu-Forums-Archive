---
title: "Qt4 Simple Example Problem"
date: 2008-05-21
forum: Programming Talk
---

### Post by Dambrosio on 2008-05-21
I have been trying to figure out qt4 by writing a simple program which calculates the area of a cirlce given the radius. I tried to declare my own class which inherits QLineEdit and my reason for this was so I could make a slot to compute the area and apply show it on the screen. I get compiling errors and I dont know if I set up my class and signal/slot stuff.
My error is attached because i cant out how to copy it out of my IDE program.

**main.cpp**
```
#include <QApplication>
#include "mainwindowimpl.h"
//
int main(int argc, char ** argv)
{
	QApplication app( argc, argv );
	MainWindowImpl win;
	win.show(); 
	app.connect( &app, SIGNAL( lastWindowClosed() ), &app, SLOT( quit() ) );
	return app.exec();
}
```

**mainwindowimpl.h**
```
#ifndef MAINWINDOWIMPL_H
#define MAINWINDOWIMPL_H
//
#include "ui_mainwindow.h"
//
class MainWindowImpl : public QMainWindow, public Ui::MainWindow
{
Q_OBJECT
public:
	MainWindowImpl( QWidget * parent = 0, Qt::WFlags f = 0 );
private slots:
protected:
void setupConnections();
void about();
};
#endif

```

**mainwindowimp.cpp**
```
#include <QtGui>
#include "mainwindowimpl.h"
//
MainWindowImpl::MainWindowImpl( QWidget * parent, Qt::WFlags f) 
	: QMainWindow(parent, f)
{
	setupUi(this);
	setupConnections();
}
void MainWindowImpl::setupConnections()
{
	connect(action_Quit, SIGNAL(triggered(bool)), qApp, SLOT(quit()));
	connect(actionAbout, SIGNAL(triggered(bool)), this, SLOT(about()));
	
	
}
void MainWindowImpl::about()
{
	QMessageBox::about(this,tr("About Area Calc."),
						tr("Area Calc 1.0 beta"
						"(c) 2008 Daniel Ambrosio"));
}
```

**myqedit.h**
```
#ifndef __MYQEDIT_H__
#define __MYQEDIT_H__
#include <QWidget>
class QLineEdit;

class MyQEdit : public QWidget
{
	
	Q_OBJECT
	public:
	MyQEdit(QWidget *parent =0);
	
	public slots:
	void setAValue(int value);
	void setText(const QString &text);
	
	signals:
	void textChanged(const QString &text);
	
	private:
	QLineEdit *aEdit;
	
};

#endif // __MYQEDIT_H__
```

**myqedit.cpp**
```
#include "myqedit.h"
#include<QLineEdit>
#include<QString>

MyQEdit::MyQEdit(QWidget *parent) : QWidget(parent)
{
	QLineEdit *edit = new QLineEdit("0");
	connect(edit,SIGNAL(textChanged(const QString &text)),this,SIGNAL(textChanged(const QString &text)));
		
}

void MyQEdit::setAValue(int value)
{
	int radius = value;
	double area = (radius*radius)*(3.1415);
	
	aEdit->insert(QString::number(area,'g',6));
	
}
```


Thanks so much for the help, Im completely stuck!
Dan

---

### Post by Sef on 2008-05-21
Moved to Programming Talk.

---

### Post by malangaman on 2008-05-21
I'm not a genious at Qt4 yet, but I'll play with this tomorrow and see. Are you using QDevelop?

---

### Post by tanderson on 2008-05-22
in your myqedit.h you have void setText(const QString &text);
but there is not a function body in myqedit.cpp. Your new class isn't inheriting QlineEdit. It has a member variable that is a QlineEdit type. It is inheriting from QWidget. I will download your code and take a look. I am thinking you can do this without creating a new class.

Maybe you are practicing by making a new class, if so, ignore the following. I am thinking that both of your line edits can be standard QLineEdit types. In your windowimple class create a public slot: that takes a qstring. In that function, take the passed in qstring, do your computation and send it to area edit line with it's public slot setText(qstring); In the windowimpl constructor connect the radius edit line signal textEdited to the windowimple slot you created above. Maybe the area output should be a qlabel or at least a read only edit line to keep user from changing the text. You can look into qvalidator on the radius edit line to keep the input to numbers. Hope I have helped.

---

### Post by Dambrosio on 2008-05-23
malangaman,
Thank you for taking the time to help me out, I'm looking forward to your ideas. And yes I am using QDevelop.

tanderson,
I could follow you for a little bit but then I got a little confused. Is there anyway you could help me with creating a class to do this? The programs that will follow this are going to be more intense and I want to learn how to make and incorporate a user created class. Thank you so much!

---

### Post by tanderson on 2008-05-23
Here is a quick program I through together on how I would start. Don't have the right signals and slot going but gets the classes started. Notice myqedit is derived from qlineedit. you were deriving from qwidget and trying to wrap a qlineedit. Not saying that isn't right or possible, but just seems like more work. I am using qdevelop version .25 on kubuntu 8.04. FYI

---

### Post by Dambrosio on 2008-05-25
tanderson,
Thank you so much! If you don't mind can I ask you a few questions just so I can completely understand your code.

In the qmyedit.h header file when you define the QMyEdit class, when you enter : public QLineEdit is that where it inherits the QLineEdit object? Not when you #include <QLineEdit>
```
class QMyEdit : public QLineEdit
{...
``` 

In the qmyedit.cpp function Calculated, when you type this->setText(...);
the "this" is referring to the QMyEdit object right? LineEditArea->setText(...); would not work because there is no private LineEditArea variable declared in the QMyEdit class, is this right?
```
void QMyEdit::Calculate(QString Radius)
{
	bool ok;
	double Area = 0;
	double r = Radius.toDouble(&ok);
	if(ok)
	{
		Area = (r*r)*(3.1415);
		this->setText(QString::number(Area,'g',6));
		return;
	}
	this->setText("Error");
	
}
```

Lastly,
In dialogimpl.cpp when you connect the LineEditRadius and the LineEditArea why do you just pass "QString" to textChanged and Calculated. Isn't that just a object not a variable?
```
connect(LineEditRadius, SIGNAL(textChanged(QString)),
		LineEditArea, SLOT(Calculate(QString)));
```

THANK YOU SO MUCH!
I can finally screw around with this now that I have a idea of creating my own class!

Dan

Ps. I don't know how to thank you so it shows in your profile so let me know and I will.

---

### Post by tanderson on 2008-05-25
Sounds like you are getting it. Yes the connect statements seem goofy to me also. Good luck.

---

### Post by jtltgl on 2008-08-01
I am trying to do the same thing. The only thing I see is you don't have a ui_mainwindow.h so I can't compile.

---

