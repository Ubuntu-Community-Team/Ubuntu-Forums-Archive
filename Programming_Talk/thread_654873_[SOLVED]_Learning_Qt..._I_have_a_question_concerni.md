---
title: "[SOLVED] Learning Qt... I have a question concerning allocated objects"
date: 2007-12-31
forum: Programming Talk
---

### Post by dwhitney67 on 2007-12-31
I have the onerous task of plowing through about 30K lines of C++ code written for a Qt application.

One of things that irks me with the code I am seeing, and similarly with the code in the Qt tutorials, is the allocation of objects, yet no where to be found, the statement to deallocate the memory when the object is destroyed.

Is this acceptable Qt development practice?  For instance, below is some code from a tutorial example, for which I have commented out the original code which I find "offensive" and replaced with what I perceive to be something better.  Is this warranted, or am I misunderstanding something fundamental with how to develop Qt applications?

My only GUI development experience is with Java and DataViews.

[PHP]#ifndef LCDRANGE_H
#define LCDRANGE_H

#include <qvbox.h>

// Added code
#include <qslider.h>
#include <qlcdnumber.h>

// Original code
//class QSlider;


class LCDRange : public QVBox
{
  Q_OBJECT

  public:
    LCDRange( QWidget *parent = 0, const char *name = 0 );

    int value() const;

  public slots:
    void setValue( int );

  signals:
    void valueChanged( int );

  private:
    // Original code
    // QSlider *slider;

    // Added
    QSlider    slider;
    QLCDNumber lcd;
};

#endif[/PHP]

[PHP]#include "lcdrange.h"
//#include <qslider.h>
//#include <qlcdnumber.h>


LCDRange::LCDRange( QWidget *parent, const char *name )
    : QVBox( parent, name ),
      slider( Horizontal, this, "slider" ),
      lcd( 2, this, "lcd" )
{
  // Original code
  // QLCDNumber *lcd = new QLCDNumber( 2, this, "lcd" );
  // slider          = new QSlider( Horizontal, this, "slider" );

  // slider->setRange( 0, 99 );
  // slider->setValue( 0 );

  // connect( slider, SIGNAL( valueChanged(int) ), lcd, SLOT( display(int) ) );
  // connect( slider, SIGNAL( valueChanged(int) ), SIGNAL( valueChanged(int) ) );

  slider.setRange( 0, 99 );
  slider.setValue( 0 );

  connect( &slider, SIGNAL( valueChanged(int) ), &lcd, SLOT( display(int) ) );
  connect( &slider, SIGNAL( valueChanged(int) ), SIGNAL( valueChanged(int) ) );
}


int
LCDRange::value() const
{
  // Original code
  // return slider->value();

  return slider.value();
}


void
LCDRange::setValue( int value )
{
  // Original code
  // slider->setValue( value );

  slider.setValue( value );
}[/PHP]

---

### Post by YourSurrogateGod on 2007-12-31
Seems like a poorly written app (based on what you've shown.) The "new" keyword is not Qt specific (it's C++ specific) and yes, it needs to be "delete"ed at the end.

---

### Post by dwhitney67 on 2007-12-31
I am an experienced s/w developer, so I know what "new" is, and I also know that is is not just used in C++; it is also used in Java.

In your closing statement, you used the word "needs" to deallocate memory.  This is normally true if one wants to prevent a memory leak when recreating the same object over and over again or for various other reasons.  But for a GUI, which may only have one instance of a panel or a button or whatever, is it really necessary?  Sure it is good practice, but when the application is terminated, the memory will get automatically freed anyways.

I get the impression from the code from the tutorials that it isn't necessary to delete allocated memory.  I also see the same when viewing the code handed down to me at work.

Textbook recommendations don't always fit into the real world.  I am merely asking if this is one of those cases.

---

### Post by Jessehk on 2007-12-31
YourSurrogateGod is wrong.

