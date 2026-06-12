---
title: "qtcreator help"
date: 2015-03-26
forum: Programming Talk
---

### Post by fugu2 on 2015-03-26
I set up QT Creator using ```
sudo apt-get install qtcreator
``` and now I'm try tp compile and run the example code from [https://qt-project.org/doc/qt-4.7/desktop-systray.html](https://qt-project.org/doc/qt-4.7/desktop-systray.html) but im getting errors that has nothing in google or anything. can anyone help?
```

systray/main.cpp:49: error: variable 'QApplication app' has initializer but incomplete type
      QApplication app(argc, argv);
systray/main.cpp:52: error: 'QMessageBox' has not been declared
          QMessageBox::critical(0, QObject::tr("Systray"),
systray/main.cpp:57: error: incomplete type 'QApplication' used in nested name specifier
      QApplication::setQuitOnLastWindowClosed(false);

```

---

### Post by spjackson on 2015-03-27
You are not including the right headers.
```

#include <QApplication>
#include <QMessageBox>

```
If you need further help, please post main.cpp.

---

### Post by fugu2 on 2015-03-27
ok, the main.cpp is at [https://qt-project.org/doc/qt-4.7/desktop-systray-window-cpp.html](https://qt-project.org/doc/qt-4.7/desktop-systray-window-cpp.html), which i'll repost below for clarity.
I'm thinking that this might be a versioning issue, where this demo was written in qt-4.7 and ubuntu's qtcreator is trying to compile it at qt-5.
How do I tell qtcreator to compile this project with qt-4.7?
```

    /****************************************************************************
    **
    ** Copyright (C) 2011 Nokia Corporation and/or its subsidiary(-ies).
    ** All rights reserved.
    ** Contact: Nokia Corporation (qt-info@nokia.com)
    **
    ** This file is part of the examples of the Qt Toolkit.
    **
    ** $QT_BEGIN_LICENSE:BSD$
    ** You may use this file under the terms of the BSD license as follows:
    **
    ** "Redistribution and use in source and binary forms, with or without
    ** modification, are permitted provided that the following conditions are
    ** met:
    **   * Redistributions of source code must retain the above copyright
    **     notice, this list of conditions and the following disclaimer.
    **   * Redistributions in binary form must reproduce the above copyright
    **     notice, this list of conditions and the following disclaimer in
    **     the documentation and/or other materials provided with the
    **     distribution.
    **   * Neither the name of Nokia Corporation and its Subsidiary(-ies) nor
    **     the names of its contributors may be used to endorse or promote
    **     products derived from this software without specific prior written
    **     permission.
    **
    ** THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
    ** "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
    ** LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
    ** A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
    ** OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
    ** SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
    ** LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
    ** DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
    ** THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
    ** (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
    ** OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE."
    ** $QT_END_LICENSE$
    **
    ****************************************************************************/
     
    #include <QtGui>
     
    #include "window.h"
     
    Window::Window()
     {
        createIconGroupBox();
        createMessageGroupBox();
     
        iconLabel->setMinimumWidth(durationLabel->sizeHint().width());
     
        createActions();
        createTrayIcon();
     
        connect(showMessageButton, SIGNAL(clicked()), this, SLOT(showMessage()));
        connect(showIconCheckBox, SIGNAL(toggled(bool)),
                trayIcon, SLOT(setVisible(bool)));
        connect(iconComboBox, SIGNAL(currentIndexChanged(int)),
                this, SLOT(setIcon(int)));
        connect(trayIcon, SIGNAL(messageClicked()), this, SLOT(messageClicked()));
        connect(trayIcon, SIGNAL(activated(QSystemTrayIcon::ActivationReason)),
                this, SLOT(iconActivated(QSystemTrayIcon::ActivationReason)));
     
        QVBoxLayout *mainLayout = new QVBoxLayout;
        mainLayout->addWidget(iconGroupBox);
        mainLayout->addWidget(messageGroupBox);
        setLayout(mainLayout);
     
        iconComboBox->setCurrentIndex(1);
        trayIcon->show();
     
        setWindowTitle(tr("Systray"));
        resize(400, 300);
    }
     
    void Window::setVisible(bool visible)
     {
        minimizeAction->setEnabled(visible);
        maximizeAction->setEnabled(!isMaximized());
        restoreAction->setEnabled(isMaximized() || !visible);
        QDialog::setVisible(visible);
    }
     
    void Window::closeEvent(QCloseEvent *event)
     {
        if (trayIcon->isVisible())  {
            QMessageBox::information(this, tr("Systray"),
                                     tr("The program will keep running in the "
                                        "system tray. To terminate the program, "
                                        "choose <b>Quit</b> in the context menu "
                                        "of the system tray entry."));
            hide();
            event->ignore();
        }
    }
     
    void Window::setIcon(int index)
     {
        QIcon icon = iconComboBox->itemIcon(index);
        trayIcon->setIcon(icon);
        setWindowIcon(icon);
     
        trayIcon->setToolTip(iconComboBox->itemText(index));
    }
     
    void Window::iconActivated(QSystemTrayIcon::ActivationReason reason)
     {
        switch (reason)  {
        case QSystemTrayIcon::Trigger:
        case QSystemTrayIcon::DoubleClick:
            iconComboBox->setCurrentIndex((iconComboBox->currentIndex() + 1)
                                          % iconComboBox->count());
            break;
        case QSystemTrayIcon::MiddleClick:
            showMessage();
            break;
        default:
            ;
        }
    }
     
    void Window::showMessage()
     {
        QSystemTrayIcon::MessageIcon icon = QSystemTrayIcon::MessageIcon(
                typeComboBox->itemData(typeComboBox->currentIndex()).toInt());
        trayIcon->showMessage(titleEdit->text(), bodyEdit->toPlainText(), icon,
                              durationSpinBox->value() * 1000);
    }
     
    void Window::messageClicked()
     {
        QMessageBox::information(0, tr("Systray"),
                                 tr("Sorry, I already gave what help I could.\n"
                                    "Maybe you should try asking a human?"));
    }
     
    void Window::createIconGroupBox()
     {
        iconGroupBox = new QGroupBox(tr("Tray Icon"));
     
        iconLabel = new QLabel("Icon:");
     
        iconComboBox = new QComboBox;
        iconComboBox->addItem(QIcon(":/images/bad.svg"), tr("Bad"));
        iconComboBox->addItem(QIcon(":/images/heart.svg"), tr("Heart"));
        iconComboBox->addItem(QIcon(":/images/trash.svg"), tr("Trash"));
     
        showIconCheckBox = new QCheckBox(tr("Show icon"));
        showIconCheckBox->setChecked(true);
     
        QHBoxLayout *iconLayout = new QHBoxLayout;
        iconLayout->addWidget(iconLabel);
        iconLayout->addWidget(iconComboBox);
        iconLayout->addStretch();
        iconLayout->addWidget(showIconCheckBox);
        iconGroupBox->setLayout(iconLayout);
    }
     
    void Window::createMessageGroupBox()
     {
        messageGroupBox = new QGroupBox(tr("Balloon Message"));
     
        typeLabel = new QLabel(tr("Type:"));
     
        typeComboBox = new QComboBox;
        typeComboBox->addItem(tr("None"), QSystemTrayIcon::NoIcon);
        typeComboBox->addItem(style()->standardIcon(
                QStyle::SP_MessageBoxInformation), tr("Information"),
                QSystemTrayIcon::Information);
        typeComboBox->addItem(style()->standardIcon(
                QStyle::SP_MessageBoxWarning), tr("Warning"),
                QSystemTrayIcon::Warning);
        typeComboBox->addItem(style()->standardIcon(
                QStyle::SP_MessageBoxCritical), tr("Critical"),
                QSystemTrayIcon::Critical);
        typeComboBox->setCurrentIndex(1);
     
        durationLabel = new QLabel(tr("Duration:"));
     
        durationSpinBox = new QSpinBox;
        durationSpinBox->setRange(5, 60);
        durationSpinBox->setSuffix(" s");
        durationSpinBox->setValue(15);
     
        durationWarningLabel = new QLabel(tr("(some systems might ignore this "
                                             "hint)"));
        durationWarningLabel->setIndent(10);
     
        titleLabel = new QLabel(tr("Title:"));
     
        titleEdit = new QLineEdit(tr("Cannot connect to network"));
     
        bodyLabel = new QLabel(tr("Body:"));
     
        bodyEdit = new QTextEdit;
        bodyEdit->setPlainText(tr("Don't believe me. Honestly, I don't have a "
                                  "clue.\nClick this balloon for details."));
     
        showMessageButton = new QPushButton(tr("Show Message"));
        showMessageButton->setDefault(true);
     
        QGridLayout *messageLayout = new QGridLayout;
        messageLayout->addWidget(typeLabel, 0, 0);
        messageLayout->addWidget(typeComboBox, 0, 1, 1, 2);
        messageLayout->addWidget(durationLabel, 1, 0);
        messageLayout->addWidget(durationSpinBox, 1, 1);
        messageLayout->addWidget(durationWarningLabel, 1, 2, 1, 3);
        messageLayout->addWidget(titleLabel, 2, 0);
        messageLayout->addWidget(titleEdit, 2, 1, 1, 4);
        messageLayout->addWidget(bodyLabel, 3, 0);
        messageLayout->addWidget(bodyEdit, 3, 1, 2, 4);
        messageLayout->addWidget(showMessageButton, 5, 4);
        messageLayout->setColumnStretch(3, 1);
        messageLayout->setRowStretch(4, 1);
        messageGroupBox->setLayout(messageLayout);
    }
     
    void Window::createActions()
     {
        minimizeAction = new QAction(tr("Mi&nimize"), this);
        connect(minimizeAction, SIGNAL(triggered()), this, SLOT(hide()));
     
        maximizeAction = new QAction(tr("Ma&ximize"), this);
        connect(maximizeAction, SIGNAL(triggered()), this, SLOT(showMaximized()));
     
        restoreAction = new QAction(tr("&Restore"), this);
        connect(restoreAction, SIGNAL(triggered()), this, SLOT(showNormal()));
     
        quitAction = new QAction(tr("&Quit"), this);
        connect(quitAction, SIGNAL(triggered()), qApp, SLOT(quit()));
    }
     
    void Window::createTrayIcon()
     {
        trayIconMenu = new QMenu(this);
        trayIconMenu->addAction(minimizeAction);
        trayIconMenu->addAction(maximizeAction);
        trayIconMenu->addAction(restoreAction);
        trayIconMenu->addSeparator();
        trayIconMenu->addAction(quitAction);
     
        trayIcon = new QSystemTrayIcon(this);
        trayIcon->setContextMenu(trayIconMenu);
    }


```

---

### Post by spjackson on 2015-03-27
To build this project with Qt 5 you need to make the following changes.
1. Replace <QtGui> with <QtWidgets> in both main.cpp and window.cpp.
2. In systray.pro remove svg and add the lines:
```

QT       += core
QT       += widgets
CONFIG   -= app_bundle

```

To use Qt 4.x, first ensure that you have the 4.x development packages installed. Possibly install the qtchooser package and use it. Within Qt Creator, Tools->Options->Qt Build & Run then select the Qt Versions tab. I don't use Qt Creator much and I haven't tried to use the latest creator to build a 4.x project, so some of these details may not be 100% accurate.

---

### Post by fugu2 on 2015-03-28
First of all thank you for your help with this. I would love to get this to work with Qt5. I made the changes you sugested but I'm getting a new error. 
```

main.cpp:41:22: fatal error: QtWidgets: No such file or directory
  #include <QtWidgets>

```
any ideas on this one?

---

### Post by steeldriver on 2015-03-28
You may need to adjust the include path to include /usr/include/qt5/QtWidgets/, or specify the subdirectory explicitly e.g.

```

#include <QtWidgets/QtWidgets>

```

---

### Post by fugu2 on 2015-04-04
Ok, I figured out what the problem is. Ubuntu will not allow Qt5 to work with QSystemTrayIcon. The 2 are incompatible. In order to get this to work, you need to have qmake-qt4 installed, and configure qtcreator to use Qt4. 
Projects >> Manage Kits... >> Add >> Qt Version: >> Qt 4.x.x 
I also set that one as Default for my purposes. Thank you all for your help.

---

