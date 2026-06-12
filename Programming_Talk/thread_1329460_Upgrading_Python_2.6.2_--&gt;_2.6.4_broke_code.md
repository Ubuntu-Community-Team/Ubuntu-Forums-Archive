---
title: "Upgrading Python 2.6.2 --&gt; 2.6.4 broke code?"
date: 2009-11-17
forum: Programming Talk
---

### Post by rob86 on 2009-11-17
I was working on my first python app and I had to upgrade to 2.6.4 by compiling it because 2.6.2 was buggy with Tix. 

My code works fine on 2.6.2, but when I use 2.6.4, weird things happen. First of all ,my simple Tkinter app had a dramatic change in appearance. Different fonts, grey form backgrounds instead of white, thinner forms, fatter scrollbars. When I revert to 2.6.2, it goes back to normal, or at least what I thought was normal (to me, it looks more like a modern gui on 2.6.2)

Second of all, my code raises this error:

```
  File "/usr/local/lib/python2.6/smtplib.py", line 615, in starttls
    raise RuntimeError("No SSL support included in this Python")
RuntimeError: No SSL support included in this Python

```

What's going on here?

---

### Post by meson2439 on 2009-11-19
Maybe it means what it says. Try loading the library one by one in interactive mode.

---

### Post by casevh on 2009-11-19
If you compile Python yourself, you'll need to install some development libraries. You need to install libssl-dev to fix this error. You probably want to install readline6-dev and probably others. IIRC, after you run make, it will list which modules it couldn't build because the required development libraries aren't present.

I think you should also specify --enable-unicode=ucs4 to match the standard Python shipped by Ubunutu.

HTH,

casevh

---

