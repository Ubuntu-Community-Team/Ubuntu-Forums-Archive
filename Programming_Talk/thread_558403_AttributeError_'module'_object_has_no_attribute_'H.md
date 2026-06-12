---
title: "AttributeError: 'module' object has no attribute 'Hbox'"
date: 2007-09-23
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-09-23
I'm still muddling my way through the PyGTK tutorial in my spare moments. I've come across an interesting error and search engines have been of no help narrowing it down.

Here's the code, typed verbatim from the tutorial sans comments:

```

#!/usr/bin/env python

import pygtk
import gtk

class HelloWorld2:
	def callback(self, widget, data):
		print "Hello again - %s was pressed." % data

	def delete_event(self, widget, event, data=None):
		gtk.main.quit()
		return False

	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("Hello Buttons!")
		self.window.connect("delete_event", self.delete_event)
		self.window.set_border_width(10)
		self.box1 = gtk.Hbox(False, 0)
		self.window.add(self.box1)
		self.button1 = gtk.Button("Button 1")
		self.button2 = gtk.Button("Button 2")
		self.button1.connect("clicked", self.callback, "button number 1")
		self.button2.connect("clicked", self.callback, "button number 2")
		self.box1.pack_start(self.button1, True, True, 0)
		self.box1.pack_start(self.button2, True, True, 0)
		self.button1.show()
		self.button2.show()
		self.box1.show()
		self.window.show()

	def main():
		gtk.main()

if __name__ == "__main__":
	hello = HelloWorld2()
	main()

```

And here's the resulting error message when I run it in the terminal after making it executable:

```

Traceback (most recent call last):
  File "./Upgraded Hello World.py", line 37, in <module>
    hello = HelloWorld2()
  File "./Upgraded Hello World.py", line 20, in __init__
    self.box1 = gtk.Hbox(False, 0)
AttributeError: 'module' object has no attribute 'Hbox'

```

I'm importing gtk; I cannot imagine why the python interpreter would think there was no such thing as an HBox. I've looked this error up everywhere I know to, but it's apparently not a common one.

Any leads on how to track this one down would be duly appreciated. You guys are spoiling me with all your recent help. :)

---

### Post by Quikee on 2007-09-24
As you said it - I also cannot imagine why the python interpreter would think there was no such thing as an HBox. But... in the example you typed:

```
self.box1 = gtk.H**b**ox(False, 0)
```

should be (just to be clear):
```
self.box1 = gtk.H**B**ox(False, 0)
```

---

### Post by Carl Hamlin on 2007-09-24
Thanks - I'll have to try that when I get a minute. If that fixes the problem I'll have to sit down and have a good cry, I think. :)

---

### Post by maarten12 on 2009-02-22
I've been busy with PyGTK too, and I seem to have some sort of related problem.
If I take the following code posted by Carl Hamlin, with the Hbox/HBox fix ofcourse, I get a related message.
My current code is as following:
```

#!/usr/bin/env python

import pygtk
import gtk

class HelloWorld2:
	def callback(self, widget, data):
		print "Hello again - %s was pressed." % data

	def delete_event(self, widget, event, data=None):
		gtk.main.quit()
		return False

	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("Hello Buttons!")
		self.window.connect("delete_event", self.delete_event)
		self.window.set_border_width(10)
		self.box1 = gtk.HBox(False, 0)
		self.window.add(self.box1)
		self.button1 = gtk.Button("Button 1")
		self.button2 = gtk.Button("Button 2")
		self.button1.connect("clicked", self.callback, "button number 1")
		self.button2.connect("clicked", self.callback, "button number 2")
		self.box1.pack_start(self.button1, True, True, 0)
		self.box1.pack_start(self.button2, True, True, 0)
		self.button1.show()
		self.button2.show()
		self.box1.show()
		self.window.show()

	def main():
		gtk.main()

if __name__ == "__main__":
	hello = HelloWorld2()
	main()

```

So, I make it executable and run it in the Terminal and it produces this:
```

Traceback (most recent call last):
  File "./gtk.py", line 36, in <module>
    hello = HelloWorld2()
  File "./gtk.py", line 15, in __init__
    self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
AttributeError: 'module' object has no attribute 'Window'

```

This is quite strange as I just read in the [documentation]("http://www.pygtk.org/docs/pygtk/gtk-constants.html#gtk-window-type-constants") that it should be excactly the same!

I've already tried reinstalling python-gtk2 and python-gnome2-extras and such things, but it didn't help.
What should I do? Am I missing a very obvious typo or is my PyGTK install screwed up or is it something else?

---

### Post by maarten12 on 2009-02-24
Does anyone have an idea of what it could be?

---

### Post by the_unforgiven on 2009-02-24
It seems to be working for me - with minor modifications..

