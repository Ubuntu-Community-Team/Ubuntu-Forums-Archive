---
title: "[SOLVED] wxPython - Is this for real?"
date: 2008-11-02
forum: Programming Talk
---

### Post by MaxVK on 2008-11-02
Hi there. I began using wxPython a week ago, using a mix of wxGlade and the Scite editor. I'm doing very well and have developed a small application.

However, I want to advance but I have spent the last two days trying to work out if wxPython (Or any other Python for that matter) has a working Rich Text Control. Thus far I have found only a demo (very good it looks too), but the Rich Text is generated in the code, and the control cannot load or save in RTF.

Is this for real? Surely there must be a Rich text Control out there somewhere that is design for use in Python?

Any information would be much appreciated.

Regards

Max

---

### Post by Sorivenul on 2008-11-02
[http://wxpython.org/docs/api/wx.richtext.RichTextCtrl-class.html]("http://wxpython.org/docs/api/wx.richtext.RichTextCtrl-class.html")
Hope that helps.  Seems to be what you're looking for.

---

### Post by MaxVK on 2008-11-02
Thanks Sorivenul.

I found this page already, but I am at a loss as to how to actually use this control, and I have a feeling that this is the same one being used in the wxWidgets demo, which looks really nice, but does not load or save RTF files.

---

### Post by MaxVK on 2008-11-08
Well, after another few days of fruitless searching it seems that while wxPython has RTF support in Windows, it does not in Linux. Iv spoken to lots of people who have pointed me at the demo, but they all seem rather surprised that it doesn't load or save RTF files.

If anyone has anything to add to this Id love to hear it.

Regards

Max

---

### Post by hessiess on 2008-11-08
Port the lib to linux yourself, then submit a patch so outhers can take advantage of it?

---

### Post by cmat on 2008-11-08
You'll have to get the RTF source of what you are editing. You can create a script to do that or use a format it does support and get a library that can convert that to RTF. 

The demo on Windows can't save as *.rtf, I've tried (more than likely I'm going to get proved wrong).

---

### Post by MaxVK on 2008-11-09
> Port the lib to linux yourself, then submit a patch so outhers can take advantage of it?

That sounds like a great idea - What does it mean? ;)

> You'll have to get the RTF source of what you are editing. You can create a script to do that or use a format it does support and get a library that can convert that to RTF.

As in the comment I made above, this sounds great, but what are you talking about? :)

Sorry guys, but I'm not that advanced in either Python or Linux - I have no idea what either of you just suggested. By the sound of it you are talking about (possibly) editing a part of the wxWidgets code and recompiling it, which is way too complex for me just yet!

All I want to do is learn to program Python with wxWidgets - If the language cant do what I need it to do then Ill have to find a language that can!

Regards

Max

---

### Post by MaxVK on 2008-11-09
Okay, the problem is solved:

Under Linux the wxWidgets demo does *NOT* load or save RTF files, however, it does save XML files that include all of the relevant formatting. The problem (with the demo) is that the filters on the load dialog are not set correctly, which leads to the XML file being loaded as raw XML and not formatted rich text.

To get around this problem you can edit the demo file:

```
def OnFileOpen(self, evt):
        wildcard, types = rt.RichTextBuffer.GetExtWildcard(save=False)
        dlg = wx.FileDialog(self, "Choose a filename", 
                            #The following line was changed from "*.*"
                            wildcard=wildcard,
                            style=wx.OPEN)
        if dlg.ShowModal() == wx.ID_OK:
            path = dlg.GetPath()
            if path:
                fileType = types[dlg.GetFilterIndex()]
                self.rtc.LoadFile(path, fileType)
        dlg.Destroy()
```

Notice the line: "*wildcard=wildcard,*" in the dialog setup. This was originally set to "*.*", which showed all the files just fine, but did not activate the filters required to convert the XML file into an RTF display.

So. There *IS* a RichTextCtrl in wxWidgets, and it *DOES* load and save rich formatted text, although it does so using XML, which is neither here nor there when it comes right down to it unless you plan to try and import the saved file into another rich text enabled application.

Thanks to everyone who tried to help out, and I hope this little expedition into the depths of wxWidgets and the RichTextCtrl helps someone else.

Regards

Max

---

### Post by WW on 2008-11-09
Thanks for reporting back with your solution.

---

