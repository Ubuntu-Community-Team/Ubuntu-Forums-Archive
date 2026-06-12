---
title: "wxPython key down events"
date: 2008-12-19
forum: Programming Talk
---

### Post by ResilientBiscuit on 2008-12-19
Does anyone know why, in a program wx.EVT_KEY_UP would work but wx.EVT_KEY_DOWN will not work?  I am using Python 2.5 with wxPython.

If I bind my frame to a key up event, it works just fine when I release the key.  But if I directly replace the EVT_KEY_UP with EVT_KEY_DOWN it does not work when I press the key.

Also noteworthy, is that the EVT_KEY_DOWN binding works just fine windows.

The code is on my laptop, so I can post it when I get home, but it seems like there may be a more general answer.

Thanks
Justin

---

### Post by stevescripts on 2008-12-20
I don't use wxPython, but I will venture a guess here ...

Many (most?) gui toolkits have existing bindings for key down in many cases,
so it is often better to bind on key up, rather than to have to sort out and program around key down events ...

And the difference between windows and other OS is wm related (in fact,
a different wm on the linux side might solve the issue)

Just a SWAG ;)

Steve

---

### Post by iQuizzle on 2008-12-21
hm sounds maybe like a case where you need to use event.skip() in an event function somewhere. post your code.

---

