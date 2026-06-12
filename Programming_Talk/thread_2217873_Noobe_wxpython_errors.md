---
title: "Noobe wxpython errors"
date: 2014-04-18
forum: Programming Talk
---

### Post by eightbits2010 on 2014-04-18
I am not sure on the proper method to include any code , so I inserted it here. If this is an error , please let me know so
I can do it properly.

I stripped out code not involved with the error, I think it mustbe a simple error and looking for help.
The error is commented at the end of the included listing.
Thanks.
```
#!/usr/bin/env python 
''' experimental code : XXXGasChkGrid.py  ''' 
import wx 
 
class GridSizerFrame(wx.Frame): 
    def __init__(self): 
        wx.Frame.__init__(self, None, -1, "GasChkGrid.py",pos=(200,100))  
         
        #calculated MPG 
        mpgLbl=wx.StaticText(self,-1,"MPG:") 
        mpg=wx.TextCtrl(self,-1,"",size=(80,20)) 
         
        #Buttons 
        button1=wx.Button(self,-1,"Calculate") 
        button2=wx.Button(self,-1,"button2") 
        #button Event(s) 
        self.Bind(wx.EVT_BUTTON, self.OnClick,button2) 
        #create sizer 
        sizer = wx.GridSizer(rows=12, cols=2,hgap=5,vgap=5) 
         # add widgets to sizer 
        sizer.Add(mpgLbl,0,wx.ALIGN_RIGHT) 
        sizer.Add(mpg,0,0) 
        #add button(s) 
        sizer.Add(button1,0,0) 
        sizer.Add(button2,0,0) 
        self.SetSizer(sizer) 
        self.Fit() 
        self.Show()         
        mpg.SetValue("123") #this is just testing, verify can change text.... 
         
    def OnClick(self,event): 
        print 'OK'    # <===this works as expected. 
        mpg.SetValue("Clicked") #<=== gives error 
  
app = wx.PySimpleApp() 
GridSizerFrame().Show() 
app.MainLoop() 
 
 
 
''' Traceback (most recent call last): 
  File "XXXGasChkGrid.py", line 33, in OnClick 
    mpg.SetValue("Clicked") #<=== gives error 
    NameError: global name 'mpg' is not defined 
'''
```

---

### Post by steeldriver on 2014-04-18
Hello and welcome to the forums - thanks for using the CODE tags!

I don't really know wxPython, but could it be as simple as adding something like

```

class GridSizerFrame(wx.Frame):
        def __init__(self):
[COLOR=#0000ff][B]                global mpg
[/B][/COLOR]                wx.Frame.__init__(self, None, -1, "GasChkGrid.py",pos=(200,100))
                .
                .
                .

```

---

### Post by eightbits2010 on 2014-04-18
In this case I don't think that will work. But I will see if that works. mpg is an object that is a TextCtrl or similar to
a Textbox as might be used in VB.
Someone else corrected the use of code tag(s). I now know how to post that, I had to use the advanced setting and then could see the tag ICON.

---

### Post by eightbits2010 on 2014-04-18
Hello steeldriver, gave it a try, no change. I tried almost everything I can think of, it does't mak a lot of sense to me:|
I will keep investigating to see if I can solve this issue.

---

### Post by spjackson on 2014-04-19
> **eightbits2010 said:**
> Hello steeldriver, gave it a try, no change. I tried almost everything I can think of, it does't mak a lot of sense to me:|
I will keep investigating to see if I can solve this issue.
I think you need mpg to be an instance attribute, like this.
```

class foo():
    def __init__(self):
        self.x = 4

    def show(self):
        print self.x

f = foo()
f.show()

```
So
```

        self.mpg=wx.TextCtrl(self,-1,"",size=(80,20))

        self.mpg.SetValue("Clicked")

```

---

### Post by eightbits2010 on 2014-04-19
spjackson: Yes I tried those suggestions already, no change. I didn't post (code) all of the various changes I made to experiment to get this resolved.
 But:
         ```
self.mpg=wx.TextCtrl(self,-1,"",size=(80,20))
self.mpg.SetValue("Clicked")
``` either of these generate errors, either coded individual or in pairs with the object
mpg created at the location where the other widgets are specified. Interesting is the fact that the code
```
mpg.SetValue("123") #this is just testing, verify can change text....
``` works as expected. Note this line is prior to the event function.
But, the button2 event process
```
   def OnClick(self,event): 
        print '\n\n\t\tOK\n\n\n'    #<===this works as expected. 
        mpg.SetValue("Clicked") #<=== gives error
```  gives the error listed at the end of the code I posted.

So, I can't understand how```
 mpg.SetValue("123")
``` works as expected but the event handler gives the error.
In the event function I had a print statement to verify that the button2 click was processed.
 

 I think this has something to do with my lack of full knowledge of Class and OOP as used in
 wxpython.
If someone is using wxpython could test the including code , I am sure this is a my bad that can be pointed out to me.

But, I can not let this prevent me from trying ...:P

---

### Post by steeldriver on 2014-04-19
I tested it both with spjackson's version and my original suggestion (spjackson's is a better solution) and both seemed to work without error
```

