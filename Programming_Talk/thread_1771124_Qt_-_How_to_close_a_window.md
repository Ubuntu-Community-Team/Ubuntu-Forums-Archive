---
title: "Qt - How to close a window?"
date: 2011-05-30
forum: Programming Talk
---

### Post by ankeetg on 2011-05-30
Hey!

I have a problem that I can't figure out..any help would be great

I'm a beginner at Qt and I'm trying to figure this out but I'm getting an error

My GUI should function such that on a specific button press  a new window pops up and the old one shuts...
I got the new window to pop up and stuff and everything works fine..but i can't figure out how to close the old one... any pointers??

```

#include <QtGui> 
#include "guistart.h"
//#include "addcluster.h"

// if we include <QtGui> there is no need to include every class used: <QString>, <QFileDialog>,...
 
guiStart::guiStart(QMainWindow *parent)
{
    setupUi(this); // this sets up GUI

    // signals/slots mechanism in action
    connect( nextButton, SIGNAL( clicked() ), this, SLOT( addClusterWindow() ) );  
}
 
 
void guiStart::addClusterWindow()
{
    addCluster *window = new addCluster();
    window->show();
    this.close();
}
```

All my windows are QMainWindow .

The above code gives me this error
```
guistart.cpp: In member function ‘void guiStart::addClusterWindow()’:
guistart.cpp:20:7: error: request for member ‘close’ in ‘this’, which is of non-class type ‘guiStart* const’
```

I know there's a problem with the this.close()

Any help would be great guys!! Thanks!

---

### Post by hakermania on 2011-05-30
i don't know a lot about Qt, but maybe
this->close(); ?

---

### Post by ankeetg on 2011-05-30
Thank you!!
I just slapped myself silly!!!

Doh!

You're a saviour

---

