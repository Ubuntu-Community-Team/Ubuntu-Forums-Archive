---
title: "Qt: QRadioButton isChecked() function causes Segmentation Fault"
date: 2007-12-12
forum: Programming Talk
---

### Post by akudewan on 2007-12-12
I'm making a program in Qt, which has a small dialog with some radio buttons. When the program reaches the isChecked() function in NewDialog::setLevel(), it crashes with a Segfault. I'm a new programmer and I can't figure out what I'm doing wrong.

Here's the code:
```

//newdialog.h
#ifndef NEWDIALOG_H
#define NEWDIALOG_H

#include<QDialog>
#include "level.h"

class QGroupBox;
class QRadioButton;

class NewDialog : public QDialog
{
	Q_OBJECT
	public:
		NewDialog(QWidget *parent=0);
	signals:
		void okClicked(Level);
	private slots:
		void setLevel();
	private:
//  		QGroupBox *groupBox;
		QRadioButton *blankRadio;
		QRadioButton *easyRadio;
		QRadioButton *mediumRadio;
		QRadioButton *hardRadio;
		QRadioButton *hardestRadio;
		QRadioButton *extremeRadio;
		QPushButton *okButton;
		QPushButton *cancelButton;
};

#endif

```

```

//newdialog.cpp
#include<QtGui>
#include "newdialog.h"

NewDialog::NewDialog(QWidget *parent) : QDialog(parent)
{
// 	QGroupBox *groupBox = new QGroupBox(tr("Select game type"));

	QRadioButton *blankRadio = new QRadioButton(tr("Blank Game"));
	QRadioButton *easyRadio = new QRadioButton(tr("Easy"));
	QRadioButton *mediumRadio = new QRadioButton(tr("Medium"));
	QRadioButton *hardRadio = new QRadioButton(tr("Hard"));
	QRadioButton *hardestRadio = new QRadioButton(tr("Hardest"));
	QRadioButton *extremeRadio = new QRadioButton(tr("Extreme"));
	
	QPushButton *okButton = new QPushButton(tr("Ok"));
	QPushButton *cancelButton = new QPushButton(tr("Cancel"));
	
	connect(okButton, SIGNAL( clicked() ), this, SLOT( setLevel() ) );
	connect(cancelButton, SIGNAL( clicked() ), this, SLOT( close() ) );
	
	QHBoxLayout *buttonLayout = new QHBoxLayout;
	QVBoxLayout *radioLayout = new QVBoxLayout;
	
	buttonLayout->addWidget(okButton);
	buttonLayout->addWidget(cancelButton);
	buttonLayout->addStretch();
	
	radioLayout->addWidget(blankRadio);
	radioLayout->addWidget(easyRadio);
	radioLayout->addWidget(mediumRadio);
	radioLayout->addWidget(hardRadio);
	radioLayout->addWidget(hardestRadio);
	radioLayout->addWidget(extremeRadio);
	radioLayout->addStretch();
	radioLayout->addLayout(buttonLayout);
	
	blankRadio->setChecked(true);
	
	setLayout(radioLayout);
	
	setWindowTitle(tr("New Game"));
}

void NewDialog::setLevel()
{
	[COLOR="Red"]if(blankRadio->isChecked())[/COLOR]
		emit okClicked(BLANK);
	/*else
	{
		if(easyRadio->isChecked())
			emit okClicked(EASY);
		else
		{
			if(mediumRadio->isChecked())
				emit okClicked(MEDIUM);
			else
			{
				if(hardRadio->isChecked())
					emit okClicked(HARD);
				else
				{
					if(hardestRadio->isChecked())
						emit okClicked(HARDEST);
					else
					{
						if(extremeRadio->isChecked())
							emit okClicked(EXTREME);
					}
				}
			}
		}
	}*/
}

```

The *emit* statement works fine when I comment out the If statement. I figured I don't really need to use QGroupBox since the dialog just has one set of buttons.

Can someone help me with this?

Thanks!

---

### Post by aks44 on 2007-12-12
In the constructor, you're declaring **local** variables that have the same name as the private variables declared in the class, so the class' private variables are "hidden".

As a consequence, the object's private variables are left uninitialized, thus the segfault.

In the constructor just use the class' variables instead of declaring new ones, and you'll be fine.
```
NewDialog::NewDialog(QWidget *parent) : QDialog(parent)
{
// 	QGroupBox *groupBox = new QGroupBox(tr("Select game type"));

	QRadioButton *blankRadio = new QRadioButton(tr("Blank Game"));
```becomes```
NewDialog::NewDialog(QWidget *parent) : QDialog(parent)
{
// 	groupBox = new QGroupBox(tr("Select game type"));

	blankRadio = new QRadioButton(tr("Blank Game"));

```etc...

---

### Post by akudewan on 2007-12-13
> **aks44 said:**
> In the constructor, you're declaring **local** variables that have the same name as the private variables declared in the class, so the class' private variables are "hidden".

As a consequence, the object's private variables are left uninitialized, thus the segfault.

In the constructor just use the class' variables instead of declaring new ones, and you'll be fine.


Right now would be a perfect moment to say.. "Doh!!"

Thanks for the help mate!

---

