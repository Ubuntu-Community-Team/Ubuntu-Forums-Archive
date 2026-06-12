---
title: "PyQt Gui Help Needed"
date: 2008-09-14
forum: Programming Talk
---

### Post by geekytechguy on 2008-09-14
Hi people,
I've wrote a source code editor using pyqt, and qt's scintilla, but theres a few things I want to add to it, but can't.
1) I want to embed a terminal in a tab, this way I can execute commands right from the program. I've found programs like pyqonsole but i can't figure out how to embed it into my programs main window.
2) I would also like to see about adding a web browser in it, or one that i can use to preview html code, I'd also like it to be embedded in a tab like the terminal; any idea on how to do this?
Thanks
P.S. is it possible to do a command like: pyuic (filename.ui) > (filename.py) using os.system? i've tryed:```
print os.system('pyuic %s' % (filename) % '%s > %s' % (filename1))
```
but it comes back with: 
Traceback (most recent call last):
  File "PyTe.py", line 528, in pyuic
    print os.system('pyuic %s'%(filename)%'%s > %s'%(filename1))
TypeError: not all arguments converted during string formatting
Again, Thanks

---

### Post by geekytechguy on 2008-09-16
Hi guys, i just figured out how i can have the pyqonsole show up when i press a button, but still can't figure out how to have it appear inside of the tab. also, anyone know how to compile, and upload files to the arduino from with in python, i want to try and use my editor to replace my arduino ide also.
thanks again
josh

---

