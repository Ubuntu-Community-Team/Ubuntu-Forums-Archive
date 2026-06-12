---
title: "QT scoping problem"
date: 2010-02-08
forum: Programming Talk
---

### Post by hollowhead on 2010-02-08
I'm reproducing the spreadsheet app from c++ gui programming with qt4 to teach myself C++ and Qt. Using Qdevelop and Qdesigner. I've created the goto dialog which compiled I've added it in plus header and source file in QDevelop.  I'm getting was "not declared in this scope errors" // commented below.  Looking at the original source in the book I don't think I've missed anything out, but I must have made a simple mistake somewhere.  It just needs a fresh eye to see something I've missed.  Can anyone help?!

Source

GoToCellDialog.h

#ifndef GOTOCELLDIALOG_H
#define GOTOCELLDIALOG_H
//
#include <QDialog>
#include "ui_GoToCellDialog.h"
//
class GoToCellDialog : public QDialog, public Ui::GoToCellDialog
{
Q_OBJECT
public:
	 GoToCellDialog( QWidget * parent = 0, Qt::WFlags f = 0 );
private slots:
void on_lineEdit_textChanged();

};
#endif

GoToCellDialog.cpp

#include <QtGui>
#include "GoToCellDialog.h"
//
GoToCellDialog::GoToCellDialog( QWidget * parent, Qt::WFlags f) 
	: QDialog(parent, f)
{
	setupUi(this);
	
    QRegExp regExp("[A-Za-z][1-9][0-9]{0,2}");
    lineEdit->setValidator(new QRegExpValidator(regExp, this));

    connect(okButton, SIGNAL(clicked()), this, SLOT(accept()));
    connect(cancelButton, SIGNAL(clicked()), this, SLOT(reject()));  //scoping error here "cancelButton was not declared in this scope"
}
//

void GoToCellDialog::on_lineEdit_textChanged()
{
    okButton->setEnabled(lineEdit->hasAcceptableInput());
}


MainWindowImpl.cpp 

#include <QtGui>
#include "mainwindowimpl.h"
#include "spreadsheet.h" // required for most menu functions
#include "GoToCellDialog.h"

//
MainWindowImpl::MainWindowImpl( QWidget * parent, Qt::WFlags f) 
	: QMainWindow(parent, f)
{
	setupUi(this);
	spreadsheet = new Spreadsheet;
	setCentralWidget(spreadsheet); // centre spreadsheet on form between statusbar, toolbar and 
	createContextMenu();
	
	// setup signals and slots for menu actions starting with basic ones
	connect(actionC_opy_Ctrl_C, SIGNAL(triggered()), spreadsheet, SLOT(copy()));
	connect(actionSelect_All_Ctrl_A, SIGNAL(triggered()), spreadsheet, SLOT(selectAll()));
	connect(actionSelect_Co_lumn, SIGNAL(triggered()), spreadsheet, SLOT(selectCurrentColumn()));
	connect(actionSelect_Ro_w, SIGNAL(triggered()),spreadsheet, SLOT(selectCurrentRow()));
	connect(action_Paste_Ctrl_V, SIGNAL(triggered()), spreadsheet, SLOT(paste()));
	connect(action_Cut_Ctrl_X, SIGNAL(triggered()), spreadsheet, SLOT(cut()));
	connect(actionFont, SIGNAL(triggered()), spreadsheet, SLOT(selectFont()));
	connect(menuGotoCell, SIGNAL(triggered()),this, SLOT(goToCell()));
	//scoping error here error: ‘menuGotoCell’ was not declared in this scope
// the menu item object name in designer is menuGotoCell
	
	
}
//

void MainWindowImpl::createContextMenu()
{
	spreadsheet->addAction(action_Cut_Ctrl_X);
    spreadsheet->addAction(actionC_opy_Ctrl_C);
    spreadsheet->addAction(action_Paste_Ctrl_V);
    spreadsheet->setContextMenuPolicy(Qt::ActionsContextMenu);
	
}

void MainWindowImpl::goToCell()
{
    GoToCellDialog dialog(this);
    if (dialog.exec())
    {
        QString str = dialog.lineEdit->text().toUpper();
        spreadsheet->setCurrentCell(str.mid(1).toInt() - 1,
                                    str[0].unicode() - 'A');
    }
}
pro file

EMPLATE = app
QT = gui core
CONFIG += qt \
 debug \
 warn_on \
 console \
 resources
DESTDIR = bin
OBJECTS_DIR = build
MOC_DIR = build
UI_DIR = build
FORMS = ui/mainwindow.ui
FORMS = ui/GoToCellDialog.ui
HEADERS = src/mainwindowimpl.h src/spreadsheet.h src/cell.h src/GoToCellDialog.h
SOURCES = src/mainwindowimpl.cpp \
 src/main.cpp \
 src/spreadsheet.cpp \
 src/cell.cpp \
 src/GoToCellDialog.cpp
RESOURCES = spreadsheet.qrc

---

### Post by hollowhead on 2010-02-08
I don't understand why I see a smiley below?

---

### Post by Zugzwang on 2010-02-08
> **hollowhead said:**
> I don't understand why I see a smiley below?

Please surround your code in "[PHP]"-tags in order to get a better formatting.

---

### Post by hollowhead on 2010-02-08
Yeah sorry- fantastic, php tags are great didn't know you could do that!

I'm reproducing the spreadsheet app from c++ gui programming with qt4 to teach myself C++ and Qt. Using Qdevelop and Qdesigner. I've created the goto dialog which compiled I've added it in plus header and source file in QDevelop. I'm getting was "not declared in this scope errors" // commented below. Looking at the original source in the book I don't think I've missed anything out, but I must have made a simple mistake somewhere. It just needs a fresh eye to see something I've missed. Can anyone help?!

