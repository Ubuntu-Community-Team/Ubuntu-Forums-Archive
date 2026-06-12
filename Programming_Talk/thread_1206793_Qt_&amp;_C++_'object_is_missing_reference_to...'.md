---
title: "Qt &amp; C++: 'object is missing reference to...'"
date: 2009-07-07
forum: Programming Talk
---

### Post by JordyD on 2009-07-07
I'm making a widget called CodeView, I created a loadFile method in my CodeView class, but it's not compiling. I'm using Qt Creator, by the way.

Whenever I compile, I get this in the Build Issues palette:
```
/home/jordy/CodeView/ui_codeview.h:32: error: object missing in reference to &#8216;Ui_CodeView::plainTextEdit&#8217;
```

This is ui_codeview.h:
[PHP]/********************************************************************************
** Form generated from reading ui file 'codeview.ui'
**
** Created: Tue Jul 7 13:03:24 2009
**      by: Qt User Interface Compiler version 4.5.2
**
** WARNING! All changes made in this file will be lost when recompiling ui file!
********************************************************************************/

#ifndef UI_CODEVIEW_H
#define UI_CODEVIEW_H

#include <QtCore/QVariant>
#include <QtGui/QAction>
#include <QtGui/QApplication>
#include <QtGui/QButtonGroup>
#include <QtGui/QGridLayout>
#include <QtGui/QHeaderView>
#include <QtGui/QPlainTextEdit>
#include <QtGui/QPushButton>
#include <QtGui/QSpacerItem>
#include <QtGui/QWidget>

QT_BEGIN_NAMESPACE

class Ui_CodeView
{
public:
    QGridLayout *gridLayout;
    QSpacerItem *horizontalSpacer;
    QPushButton *configureButton;
    QPlainTextEdit *plainTextEdit; //This is the problem line

    void setupUi(QWidget *CodeView)
    {
        if (CodeView->objectName().isEmpty())
            CodeView->setObjectName(QString::fromUtf8("CodeView"));
        CodeView->resize(407, 365);
        gridLayout = new QGridLayout(CodeView);
        gridLayout->setSpacing(6);
        gridLayout->setMargin(11);
        gridLayout->setObjectName(QString::fromUtf8("gridLayout"));
        horizontalSpacer = new QSpacerItem(277, 20, QSizePolicy::Expanding, QSizePolicy::Minimum);

        gridLayout->addItem(horizontalSpacer, 1, 0, 1, 1);

        configureButton = new QPushButton(CodeView);
        configureButton->setObjectName(QString::fromUtf8("configureButton"));

        gridLayout->addWidget(configureButton, 1, 1, 1, 1);

        plainTextEdit = new QPlainTextEdit(CodeView);
        plainTextEdit->setObjectName(QString::fromUtf8("plainTextEdit"));
        QFont font;
        font.setFamily(QString::fromUtf8("Monospace"));
        plainTextEdit->setFont(font);
        plainTextEdit->setLineWrapMode(QPlainTextEdit::NoWrap);

        gridLayout->addWidget(plainTextEdit, 0, 0, 1, 2);


        retranslateUi(CodeView);

        QMetaObject::connectSlotsByName(CodeView);
    } // setupUi

    void retranslateUi(QWidget *CodeView)
    {
        CodeView->setWindowTitle(QApplication::translate("CodeView", "CodeView", 0, QApplication::UnicodeUTF8));
        configureButton->setText(QApplication::translate("CodeView", "Configure...", 0, QApplication::UnicodeUTF8));
        Q_UNUSED(CodeView);
    } // retranslateUi

};

namespace Ui {
    class CodeView: public Ui_CodeView {};
} // namespace Ui

QT_END_NAMESPACE

#endif // UI_CODEVIEW_H
[/PHP]

And codeview.cpp:
[PHP]#include "codeview.h"
#include "ui_codeview.h"

CodeView::CodeView(QWidget *parent)
    : QWidget(parent), ui(new Ui::CodeView)
{
    ui->setupUi(this);
}

CodeView::~CodeView()
{
    delete ui;
}

void CodeView::loadFile(QFile &file)
{
    if (file.open(QIODevice::ReadOnly | QIODevice::Text))
        Ui_CodeView::plainTextEdit->setPlainText(file.readAll());
    file.close();
}
[/PHP]

And if you want it, codeview.h:
[PHP]#ifndef CODEVIEW_H
#define CODEVIEW_H

#include <QtGui/QWidget>
#include <QFile>

namespace Ui
{
    class CodeView;
}

class CodeView : public QWidget
{
    Q_OBJECT

public:
    CodeView(QWidget *parent = 0);
    ~CodeView();
    void loadFile(QFile &file);

private:
    Ui::CodeView *ui;
};

#endif // CODEVIEW_H
[/PHP]

Having no call to 'CodeView::loadFile()' was on purpose. I'm going to test this function after I can get it to compile.

I get the feeling that there is a simple explanation for this. This would be my first project using classes.

