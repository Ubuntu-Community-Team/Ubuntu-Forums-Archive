---
title: "Qt Text Editor crashing when saving/opening text files"
date: 2013-06-05
forum: Programming Talk
---

### Post by dsomers1024 on 2013-06-05
Hello everyone,

I am teaching myself Qt development and I'm working on a simple text editor as my first project to help me learn. I am using KDevelop as my IDE. The problem that I'm getting is my program crashes whenever I attempt to save or open text files.

Here is my code:

gui_output2.cpp:
```

#include "gui_output2.h"

#include <QtGui>

gui_output2::gui_output2()
{
    QMenu *fileMenu;
    QTextEdit* textEdit = new QTextEdit(this);
    setCentralWidget(textEdit);
    
    QAction* openaction = new QAction(this);
    QAction* saveaction = new QAction(this);
    QAction* quitaction = new QAction(this);
    
    openaction->setText("Open");
    saveaction->setText("Save");
    quitaction->setText( "Quit" );
    
    connect(openaction, SIGNAL(triggered()), this, SLOT(fileOpen()));
    connect(saveaction, SIGNAL(triggered()), this, SLOT(fileSave()));
    connect(quitaction, SIGNAL(triggered()), SLOT(close()));
    
    fileMenu = menuBar()->addMenu( "File" );
    fileMenu->addAction( openaction );
    fileMenu->addAction( saveaction );
    fileMenu->addSeparator();
    fileMenu->addAction( quitaction );
    
    setWindowTitle("Disturbed Edit");
}

void gui_output2::fileOpen()
{
  QString fileName = QFileDialog::getOpenFileName(this, tr("Open File"), "", tr("Text Files (*.txt);;C++ Files (*.cpp *.h)"));
  
  if (fileName != "") {
    QFile file(fileName);
    if (!file.open(QIODevice::ReadOnly)) {
      QMessageBox::critical(this, "Error", "Could not open file");
      return;
    }
    QTextStream in(&file);
    textEdit->setText(in.readAll());
    file.close();
  }
}  

void gui_output2::fileSave()
{
  QString fileName = QFileDialog::getSaveFileName(this, "Save File", "", "Text Files (*.txt);;C++ Files (*.cpp, *.h)");
  
  if (fileName != "") {
    QFile file(fileName);
    if (!file.open(QIODevice::WriteOnly)) {
      // error message
    } else {
      QTextStream stream(&file);
      stream << textEdit->toPlainText();
      stream.flush();
      file.close();
    }
  }
}


gui_output2::~gui_output2()
{}

#include "gui_output2.moc"

```

gui_output2.h
```

#ifndef gui_output2_H
#define gui_output2_H

#include <QtGui/QMainWindow>
#include <QtGui/QTextEdit>

class gui_output2 : public QMainWindow
{
Q_OBJECT
public:
    gui_output2();
    virtual ~gui_output2();
    
    QTextEdit *textEdit;
private slots:
    void fileOpen();
    void fileSave();
};

#endif // gui_output2_H

```

main.cpp:
```

#include <QtGui/QApplication>
#include "gui_output2.h"


int main(int argc, char** argv)
{
    QApplication app(argc, argv);
    gui_output2 foo;
    foo.show();
    return app.exec();
}

```

When I run it thru the debugger the open function is crashing when the line "textEdit->setText(in.readAll());" is executed. 

The save function is crashing when the line "stream << textEdit->toPlainText();" is executed.

Can any tell me what I am doing wrong? I apologize if this is a trivial question as I'm trying to learn Qt4 programming.

Thanks,

David

---

### Post by GeneralZod on 2013-06-06
You aren't initialising your textEdit member variable declared in gui_output2.h (you initialise a local variable with that name in gui_output2::gui_output2()).

---

### Post by spjackson on 2013-06-06
In the constructor, this:
```

    QTextEdit* textEdit = new QTextEdit(this);
```should be:```

   textEdit = new QTextEdit(this);
```
As it stands, your constructor has a local variable textEdit which is not the same as this->textEdit. As a result, in your open and save functions textEdit is a pointer which has not been assigned a value.

---

### Post by dsomers1024 on 2013-06-06
> **spjackson said:**
> In the constructor, this:
```

    QTextEdit* textEdit = new QTextEdit(this);
```should be:```

   textEdit = new QTextEdit(this);
```
As it stands, your constructor has a local variable textEdit which is not the same as this->textEdit. As a result, in your open and save functions textEdit is a pointer which has not been assigned a value.

That did it. Thank you both for the help. 

Also just a general question... do most people use an IDE such as Eclipse or KDevelop for Qt development or do they just use a simple text editor?

Thanks,

David

---

### Post by Vaphell on 2013-06-06
i'd go with QtCreator and friends

---

