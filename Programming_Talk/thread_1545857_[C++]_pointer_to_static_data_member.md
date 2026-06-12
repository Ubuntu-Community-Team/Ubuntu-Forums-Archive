---
title: "[C++] pointer to static data member?"
date: 2010-08-04
forum: Programming Talk
---

### Post by agnes on 2010-08-04
Hi, I have a class "Block" that has a static data member of type "MyGrid", named "grid".
I need to pass the address of this static member to a function. 
But if I do, afterwards I get memory errors. 

My code:
```
#include "block.h"
// other stuff
Block::grid.init(gridRandInterval, gridRandInterval, hokjesInterval, hokjes);
myScene.addItem(&(Block::grid));
```

This way, the program (and grid) works fine, but after closing it I get this:
```
*** glibc detected *** ./gvt3: free(): invalid pointer: 0x08052080 ***
======= Backtrace: =========
/lib/i686/cmov/libc.so.6(+0x6b321)[0xb68b9321]
/lib/i686/cmov/libc.so.6(+0x6cb78)[0xb68bab78]
/lib/i686/cmov/libc.so.6(cfree+0x6d)[0xb68bdc5d]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb6a94701]
/usr/lib/libQtGui.so.4(_ZN14QGraphicsScene5clearEv+0x5b)[0xb755b7ab]
 ... etc etc 
```
 
This, however, does not give that error:
```
MyGrid gridje;
gridje.init(gridRandInterval, gridRandInterval, hokjesInterval, hokjes); 
myScene.addItem(&gridje);
```

Why could that be?

---

### Post by dwhitney67 on 2010-08-04
Are you by chance attempting to free (delete) the address of the static grid variable at a later time?  This is my first guess as to what is causing your app's error.


P.S.  It would be helpful if you posted the code for the myScene class, and in particular what the addItem() method is doing, and whether you implement a destructor for the myScene class.

---

### Post by agnes on 2010-08-04
No I don't free/delete anything. 
By the way I also do not use dynamic arrays or something.

The program uses Qt 4.6: [addItem]("http://doc.trolltech.com/4.6/qgraphicsscene.html#addItem") is a method from the class QGraphicsScene of the Qt library; myScene is an instance of QGraphicsScene.

But I think it's Qt related if this pointer-to-static-thing should normally be possible. 

I just tried to add a very simple other variable of a standard type (QGraphicsRectItem, a subclass of QGraphicsItem) to the scene with addItem. In the same manner as above (so, as an static member of class "Block"). 
```
myScene.addItem(&(Block::myRectangle));
```
again it shows, but I get now a "Segmentation fault" 
So perhaps it is a Qt thing with the addItem method of QGraphicsScene.
Maybe the problem is this quote
> QGraphicsScene will send ItemSceneChange notifications to item while it is added to the scene. 
Perhaps it cannot send to static members... wouldn't know how this notifications thing would work though.

---

### Post by dwhitney67 on 2010-08-04
IIRC, Qt does use smart-pointers, and it will automatically free (delete) objects when they are no longer used.  Basically it relieves the programmer of this burden.

If you require a static object (think carefully here!), I suggest that you declare it as a pointer.  For example:
```

class Block
{
public:
   ...

   static MyGrid* grid;
};

...

MyGrid* Block::grid = new MyGrid(...);

...

```

---

### Post by agnes on 2010-08-04
Thanks! It works now :KS

I did not know about smart pointers.
A static object is the easiest here because I need a lot of instances of "Block" and all the instance's (relative) positions must be maintained, in such a way Block itself can access it.

---

### Post by interval1066 on 2010-08-04
I don't use Qt for anything myself, at least haven't needed to yet, but the trolltechies probably don't use std::auto_ptr because its written to one of the more crazily-written specifications of the stl. Its being deprecated in the upcoming c++0x specification in favor of std::unique_ptr. Or maybe they simply have a problem with the philosophy behind smart pointers, whatever.

---

