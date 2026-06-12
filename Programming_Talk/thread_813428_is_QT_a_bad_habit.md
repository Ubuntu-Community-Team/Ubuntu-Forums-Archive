---
title: "is QT a bad habit?"
date: 2008-05-30
forum: Programming Talk
---

### Post by StOoZ on 2008-05-30
Im kinda new to C++ , read two primer books (huge ones...), and programmed the exercises from the books , and more from my mind... some STL code etc.
now I would like to develop a cross-platform app, I find QT to match all my requirements, BUT, as a newcomer to C++, is QT a bad C++ coding style for new C++ users?
The app is not going to be only GUI, if it was , I could use wxwidgets,etc, but also XML,sockets..etc.

---

### Post by LaRoza on 2008-05-30
> **StOoZ said:**
> Im kinda new to C++ , read two primer books (huge ones...), and programmed the exercises from the books , and more from my mind... some STL code etc.
now I would like to develop a cross-platform app, I find QT to match all my requirements, BUT, as a newcomer to C++, is QT a bad C++ coding style for new C++ users?
The app is not going to be only GUI, if it was , I could use wxwidgets,etc, but also XML,sockets..etc.

No, it is a fine library (or set of libraries). It should fulfill your needs fine if you are writing non commercial software.

---

### Post by StOoZ on 2008-05-31
im writing an open source application.
the problem is, I feel that , its not quite the C++ syntax,everything is so clean and neat , which is good , but is it a good practice for a new C++ programmer?

also , I've heard that KDE is based on Qt , which means, KDE did not pay to trolltech a dime because KDE is an open source software?

---

### Post by DavidBell on 2008-05-31
> **StOoZ said:**
> everything is so clean and neat , which is good , but is it a good practice for a new C++ programmer?


Umm, yeah it is.

---

### Post by Jessehk on 2008-05-31
The one thing that has always bothered me about Qt is the strange memory management. Contrary to normal C++, they actually **encourage** you to avoid initialization lists and delete'ing memory because the classes do their own cleanup.

For example, the "correct" way of subclassing QWidget to make a Widget with a single button is something like this:

```

#include <QtGui/QWidget>
#include <QtGui/QPushButton>
#include <QtGui/QVBoxLayout>
#include <QApplication>

class MyWidget : public QWidget {
    QPushButton *button_;
public:
    explicit MyWidget( QWidget *parent = 0 );
};

MyWidget::MyWidget( QWidget *parent )
    : QWidget( parent ) {

    QVBoxLayout *layout = new QVBoxLayout;

    button_ = new QPushButton( tr( "Quit" ) );
    connect( button_, SIGNAL( clicked() ),
             qApp, SLOT( quit() ) );

    layout->addWidget( button_ );
    setLayout( layout );
}

int main( int argc, char **argv ) {
    QApplication app( argc, argv );

    MyWidget widget;
    widget.show();

    return app.exec();
}

```

Very weird.

On the other hand, Qt has amazing documentation and is technically very good.

---

### Post by samjh on 2008-05-31
> **StOoZ said:**
> im writing an open source application.
the problem is, I feel that , its not quite the C++ syntax,everything is so clean and neat , which is good , but is it a good practice for a new C++ programmer?

also , I've heard that KDE is based on Qt , which means, KDE did not pay to trolltech a dime because KDE is an open source software?

Qt makes use of a lot of macros and wrappers on top of standard C++.  This does not make it BAD practice.  If you are familiar with the basic usage of standard C++, it will not hamper you.

KDE was and still is written using Qt.  KDE 3.x.x is based on Qt3, while KDE 4.x.x is based on Qt4.

The Qt license allows anyone to use Qt for non-commercial purposes as long as the source code is released, as per GPL requirements.  Closed-source projects need a commercial license.  (As an aside, there is also an agreement between Trolltech and the KDE project, to release Qt under a BSD-style permissive license if Trolltech ceases to exist.)

---

### Post by Npl on 2008-05-31
> **Jessehk said:**
> The one thing that has always bothered me about Qt is the strange memory management. Contrary to normal C++, they actually **encourage** you to avoid initialization lists and **delete'ing memory** because the classes do their own cleanup.Well, thats a good practice in C++, if Objects can live on the stack then for all means **dont** use new/delete.

---

