---
title: "using tabs and a question on string formatting."
date: 2014-04-21
forum: Programming Talk
---

### Post by eightbits2010 on 2014-04-21
Hello, I am posting a duel question and this may not be a proper post on posting two seperate questions.
If so, please inform me and I will modify the post as required.:confused:

Working with wxpython I have a couple of issues that I don't quite understand,
(1) The tab between TextCtrl works on  one script but not on a different on. On the one that
      doesn't work is based on using a GridSizer only. The script that tabs DO work is based on
      placing the widgets by size and position. So, I am thinking there is something in the GridSizer
                    to place widgets on the Panel is an issue(?).

                    (2) Is there a way to use python string formatting to generate a variable that the string can be
     placed in a TextCtrl (?).

Thanks for any advice or explanation. :-)

---

### Post by eightbits2010 on 2014-04-22
Well, I have searched every where on using tabs in wxpython. So far I have found nothing that doesn't look overly complicated and the examples seem to indicate multiple functions to accomplish  what I thought should be a straight forward method(?).  The book “wxpython in action” doesn't seem to address using tabs at all. At least I haven't found it yet.
 

 One thing that has me confused is a example script from that book, the tabs work as expected. Using a script that I coded, the tab key doesn't do anything at all. The only difference between the scripts is that the one that works (example code) is based on TextCtrl located is using manual positioning and the script I generated (no tab key function) is using FlexGrid sizer for widget placement. I can't figure that out and from what I find searching on line is that using the tab key in wxpython just doesn't seem to work?

 

 I have looked at using pyQt , but to change now would be like taking 10 steps backward.:sad:

---

### Post by eightbits2010 on 2014-04-23
It was suggested that I post code pertinent to my question, so I have posted two scripts.

 (1) firststart.py – this snippet is     a modified code version that is in the “wxpython in action”     book. 

             In this snippet  the tabs work OK and as expected.  The book doesn't cover tabs at all. At least
             I don't find it.
       
    (2) XXXGasChk.py – In this code the         tab key does NOT work. I can't see what the issue is at all.

               As a side note, I added a panel to the code and it did not change anything. Adding the panel
               did display an abdominally in that the first StaticText label causes a display problem on line 12
                 the text does not display properly. The first character isn't displayed.  

 So, I am at loss here on the use of the tab key using this GUI tool set. Can not understand why one
 script it works and the other it does not work.
 
 I am sure this is something I am not doing properly/correctly, just can't see it. By posting the two codes, I hope that can bring up an answer.

