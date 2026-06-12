---
title: "[Python] Read from a serial connection every few seconds and update a wxPython window"
date: 2008-12-02
forum: Programming Talk
---

### Post by buttertoad on 2008-12-02
I have a python program that reads a set chunk of data from a serial connection, cleans it up, and displays in a gui window.

What is the best way to get the program to read from the connection every 10 seconds or so and update the window? I want this to be a status window that stays on all the time.

The program seems to be working great right now but it only reads once. I would be happy to provide any code or further information if it would help.

thanks.

---

### Post by buttertoad on 2008-12-12
Still trying to work this out. I've been playing with while loops and the module reload but it's not working yet.

Whenever I have a while loop in a wxPython gui window I can't close the window by clicking the close "X". Is there an exception I can add to handle this?

I'm hoping a simple loop can be the answer because all the reading I've done seems to be pointing to Idle events and threads which are WAY beyond me right now.

---

### Post by finnjimm on 2008-12-13
You have to set up a WxPython Timer that triggers every 10 seconds. Instructions here: [http://wiki.wxpython.org/Timer]("http://wiki.wxpython.org/Timer"). Note that the time value is in milliseconds.

---

### Post by buttertoad on 2008-12-15
Thanks for the tip. I'm going to see if I can figure that out. :)

---

### Post by ZuLuuuuuu on 2008-12-15
And starting a new Python thread with a timer which controls the serial port every ten seconds might be another solution. This might help about threeads in Python:

[http://www.devshed.com/c/a/Python/Basic-Threading-in-Python](http://www.devshed.com/c/a/Python/Basic-Threading-in-Python)

---

### Post by aapocketz on 2008-12-15
seems like this may be an application for threads, and consider a blocking approach to reading the serial port (pyserial?).  That way you aren't burning CPU time if you are just reading every few seconds non-blocking. 

I am not very familiar with wxPython but I have used pyQT and tkinter.  Typically I would set up a "listener" thread that would handle the serial buffer do some sort of callback to update the GUI widget display.  You don't want this running in your main thread (unless reading a serial port is the only thing your app does).

---

### Post by buttertoad on 2008-12-16
Thank you for the suggestions.

So could I have a thread that reads 1000 bytes from the serial connection every 10 seconds and then returns a string to be displayed in a window?

Once I start a thread does it keep running until I stop it or does it run just once?

Thanks for bearing with me. I'm trying to figure all this stuff out as fast as I can.

---

### Post by iQuizzle on 2008-12-17
> **buttertoad said:**
> Thank you for the suggestions.

So could I have a thread that reads 1000 bytes from the serial connection every 10 seconds and then returns a string to be displayed in a window?

Once I start a thread does it keep running until I stop it or does it run just once?

Thanks for bearing with me. I'm trying to figure all this stuff out as fast as I can.


the wx timer will continuously run unless you set the oneShot flag...i think you want to keep it running so just point the timer to your function and call the timer start in your wx class __init__

you can also run multiple timers simultaneously if you have other things that need to be updated. off the top of my head it would look something like this:

```

ID_TIMER = 100

class MyFrame(wx.Frame):
  def __init__(self,*args,*kwargs):
    wx.Frame.__init__(self,None,-1,'Report Serial')
    self.timer=wx.Timer(self, ID_TIMER)
    self.Bind(wx.EVT_TIMER, self.ReadSerial, self.timer)
    self.timer.Start(10000)
    #more wx stuff
 
  def ReadSerial(self,event):
    #code to read the serial port and update statictext


```


this should loop the ReadSerial every 10 seconds indefinitely or until you stop the program.

---

### Post by ZuLuuuuuu on 2008-12-17
You start a thread and then go into an infinite loop. Like this:

```
while "1" == "1":
    control the serial port
    time.sleep(10)
```

Because it is in a different thread, the infinite loop will not effect the main program.

---

