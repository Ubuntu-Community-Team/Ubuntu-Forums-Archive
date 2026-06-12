---
title: "BrainWorkshop [python] totally fails to launch"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by zediks on 2012-10-26
Hello!
I am trying to run brainworkshop:
[http://brainworkshop.sourceforge.net/](http://brainworkshop.sourceforge.net/)

and I got an error:

python brainworkshop.pyw 
Traceback (most recent call last):
  File "brainworkshop.pyw", line 868, in <module>
    window = MyWindow(cfg.WINDOW_WIDTH, cfg.WINDOW_HEIGHT, caption=''.join(caption), style=style, vsync=VSYNC)
  File "/home/zediks/EPD/lib/python2.7/site-packages/pyglet/window/xlib/__init__.py", line 474, in __init__
    super(XlibWindow, self).__init__(*args, **kwargs)
  File "/home/zediks/EPD/lib/python2.7/site-packages/pyglet/window/__init__.py", line 641, in __init__
    raise NoSuchConfigException('No standard config is available.')
pyglet.window.NoSuchConfigException: No standard config is available.

I have found some tips in google groups:
[link]("https://groups.google.com/forum/?fromgroups=#!topic/brain-training/FxTe4KKKnXM")

But I still didn't manage to fix it.

Any help is appreciated.

---

### Post by drmrgd on 2012-10-26
I just tried it out on my system, and got the same exact error.  I also tried it with Python 3.2, and that doesn't seem to help.  You may have to contact the developer on this one as it seems it won't run in Ubuntu due to either a conflict with the way Python is implemented (unlikely) or a problem with their code.

---

### Post by zediks on 2012-10-29
Thanks!
Done. I've sent them a message.

---

