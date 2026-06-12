---
title: "webbrowsers help ect.....python...."
date: 2007-05-04
forum: Programming Talk
---

### Post by hockey97 on 2007-05-04
HI I  want to know if it's possible to script a whole new internet browser??

I have seen on google people asking this and most respond syaing ti's hard and advise just using an exisiting browser engine ect.

I want to start making my own web broswer, from ground up , I know it's a hard task and would talk long, I

don't mind it and I am not a noob at programming but never fully used python in such a task, I know how to make the gui but what I am asking is, does python support webbrowser controler meaning the code or scirpt that would display http or any html or internet documnet.

and Does python support server sided and client sided server;s ect like ftp or  webserver ect?

I have been looking at modules of python and seend some of these stuff in the libary index.

the webbrowser module to me as I see it look's like controls for existing web browsers, as how I understood
it was that if I made a program and could embed a web browser thing in my program, or  is it  that when you click somthing in a application that takes you to a website that would use the webbrowser module to do this function.


thanks for your time.

---

### Post by AdamG on 2007-05-04
It is possible to write your own web browser. 

But you don't want to. It's not "going to take a long time." Writing a web browser from the ground up, in 2007, can't really happen. Any web browser that gets off the ground is pretty much going to come from the Mozilla/Gecko codebase, hacked away into something unrecognizable perhaps, but still from there. 

Most people underestimate the amount of work that a modern-day web browser does. It's not just downloading, parsing, putting in a DOM tree, correcting HTML errors, calculating box model widths/heights, rendering widgets, and displaying on a screen. Oh no... there is a lot more involved than that. First, for any Javascript support at all, you essentially have to not only write a browser, but write a javascript engine (Ever written your own programming language before?). Don't forgot to not allow the JS code to: Modify any files, change the state of the browser, execute arbitrary statments, get/set cookies not for the site in question, tie up the CPU for too long, or a few hundred other things. At the same time, it has to be pretty blazing quick - and writing an interpreted language in an interpreted language isn't real high on the list of ways to write fast programs. While we're on Cookies, make sure you find some way to reliably set cookies which will not necessarily be sent by the server correctly, while still never sending the wrong cookie to the wrong site (Ever implemented your own permissions system?). 

Not to be discouraging or anything, but Firefox will have Python support long before any of us could write a Firefox clone in Python. It's not even a close race. It's not even a race! Python doesn't exist to implement web browsers, and full-fledged web browsers ARE scripting language interpreters, whether that language be HTML, CSS or Javascript (or Python!). It's like trying to rewrite the Emacs core in Python... Why? The functionality is added through Emacs-Lisp, not through the core... that's the whole point!

Sigh... I've got to go, I'm upgrading to Feisty.

---

### Post by hockey97 on 2007-05-05
I am not trying to rewrite the web browsers engine ect, in bordland c++ I made a small web browsers using a web control libaray, what I want to do is import exisiting web browsers engines to do the borwsing but mod the engine in some way's like the error messages and other stuff ot it. 

I also will make a gui  for it. what your talking about is the engine that runs the browser where it goes to the rawest state where it deals with proto calls and programming interpertations which makes no sence on redoing those since it's already their.

I want to give my browser a newish look and have some additions to it, I am not going to script from the rawest state.

just was asking if their are such modules or any place that I can download the web browser control or files that contains the engine or functions of exisiting web browsers.

Thanks for your time.

---

### Post by b1g4L on 2007-05-05
This might be of some help. I pulled this directly from the demo for wxPython. It only works on Windows (because it uses ActiveX and IE engine). It's relatively short and can give you some direction possibly. It emulates a full, but limited browser.