Code follows:
**firststart.py**
```
#!/usr/bin/env python
''' from Chapter 2, pg. 47, highly modified ....     '''
import wx

class InsertFrame(wx.Frame):
    def __init__(self,parent,id):
        wx.Frame.__init__(self,parent,id,'firststart.py',size=(400,200))
        panel= wx.Panel(self)
        
        ''' set up text box displays '''
        wx.StaticText(panel,-id,label='Master:',pos=(80,8),size=(90,20 ))
        self.Txtcontrol=wx.TextCtrl(panel,-1, pos=(140,8),size=(100,25),style=wx.TE_RIGHT)  
              
        wx.StaticText(panel,-id,label='Secondary:',pos=(60,35),size=(90,20 ))        
        self.dispText=wx.TextCtrl(panel,-1, pos=(140,35),size=(100,25),style=wx.TE_RIGHT)
        
        
        ''' BUTTONS '''
        button=wx.Button(panel,label='Count',pos=(300,110),size=(90,28))
        xferButton=wx.Button(panel,label='Copy',pos=(300,140),size=(90,28))
        clrAll=wx.Button(panel,label='CLR Displays',pos=(300,170),size=(90,28))

        ''' setup button event handler's...           '''  
        self.Bind(wx.EVT_BUTTON, self.buttonAction,button)
        self.Bind(wx.EVT_BUTTON, self.xferAction,xferButton)
        self.Bind(wx.EVT_BUTTON, self.ClrTbox,clrAll)
        
        self.count= 0   #misc variable used in buttonAction event
        
    ''' Respond to button event '''
    def buttonAction(self,e):
         self.count += 1
         self.Txtcontrol.SetBackgroundColour("red")
         self.Txtcontrol.SetValue("")  
         a=str(self.count)
         self.Txtcontrol.SetValue(a)
         self.dispText.SetBackgroundColour("green")   #("Green")
         self.Txtcontrol.SetBackgroundColour("red")
         #!/usr/bin/env python 
# 04/23/2014 21:45 
import wx 
class MyFrame(wx.Frame): 
    def __init__(self): 
        wx.Frame.__init__(self,None,-1,"GasChk.py") #,pos=(200,600)) 
         
        #panel= wx.Panel(self) # causes display problem on line 12. The full 
                               # text does not display. The first character isn't 
                               #displayed (?) 
                                
        ############### widgets ############ 
        #date of purchase 
        dateLbl=wx.StaticText(self,-1,"Date of Purchase:") 
        self.date=wx.TextCtrl(self,-1,"",size=(120,20)) 
        # Amount of gallons purchased 
        galLbl=wx.StaticText(self,-1,"Gallons Purchased:") 
        self.gallons=wx.TextCtrl(self,-1,"0.0",size=(120,20),style=wx.TE_RIGHT) 
          
        ############### Buttons ############ 
        button1=wx.Button(self,-1,"Calculate") 
        button2=wx.Button(self,-1,"button2") 
        #button Event(s) 
       # self.Bind(wx.EVT_BUTTON, self.calc,button1) 
         
        #create sizer 
        sizer = wx.FlexGridSizer(rows=6, cols=2,hgap=2,vgap=5) 
       
        # add widgets to sizer 
        sizer.Add(dateLbl,0,wx.ALIGN_RIGHT) 
        sizer.Add(self.date,0,wx.ALIGN_LEFT) 
         
        sizer.Add(galLbl,0,wx.ALIGN_RIGHT) 
        sizer.Add(self.gallons,0,wx.ALIGN_LEFT) 
        #add button(s) 
        sizer.Add(button1,0,0) 
        sizer.Add(button2,0,0) 
         
        # setup sizer(s) 
        self.SetSizer(sizer) 
        #self.Fit() 
 #=============== main ===============    
app = wx.PySimpleApp() 
MyFrame().Show() 
app.MainLoop() 
 
 
 

    ''' Clear both displays on button '''     
    def ClrTbox(self,e):
         self.Txtcontrol.SetValue("")
         self.dispText.SetValue("") 
         self.dispText.SetBackgroundColour("White") 
         self.Txtcontrol.SetBackgroundColour("white") 
         self.count=0 
         
    ''' Clear all Text control Contents '''
    def xferAction(self,e):
         gval= self.Txtcontrol.GetValue()
         self.dispText.SetValue(gval)
         
''' main stuff here '''         
if __name__ =='__main__':
    app= wx.PySimpleApp()
    frame = InsertFrame(parent=None, id = -1)
    frame.Show()
    app.MainLoop()
''' This has a tab order , and several TextBox that works ok. 
'''
```



