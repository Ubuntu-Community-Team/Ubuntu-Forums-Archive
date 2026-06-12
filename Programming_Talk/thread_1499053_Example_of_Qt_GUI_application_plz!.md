---
title: "Example of Qt GUI application plz!"
date: 2010-06-01
forum: Programming Talk
---

### Post by hakermania on 2010-06-01
Hello, can anybody give me an example of a Qt GUI application, that has a button and when you push it, a file.txt file is created in the same directory which contains "hello, world"
I would like to have its source code.
thx in advance...

---

### Post by Igorpan on 2010-06-01
just create new program.

**in mainwindow.h add:**

```
private slots:
void CreateFile();
```

**than drag a pushButton on your form.**

**in mainwindow.cpp **

add this to beginning of file: ```
#include <fstream>
```

add this in MainWindow constructor:

```
QObject::connect(ui->pushButton,SIGNAL(clicked()),this,SLOT(CreateFile()));
```

than declare what CreateFile function will do:

```
void MainWindow::CreateFile()
{
ofstream a;
a.open("file.txt");
a << "Hello World";
a.close();
}
```

Thats it I guess :D

---

### Post by nvteighen on 2010-06-02
Although not perfect, LaRoza's sysres project that was alive here for a while had a really good and basic PyQt interface; it's possibly the best coded part of the project. I know it is Python and not C++, but the logic when using Qt is exactly the same and it may teach you how the library is meant to be used. The code is still available at [https://code.launchpad.net/~laroza/sysres/sysres](https://code.launchpad.net/~laroza/sysres/sysres)

---

### Post by hakermania on 2010-06-03
Thanks for your answers. Can you please give me the full files ?
(I am a begginer and I didn't understand some things, I would be really thankful if you do so...)

---

