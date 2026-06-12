---
title: "wxPython simple app error please help"
date: 2011-07-19
forum: Programming Talk
---

### Post by kaloasd on 2011-07-19
I'm new to wxPython and don't get the error to this app:

App:
```
#!/usr/bin/env python
import wx

class kalo(wx.Frame):       #Important

    def __init__(self,parent,id):
        wx.Frame.__init__(self,parent,id,'My first frame', size=(300,200))  #actual frame
        panel=wx.Panel(self)   #this is a pannel

        test=wx.TextEntryDialog(None,'The alphabet shift requires an index - positive or negative','Index','enter shift index')
        if test.ShowModal()==wx.ID_OK:
            n=test.GetValue()

        test2=wx.TextEntryDialog(None,'This is the text you want','Text','enter text here')
        if test2.ShowModal()==wx.ID_OK:
            t=test.GetValue()

        n=int(n)
        m=len(t)
        t=list(t)
        a="abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
        str(a)
        s={'a':a[0+n],'b':a[1+n],'c':a[2+n],'d':a[3+n],'e':a[4+n],'f':a[5+n],'g':a[6+n],'h':a[7+n],'i':a[8+n],'j':a[9+n],'k':a[10+n],'l':a[11+n],'m':a[12+n],'n':a[13+n],'o':a[14+n],'p':a[15+n],'q':a[16+n],'r':a[17+n],'s':a[18+n],'t':a[19+n],'u':a[20+n],'v':a[21+n],'w':a[22+n],'x':a[23+n],'y':a[24+n],'z':a[25+n],' ':' ',',':','}
        o=""
        for f in range(m):
            o=o+s[t[f]]

        

        wx.StaticText(panel,-1,"Index = " + n2,(10,10))
        wx.StaticText(panel,-1,"Input text = " + t,(10,30))
        wx.StaticText(panel,-1,o,(10,50))

if __name__=='__main__':
    app=wx.PySimpleApp()
    frame=kalo(parent=None,id=-1)
    frame.Show()
    app.MainLoop()
```Error:
```
Traceback (most recent call last):
  File "test.py", line 36, in <module>
    frame=kalo(parent=None,id=-1)
  File "test.py", line 26, in __init__
    o=o+s[t[f]]
KeyError: u'2'
```Please help

---

### Post by cgroza on 2011-07-19
A few tips.

str(a) will have no effect in this case, because it produces a new string, it does not modify it's argument because strings are immutable. And I do not think you need it because a is already a string.

Your variables could be more descriptive, and a few comments about what the program is supposed to do would be very helpful

Also, to generate your dictionary, you could make it much cleaner using some kind of loop.

---

### Post by Arndt on 2011-07-19
> **kaloasd said:**
> I'm new to wxPython and don't get the error to this app:

App:
```
#!/usr/bin/env python
import wx

class kalo(wx.Frame):       #Important

    def __init__(self,parent,id):
        wx.Frame.__init__(self,parent,id,'My first frame', size=(300,200))  #actual frame
        panel=wx.Panel(self)   #this is a pannel

        test=wx.TextEntryDialog(None,'The alphabet shift requires an index - positive or negative','Index','enter shift index')
        if test.ShowModal()==wx.ID_OK:
            n=test.GetValue()

        test2=wx.TextEntryDialog(None,'This is the text you want','Text','enter text here')
        if test2.ShowModal()==wx.ID_OK:
            t=test.GetValue()

        n=int(n)
        m=len(t)
        t=list(t)
        a="abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"
        str(a)
        s={'a':a[0+n],'b':a[1+n],'c':a[2+n],'d':a[3+n],'e':a[4+n],'f':a[5+n],'g':a[6+n],'h':a[7+n],'i':a[8+n],'j':a[9+n],'k':a[10+n],'l':a[11+n],'m':a[12+n],'n':a[13+n],'o':a[14+n],'p':a[15+n],'q':a[16+n],'r':a[17+n],'s':a[18+n],'t':a[19+n],'u':a[20+n],'v':a[21+n],'w':a[22+n],'x':a[23+n],'y':a[24+n],'z':a[25+n],' ':' ',',':','}
        o=""
        for f in range(m):
            o=o+s[t[f]]

        

        wx.StaticText(panel,-1,"Index = " + n2,(10,10))
        wx.StaticText(panel,-1,"Input text = " + t,(10,30))
        wx.StaticText(panel,-1,o,(10,50))

if __name__=='__main__':
    app=wx.PySimpleApp()
    frame=kalo(parent=None,id=-1)
    frame.Show()
    app.MainLoop()
```Error:
```
Traceback (most recent call last):
  File "test.py", line 36, in <module>
    frame=kalo(parent=None,id=-1)
  File "test.py", line 26, in __init__
    o=o+s[t[f]]
KeyError: u'2'
```Please help

It looks to me as if t contains the character '2', which probably means that you entered a 2. But there is no '2' in your dictionary, so you get a key error.

---

