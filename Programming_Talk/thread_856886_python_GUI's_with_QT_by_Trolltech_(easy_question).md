---
title: "python GUI's with QT by Trolltech (easy question)"
date: 2008-07-11
forum: Programming Talk
---

### Post by WinterMadness on 2008-07-11
so I was reading this tutorial on it: [http://www.cs.usfca.edu/~afedosov/qttut/](http://www.cs.usfca.edu/~afedosov/qttut/)

and I get confused when he says:

"Now you end up with form1.py which is a module containing your dialog as a Python class. Since it has no main() function, you can't run it directly. Instead, we need to create a simple wrapper for it, like so:

from qt import *
from form1 import *
import sys
if __name__ == "__main__":
    app = QApplication(sys.argv)
    f = Form1()
    f.show()
    app.setMainWidget(f)
    app.exec_loop()

Without going into too much detail, we import the QT library Python module, as well as our dialog class. Then we create a context for our QT application, instantiate our dialog, show it on the screen, set it as the main widget of the application, and let QT enter its event loop, processing all the signals and calling our slots. Save this in a separate Python file, e.g. mygui.py. Needless to say, this wrapper is fairly generic and can be reused for most of your Python/QT applications. Finally, we are ready to run! Execute your app with:
python mygui.py"

i dont have any idea what hes talking about in the slightest. i have the mygui.py but I dont know how to use that file because at this point i dont know what half the things hes saying even means.

thanks in advance

---

### Post by LaRoza on 2008-07-12
> **WinterMadness said:**
> 
i dont have any idea what hes talking about in the slightest. i have the mygui.py but I dont know how to use that file because at this point i dont know what half the things hes saying even means.

thanks in advance

There is really no way to translate it. I didn't follow the link, so the file in question is unknown to me, but it seems to contain a class or set of function. A file with just class or functions won't do anything.

The "wrapper" is just a way of using it. 

If you don't get that, you have to back up and study some more.

---

### Post by fifth on 2008-07-12
If it helps any, this is what I generally do using PyQt;

```

#!/usr/bin/env python
from PyQt4.QtCore import *
from PyQt4.QtGui import *

class MyDialog(QDialog):
    
    def __init__(self, parent=None):
        super(MyDialog,self).__init__(parent)
        
def main():
    import sys
    
    app = QApplication(sys.argv)    
    myDialog = MyDialog()
    myDialog.show()
    sys.exit(app.exec_())

if __name__ == "__main__":
    main()

```

Means I can test each form by running it directly without having to start the full application.

However, as LaRoza said, if your not getting this, I would go back over some of the tutorial.

[Edit]
Just looked at your code again (and the web link). The tutorial is very dated using Qt3. I would recommend looking at a more up to date tutorial.

---

### Post by fifth on 2008-07-12
This tutorial ([http://zetcode.com/tutorials/pyqt4/](http://zetcode.com/tutorials/pyqt4/)) looks more recent, and gets you started without using the designer - this should give you a better idea of whats going on.

---

