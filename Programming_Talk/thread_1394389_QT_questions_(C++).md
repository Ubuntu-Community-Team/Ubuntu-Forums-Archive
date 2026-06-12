---
title: "QT questions (C++)"
date: 2010-01-30
forum: Programming Talk
---

### Post by caelestis2 on 2010-01-30
I have a QMainWindow with a menubar with an action to open a new window. I made it connect to a slot function to open that new window by doing:

[PHP]
MyWindow * window = new MyWindow(this);
window->show();
[/PHP]

Since the window is made on the heap, does it get deleted when you close that new window? Is using a connection from the action to the function the best way of opening a new window?
Also, I want this sub-window to require focus, so that the parent window won't be able to gain focus until the sub-window closes; how do I do that?

Also, if I declare a few widgets apart of that window:

[PHP]
MyWindow() {
  QWidget * widget = new QWidget(this);
}
[/PHP]

Do the widgets automatically get deleted when the window closes?
Or do I have to add a widget pointer to the private section and make a destructor to delete it?

---

### Post by dwhitney67 on 2010-01-30
It's been awhile since I did any Qt programming; from what I learned, a Qt object, once allocated, does not need to be deleted... that is handled automatically.  For your home-made objects, that may be different.  You may need to do that yourself.

Btw, if you want to avoid having to explicitly "delete" an object, you can declare said object using a smart pointer construct.  Such construct is available under TR1 and/or Boost.  I wouldn't be half surprised if Qt does something similar (for their 'Q' objects).

Here's an example of the TR1 shared_ptr...
```

#include <tr1/memory>

class MyClass
{
public:
   MyClass() {}

   void doSomething() {}
};

int main()
{
   using namespace std;

   tr1::shared_ptr<MyClass> mc(new MyClass);

   mc->doSomething();

   // mc is automatically deallocated here
}

```
You can verify that all memory has been freed using 'valgrind'.


P.S.  Oftentimes folks unnecessarily allocate their objects on the heap.  Try considering if it is possible to instantiate the object on the stack.

---

### Post by caelestis2 on 2010-01-30
I have found out what I needed to stop editing the parent window is a modal QDialog, and I believe you might be correct, but I want to be sure about that auto-delete thing.

[http://qt.nokia.com/doc/qtopia2.2/html/qobject.html#details](http://qt.nokia.com/doc/qtopia2.2/html/qobject.html#details)

That says that any children of an object get deleted automatically in it's destructor, but do I need to explicitly need to call the parent (QDialog) destructor?

The dialog is created from scratch so it needs to be allocated off the heap. One thing I'm not sure about however, is if the child widgets in the new object need to be allocated on the heap as well. (They don't work if I don't)

Edit: In the destructor docs of QObject it says:
> Warning: All child objects are deleted. If any of these objects are on the stack or global, your program will sooner or later crash. We do not recommend holding pointers to child objects from outside the parent. If you still do, the QObject::destroyed() signal gives you an opportunity to detect when an object is destroyed.

So I guess the need to be on the heap. Still don't know if I have to delete the parent though.

---

### Post by rex_virtutis on 2010-01-31
As a rule of thumb with QT, if you passed a pointer to the parent to the widget constructor, it will be deleted automatically when the parent is. QT does ref counting so when no references to an object exist it usually gets destroyed.

If you want the dialog to be destroyed when it is closed, I believe there is a flag for that which you can pass in the constructor but that makes it a little tricker to get user input from it.

---

