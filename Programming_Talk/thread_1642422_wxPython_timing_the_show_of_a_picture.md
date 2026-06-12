---
title: "wxPython: timing the show of a picture"
date: 2010-12-10
forum: Programming Talk
---

### Post by vmsda on 2010-12-10
I am writing this small GUI appl in Python (for a child), and would like to show a picture for a second or two, but have not managed to find a satisfactory solution.

I have tried something like:
   - pic.Show()
   - wx.Sleep(5)
   - pic.Destroy()

The problem seems to be that before the picture actually comes on screen the system executes the sleep function and then the picture is destroyed.

Could anyone please suggest a more imaginative and workable approach? Thank you in advance.

---

### Post by Arndt on 2010-12-10
> **vmsda said:**
> I am writing this small GUI appl in Python (for a child), and would like to show a picture for a second or two, but have not managed to find a satisfactory solution.

I have tried something like:
   - pic.Show()
   - wx.Sleep(5)
   - pic.Destroy()

The problem seems to be that before the picture actually comes on screen the system executes the sleep function and then the picture is destroyed.

Could anyone please suggest a more imaginative and workable approach? Thank you in advance.

You can use the timer event functions (the wx.Timer class).

---

### Post by vmsda on 2010-12-10
> **Arndt said:**
> You can use the timer event functions (the wx.Timer class).
Thank you for your prompt reply, Arndt. I tried but could not get it to do what I needed. Is there a sample somewhere, I wonder (even in metalanguage).

---

