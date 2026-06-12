---
title: "what this compiler error in qt??"
date: 2009-07-11
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-11
i have a header file widget.h, widget.cpp and widget.ui file, i din't get compiler error which says error in main function
```

#include <QtGui/QApplication>
#include "widget.h"

int main(int argc, char *argv[])
    {
          QApplication a(argc, argv);
          Widget w;
          w.hello();
          w.show();
          return a.exec();
    }


```

compiler error is,
main.cpp:4: error: new types may not be defined in a return type
main.cpp:4: note: (perhaps a semicolon is missing after the definition of ‘Widget’)
main.cpp:4: error: two or more data types in declaration of ‘main’

where actually is this error, its showing error in 4 line, i din't understand what sort of error is it?? please anyone could explain??

---

### Post by McNils on 2009-07-11
It looks like the problem is in widget.h. maybe you forgot a semicolon after the class definition...

---

### Post by JordyD on 2009-07-11
May we see your other files, if you don't mind? Errors are not always where the compiler claims.

---

