---
title: "qt compiling error............"
date: 2009-05-07
forum: Programming Talk
---

### Post by abhilashm86 on 2009-05-07
just did a short code, like this, is GUI 
```
#include <QtGui/QApplication>
#include "window.h"

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);

    QWidget *window = new QWidget();
     window->resize(320, 240);
     window->show();
    return a.exec();
}
```

when i build, error is, 
:-1: error: collect2: ld returned 1 exit status

whats exact meaning of this error?? how to overcome?

---

### Post by snova on 2009-05-07
> **abhilashm86 said:**
> :-1: error: collect2: ld returned 1 exit status

That in itself just means something went wrong. What came before it? Post the entire output, please.

---