#!/usr/bin/env python
''' experimental code : XXXGasChkGrid.py '''
import wx

class GridSizerFrame(wx.Frame):
    def __init__(self):
        wx.Frame.__init__(self, None, -1, "GasChkGrid.py",pos=(200,100))
        
        #calculated MPG
        mpgLbl=wx.StaticText(self,-1,"MPG:")
        **[COLOR=#0000ff]self.mpg[/COLOR]**=wx.TextCtrl(self,-1,"",size=(80,20))
        
        #Buttons
        button1=wx.Button(self,-1,"Calculate")
        button2=wx.Button(self,-1,"button2")
        #button Event(s)
        self.Bind(wx.EVT_BUTTON, self.OnClick,button2)
        #create sizer
        sizer = wx.GridSizer(rows=12, cols=2,hgap=5,vgap=5)
        # add widgets to sizer
        sizer.Add(mpgLbl,0,wx.ALIGN_RIGHT)
        sizer.Add(**[COLOR=#0000ff]self.mpg[/COLOR]**,0,0)
        #add button(s)
        sizer.Add(button1,0,0)
        sizer.Add(button2,0,0)
        self.SetSizer(sizer)
        self.Fit()
        self.Show() #redundit? see line 67
        [COLOR=#0000ff]**self.mpg**[/COLOR].SetValue("123") #this is just testing, verify can change text....
    
    def OnClick(self,event):
        print 'OK' # <===this works as expected.
        [COLOR=#0000ff]**self.mpg**[/COLOR].SetValue("Clicked") #<=== gives error

app = wx.PySimpleApp()
GridSizerFrame().Show()
app.MainLoop()

```
```

#!/usr/bin/env python
''' experimental code : XXXGasChkGrid.py '''
import wx

class GridSizerFrame(wx.Frame):
    def __init__(self):
        [COLOR=#0000ff]**global mpg**[/COLOR]
        wx.Frame.__init__(self, None, -1, "GasChkGrid.py",pos=(200,100))
        
        #calculated MPG
        mpgLbl=wx.StaticText(self,-1,"MPG:")
        mpg=wx.TextCtrl(self,-1,"",size=(80,20))
        
        #Buttons
        button1=wx.Button(self,-1,"Calculate")
        button2=wx.Button(self,-1,"button2")
        #button Event(s)
        self.Bind(wx.EVT_BUTTON, self.OnClick,button2)
        #create sizer
        sizer = wx.GridSizer(rows=12, cols=2,hgap=5,vgap=5)
        # add widgets to sizer
        sizer.Add(mpgLbl,0,wx.ALIGN_RIGHT)
        sizer.Add(mpg,0,0)
        #add button(s)
        sizer.Add(button1,0,0)
        sizer.Add(button2,0,0)
        self.SetSizer(sizer)
        self.Fit()
        self.Show() #redundit? see line 67
        mpg.SetValue("123") #this is just testing, verify can change text....
    
    def OnClick(self,event):
        print 'OK' # <===this works as expected.
        mpg.SetValue("Clicked") #<=== gives error

app = wx.PySimpleApp()
GridSizerFrame().Show()
app.MainLoop()

```

[ATTACH=CONFIG]252232[/ATTACH]

---

### Post by eightbits2010 on 2014-04-19
Thanks to steeldriver and spjackson. I loaded the corrections and tested on my PC and everything worked.
I didn't understand that once you used ```
self.
``` on a object that everyuse of that object must also use ```
self.
```. Once again, thanks > 1 million for that help. I had not much hair to pull out ;).

So, now I will modify the more compleat code of my post and the learning continues......

I also will look into using the book (wxPython IN ACTION) in chapter 11 there is a sample script (realworldtest.py) that
I also had problems in a quick change to use one of the existing buttons in the example and was getting the same error's.
I think I am a little better prepared to face the errors.

---

### Post by llanitedave on 2014-04-21
Your problem was that, as far as Python is concerned, the object named mpg that was defined in __**init__** belongs exclusively to the __**init__** function.  Once you leave that function, mpg has no existence, and trying to use mpg in another function will be treated as a different object -- one that was never defined in the OnClick function.

Assigning as self.mpg changes the scope from the init function to the class.  At that point it can be called anywhere within the class, and can be called from elsewhere as well, via a call to
*classinstance.mpg, *where *classinstance* is a defined instance of the GridSizerFrame class.

BTW, wxPython In Action helped me tremendously when I was trying to learn it.  It's the main reason I chose wx over QT for GUI development.

---

### Post by eightbits2010 on 2014-04-21
llanitedave: Thanks for your response, it helped to clarify what I was having problems understanding.
 I agree that the book as previously mentioned has been the only way for me to get to where I can accomplish  in using Python in a GUI environment. I too have looked at Tkinter, Glade and Qt (pyQT)
 but didn't get too far.
 I know that my problem(s) are centered around namespace, scope and using classes. It does seem difficult to get a great abundance of information on Python and the GUI toolset(s) associated with Phython. And once again, thanks again for your information.

---

