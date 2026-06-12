---
title: "[SOLVED] no errors but not running...&amp;gt;&amp;gt;&amp;gt;python problem"
date: 2008-01-15
forum: Programming Talk
---

### Post by seventhc on 2008-01-15
Ok, I've been doing some tutorials on python and today decided to type in the code for an led clock. This isn't my code, I am just trying to get familiar with python, so I retyped the code line for line, but the thing is when I try to run it I get absolutely no errors, yet nothing happens.
Any ideas what could be wrong?
here is the code:
```

# use the wxPython LEDNumberCtrl widget for nice LED clock
# Python25 and wxPython28   by  HAB     07/30/2007
#! /usr/bin/python
import time
import wx
import wx.gizmos as gizmos

class LED_clock(wx.Frame):
    """
    create nice LED clock showing the current time
    """
    def __init__(self, parent, id):
        pos = wx.DefaultPosition
        wx.Frame.__init__(self, parent, id, title='LED Clock' , pos=pos,
                size=(350, 100))
        size = wx.DefaultSize
        style = gizmos.LED_ALIGN_CENTER
        self.led = gizmos.LEDNumberCtrl(self, -1, pos, size, style)
        # default colors are green on black
        self.led.SetBackgroundColour("blue")
        self.led.SetForegroundColour("yellow")
        self.OnTimer(none)
        self.timer = wx.Timer(self, -1)
        # update clock digits every second (1000ms)
        self.timer.Start(1000)
        self.Bind(wx.EVT_TIMER, self.OnTimer)
        #self.Centre()

        def OnTimer(self, event):
            #get current time from computer
            current = time.localtime(time.time())
            # time string can have characters 0..9, -, period, or space
            ts = time.strftime("%H %M %S", current)
            self.led.SetValue(ts)

            #test the clock
            if __name__ == '__main__':
               app = wx.App()
               frame = LED_clock(none, -1)
               frame.Show(true)
               app.SetTopWindow(frame)
               app.MainLoop()

```

---

### Post by popch on 2008-01-15
When the program does not do anything, that's not wrong at all. You do not tell it to do anything.

That 'module' defines a class called LED_clock. By defining such a class you teach Python how to 'create a clock' in case someone wants one.

Having read and executed, Python knows how to 'create a clock'.

What's missing is another program which actually wants to 'create a clock'. So long as no one orders a clock to be created, none will do so.

---

### Post by seventhc on 2008-01-15
oh, thanks for the explanation, it does make sense.
But there I was thinking I'm creating a clock lol.
So would I basically need to write a second program creating a clock and then import this?

---

### Post by popch on 2008-01-15
> **seventhc said:**
> 
So would I basically need to write a second program creating a clock and then import this?

Yes.

---

### Post by seventhc on 2008-01-15
> **popch said:**
> Yes.
ok, Thanks so much for your help and the quick response.
I wish I tried here sooner, I spent well over an hour trying to figure out what was going on, and here you made it clear to me in just a few minutes. :)
Thanks again.

---

### Post by popch on 2008-01-15
Keep it up. In time, you will realize that the hour you spent in trying to understand what was going on was spent very well indeed. Sometimes the effort is worth more than the immediate result.

---

### Post by Quikee on 2008-01-16
I don't know why popch recommended you to write another program to execute this one (everything after if __name__ == "__main__" does start the program) but the only thing I see wrong is that the the whole program is not properly indented and that True and None are not capital cased. 

Here is the fixed version:

[PHP]
# Python25 and wxPython28   by  HAB	 07/30/2007
#! /usr/bin/python
import time
import wx
import wx.gizmos as gizmos

class LED_clock(wx.Frame):
	"""
	create nice LED clock showing the current time
	"""
	def __init__(self, parent, id):
		pos = wx.DefaultPosition
		wx.Frame.__init__(self, parent, id, title='LED Clock' , pos=pos,
				size=(350, 100))
		size = wx.DefaultSize
		style = gizmos.LED_ALIGN_CENTER
		self.led = gizmos.LEDNumberCtrl(self, -1, pos, size, style)
		# default colors are green on black
		self.led.SetBackgroundColour("blue")
		self.led.SetForegroundColour("yellow")
		self.onTimer(None)
		self.timer = wx.Timer(self, -1)
		# update clock digits every second (1000ms)
		self.timer.Start(1000)
		self.Bind(wx.EVT_TIMER, self.onTimer)
		#self.Centre()

	def onTimer(self, event):
		#get current time from computer
		current = time.localtime(time.time())
		# time string can have characters 0..9, -, period, or space
		ts = time.strftime("%H %M %S", current)
		self.led.SetValue(ts)

#test the clock
if __name__ == '__main__':
	app = wx.App()
	frame = LED_clock(None, -1)
	frame.Show(True)
	app.SetTopWindow(frame)
	app.MainLoop()
[/PHP]

---

### Post by seventhc on 2008-01-16
Thanks for that, i tried it and it works. 
When I originally  typed it in, I thought it should autoindent, so I'm not sure why it wasn't indented correctly. I did it in vim
Can you think of why it never gave me any errors with the original code? 
No errors at all, but nothing happened either, so thats a bit confusing.

---

### Post by seventhc on 2008-01-16
I went through the corrected version and mine line for line to see where my mistakes were...fianlly got it to work without copying and pasting :D but how do you know where something gets indented??
I also ended up changing the size to 450,100 and changed the colors from blue to black, and yellow to red. it just looks better.
My indentation was way off on the last section of code though.
Thanks for your help though, it opened my eyes to the importance of indentation quite a bit, as well as the use of capitals when needed. I must not of noticed it when i was typing it in. I guess I'll just keep playing around with it until I have a better understanding of it all.

---

### Post by popch on 2008-01-16
> **Quikee said:**
> I don't know why popch recommended you to write another program to execute this one (everything after if __name__ == "__main__" does start the program) but the only thing I see wrong is that the the whole program is not properly indented

I did so because I did not bother to read the program line by line. I did a cursory inspection to see if I could be of any help and saw there was no code which creates and runs an instance of the class.

The recommendation I gave is still valid in the sense that it would fix the problem. Your recommandation should work, too, with the added benefit of less 'work'.

---

### Post by Quikee on 2008-01-16
> **seventhc said:**
> 
Can you think of why it never gave me any errors with the original code?

There were no syntactic errors and you had the code indented so that the "if __name__..." looked like it belonged into the LED_clock class, but LED_clock class was never instantiated... 


> **popch said:**
> I did so because I did not bother to read the program line by line. I did a cursory inspection to see if I could be of any help and saw there was no code which creates and runs an instance of the class.

The recommendation I gave is still valid in the sense that it would fix the problem. Your recommandation should work, too, with the added benefit of less 'work'.

Yes the recommendation is still valid and I also saw nothing wrong at the first sight - when I inspected the code for the second time I saw the actual problem.

---

### Post by seventhc on 2008-01-16
*looks up instantiated*
Thanks to both of you for your help.
I need to find out how indentation works.
Are the indented parts of the code associated with all the other indented code, and the non-indented code goes with the non??
If I understand correctly, then code indented the same amount belongs to the same block of code, or something close to that explanation.

---