[quote=http://doc.trolltech.com/4.3/tutorial-t4.html]
Note that quit is a local variable in the constructor. MyWidget does not keep track of it; Qt does, and will automatically delete it when the MyWidget object is deleted. This is why MyWidget doesn't need a destructor. (On the other hand, there is no harm in deleting a child when you choose to. The child will automatically tell Qt about its imminent death.)
[/quote]

As somebody who wrote a Qt program of about 2000 lines, I find it a bit confusing too. It's probably the only thing I dislike about Qt.
I never really understood how it works and it's always bothered me.

---

### Post by YourSurrogateGod on 2007-12-31
> **Jessehk said:**
> YourSurrogateGod is wrong.



As somebody who wrote a Qt program of about 2000 lines, I find it a bit confusing too. It's probably the only thing I dislike about Qt.
I never really understood how it works and it's always bothered me.

How am I wrong :) ?

I was talking about how memory should be (theoretically speaking) managed in C++ the whole time. Every time that you allocate a piece of memory on the heap, you should deallocate it (theoretically.)

---

### Post by YourSurrogateGod on 2007-12-31
> **dwhitney67 said:**
> I am an experienced s/w developer, so I know what "new" is, and I also know that is is not just used in C++; it is also used in Java.

In your closing statement, you used the word "needs" to deallocate memory.  This is normally true if one wants to prevent a memory leak when recreating the same object over and over again or for various other reasons.  But for a GUI, which may only have one instance of a panel or a button or whatever, is it really necessary?  Sure it is good practice, but when the application is terminated, the memory will get automatically freed anyways.

I get the impression from the code from the tutorials that it isn't necessary to delete allocated memory.  I also see the same when viewing the code handed down to me at work.

Textbook recommendations don't always fit into the real world.  I am merely asking if this is one of those cases.
Sure, you can do that.

But it is a good way to dissuade any potentially problematic behavior in the future by continue to stick to a safer convention (say you get to be less strict or someone new looks at your code and the impression that it never hurts to be more careful than less when it comes to memory management in C++ is not made.)

And yes, I know that new is used in Java. But since the topic was about C++ and Qt specifically...

---

### Post by Jucato on 2008-01-01
The reason why no delete/deallocation is necessary for widgets in Qt is explained in this discussion about the QObject class (which is inherited by all Qt widgets):

[http://doc.trolltech.com/3.3/qobject.html#details](http://doc.trolltech.com/3.3/qobject.html#details)

> QObjects organize themselves in object trees. When you create a QObject with another object as parent, the object will automatically do an insertChild() on the parent and thus show up in the parent's children() list. The parent takes ownership of the object i.e. it will automatically delete its children in its destructor...

Qt does this automatically. So when the main application (which is the topmost parent, so to speak) is destroyed, all children of the main application, and the children of those children, are deallocated/destroyed automatically.

---

### Post by dwhitney67 on 2008-01-01
So, you are implying that when insertChild() is called, the parent is "this", which is specified as the second arg in this constructor call:

[PHP]QLCDNumber *lcd = new QLCDNumber( 2, this, "lcd" );[/PHP]

Is this correct?

---

### Post by Jucato on 2008-01-01
Yes. In this context, "this" is the LCDRange class which, in turn, becomes a child of the main application/window (QApplication).

(Parent) QApplication ---> LCDRange --> QLCDNumber (Child)

When QApplication is destroyed, it's children (LCDRange) is destroyed, which in turn also destroys and deallocates its own children (QLCDNumber and QSlider).

---

### Post by dwhitney67 on 2008-01-01
Jucato, thank you for your replies.  Happy New Year!

---

### Post by Jessehk on 2008-01-01
> **dwhitney67 said:**
> So, you are implying that when insertChild() is called, the parent is "this", which is specified as the second arg in this constructor call:

[PHP]QLCDNumber *lcd = new QLCDNumber( 2, this, "lcd" );[/PHP]

Is this correct?

Just so you know, you could still use the arguably correct syntax of the initializer list and member variables. The **parent** argument in the QLCDNumber is the one that should allow it to be added as a child.

---

