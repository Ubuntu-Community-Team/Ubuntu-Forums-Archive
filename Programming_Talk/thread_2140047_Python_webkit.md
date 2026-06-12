---
title: "Python webkit"
date: 2013-04-28
forum: Programming Talk
---

### Post by Fxy on 2013-04-28
HI everyone

Using python I am trying to create a webview that loads a defined webpage.

```
 [FONT=monospace]#!/usr/bin/env python[/FONT]import gtk
import webkit
import gobject
gobject.threads_init()
win = gtk.Window()
bro = webkit.WebView()
bro.open("http://www.google.com")
win.add(bro)
win.show_all()
[FONT=monospace]gtk.main() [/FONT]
```

However whenever I try to execute inside terminal I get the following error...

```
 cd '/Volumes/Terminal/Terminal101/Porgramming/LaurenBrowser/' && '/usr/bin/pythonw'  '/Volumes/Terminal/Terminal101/Porgramming/LaurenBrowser/Laurenbrowser101.py'  && echo Exit status: $? && exit 1Furycd001:~ Furycd001$ cd '/Volumes/Terminal/Terminal101/Porgramming/LaurenBrowser/' && '/usr/bin/pythonw'  '/Volumes/Terminal/Terminal101/Porgramming/LaurenBrowser/Laurenbrowser101.py'  && echo Exit status: $? && exit 1
Traceback (most recent call last):
  File "/Volumes/Terminal/Terminal101/Porgramming/LaurenBrowser/Laurenbrowser101.py", line 4, in <module>
    import webkit
ImportError: No module named webkit
Furycd001:LaurenBrowser Furycd001$ 
``` 

I have tried on both debian, ubuntu & osx getting the same error output on all 3 systems. Anyone any help or ideas :?

---

### Post by oldfred on 2013-04-28
Have you installed the webkit support files.

I am using qt even with gnome, but I seem to have also installed gtk support files also.
[http://www.rkblog.rk.edu.pl/w/p/webkit-pyqt-rendering-web-pages/](http://www.rkblog.rk.edu.pl/w/p/webkit-pyqt-rendering-web-pages/)

Look in synaptic for webkit.
I have libwebkitgtk as well as several others that look like they are for gtk. I then have some for qt and java.

---

### Post by Fxy on 2013-04-28
> **oldfred said:**
> Have you installed the webkit support files.

I am using qt even with gnome, but I seem to have also installed gtk support files also.
[http://www.rkblog.rk.edu.pl/w/p/webkit-pyqt-rendering-web-pages/](http://www.rkblog.rk.edu.pl/w/p/webkit-pyqt-rendering-web-pages/)

Look in synaptic for webkit.
I have libwebkitgtk as well as several others that look like they are for gtk. I then have some for qt and java.

I have verified that I do have webkit installed on both debian & ubuntu systems. I have also followed steps for installing gtkwebkit files on my mac. Have tried looking on google, but anything I find is of no help thus me posing here...

---

### Post by oldfred on 2013-04-28
I then had to install python-webkit

status installed python-webkit 1.1.8-2ubuntu2

And this worked.

```
  #!/usr/bin/env python
import webkit
import gobject
import gtk

gobject.threads_init()
win = gtk.Window()
bro = webkit.WebView()
bro.open("http://www.google.com")
win.add(bro)
win.show_all()
gtk.main()

```

---

### Post by Fxy on 2013-04-29
Thank you that seemed to do the trick nicly :)

---