Source

[PHP]
GoToCellDialog.h

#ifndef GOTOCELLDIALOG_H
#define GOTOCELLDIALOG_H
//
#include <QDialog>
#include "ui_GoToCellDialog.h"
//
class GoToCellDialog : public QDialog, public Ui::GoToCellDialog
{
Q_OBJECT
public:
GoToCellDialog( QWidget * parent = 0, Qt::WFlags f = 0 );
private slots:
void on_lineEdit_textChanged();

};
#endif

GoToCellDialog.cpp

#include <QtGui>
#include "GoToCellDialog.h"
//
GoToCellDialog::GoToCellDialog( QWidget * parent, Qt::WFlags f)
: QDialog(parent, f)
{
setupUi(this);

QRegExp regExp("[A-Za-z][1-9][0-9]{0,2}");
lineEdit->setValidator(new QRegExpValidator(regExp, this));

connect(okButton, SIGNAL(clicked()), this, SLOT(accept()));
connect(cancelButton, SIGNAL(clicked()), this, SLOT(reject())); //scoping error here "cancelButton was not declared in this scope"
}
//

void GoToCellDialog:n_lineEdit_textChanged()
{
okButton->setEnabled(lineEdit->hasAcceptableInput());
}


MainWindowImpl.cpp

#include <QtGui>
#include "mainwindowimpl.h"
#include "spreadsheet.h" // required for most menu functions
#include "GoToCellDialog.h"

//
MainWindowImpl::MainWindowImpl( QWidget * parent, Qt::WFlags f)
: QMainWindow(parent, f)
{
setupUi(this);
spreadsheet = new Spreadsheet;
setCentralWidget(spreadsheet); // centre spreadsheet on form between statusbar, toolbar and
createContextMenu();

// setup signals and slots for menu actions starting with basic ones
connect(actionC_opy_Ctrl_C, SIGNAL(triggered()), spreadsheet, SLOT(copy()));
connect(actionSelect_All_Ctrl_A, SIGNAL(triggered()), spreadsheet, SLOT(selectAll()));
connect(actionSelect_Co_lumn, SIGNAL(triggered()), spreadsheet, SLOT(selectCurrentColumn()));
connect(actionSelect_Ro_w, SIGNAL(triggered()),spreadsheet, SLOT(selectCurrentRow()));
connect(action_Paste_Ctrl_V, SIGNAL(triggered()), spreadsheet, SLOT(paste()));
connect(action_Cut_Ctrl_X, SIGNAL(triggered()), spreadsheet, SLOT(cut()));
connect(actionFont, SIGNAL(triggered()), spreadsheet, SLOT(selectFont()));
connect(menuGotoCell, SIGNAL(triggered()),this, SLOT(goToCell()));
//scoping error here error: ‘menuGotoCell’ was not declared in this scope
// the menu item object name in designer is menuGotoCell


}
//

void MainWindowImpl::createContextMenu()
{
spreadsheet->addAction(action_Cut_Ctrl_X);
spreadsheet->addAction(actionC_opy_Ctrl_C);
spreadsheet->addAction(action_Paste_Ctrl_V);
spreadsheet->setContextMenuPolicy(Qt::ActionsContextMenu);

}

void MainWindowImpl::goToCell()
{
GoToCellDialog dialog(this);
if (dialog.exec())
{
QString str = dialog.lineEdit->text().toUpper();
spreadsheet->setCurrentCell(str.mid(1).toInt() - 1,
str[0].unicode() - 'A');
}
}
pro file

TEMPLATE = app
QT = gui core
CONFIG += qt \
debug \
warn_on \
console \
resources
DESTDIR = bin
OBJECTS_DIR = build
MOC_DIR = build
UI_DIR = build
FORMS = ui/mainwindow.ui
FORMS = ui/GoToCellDialog.ui
HEADERS = src/mainwindowimpl.h src/spreadsheet.h src/cell.h src/GoToCellDialog.h
SOURCES = src/mainwindowimpl.cpp \
src/main.cpp \
src/spreadsheet.cpp \
src/cell.cpp \
src/GoToCellDialog.cpp
RESOURCES = spreadsheet.qrc 



[/PHP]

---

### Post by dwhitney67 on 2010-02-08
Do you have a typo here with this statement?
```

void GoToCellDialog[COLOR="Red"]:n[/COLOR]_lineEdit_textChanged()
{
   ...
}

```
Shouldn't that statement contain two colon characters, and with the method name as "on_lineEdit_textChanged"??  It is better to copy/paste code, than hand-type code, when you are posting on this forum.

As for the other error concerning "menuGotoCell", what is this variable?  I do not see it declared anywhere.

---

### Post by lykwydchykyn on 2010-02-08
I'm guessing "menuGotoCell" is a widget defined in "ui_GoToCellDialog.h".  If so, then my next guess is that the "t" should be capitalized since that seems to be consistent with the naming convention used.

just a guess though.

---

### Post by hollowhead on 2010-02-08
Your both right its a typo and the variable was declared in the header file.  Thanks.

I've solved it -it works perfectly.  The cancelButton scoping error was my fault the object was called cancelButton2 in the designer.  The signal and slot error was not, something was giving a bug.  Here's how I solved it if anyone has the same problem.  I tried in designer deleting the goto cell menu item putting it back in and rebuilding in QDevelop, this didn't work.  I tried renaming it and putting the new signal name in, this didn't work. But what I noticed was the new goto cell menu item did not appear in the debug version of the program even though it was there in designer.  I commented out the signal added some more code for print(preview) and noticed when I ran the debug version the goto cell menu item was there.  Uncommented out the signal/slot and it worked.  In the intervening period I tried running make in a terminal and got the same error so I don't think its a QDevelop bug.

---