EDIT: This is the compilation output:
```
Running build steps for project CodeView...
Configuration unchanged, skipping QMake step.
Starting: /usr/bin/make -w 
make: Entering directory `/home/jordy/CodeView'
g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/lib/qt4/mkspecs/linux-g++ -I. -I/usr/lib/qt4/include/QtCore -I/usr/lib/qt4/include/QtGui -I/usr/lib/qt4/include -I. -I. -o codeview.o codeview.cpp
ui_codeview.h: In member function &#8216;void CodeView::loadFile(QFile&)&#8217;:
ui_codeview.h:32: error: object missing in reference to &#8216;Ui_CodeView::plainTextEdit&#8217;
codeview.cpp:18: error: from this location
make: *** [codeview.o] Error 1
make: Leaving directory `/home/jordy/CodeView'
Exited with code 2.
Error while building project CodeView
When executing build step 'Make'
```

Thanks,
Jordy

---

### Post by Mirge on 2009-07-07
Not sure how you're attempting to compile, but use:

qmake -project
qmake
make

---

### Post by JordyD on 2009-07-07
> **Mirge said:**
> Not sure how you're attempting to compile, but use:

qmake -project
qmake
make

I'm using Qt Creator. It has a build button and a run qmake button.

---

### Post by Mirge on 2009-07-07
> **JordyD said:**
> I'm using Qt Creator. It has a build button and a run qmake button.

Never worked for me. I use it as well (or did, until I found the Qt plugin for Eclipse)... I always had to qmake -project ; qmake ; make

---

### Post by JordyD on 2009-07-07
> **Mirge said:**
> Never worked for me. I use it as well (or did, until I found the Qt plugin for Eclipse)... I always had to qmake -project ; qmake ; make
:( So I have to learn how to make a makefile?

I added the compilation output (from the Compile Output palette) to my OP. I don't don't think it means much, though.

EDIT: I get the same output when I try a qmake -project, qmake, make.

---

### Post by Zugzwang on 2009-07-07
> **JordyD said:**
> EDIT: I get the same output when I try a qmake -project, qmake, make.

Ok, this is what we need to know here.

Can you also tell us to which line in your header file the error message refers to? I don't actually think it's line 32 of what you actually posted ("gridLayout->setMargin(11); "). Can you please verify this and copy&paste the line here such that we are all talking about the same line?

---

### Post by JordyD on 2009-07-07
> **Zugzwang said:**
> Ok, this is what we need to know here.

Can you also tell us to which line in your header file the error message refers to? I don't actually think it's line 32 of what you actually posted ("gridLayout->setMargin(11); "). Can you please verify this and copy&paste the line here such that we are all talking about the same line?

Whoops. There is a missing chunk in the file. I'll add it in my OP. But the line it brings me to is:
```
    QPlainTextEdit *plainTextEdit;
```

The chunk that was missing:
```
/********************************************************************************
** Form generated from reading ui file 'codeview.ui'
**
** Created: Tue Jul 7 13:03:24 2009
**      by: Qt User Interface Compiler version 4.5.2
**
** WARNING! All changes made in this file will be lost when recompiling ui file!
********************************************************************************/

```

---

### Post by Zugzwang on 2009-07-07
Actually, I don't know where the problem comes from. However, I did notice that you are doing some mess with namespaces. Why do you declare your own class in the QT namespace? Also, you declare a class called CodeView and use the same text as variable name in your setupUI function. Finally, you put the namespace Ui into the QT namespace and declare another class called "CodeView".

What I would do: Commenting out all commands until purely the class structure remains. If that compiles, gradually remove the comment tags until you find the problem.

---

### Post by Mirge on 2009-07-07
> **JordyD said:**
> :( So I have to learn how to make a makefile?

I added the compilation output (from the Compile Output palette) to my OP. I don't don't think it means much, though.

EDIT: I get the same output when I try a qmake -project, qmake, make.

I know it didn't solve the problem, but using qmake actually creates the Makefile for you.

---

### Post by JordyD on 2009-07-07
> **Zugzwang said:**
> Actually, I don't know where the problem comes from. However, I did notice that you are doing some mess with namespaces. Why do you declare your own class in the QT namespace? Also, you declare a class called CodeView and use the same text as variable name in your setupUI function. Finally, you put the namespace Ui into the QT namespace and declare another class called "CodeView".

What I would do: Commenting out all commands until purely the class structure remains. If that compiles, gradually remove the comment tags until you find the problem.
:D Those classes (EDIT: and namespaces) you're mentioning are created by Qt Creator. The only code I wrote myself was the loadFile method in the CodeView class.

---

### Post by Roptaty on 2009-07-07
Try changing this line:
 Ui_CodeView::plainTextEdit->setPlainText(file.readAll());
to:
 ui->plainTextEdit->setPlainText(file.readAll());

---

### Post by JordyD on 2009-07-07
> **Roptaty said:**
> Try changing this line:
 Ui_CodeView::plainTextEdit->setPlainText(file.readAll());
to:
 ui->plainTextEdit->setPlainText(file.readAll());
:D That fixed it. Thanks!

---

