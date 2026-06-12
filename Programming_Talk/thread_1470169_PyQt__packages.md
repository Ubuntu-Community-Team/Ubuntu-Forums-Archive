---
title: "PyQt  packages"
date: 2010-05-02
forum: Programming Talk
---

### Post by themusicwave on 2010-05-02
Hey everyone,

This is a very easy question I hope.  What packages do I need to install on 10.04 to write pyqt code?  I want to try out writing a small App using QT, but I can't even import qt yet.  I must be missing a library or something.


Thanks,

Jon

---

### Post by Bachstelze on 2010-05-02
You need [font=monospace]python-qt4[/font].

---

### Post by themusicwave on 2010-05-02
I have that one, but still if I go to the interactive shell and type import qt I get "No module named qt"

Any other ideas?

Thanks.

---

### Post by themusicwave on 2010-05-02
Well I found a different example with different imports and it worked.

This is the example:

[PHP]
import sys
from PyQt4.QtGui import *
app = QApplication(sys.argv)
button = QPushButton("Hello World", None)
button.show()
app.exec_()
[/PHP]

---

