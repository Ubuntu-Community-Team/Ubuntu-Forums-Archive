---
title: "Errors from first wxpython app"
date: 2011-12-11
forum: Programming Talk
---

### Post by memilanuk on 2011-12-11
Hello,

I have a 'fresh' install of Ubuntu 11.10, installed 'Quickly' so I'm fairly sure all the wxpython and GTK stuff should have been pulled in along with... but when I went to run a first wxpython 'Hello World' app (not involving quickly in any way), I get four of these error printouts in the terminal window:

```

(python:24504): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


```

Here is the code that was ran:

[php]
import wx

class MyApp(wx.App):
    def OnInit(self):
        wx.MessageBox("Hello wxPython", "wxApp")
        return True

if __name__ == "__main__":
    app = MyApp(False)
    app.MainLoop()
[/php]

Any ideas whats causing the error messages?

TIA,

Monte

---

### Post by dodle on 2011-12-11
I get those warnings all the time. It's not an issue with wxPython, but with Gtk. It sounds like Gtk is looking for a piece of the system theme that is missing. I don't think it is anything to worry about. Try switching themes and see if you still get the warning.

---

### Post by memilanuk on 2011-12-11
...then maybe I'm looking at this wrong, because imho with default packages on a fresh install there shouldn't be any error messages from something as main stream as wxpython or gtk.  Sounds like the ubuntu version of things is broken (again).

---

### Post by pbrane on 2011-12-11
> **memilanuk said:**
> ...then maybe I'm looking at this wrong, because imho with default packages on a fresh install there shouldn't be any error messages from something as main stream as wxpython or gtk.  Sounds like the ubuntu version of things is broken (again).

On xubuntu 11.10 I installed python-wxgtk2.8 and then ran your app. I don't get any errors at all.

---

### Post by memilanuk on 2011-12-11
okay... *thats* weird.

I ran the script on another computer; another one that is a fairly fresh 11.10 install, also with wx and gtk installed (again, by installing quickly to pull in everything) and it ran with no issues.

So now the question is... whats different on this one laptop?

---

### Post by cgroza on 2011-12-11
Don't worry about it. The problem is not on your side and there is nothing your program can do about it.
Those are just warnings, not errors.

---

### Post by Arndt on 2011-12-11
> **memilanuk said:**
> ...then maybe I'm looking at this wrong, because imho with default packages on a fresh install there shouldn't be any error messages from something as main stream as wxpython or gtk.  Sounds like the ubuntu version of things is broken (again).

I share your opinion, but in practice, I find that programs that create windows and don't read anything from the terminal where they were started typically emit lots of mysterious warning messages (gtk, vlc, openoffice, acroread, etc.). Why the developer didn't stop them from appearing isn't clear to me - a program of mine wouldn't do this, if I could at all avoid it.

---

