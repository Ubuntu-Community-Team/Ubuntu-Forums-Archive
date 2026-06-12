---
title: "wxPython, Tab Program, Taking Values from needed tab."
date: 2010-12-01
forum: Programming Talk
---

### Post by cgroza on 2010-12-01
Hello everyone!
I am thinking of making my own text editor in wxPython with multiple tab support.
Right now I am just scketching code for quick reference when I will start building it.
So, lets say I open multiple tabs, start writing text in all of them and then I go to one tab and click save. 

So, I have a function that will create a new tab with all its contents and a save function that will save the contents of a certain widget, How do I get the value from the right tab?
So far I have this mockup:

```
import wx 
import wx.lib.inspection 
class vikk(wx.Frame):     
     
    def printer(self,event): 
        print(self.bro.GetValue()) 
 
    def new_panel(self, nm): 
        pnl = wx.Panel(self) 
        pnl.identifierTag = nm 
        self.nb.AddPage(pnl, nm) 
        self.bro = wx.TextCtrl(pnl,id,pos=(200,100),size=(200,20)) 
        butty =wx.Button(pnl,id,label="TEXT!",pos=(100,40),size = (-1,-1)) 
        self.Bind(wx.EVT_BUTTON,self.printer,butty) 
         
     
    def __init__(self,parent,id): 
        wx.Frame.__init__(self,parent,id,'Frame', size=(400,500)) 
 
        self.nb = wx.aui.AuiNotebook(self) 
         
         
        self.new_panel('Page 1') 
        self.new_panel('Page 2') 
  
if __name__=='__main__': 
    app=wx.PySimpleApp() 
    frame=vikk(parent=None,id=-1) 
    frame.Show() 
    app.MainLoop()
```But this one takes the value from the latest created tab due to obvious reasons.
Thanks.

---

### Post by smartbei on 2010-12-02
Here is one solution to the problem (I am sure there are many):
```

import wx 
import wx.lib.inspection 
class vikk(wx.Frame):     
     
    def printer(self,event,text_id):
        print wx.FindWindowById(text_id).GetValue()
 
    def new_panel(self, nm): 
        pnl = wx.Panel(self) 
        pnl.identifierTag = nm 
        self.nb.AddPage(pnl, nm)
        
        # Put text_id into a local variable.
        # We do this so that the lambda takes the current value,
        # and not the constantly-incrementing one.
        text_id = self.text_id
        
        self.bro = wx.TextCtrl(pnl, self.text_id, pos=(200,100), size=(200,20)) 
        butty = wx.Button(pnl, label="TEXT!", pos=(100,40)) 
        self.Bind(wx.EVT_BUTTON, lambda event: self.printer(event, text_id), butty) 
     
        # Increment the ID.
        self.text_id += 1
     
    def __init__(self,parent,id): 
        wx.Frame.__init__(self,parent,id,'Frame', size=(400,500)) 
 
        self.nb = wx.aui.AuiNotebook(self) 
        self.text_id = 0
         
        self.new_panel('Page 1') 
        self.new_panel('Page 2') 
  
if __name__=='__main__': 
    app=wx.PySimpleApp() 
    frame=vikk(parent=None,id=-1) 
    frame.Show() 
    app.MainLoop()

```

We use a lambda to pass the ID of the TextCtrl, and then get the text using FindWindowById.

---

### Post by cgroza on 2010-12-02
Thank you! You solved my main problem and now I can start coding!

---

### Post by cgroza on 2010-12-10
Ok, now I need to implement the same thing but with a wx.Menubar. I tried the above but it does not work for some reason. If someone knows how can I adapt the above code for a wx.Menubar I would be thankfull if he posts here.

---

### Post by cgroza on 2010-12-10
The code that creates a new tab looks like this right now:

```
def new_panel(self, nm):  
        pnl = wx.Panel(self)  
        menubar = wx.MenuBar() 
        file = wx.Menu() 
        test = file.Append(-1, 'Quit', 'Quit application') 
        menubar.Append(file, '&File') 
        self.SetMenuBar(menubar) 
        self.Bind(wx.EVT_MENU, lambda event: self.printer(event, text_id), test) 
        pnl.identifierTag = nm  
        self.nb.AddPage(pnl, nm) 
         
        # Put text_id into a local variable. 
        # We do this so that the lambda takes the current value, 
        # and not the constantly-incrementing one. 
        text_id = self.text_id 
         
        self.bro = wx.TextCtrl(pnl, self.text_id, pos=(200,100), size=(200,20))  
        butty = wx.Button(pnl, label="TEXT!", pos=(100,40))  
        self.Bind(wx.EVT_BUTTON, lambda event: self.printer(event, text_id), butty)  
      
        # Increment the ID. 
        self.text_id += 1
```

If the function is launched from the menubar, it prints only the text from the last created tab, but not from the current one.

---

### Post by cgroza on 2010-12-11
Bump?

---