1. The quit part is gtk.main_quit() and not gtk.main.quit().
2. The main() function is under the class level - so, you either pull it out of class by de-indenting it OR make it a class method by accepting the self ref. in it and calling it as 'hello.main()' instead of just 'main()'

---

### Post by imdano on 2009-02-24
> **maarten12 said:**
> So, I make it executable and run it in the Terminal and it produces this:
```

Traceback (most recent call last):
  File "./gtk.py", line 36, in <module>
    hello = HelloWorld2()
  File "./gtk.py", line 15, in __init__
    self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
AttributeError: 'module' object has no attribute 'Window'

```Name your file something other than gtk.py.  Trying to import a module with the same name as your executable causes errors like the one you see there.

---

### Post by spupy on 2009-02-24
```
gtk.HBox()
```

```
gtk.main_quit()
```

And the last line should be
```
**gtk**.main()
```
or
```
**hello**.main()
```
The "main" method of the HelloWorld2 class should be:
```
	def main(self):
		gtk.main()
```
(note the **"self"**. In classes, self is always the first argument)

---

### Post by eng.sfft on 2009-12-13
def start (self):
        global db        
        db=MySQLdb.Connect(host="localhost",user="root",passwd="12345",db="example")
        global cursor        
        cursor=db.cursor
        number=int(self.ui.lineEdit_5.text())

         password=int(self.ui.lineEdit_6.text())

            sql="select no from admin where number='no' and pasword='pasword'"
            result=self.cursor.execute(sql)    
        if result==1 and self.ui.teacher.isChecked ():
            QtGui.QApplication.exit (1)
            
        elif result==1 and self.ui.ylisans.isChecked ():
            QtGui.QApplication.exit (2)
            
        elif result==1 and self.ui.lisans.isChecked ():
            QtGui.QApplication.exit (3)


the code is given 

Traceback (most recent call last):
  File "/home/eng/Desktop/i.py", line 25, in start
    number=int(self.ui.lineEdit_5.text())
ValueError: invalid literal for int() with base 10: ''
Traceback (most recent call last):
  File "/home/eng/Desktop/i.py", line 30, in basla
    number=self.Cursor.execute(sql)    
AttributeError: 'singnal' object has no attribute 'Cursor'

 help me please

---

### Post by Can+~ on 2009-12-13
> **eng.sfft said:**
> def start (self):
        global db        
        db=MySQLdb.Connect(host="localhost",user="root",passwd="12345",db="example")
        global cursor        
        cursor=db.cursor
        number=int(self.ui.lineEdit_5.text())

         password=int(self.ui.lineEdit_6.text())

            sql="select no from admin where number='no' and pasword='pasword'"
            result=self.cursor.execute(sql)    
        if result==1 and self.ui.teacher.isChecked ():
            QtGui.QApplication.exit (1)
            
        elif result==1 and self.ui.ylisans.isChecked ():
            QtGui.QApplication.exit (2)
            
        elif result==1 and self.ui.lisans.isChecked ():
            QtGui.QApplication.exit (3)


the code is given 

Traceback (most recent call last):
  File "/home/eng/Desktop/i.py", line 25, in start
    number=int(self.ui.lineEdit_5.text())
ValueError: invalid literal for int() with base 10: ''
Traceback (most recent call last):
  File "/home/eng/Desktop/i.py", line 30, in basla
    number=self.Cursor.execute(sql)    
AttributeError: 'singnal' object has no attribute 'Cursor'

 help me please

You should be more specific, and this thread is about PyGTK, not PyQT and MySQL.

Start another thread.

---

### Post by Jefferythewind on 2010-01-29
Hi Everyone, I am having a similar problem.  I have been using python to do simple prgrams, and I am trying to get into the GUI, pyGTK.  I have been going to through the pyGTK tutorial, and I tried executing the script found [here]("http://www.pygtk.org/pygtktutorial/examples/helloworld.py"), followed by this error:

Traceback (most recent call last):
  File "<pyshell#10>", line 1, in <module>
    execfile('helloworld.py')
  File "helloworld.py", line 79, in <module>
    hello = HelloWorld()
  File "helloworld.py", line 32, in __init__
    self.window = gtk.GtkWindow(gtk.WINDOW_TOPLEVEL)
AttributeError: 'module' object has no attribute 'GtkWindow'

It seems to be the same type of problem listed above, does anyone know what the problem may be?

---

### Post by Tony Flury on 2010-01-30
make sure your file is not call gtk.py or gtk2.py - or does not have any clashes with any of the other gtk files.

If your file is call gtk.py - when you do 

```

import gtk

```

your code will import itself - rather than the expected GTK library. The search path for libraries includes the current directory first, which is why it finds your gtk.py first.

---

### Post by keyboardslave on 2011-03-26
cmon carl why no reply in regards to you crying?

I know you would of sat down and had a big cry for the Hbox problem is anoying, i to have done Hbox and not HBox 

:)

---

