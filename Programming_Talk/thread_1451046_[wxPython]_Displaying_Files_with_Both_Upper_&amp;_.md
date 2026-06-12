---
title: "[wxPython] Displaying Files with Both Upper &amp; Lower Extensions"
date: 2010-04-09
forum: Programming Talk
---

### Post by dodle on 2010-04-09
I haven't been able to find information about this in the [[color=blue]wxPython docs[/color]](http://www.wxpython.org/docs/api/wx.FileDialog-class.html) or the Demo code.

I am creating a [color=red]wx.FileDialog[/color] to open a file type.  I understand that on Linux systems ".txt" and ".TXT" are different, but I want to be able to display both at the same time in the dialog.  Currently I have to chose to display either ".txt" or ".TXT".

[php]wildcard = "Text File|*.txt" \ #I want only one entry for both .txt & .TXT
           "Text File|*.TXT" \ #instead of having to chose one or the other

dia = wx.FileDialog(self, "Select a File", os.getcwd(), "", wildcard)
[/php]

---

### Post by dodle on 2010-04-12
Found the answer thanks to avisser from [python-forum.org](python-forum.org):
[quote="avisser"]Did you try```
wildcard = "Text File|*.txt;*.TXT"
```?[/quote]

---

