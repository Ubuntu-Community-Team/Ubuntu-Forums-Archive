---
title: "GUI by using qt"
date: 2010-04-24
forum: Programming Talk
---

### Post by kishorebjv on 2010-04-24
hi all...
  i dont know any thing about Qt other than my friend told that it generates the GUI for c++ code....
  please let me know 
  1.How to execute some command when a button in window is clicked..?
  "g++ encryption.cpp -lgmp" command should be executed when i pressed "enc" button..
  2.How to accept the text from text area(in the window) to a textfile and the text(need not be text,it can be any data..) in a text file should be displayed in Textarea of window ?
  please help me out... im running out of time... 
  thanks in advance....

---

### Post by lisati on 2010-04-24
Moved to "Programming Talk"

---

### Post by Alan James on 2010-04-25
I have played a little with QT Creator and found that it makes the process of making GUIs very easy. I am not a programmer but I was able to still make a simple GUI in a few minutes, although getting it to function was harder. I believe QT Creator is available in the repos, check it out.

---

### Post by benson444 on 2010-04-25
If you install Qt Creator, Qt Assistant will also be installed. Qt has fantastic documentation. Start Qt Assistant and check out Qt Reference Documentation->Classes. QProcess handles external programs and QFile deals with reading/writing files.

Qt uses the signal/slot mechanism for handling program events. You connect a particular object's particular signal to a slot function. Connect the signals/slots in the constructor or in a utility function that you call in the constructor. eg

```
connect(encButton, SIGNAL(clicked()), this, SLOT(encButtonClicked()));
```

The function would be something along these lines:

```
void MyClass::encButtonClicked() {
  QString program = "/usr/bin/g++";
  QStringList args;
  args << "encryption.cpp" << "-lgmp";

  QProcess *proc = new QProcess(parent);
  proc->start(program, args);
}
```

For reading a text file and putting the contents in a QTextEdit window:

```
connect(openButton, SIGNAL(clicked()), this, SLOT(openButtonClicked()));
```

```
void MyClass::openButtonClicked() {
  QFile file("filename.txt");
  if(!file.open(QFile::ReadOnly | QFile::Text))
    return;

  QTextStream in(&file);
  textArea->setPlainText(in.readAll());
}
```

As I say, the documentation is great. Full program examples covering all major topics and a hugely detailed class reference.

---

