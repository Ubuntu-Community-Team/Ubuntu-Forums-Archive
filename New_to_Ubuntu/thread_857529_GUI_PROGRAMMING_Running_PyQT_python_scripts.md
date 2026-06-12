---
title: "GUI PROGRAMMING: Running PyQT python scripts"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-07-12
I have written a python script with the PyQT module.

When I go to run it, I get no errors at all. It just doesn't load.

Does anyone have any idea what is wrong?

Maybe someone else knows a different way to run it.

I tried - python ./file.py and also tried running from IDLE

Thanks

---

### Post by braddcadd on 2008-07-14
Can you post the code that connects your python script to the GUI?

---

### Post by pluckypigeon on 2008-07-14
> **braddcadd said:**
> Can you post the code that connects your python script to the GUI?

How do you mean connects? Do I have to connect it? I used the PyQT Module

---

### Post by braddcadd on 2008-07-14
You should have some code in a *.py file like this:
```

from qt import *
from form1 import *
import sys
if __name__ == "__main__":
    app = QApplication(sys.argv)
    f = Form1()
    f.show()
    app.setMainWidget(f)
    app.exec_loop()

```

Here is a tutorial if it helps:
[http://www.cs.usfca.edu/~afedosov/qttut/](http://www.cs.usfca.edu/~afedosov/qttut/)

At any rate, you need to post some code so people can help debug the problem :)

---

### Post by pluckypigeon on 2008-07-15
> **braddcadd said:**
> You should have some code in a *.py file like this:
```

from qt import *
from form1 import *
import sys
if __name__ == "__main__":
    app = QApplication(sys.argv)
    f = Form1()
    f.show()
    app.setMainWidget(f)
    app.exec_loop()

```

Here is a tutorial if it helps:
[http://www.cs.usfca.edu/~afedosov/qttut/](http://www.cs.usfca.edu/~afedosov/qttut/)

At any rate, you need to post some code so people can help debug the problem :)

i do have that.

how do you run it?

---

