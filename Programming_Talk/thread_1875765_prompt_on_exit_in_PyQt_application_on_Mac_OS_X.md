---
title: "prompt on exit in PyQt application on Mac OS X"
date: 2011-11-05
forum: Programming Talk
---

### Post by flyinflash on 2011-11-05
I know it possible prompt on exit if you click 'X' on window.
[http://stackoverflow.com/questions/1414781/prompt-on-exit-in-pyqt-application](http://stackoverflow.com/questions/1414781/prompt-on-exit-in-pyqt-application)

How to prompt on exit if user press command + q on Mac OS X ? Almost all native Cocoa applications could do that.


My code:

```
import sys

try:
    from PySide import QtCore
    from PySide import QtGui
except ImportError:
    from PyQt4 import QtCore
    from PyQt4 import QtGui


default_settings = {
    "confirm" : True,
    "x_action_is_quit" : 0,
}

settings = default_settings



def confirm_quit(main_win, evt):
    if settings["confirm"]:
        if settings['x_action_is_quit']:
            # process will exit if you do nothing here ...
            print 'quit'
            evt.accept()
        else:
            # ignore close event, hide the main window
            print 'hide'
            evt.ignore()
            main_win.hide()


class Demo(QtGui.QMainWindow):
    def __init__(self):
        super(Demo, self).__init__()

        x, y, w, h = 500, 200, 300, 400
        self.setGeometry(x, y, w, h)

    def closeEvent(self, evt):
        confirm_quit(self, evt)

    def event(self, evt):
        # print evt.type == QtCore.QEvent.Close, evt == QtCore.QEvent.Close
        pass


if __name__ == "__main__":
    app = QtGui.QApplication(sys.argv)

    main = Demo()

    main.show()
    main.raise_()

    sys.exit(app.exec_())

```

---

