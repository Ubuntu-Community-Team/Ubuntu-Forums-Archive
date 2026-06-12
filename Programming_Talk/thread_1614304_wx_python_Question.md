---
title: "wx python Question"
date: 2010-11-05
forum: Programming Talk
---

### Post by yanes on 2010-11-05
Hi all ,

I made a frame containing a TextCtrl in python under WXGlade 
where the textCtrl is diabled , When users invokes an event i want to make this 
control Enabled and editable ,Itried the Enable() function , but is doesn't works 

how to proceed ? 

wxpython version : 2.8

---

### Post by Arndt on 2010-11-05
> **yanes said:**
> Hi all ,

I made a frame containing a TextCtrl in python under WXGlade 
where the textCtrl is diabled , When users invokes an event i want to make this 
control Enabled and editable ,Itried the Enable() function , but is doesn't works 

how to proceed ? 

wxpython version : 2.8

I would check:
1) Is the event really received as it should? Use print on stdout.
2) Is Refresh() done on the frame/window/panel?

---

### Post by yanes on 2010-11-06
thank you for reply ,
1) Is the event really received as it should? YES , i execute my program in a terminal, the event is received correctly
 
2) Is Refresh() done on the frame/window/panel? No 

please ,what 's the correct syntax to use this function ?, :) I tried many forms but no success
 
thanks in advance

---

### Post by Arndt on 2010-11-06
> **yanes said:**
> thank you for reply ,
1) Is the event really received as it should? YES , i execute my program in a terminal, the event is received correctly
 
2) Is Refresh() done on the frame/window/panel? No 

please ,what 's the correct syntax to use this function ?, :) I tried many forms but no success
 
thanks in advance

It's a method, so you do something like frame.Refresh(), or self.Refresh() if your event handler is a method of the frame.

---

### Post by yanes on 2010-11-06
I think the Refresh() function is just to apply changes to controls , 
but when I call the Enable() function it gives an error ,
IF , there's no problem , I attached example , you can see it 
and insert the missing line of code ;) 

thank you , another once

---

### Post by yanes on 2010-11-08
No reply !!

---

### Post by Arndt on 2010-11-08
> **yanes said:**
> No reply !!

I thought you would look up the documentation for Refresh and proceed from there. There are examples too, on the wxPython site, which you can download and study. Some of them use Refresh for some purpose.

What error does Enable give you? When you first said it doesn't work, I thought nothing at all happened.

---

### Post by Arndt on 2010-11-08
> **Arndt said:**
> I thought you would look up the documentation for Refresh and proceed from there. There are examples too, on the wxPython site, which you can download and study. Some of them use Refresh for some purpose.

What error does Enable give you? When you first said it doesn't work, I thought nothing at all happened.

Now I looked at your code too. I don't know anything about wxGlade, but it seems to have generated some code for you, from what specification I don't know. The key point is this method:

```
    def Bttm_enable_click(self, event): # wxGlade: MyFrame.<event_handler>
        print "Event handler `Bttm_enable_click' not implemented!"
        event.Skip()

```

So when you press the Enable button, the above text is shown. Is this what you mean "doesn't work"? You're supposed to fill in code that implements the enabling of the text. Refresh(), which I mentioned, is probably not needed.

So what is your suggestion for the implementation? Is this homework?

---

### Post by yanes on 2010-12-18
En tout cas ;)

Thank you very much Arndt , I found the solution ,

The solved example is attached it can perhaps be useful for someone .

one line of code added

---

