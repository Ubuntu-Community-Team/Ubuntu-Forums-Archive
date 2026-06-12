---
title: "Python: Twisted"
date: 2010-11-30
forum: Programming Talk
---

### Post by Sailor5 on 2010-11-30
Ahoy Sailors!

So I'm merging my Twisted driven application with a PyQt interface. I'm  currently trying to send a variable when a button is clicked. But I  can't figure it out. I'd need to be able to it some what like this.
```
def Button_Clicked(self):
        out ="s:"+self.lineEdit.text()
        out = str(out)
        self.sendLine(out)
```You could run this deferred under  connectionMade passing it's self variable as an argument. But I don't  want to send text just when someone has connected. I want to send it  when a button is pressed.

Anyone know how?

Thanks Bye!

---

### Post by smartbei on 2010-12-02
It looks like you want:
```

class MyApp(wx.Frame):

    def Button_Clicked(self, event):
        out ="s:"+self.lineEdit.text()
        out = str(out)
        self.sendLine(out)

    ...

    def __init__(self, ...):
        ...
        button = wx.Button(...)
        self.Bind(wx.EVT_BUTTON, self.Button_Clicked, button) 
        ...

```

The important line is the self.Bind - this tells wx to send button click events to the callback function self.Button_Clicked.

---

### Post by Sailor5 on 2010-12-02
> **smartbei said:**
> It looks like you want:
```

class MyApp(wx.Frame):

    def Button_Clicked(self, event):
        out ="s:"+self.lineEdit.text()
        out = str(out)
        self.sendLine(out)

    ...

    def __init__(self, ...):
        ...
        button = wx.Button(...)
        self.Bind(wx.EVT_BUTTON, self.Button_Clicked, button) 
        ...

```The important line is the self.Bind - this tells wx to send button click events to the callback function self.Button_Clicked.

How do you do it using PyQt? I'm having a little trouble understanding that.

---

### Post by MadCow108 on 2010-12-02
read a bit about signals and slots. Most gui's use this event processing schema.
A good book for "pyqt is rapid gui programming with python" and qt by marks summerfield.


traditional way:
> 
self.connect(self.button, SIGNAL("Clicked()"), self.Button_Clicked)

the signals and slot signatures are the same as c++ qt.

newer pyqt has a also an alternative more pythonic way:
[http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#new-style-signal-and-slot-support](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#new-style-signal-and-slot-support)

---

### Post by Sailor5 on 2010-12-02
> **MadCow108 said:**
> read a bit about signals and slots. Most gui's use this event processing schema.
A good book for "pyqt is rapid gui programming with python" and qt by marks summerfield.


traditional way:

the signals and slot signatures are the same as c++ qt.

newer pyqt has a also an alternative more pythonic way:
[http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#new-style-signal-and-slot-support](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/pyqt4ref.html#new-style-signal-and-slot-support)

So your saying I should use.

```
[FONT=monospace]
QtCore.QObject.connect(self.pushButton_7, QtCore.SIGNAL("clicked()"),
           Twisted().Button_Clicked('abc'))


class Twisted(LineReceiver):

[/FONT]   def Button_Clicked(self,out):
        self.sendLine(out)
``````
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 484, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/home/zack/Desktop/py.py", line 278, in Window
    ui.setupUi(Form)
  File "/home/zack/Desktop/py.py", line 181, in setupUi
    Chimera().Button_Clicked('abc'))
  File "/home/zack/Desktop/py.py", line 290, in Button_Clicked
    self.sendLine(out)
  File "/usr/lib/python2.6/dist-packages/twisted/protocols/basic.py", line 296, in sendLine
    return self.transport.write(line + self.delimiter)
AttributeError: 'NoneType' object has no attribute 'write'


```Could you post an example of using the sendLine function when a PyQt button is pressed? I'm obviously missing something here.

---

### Post by MadCow108 on 2010-12-02
this particular case could be done by function currying.
the functools.partial function binds arguments of functions so you can use one function (or slot) with several simple signals like Clicked().

```

self.connect(self.pushButton_7, QtCore.SIGNAL("clicked()"),
             functools.partial(Twisted().Button_Clicked, out='abc'))


class Twisted(LineReceiver):
     def Button_Clicked(self,out):
          self.sendLine(out)

```

or new style:
```

self.pushButton_7.clicked.connect(functools.partial(Twisted().Button_Clicked, out='abc'))

```

sure you want to create a Twisted instance on signal connect?

---

### Post by Sailor5 on 2010-12-02
```
abc
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 484, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/home/zack/Desktop/py.py", line 277, in Window
    ui.setupUi(Form)
  File "/home/zack/Desktop/py.py", line 181, in setupUi
    Twisted().Button_Clicked('abc'))
  File "/home/zack/Desktop/py.py", line 289, in Button_Clicked
    self.sendLine(out)
  File "/usr/lib/python2.6/dist-packages/twisted/protocols/basic.py", line 296, in sendLine
    return self.transport.write(line + self.delimiter)
AttributeError: 'NoneType' object has no attribute 'write'

```Dang still doesn't want to work.

---

### Post by MadCow108 on 2010-12-02
does it work when you call the Button_Clicked function without the signal?

self.transport seems to be None, which might be related to the fact that you create a new Twisted object in the connect call.

---

### Post by Sailor5 on 2010-12-02
> **MadCow108 said:**
> does it work when you call the Button_Clicked function without the signal?

self.transport seems to be None, which might be related to the fact that you create a new Twisted object in the connect call.

This is going to be a little hard to explain so I'll use some scenarios to help demonstrate.

```
class Twisted(LineReceiver):
   def connectionMade(self):
        self.sendLine('Ahoy!')
```We've got the self argument from the deferred and thus using self.sendLine() _will_ work.

```
class NastyNoWorkClass():
   Twisted().ButtonClicked('abc')

 class Twisted(LineReceiver):
     def ButtonClicked(self,out):
       self.sendLine(out)
```This would _not_ work as [bear with me here] the self argument was not given by Twisted. How some how that gets us the AttributeError: 'NoneType' object has no attribute 'write' error.

Hopefully someone who's good with Twisted will come along and explain this a tad better,

---

### Post by MadCow108 on 2010-12-02
I don't know Twisted but I guess you have to have a connection to send a message.
This is probably what connectionMade is there
and this you skip by your direct call of sendLine after construction of the object.

So you either have to do some redesigning, like deferring the sendLine until the connection is made, pre-creating one and use that on the click, or whatever else Twisted has to over (e.g. endpoint)

---

### Post by Sailor5 on 2010-12-03
I've tried waiting until upon receiving a connection and then use sendLine(). However we still get the Nonetype has no attribute 'write' error. Can anyone shed some light onto this? It's been bogging me down for awhile now.

---

### Post by MadCow108 on 2010-12-03
have you tried instead of creating a new twisted object on the signal binding to use an already existing one which "works" (meaning you executed sendLine successfully by a direct call in the active program)?

---

