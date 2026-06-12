---
title: "itertools and urllib.request issue upon implementing PyQt."
date: 2010-04-12
forum: Programming Talk
---

### Post by Stev0 on 2010-04-12
Couple weeks ago I made a very simple web crawler to get  a feel for urllib that was designed to simply grab robots.txt from a range of IP addresses. In it's initial CLI based form, it was working perfectly. I've started learning my way around GUI programming, with PyQt, and figured the easiest way to get started was to add a GUI to my web crawler. I've made some sort of error, but can't figure out where. I've determined what the problem is, but not sure how to fix it. 

What's happening is that the itertools.product method is executing like normal, I even inserted a print statement in the middle of the code just to see what was happening, and the method is creating IP address tuples in the same manner that it did as the CLI version. The problem however, is that the portion of the code that actually makes the HTTP connection is not executing until the last IP address in the range has been generated. I don't know what the problem is, especially since the only code that has changed from the original form, is the portions which indicate the input coming from the GUI elements as opposed to the command line. Anyone who is more familiar with PyQt have any ideas? BTW this is with Python 3.1.1, and PyQt 4. Code is as follows:
```

import urllib
import urllib.request
import sys
import itertools
import time

from PyQt4 import QtCore, QtGui
from robo_ui import Ui_robominer


class Start(QtGui.QMainWindow):
    def __init__(self, parent=None):
        QtGui.QWidget.__init__(self, parent)
        self.ui = Ui_robominer()
        self.ui.setupUi(self)

        QtCore.QObject.connect(self.ui.mine_button, QtCore.SIGNAL("clicked()"), self.go_mining)
        QtCore.QObject.connect(self.ui.quit_button, QtCore.SIGNAL("clicked()"), self.quit_mining)
   
    def go_mining(self):
        ip_parts =[]
        for part in self.ui.robo_target.text().split("."):
            if "-" in part:
                min, max = part.split("-")
                ip_parts.append(range(int(min), int(max)+1))
            else:
                ip_parts.append([int(part)])
        
        ip_addresses = itertools.product(*ip_parts)
        for ip_addy in ip_addresses:
            self.ui.textBrowser.append("Trying to fetch from %d.%d.%d.%d..." %ip_addy)
            try:        
                roboFile = urllib.request.urlopen("http://%d.%d.%d.%d/robots.txt" %ip_addy, timeout=5)
                fetched = roboFile.read()
                decoded = fetched.decode("utf8")
                self.ui.textBrowser.append(fetched)
               

            except Exception as err:
                e = str(err)
                self.ui.textBrowser.append(e)

    def quit_mining(self):
        sys.exit()

           
           



if __name__ == "__main__":
    app = QtGui.QApplication(sys.argv)
    myapp = Start()
    myapp.show()
    sys.exit(app.exec_())

```

---

