---
title: "TK with python 2.5 isn't &quot;native?!&quot;"
date: 2008-03-02
forum: Programming Talk
---

### Post by irrdev on 2008-03-02
TK versions 8.0 and newer are supposed to look native when running on Windows, Linux and the Mac. However, my default Python 2.5 installation runs TK using an absolutely awful theme.  I have posted two screenshots to demonstrate what I mean. What can I do to fix this? I use wxPython for large gui applications, but for simple interfaces I wish to use TK- is there a solution to the theme problem?

---

### Post by scooper on 2008-03-02
This isn't very helpful.  But I've always found Tk apps to look and function non-natively, and to be ugly.  I don't think Tk claims to provide native look and feel, but could (easily) be wrong.  I hope I'm not misleading you.

---

### Post by pmasiar on 2008-03-02
IIUC it wxWidgets what claims to look native, not Tk. But I am definitely not an expert on GUI, so...

---

### Post by stevescripts on 2008-03-02
For what it's worth, the de-uglification of Tk is being actively developed.

I dont not know for sure whether Tkinter supports tcl/tk 8.5, which includes
a newer widget set (previously called Tile).

I *will* get the answer within the next day or so.

Personally, I am *so* old, that I am still *thrilled* by computer output on anything
other than green/white bar paper ...

Steve
(Heavy Tk user)

---

### Post by LaRoza on 2008-03-02
> **stevescripts said:**
> For what it's worth, the de-uglification of Tk is being actively developed.

I dont not know for sure whether Tkinter supports tcl/tk 8.5, which includes
a newer widget set (previously called Tile).

I *will* get the answer within the next day or so.

Personally, I am *so* old, that I am still *thrilled* by computer output on anything
other than green/white bar paper ...

Steve
(Heavy Tk user)

I look forward to Tk looking pretty, but as long as it works, I am happy with it.

---

### Post by stevescripts on 2008-03-02
> **LaRoza said:**
> I look forward to Tk looking pretty, but as long as it works, I am happy with it.

Me too!

Steve
(I forgot to mention, that you can do a lot with the option 
database, to make Tk (from 8.0 thru 8.4) look more like
you might want)

---

### Post by irrdev on 2008-03-03
I hunted up an image of Tkinter runnong on Windows 2000. The widgets are not 100% native looking, although they are very close. In comparison, TKinter on Linux is totally unbearable.
[IMG]http://www.oreilly.com/catalog/pythonwin32/chapter/ppw.2003.gif[/IMG]

---

### Post by stevescripts on 2008-03-03
yep, it looks much better using default values on windoze (as does Tk)

I just spoke with one of the Tile (newer widgets for Tk) developers -
he is under the impression that Tkinter, built using tcl/tk 8.5 - should
provide access to the Tile widgets.  Although I have RubyTk using 8.5
and tile here, I dont have Tkinter built that way - and may not get around
to it for some time.

Maybe a post to some python group might provide insight on Tkinter
and Tk 8.5 ?

Steve

---

### Post by irrdev on 2008-03-04
I did a bit of searching, and TK 8.5 is slated to be released with Python 3.0. However, the new Tile theme engine only works for Windows and Mac OS X. Linux users are currently out of luck, although there has apparently been some discussion about making TKinter GDK themable. In the meantime, I guess that I am out luck. I'll probably keep on using wxPython, even though it means extra modules. Thanks for all of your help on this issue!

---

