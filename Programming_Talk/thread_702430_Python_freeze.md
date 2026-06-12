---
title: "Python freeze"
date: 2008-02-20
forum: Programming Talk
---

### Post by cmat on 2008-02-20
I'm currently working on an application that uses a GUI interface. When I run the code- os.system("command") the interface locks up until I terminate the application that was called? Any way to get around this?

---

### Post by LaRoza on 2008-02-20
Use threads.

---

### Post by cmat on 2008-02-20
I was afraid of that. I'm trying that but I'm having no luck. I'll continue some more and I'll post back when I'm really stuck.

---

### Post by strider1551 on 2008-02-20
I remember running into a problem like that when working with wxPython.  The gui would lock until the function called by the event finished.  I believe tossing in a wx.Yield() did the trick.

---

### Post by cmat on 2008-02-21
> **strider1551 said:**
> I remember running into a problem like that when working with wxPython.  The gui would lock until the function called by the event finished.  I believe tossing in a wx.Yield() did the trick.

Interesting, is there an equivalent in GTK+?

---

### Post by strider1551 on 2008-02-21
> Interesting, is there an equivalent in GTK+?

I've only worked with wxPython.  The documentation for wx.Yield() is [here]("http://wxwidgets.org/manuals/stable/wx_wxapp.html#wxappyield"). Perhaps the description will give you an idea of where to look in your documentation.  Best of luck!

---

