---
title: "Python: Taking a screenshot"
date: 2007-05-18
forum: Programming Talk
---

### Post by musicinmybrain on 2007-05-18
I want to take a screenshot using Python. I can import and use any module necessary, and the solution can be platform-dependent. This seems like it should be simple using pygtk or something, but my Google-fu fails me. Any ideas?

---

### Post by earobinson on 2007-05-18
you could install a program like scrott, then just call that program from python

---

### Post by musicinmybrain on 2007-05-18
Aha! Yes, immediately after posting this it occurred to me I could just call ImageMagick (or scrot).

```
import os
os.system("import -window root temp.png")
```

Perfect! Thanks.

---

### Post by earobinson on 2007-05-18
sweet. Glad things are working.

---

### Post by WW on 2007-05-18
In case you ever want to do it without using system():
```

import gtk.gdk

w = gtk.gdk.get_default_root_window()
sz = w.get_size()
print "The size of the window is %d x %d" % sz
pb = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB,False,8,sz[0],sz[1])
pb = pb.get_from_drawable(w,w.get_colormap(),0,0,0,0,sz[0],sz[1])
if (pb != None):
    pb.save("screenshot.png","png")
    print "Screenshot saved to screenshot.png."
else:
    print "Unable to get the screenshot."

```

---

### Post by musicinmybrain on 2007-05-18
Now, that's nice, too! It's a good bit faster that invoking ImageMagick, as well. That's pretty much what I had originally thought I might be able to do, but hadn't been able to spelunk through the pygtk docs well enough to figure out. It's excellent to have two ways to do it.

I greatly appreciate the help from both of you.

---

### Post by Imagist on 2008-08-11
Sorry to revive this thread from the dead, but I'm looking for the EXACT same thing, except that my program needs to be cross-platform.  Obviously the system-based solution won't work, but what about the other one?  Does the GTK module come with Python for Windows or does it require a separate installation?  I would try this myself except that my laptop is currently down with its motherboard broken.

---

### Post by musicinmybrain on 2008-08-11
Unfortunately, installing PyGTK on Windows requires [four separate installations]("http://faq.pygtk.org/index.py?req=show&file=faq21.001.htp") for the GTK+ stack bundle, PyCairo, PyGobject and PyGTK. It's a bit of a pain, although it does work. If you're not using GTK+ for a GUI, it may be easier just to [use PIL to take the screenshot]("http://www.pythonware.com/library/pil/handbook/imagegrab.htm") on Windows.

---

### Post by days_of_ruin on 2008-08-11
> **musicinmybrain said:**
> Unfortunately, installing PyGTK on Windows requires [four separate installations]("http://faq.pygtk.org/index.py?req=show&file=faq21.001.htp") for the GTK+ stack bundle, PyCairo, PyGobject and PyGTK. It's a bit of a pain, although it does work. If you're not using GTK+ for a GUI, it may be easier just to [use PIL to take the screenshot]("http://www.pythonware.com/library/pil/handbook/imagegrab.htm") on Windows.

They would still have to install image magick otherwise.

---

### Post by musicinmybrain on 2008-08-12
> **days_of_ruin said:**
> They would still have to install image magick otherwise.

In which case?

---

### Post by lukerazor on 2009-12-10
I just came across this thread while looking for the same thing.  It seems that QT has a the ability to do this using the QPixmap object. see [this link]("http://doc.trolltech.com/4.2/desktop-screenshot.html") for a c++ example, easily converted to PyQT. (look for Screenshot::shootScreen() for the guts of taking the screenshot)

---

### Post by DomusMaximus on 2012-05-29
There is alwats the option of using a third party tool like [GrabzIt]("http://grabz.it") they have a good [Python API]("http://grabz.it/api/python/") that lets you do this quickly and easily for free.


  To take a screenshot just use:

```

import GrabzItClient

grabzIt = GrabzItClient.GrabzItClient("APPLICATION KEY", "APPLICATION SECRET")
id = grabzIt.TakePicture("http://www.google.com", "http://www.example.com/GrabzItHandler.py")

#Wait a certain amount of time

result = grabzIt.GetPicture(id)

if result != None:
    fo = open("images" + os.sep + filename, "wb")
    fo.write(result)
    fo.close()


```

---