```
# 11/18/2003 - Jeff Grimmett (grimmtooth@softhome.net)
#
# o Updated for wx namespace
# 

import  wx

if wx.Platform == '__WXMSW__':
    import  wx.lib.iewin    as  iewin

#----------------------------------------------------------------------

class TestPanel(wx.Panel):
    def __init__(self, parent, log, frame=None):
        wx.Panel.__init__(
            self, parent, -1,
            style=wx.TAB_TRAVERSAL|wx.CLIP_CHILDREN|wx.NO_FULL_REPAINT_ON_RESIZE
            )
            
        self.log = log
        self.current = "http://wxPython.org/"
        self.frame = frame

        if frame:
            self.titleBase = frame.GetTitle()

        sizer = wx.BoxSizer(wx.VERTICAL)
        btnSizer = wx.BoxSizer(wx.HORIZONTAL)

        self.ie = iewin.IEHtmlWindow(self, -1, style = wx.NO_FULL_REPAINT_ON_RESIZE)


        btn = wx.Button(self, -1, "Open", style=wx.BU_EXACTFIT)
        self.Bind(wx.EVT_BUTTON, self.OnOpenButton, btn)
        btnSizer.Add(btn, 0, wx.EXPAND|wx.ALL, 2)

        btn = wx.Button(self, -1, "Home", style=wx.BU_EXACTFIT)
        self.Bind(wx.EVT_BUTTON, self.OnHomeButton, btn)
        btnSizer.Add(btn, 0, wx.EXPAND|wx.ALL, 2)

        btn = wx.Button(self, -1, "<--", style=wx.BU_EXACTFIT)
        self.Bind(wx.EVT_BUTTON, self.OnPrevPageButton, btn)
        btnSizer.Add(btn, 0, wx.EXPAND|wx.ALL, 2)

        btn = wx.Button(self, -1, "-->", style=wx.BU_EXACTFIT)
        self.Bind(wx.EVT_BUTTON, self.OnNextPageButton, btn)
        btnSizer.Add(btn, 0, wx.EXPAND|wx.ALL, 2)

        btn = wx.Button(self, -1, "Stop", style=wx.BU_EXACTFIT)
        self.Bind(wx.EVT_BUTTON, self.OnStopButton, btn)
        btnSizer.Add(btn, 0, wx.EXPAND|wx.ALL, 2)

        btn = wx.Button(self, -1, "Search", style=wx.BU_EXACTFIT)
        self.Bind(wx.EVT_BUTTON, self.OnSearchPageButton, btn)
        btnSizer.Add(btn, 0, wx.EXPAND|wx.ALL, 2)

        btn = wx.Button(self, -1, "Refresh", style=wx.BU_EXACTFIT)
        self.Bind(wx.EVT_BUTTON, self.OnRefreshPageButton, btn)
        btnSizer.Add(btn, 0, wx.EXPAND|wx.ALL, 2)

        txt = wx.StaticText(self, -1, "Location:")
        btnSizer.Add(txt, 0, wx.CENTER|wx.ALL, 2)

        self.location = wx.ComboBox(
                            self, -1, "", style=wx.CB_DROPDOWN|wx.PROCESS_ENTER
                            )
        
        self.Bind(wx.EVT_COMBOBOX, self.OnLocationSelect, self.location)
        self.location.Bind(wx.EVT_KEY_UP, self.OnLocationKey)
        self.location.Bind(wx.EVT_CHAR, self.IgnoreReturn)
        btnSizer.Add(self.location, 1, wx.EXPAND|wx.ALL, 2)

        sizer.Add(btnSizer, 0, wx.EXPAND)
        sizer.Add(self.ie, 1, wx.EXPAND)

        self.ie.LoadUrl(self.current)
        self.location.Append(self.current)

        self.SetSizer(sizer)
        # Since this is a wxWindow we have to call Layout ourselves
        self.Bind(wx.EVT_SIZE, self.OnSize)

        # Hook up the event handlers for the IE window
        self.Bind(iewin.EVT_BeforeNavigate2, self.OnBeforeNavigate2, self.ie)
        self.Bind(iewin.EVT_NewWindow2, self.OnNewWindow2, self.ie)
        self.Bind(iewin.EVT_DocumentComplete, self.OnDocumentComplete, self.ie)
        ##self.Bind(iewin.EVT_ProgressChange,  self.OnProgressChange, self.ie)
        self.Bind(iewin.EVT_StatusTextChange, self.OnStatusTextChange, self.ie)
        self.Bind(iewin.EVT_TitleChange, self.OnTitleChange, self.ie)


    def ShutdownDemo(self):
        # put the frame title back
        if self.frame:
            self.frame.SetTitle(self.titleBase)


    def OnSize(self, evt):
        self.Layout()


    def OnLocationSelect(self, evt):
        url = self.location.GetStringSelection()
        self.log.write('OnLocationSelect: %s\n' % url)
        self.ie.Navigate(url)

    def OnLocationKey(self, evt):
        if evt.GetKeyCode() == wx.WXK_RETURN:
            URL = self.location.GetValue()
            self.location.Append(URL)
            self.ie.Navigate(URL)
        else:
            evt.Skip()


    def IgnoreReturn(self, evt):
        if evt.GetKeyCode() != wx.WXK_RETURN:
            evt.Skip()

    def OnOpenButton(self, event):
        dlg = wx.TextEntryDialog(self, "Open Location",
                                "Enter a full URL or local path",
                                self.current, wx.OK|wx.CANCEL)
        dlg.CentreOnParent()

        if dlg.ShowModal() == wx.ID_OK:
            self.current = dlg.GetValue()
            self.ie.Navigate(self.current)

        dlg.Destroy()

    def OnHomeButton(self, event):
        self.ie.GoHome()    ## ET Phone Home!

    def OnPrevPageButton(self, event):
        self.ie.GoBack()

    def OnNextPageButton(self, event):
        self.ie.GoForward()

    def OnStopButton(self, evt):
        self.ie.Stop()

    def OnSearchPageButton(self, evt):
        self.ie.GoSearch()

    def OnRefreshPageButton(self, evt):
        self.ie.Refresh(iewin.REFRESH_COMPLETELY)


    def logEvt(self, evt):
        pst = ""
        for name in evt.paramList:
            pst += " %s:%s " % (name, repr(getattr(evt, name)))
        self.log.write('%s: %s\n' % (evt.eventName, pst))


    def OnBeforeNavigate2(self, evt):
        self.logEvt(evt)

    def OnNewWindow2(self, evt):
        self.logEvt(evt)
        # Veto the new window.  Cancel is defined as an "out" param
        # for this event.  See iewin.py
        evt.Cancel = True   

    def OnProgressChange(self, evt):
        self.logEvt(evt)
        
    def OnDocumentComplete(self, evt):
        self.logEvt(evt)
        self.current = evt.URL
        self.location.SetValue(self.current)

    def OnTitleChange(self, evt):
        self.logEvt(evt)
        if self.frame:
            self.frame.SetTitle(self.titleBase + ' -- ' + evt.Text)

    def OnStatusTextChange(self, evt):
        self.logEvt(evt)
        if self.frame:
            self.frame.SetStatusText(evt.Text)


#----------------------------------------------------------------------
# for the demo framework...

def runTest(frame, nb, log):
    if wx.Platform == '__WXMSW__':
        win = TestPanel(nb, log, frame)
        return win
    else:
        from Main import MessagePanel
        win = MessagePanel(nb, 'This demo only works on Microsoft Windows.',
                           'Sorry', wx.ICON_WARNING)
        return win



overview = """\
<html><body>
<h2>wx.lib.iewin.IEHtmlWindow</h2>

The wx.lib.iewin.IEHtmlWindow class is one example of using ActiveX
controls from wxPython using the new wx.activex module.  This allows
you to use an ActiveX control as if it is a wx.Window, you can call
its methods, set/get properties, and receive events from the ActiveX
control in a very intuitive way.

<p> Using this class is simpler than ActiveXWrapper, doesn't rely on
the win32all extensions, and is more "wx\'ish", meaning that it uses
events and etc. as would be expected from any other wx window.

</body></html>
"""



if __name__ == '__main__':
    import sys,os
    import run
    run.main(['', os.path.basename(sys.argv[0])] + sys.argv[1:])


#----------------------------------------------------------------------


```

---

### Post by hockey97 on 2007-05-12
that kinda helps, but does python have libary's that handle's http and other web protocals and also can do http request and handle html and other programming web pages like java flash ect. 

I am starting to start on the art part the gui ect trying to use my custom art for the buttons ec and the windows.

I have been reading about webbrowser and web.py To what I understand it look's like those are only or can be only used with applications to have a import form in a  regular application to give a request to a web browser that's already installed on the person's computer, am I right???

I want to make a custome web browser that I will still use modules that can handle http and other web protocals ect, I have the time to spend and do have  a hige range of knowledge in computers, so I know it's not easy but still going to use already made protocalls and other stuff that already has been made, trying to keep it simple as possible.

I just need some guid on what modules to get that would have the functions that can be used for the browser.

I will still search the web for any light on the modules or any package to get to embed in my program.

Thanks for your time.

---

### Post by JT673 on 2007-05-12
I'd actually do the web browser in Java, because Swing has several components that parses HTML for you, like JEditorPane.  There is also a Gecko (of Mozilla fame) port called JRex, and it's pretty good.

---

