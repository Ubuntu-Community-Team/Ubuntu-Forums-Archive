---
title: "Black screen when restarting computer"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by mdavis1231 on 2012-01-05
When I restart my computer, and instead of directly loading Ubuntu, I get a black screen that says:

Ubuntu 10.04 LTS xxxxxxxx-pc TTY1

xxxxxxxxxx-pc desktop login:

Is there any way to log in from this screen, or do I have to wait for it to release for my Ubuntu to then load?  It only stays on that screen for about 1 minute.

---

### Post by Sigma1 on 2012-01-05
What does it do after a minute, shut down again, or boot up as usual?
Otherwise, you can log in, without a graphical interface. Once you've logged in, you might be able to try the command "startx" (perhaps "sudo startx") to get the graphics running properly. That worked once for me.
That said, the symptoms are not normal, and suggest an installation problem, a problem with the graphics card recognition or perhaps, if the machine boots normally after a minute, a quirky grub configuration, but I'm guessing a bit!

---

### Post by mdavis1231 on 2012-01-17
> **Sigma1 said:**
> What does it do after a minute, shut down again, or boot up as usual?
Otherwise, you can log in, without a graphical interface. Once you've logged in, you might be able to try the command "startx" (perhaps "sudo startx") to get the graphics running properly. That worked once for me.
That said, the symptoms are not normal, and suggest an installation problem, a problem with the graphics card recognition or perhaps, if the machine boots normally after a minute, a quirky grub configuration, but I'm guessing a bit!

It doesn't shut down again, but yes, after a minute, Ubuntu loads as usual.  I guess this is just something I have to put up with when it happens, which is not that often.  Thanks!!!

---

