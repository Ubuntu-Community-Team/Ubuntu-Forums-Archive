---
title: "Qt/GTK/Other (C++)"
date: 2008-10-06
forum: Programming Talk
---

### Post by l337a on 2008-10-06
Greetings, everyone. I haven't been here in a while, but I have a few questions.

```
#include <iostream>
#include <Qt>


int main(int argc, char** argv)
{
	
	return 0;
}
```

Why on earth am I running into this so early in my program? You would think that a compiler could at least find an include that IS in /usr/lib/qt

I tried doing it manually by using:

```
#include </usr/lib/qt>
```

No go. I'd like to figure out as to why I can't include anything other than the standard library. I'd also like to know how I can include more than one thing that's outside the standard library.

If all else fails, I'd like to create my own widget system. No, I'm not going to re-invent the wheel, but I'm honestly tired of a simple desktop interface. If anyone is interested in such a project, or they're also tired of such things; Email [email]ren.zerochan@gmail.com[/email]


P.s, I'm running Zenwalk. I didn't want to post it in their forums since there is little to no activity. I am using Geany as my IDE.

And on the compile parameters I added:

```
g++ -l /usr/lib/qt4 -Wall -c "%f"
```

Nothing. I'm stumped. Anyone?

---

### Post by snova on 2008-10-06
The headers are in /usr/include/qt4, and the libraries are where they should be, in /usr/lib. Well, assuming "Zenwalk" adheres (more or less) to the FHS.

```
g++ -I/usr/include/qt4 -I/usr/include/qt4/Qt -I/usr/include/QtCore -I/usr/include/QtGui -lQtCore -lQtGui -o program main.cpp
```

```
#include <QtGui/QApplication>
#include <QtGui/QPushButton>

int main( int ac, char* av[] )
{
    QApplication app( ac, av );
    QPushButton button( "Hello, World!" );
    QObject::connect( &button, SIGNAL( clicked() ), &app, SLOT( quit() ) );
    button.show();
    return app.exec();
}
```

---