**XXXGasChk.py**
```
#!/usr/bin/env python 
# 04/23/2014 21:45 
import wx 
class MyFrame(wx.Frame): 
    def __init__(self): 
        wx.Frame.__init__(self,None,-1,"GasChk.py") #,pos=(200,600)) 
         
        #panel= wx.Panel(self) # causes display problem on line 12. The full 
                               # text does not display. The first character isn't 
                               #displayed (?) 
                                
        ############### widgets ############ 
        #date of purchase 
        dateLbl=wx.StaticText(self,-1,"Date of Purchase:") 
        self.date=wx.TextCtrl(self,-1,"",size=(120,20)) 
        # Amount of gallons purchased 
        galLbl=wx.StaticText(self,-1,"Gallons Purchased:") 
        self.gallons=wx.TextCtrl(self,-1,"0.0",size=(120,20),style=wx.TE_RIGHT) 
          
        ############### Buttons ############ 
        button1=wx.Button(self,-1,"Calculate") 
        button2=wx.Button(self,-1,"button2") 
        #button Event(s) 
       # self.Bind(wx.EVT_BUTTON, self.calc,button1) 
         
        #create sizer 
        sizer = wx.FlexGridSizer(rows=6, cols=2,hgap=2,vgap=5) 
       
        # add widgets to sizer 
        sizer.Add(dateLbl,0,wx.ALIGN_RIGHT) 
        sizer.Add(self.date,0,wx.ALIGN_LEFT) 
         
        sizer.Add(galLbl,0,wx.ALIGN_RIGHT) 
        sizer.Add(self.gallons,0,wx.ALIGN_LEFT) 
        #add button(s) 
        sizer.Add(button1,0,0) 
        sizer.Add(button2,0,0) 
         
        # setup sizer(s) 
        self.SetSizer(sizer) 
        #self.Fit() 
 #=============== main ===============    
app = wx.PySimpleApp() 
MyFrame().Show() 
app.MainLoop() 
 
```

---

### Post by steeldriver on 2014-04-23
There seems to be a nice minimal FlexGridSizer example [here]("http://zetcode.com/wxpython/layout/") [zetcode.com] - perhaps you can use that as a starting point?

Your first code sample seems to have got screwed up btw

---

### Post by eightbits2010 on 2014-04-23
steeldriver: Thanks for the tip(s). I did download the suggested file, and the tab key does work. I can't see any thing in the example code that enables tab key functionality. I will study this example and see
 if I can get insight on what is going on.
 This example code uses the **super**(Example, self).__init__(parent, title=title,  size=(300, 250))
 and I really don't know how the super function works :confused:.  I have read a little but I am just attempting
 to put to gather what I think should be a simple GUI script that has about 6-8 fields and use TextCtrl's
 to get the inputs and also a TextCtrl to display the math results. This is a duplicate of a small project I did a few years
ago in VisualBasic. Now that I perfer to use Linux(Ubuntu 12.04) I find python easy to use except ina GUI setting.
So far, wxpython has been the most fruitful for me, but I must admit I miss some of the features of VB.
 

 From the things I have read online, it would appear that the tab key just doesn't work without a lot
 of additional code to make it work. Yet, I look at code such as this example and can't ass anything that
 makes the tab key work.

Not sure why the first code is mangled, I will copy it from the post and then check on the pc.:(

---

### Post by steeldriver on 2014-04-23
I think the behavior you're looking for is built into the wx.Panel object (the default TAB_TRAVERSAL style attribute) - so you need to put the text controls back inside a panel and figure out whatever other issues that was causing

---

### Post by eightbits2010 on 2014-04-24
Thank you steeldriver. I will try that, as can be detected OOP and classes are not my most competent
 skills in using wxpython or Python for that matter. I have been studying class and OOP in the book
 by Mark Lutz “Learning Python” which covers almost everything in using Python. I am also using
 the Edx (edx.com course 6.00.1x web site and auditing a course on Python as the language of choice for the course.   There is also a third quarter Linux course (August 2014) which I also enrolled.


 But, I am learning  more or less on my own, like many I guess, almost doing that with out any local schools that cover Python

 period. And, I have noticed that approaching 70 years of age, it seems my ability to have information
 stick is not what it used to be. However, quiting is not something I wish to contemplate  and thanks to this forum, I believe that I can still get the few projects I wanted is not impossible.

So, I will look into how to place the panel in the proper place and understand how the scope of the widgets play in the the issue I am dealing with.

Once again, your help and suggestings and I will post again as soon as I learn more.

---

