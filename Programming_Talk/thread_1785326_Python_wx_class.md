---
title: "Python wx class"
date: 2011-06-18
forum: Programming Talk
---

### Post by Mosabama on 2011-06-18
Hello, 

I want to define a class in python that uses the wx.timer, I dont want to use any GUI wx classes.

I have the following class:

```

class Data():

    def __init__(self):
                                                   
        self.timer=wx.Timer(self)
        self.Bind(wx.EVT_TIMER, self.getdata,self.timer)
        self.timer.Start(1000)

    def getdata(self,event): 
        """This function will get data from mysql""" 

```

but python returns an error:
```


File "dev.py", line 137, in __init__
    self.timer=wx.Timer(self)
  File "/usr/lib/python2.7/dist-packages/wx-2.8-gtk2-unicode/wx/_misc.py", line 1295, in __init__
    _misc_.Timer_swiginit(self,_misc_.new_Timer(*args, **kwargs))
TypeError: in method 'new_Timer', expected argument 1 of type 'wxEvtHandler *'
```

Any help is appreciated,

---

### Post by cgroza on 2011-06-18
You must inherit from wxEvtHandler or another widget that inherits from it..

---

### Post by Mosabama on 2011-06-18
Thanks,

the following code worked!, but my question is : is this the god way to do it:

```

class Data(wx.Timer):

    def __init__(self):

        wx.Timer.__init__(self)                     
        self.timer=wx.Timer(self)
        self.Bind(wx.EVT_TIMER, self.getdata,self.timer)
        self.timer.Start(1000)

    def getdata(self,event): 
        """This function will get data from mysql"""

```

---

### Post by cgroza on 2011-06-18
> **Mosabama said:**
> Thanks,

the following code worked!, but my question is : is this the god way to do it:

```

class Data(wx.Timer):

    def __init__(self):

        wx.Timer.__init__(self)                     
        self.timer=wx.Timer(self)
        self.Bind(wx.EVT_TIMER, self.getdata,self.timer)
        self.timer.Start(1000)

    def getdata(self,event): 
        """This function will get data from mysql"""

```
The self.timer variable is not needed. You can use self directly.
NOTE: Not tested!

```

class Data(wx.Timer):

    def __init__(self):

        wx.Timer.__init__(self)                     
        self.Bind(wx.EVT_TIMER, self.getdata)
        self.Start(1000)

    def getdata(self,event): 
        """This function will get data from mysql"""
```

---

### Post by Mosabama on 2011-06-18
dude, I know you didnt say much.. but I learned so much from you :)

it works, Thanks alot

---

