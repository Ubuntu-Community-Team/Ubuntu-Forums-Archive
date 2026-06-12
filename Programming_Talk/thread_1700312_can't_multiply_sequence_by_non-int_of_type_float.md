---
title: "can't multiply sequence by non-int of type float"
date: 2011-03-04
forum: Programming Talk
---

### Post by steveone on 2011-03-04
Hey guys. I'm new to python and I've been struggling with this problem for a while. I've search google and youtube but no luck so far. I've written this in IDLE 2.6.5. If someone could tell me why I'm getting the can't multiply sequence by non-int of type float error.


#GUIConverter.py
#This is the GUI version of the converter

import wx
import math

class converter(wx.Frame):
    def __init__(self, parent, id):
        wx.Frame.__init__(self, parent, id, 'Temperature Converter', size = (300, 200))
        panel = wx.Panel(self)
        
        self.status = wx.StaticText(panel, wx.ID_ANY, 'Enter The Temperature Below', pos=(10,5))
        self.input = wx.TextCtrl(panel, -1, "30", size=(125, -1), pos=(15, 30), style=wx.TE_PROCESS_ENTER) 
        celsius = wx.Button(panel, label = "Celsius", pos = (10, 100), size = (75, 30) )
        fehrenheit = wx.Button(panel, label = "Fehrenheit", pos = (130, 100), size = (95, 30) )
        button = wx.Button(panel, label ="exit", pos = (75, 140), size = (60, 30))

       
        
        self.Bind(wx.EVT_BUTTON, self.celsiusClick, celsius)
        self.Bind(wx.EVT_BUTTON, self.fehrenheitClick, fehrenheit)
        self.Bind(wx.EVT_BUTTON,self.closebutton, button)
        self.Bind(wx.EVT_CLOSE, self.closewindow)

        self.Show(True)

    def celsiusClick(self, event):
        #this gets the title of the button clicked
        label = event.GetEventObject().GetLabel()
        if label == "Celsius":
            try:
                c = self.input.GetValue()
                c = (9.0/5.0) * c + 32
                if not c.strip():
                    return
                result = eval(c)
                
                self.input.Insert(c, 0)
                self.input.SetValue(str(result))
            except Exception, e:
                wx.LogError(str(e))
                return
            else:
                self.equal.SetFocus()


    def fehrenheitClick(self, event):
        label = event.GetEventObject().GetLabel()
        if label == "Fehrenheit":
            try:
                c = self.display.GetValue()
                celsius = c - 32.0 / 9.0/5.0
                if not celsius.strip():
                    return
                result = eval(celsius)

                self.display.SetValue(str(result))
            except Exception, e:
                wx.LogError(str(e))
                return

    def closebutton(self, event):
        self.Close(True)

    def closewindow(self, event):
        self.Destroy()

if __name__=='__main__':
    app = wx.PySimpleApp()
    frame = converter(parent = None, id = -1)
    #dlg = converter(None, -1)

    try:
        
        app.MainLoop()

    finally:
        del app

---

### Post by johnl on 2011-03-04
Hi,

Please edit your post to put your code in ```
 
``` tags so that the indentation and formatting is preserved.

Also, post the full error message including line number. The problem is that you are (somewhere) doing:

```

3.0 * x

```

where x is a list.  You probably meant x to be a single item, so you need to figure out why your variable is a list and correct it.

---

### Post by talonmies on 2011-03-05
wx.TextCtrl.GetValue() returns a string. Performing arithmetic on a string is illegal in Python. You should also check the operator precedence rules in your conversion formula. One of them is clearly wrong.

---

### Post by foxmuldr on 2011-03-05
> **talonmies said:**
> wx.TextCtrl.GetValue() returns a string. Performing arithmetic on a string is illegal in Python. You should also check the operator precedence rules in your conversion formula. One of them is clearly wrong.

You need something like int(wx.TextCtrl.GetValue()).

- Rick C. Hodgin

---

### Post by steveone on 2011-03-05
> **johnl said:**
> Hi,

Please edit your post to put your code in  tags so that the indentation and formatting is preserved.

Also, post the full error message including line number. The problem is that you are (somewhere) doing:

```

3.0 * x

```where x is a list.  You probably meant x to be a single item, so you need to figure out why your variable is a list and correct it.
Thanks for replying. I apologize for the code not maintaining it's indentations and such. When I pasted it in, it looked exactly the way it does in IDLE. For some reason it changes once it's posted. If you could explain to me how to preserve it, I would be happy to comply. 

This is the original code that I wrote, which works perfectly, but I wanted to create a GUI for it:

#convert.py
#This converts temperatures from Celsius to Fahrenheit

def main():
    c = input("What is the number in Celcius? ")
    f = 9.0/5.0 * c + 32
    print "The temperature is", f, "degrees Fahrenheit."
main()
raw_input("Press<enter>")

If you would like to run it, you can see there is no float error. I'm assuming the error occurs because of the way I'm attempting to get the input from the user in the GUI. The problem is I am quite new to Python and don't know which method will take the input as an int. I tried using GetNumberFromUser, but could not process the number after because the GetValue could not be applied. Again any and all input and suggestions are appreciated. Thanks.

---

### Post by johnl on 2011-03-05
> **steveone said:**
> Thanks for replying. I apologize for the code not maintaining it's indentations and such. When I pasted it in, it looked exactly the way it does in IDLE. For some reason it changes once it's posted. If you could explain to me how to preserve it, I would be happy to comply. 


Sorry -- I could have sworn I checked to make sure my post didn't eat the tags, but it looks like it did.  You can either click the **#** button at the top right of the editor, or manually surround your code with &#91;code] [/code] tags

---

### Post by steveone on 2011-03-05
> **johnl said:**
> Sorry -- I could have sworn I checked to make sure my post didn't eat the tags, but it looks like it did.  You can either click the **#** button at the top right of the editor, or manually surround your code with  tags
Ok. Thanks for the education.

---

### Post by steveone on 2011-03-06
Ok guys, I figured it out. Like I said before, I am new to Python and programming in general, so it took me a little while. This was a simple fix, but if you don't know, you don't know. The can't multiply sequence by non-int of type 'float' error was because the input taken in the text-box is a string. So when Python sees:

 #c = self.input.GetValue()#

the value is still a string. Therefore, that value in c has to be converted, in this case to a float type:

#c = float(c)#

so Python can process it as part of the equation:
#c = 9.0/5.0 * c + 32# 

I had to do some house cleaning which simplified the code, but this is a learning process. I have written my first GUI application in Python. Simple as it may be, it is a great feeling. :D
I hope this will help someone else.

Thanks again to everyone who responded with suggestions.

---

