---
title: "Program for counting available characters in a input, like a twitter letter countdown"
date: 2015-06-07
forum: Programming Talk
---

### Post by Justin C on 2015-06-07
Hello,

I need to build a program that will display a countdown that updates as I'm typing.

So every time I enter a character into the input, the countdown goes down. 

Something like this: [http://jsfiddle.net/patelriki13/ba9yp/](http://jsfiddle.net/patelriki13/ba9yp/)

But I would like to have it as a standalone script rather than needing to use a browser.

Anyone have any ideas?
I have not programmed anything in linux besides bash scripting so I don't know what language I would need to get into making a GUI to accomplish this.
I'm open to any other approaches as well! 

Thanks

---

### Post by Vaphell on 2015-06-08
somewhat working bash code

```
#!/bin/bash

len=100
text=
while :
do
    printf '\r%3d: %s   \b\b\b'   $(( len-${#text} )) "$text"
    IFS= read -sn1 input
    if [[ $input = '' ]] # enter
    then
        break
    elif [[ $input = $'\177' ]]  # backspace
    then
        text=${text%?}
    else
        (( ${#text}<len )) || continue
        text=$text$input
    fi
done

printf '\nyour text is %d char(s) long\n%s\n' ${#text} "$text"
```

kind of breaks when text overflows and it needs more hardening against arrows, deletes and other things that can introduce garbage to the text and visuals.

other than that, for a pretty gui you need to use some framework like gtk, qt, tkinter, wxwidgets.

Qt is probably the best gui framework there is and it has python bindings if c++ is too much.
quick and dirty example based on some tutorial found on the net (requires python3-pyqt4)

```
#!/usr/bin/env python3

import sys
from PyQt4 import QtGui, QtCore

class TextWithCounter(QtGui.QWidget):
    
    def __init__(self):
        super(TextWithCounter, self).__init__()
        
        self.initUI()
        
    def initUI(self):      

        self.counter = QtGui.QLabel(self)        
        self.counter.setText('[1] 140')
        self.counter.move(10, 10)
        
        self.textedit = QtGui.QPlainTextEdit(self)
        self.textedit.resize(380, 200)
        self.textedit.move(10, 60)

        self.textedit.textChanged.connect(self.updateCounter)
        
        self.setGeometry(0, 0, 400, 300)
        self.show()
        
    def updateCounter(self):
        p = 140
        strlen = len(self.textedit.toPlainText())
        parts = (strlen-1)//p+1
        remaining = p-((strlen-1)%p+1)
        counter_txt = "[{}] {}".format(parts, remaining)
        self.counter.setText(counter_txt)
        self.counter.adjustSize()        
        
        
def main():
    
    app = QtGui.QApplication(sys.argv)
    text = TextWithCounter()
    sys.exit(app.exec_())


if __name__ == '__main__':
    main()
```

---

### Post by Justin C on 2015-06-08
That first bash script will work great, thanks a lot Vaphell.

---

