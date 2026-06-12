---
title: "Qt programming"
date: 2010-02-16
forum: Programming Talk
---

### Post by reggler on 2010-02-16
Hi,

I would like to compile a simple hello world application.
My code looks like this:
```
#include <qapplication.h>
#include <qpushbutton.h>


int main( int argc, char **argv )
{
    QApplication a( argc, argv );

    QPushButton hello( "Hello world!", 0 );
    hello.resize( 100, 30 );

    a.setMainWidget( &hello );
    hello.show();
    return a.exec();
}
```
if I make a **qmake -project** and a **qmake** followed by a **make**
I get following compiler errors:
h```
elloworld.c: In function ‘main’:
helloworld.c:13: error: ‘QApplication’ undeclared (first use in this function)
helloworld.c:13: error: (Each undeclared identifier is reported only once
helloworld.c:13: error: for each function it appears in.)
helloworld.c:13: error: expected ‘;’ before ‘a’
helloworld.c:15: error: ‘QPushButton’ undeclared (first use in this function)
helloworld.c:15: error: expected ‘;’ before ‘hello’
helloworld.c:16: error: ‘hello’ undeclared (first use in this function)
helloworld.c:18: error: ‘a’ undeclared (first use in this function)
helloworld.c:11: warning: unused parameter ‘argc’
helloworld.c:11: warning: unused parameter ‘argv’
make: *** [helloworld.o] Error 1
reg@reg-desktop:~/src/Qt$
```

Why is that? Why would it not recognize **QApplication**... :o

Thanks for help!

---

### Post by korvirlol on 2010-02-17
I am pretty sure it is (unless there was loss of translation in your copy-paste):

```
#include <QApplication>
#include <QPushButton>
```

---

### Post by reggler on 2010-02-17
> **korvirlol said:**
> I am pretty sure it is (unless there was loss of translation in your copy-paste):

```
#include <QApplication>
#include <QPushButton>
```

nope, 

```
#include <qapplication.h>
#include <qpushbutton.h>
```
was correct but i just realized that i get 100s of error messages above when compiling the headers and some of them look like:
**In file included from /usr/include/qt3/qwindowdefs.h** which probably appear because it's trying to compile qt3 stuff but i only have qt4 installed....how can i fix that?
Thanks!
Ron

---

### Post by mdurham on 2010-02-17
Try #include <QtGui/QApplication>, that's what I get automatically generated.
And, I don't think that QApplication has a setMainWidget() method.
How confusing. Cheers, Mike

---

### Post by scourge on 2010-02-17
Did you even try what korvirlol suggested, before deciding that your way was the correct one? Because he's right.

---

