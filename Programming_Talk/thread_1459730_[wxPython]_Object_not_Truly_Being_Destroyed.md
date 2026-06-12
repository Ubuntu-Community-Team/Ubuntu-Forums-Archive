---
title: "[wxPython] Object not Truly Being Destroyed"
date: 2010-04-21
forum: Programming Talk
---

### Post by dodle on 2010-04-21
I've been trying to destroy a dialog using a custom function.  The dialog dissapears, but my IDE (DrPython) says that it is still running.  If I hit the "X" box it closes correctly, but not if I use my function.  How can I do this correctly?

[php]import wx

def DestroyDia(event, object):
	object.Destroy()

def ShowDia(event):
	# Create the dialog
	dia = wx.Dialog(None, -1, "Destroy Me?")
	
	yes = wx.Button(dia, wx.OK, "Yes")

	# Destroy dialog when button pressed
	yes.Bind(wx.EVT_BUTTON, lambda evt, temp=dia: DestroyDia(evt, temp))
	
	sizer = wx.BoxSizer(wx.HORIZONTAL)
	sizer.Add(yes, 1, wx.EXPAND)
	
	dia.SetSizer(sizer)
	
	dia.ShowModal()
	dia.Destroy()

app = wx.App()
ShowDia(0)
app.MainLoop()[/php]

I've also tried it with an inline (I think it's called) function:
[php]	def OnButton(event):
		DestroyDia(dia)
	
	wx.EVT_BUTTON(yes, -1, OnButton)[/php]

**A couple other questions about programming terminology:**

This is an event?
```
wx.EVT_COMMAND_BUTTON_CLICKED
```
This is a callback?
```
wx.EVT_BUTTON(wx.Button, -1, self.OnButton)
```
And this is an event handler?
```
def OnButton(self, event):
    print "Hello World"
```

---

### Post by dodle on 2010-04-21
Replaced:```
object.Destroy()
```with:```
object.Close()
```and it works.  Apparently the dialog cannot be "destroyed" until after the function.

---

