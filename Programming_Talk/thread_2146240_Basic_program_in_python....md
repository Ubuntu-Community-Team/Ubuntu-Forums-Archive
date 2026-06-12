---
title: "Basic program in python..."
date: 2013-05-17
forum: Programming Talk
---

### Post by Fxy on 2013-05-17
HI everyone

Basically I am trying to create a basic python program that will contain a few buttons that when clicked will take you to specified hardcoded urls. Heres the code that I have written...

```
[COLOR=#008D00][FONT=Menlo]#!/usr/bin/python
[/FONT][/COLOR][COLOR=#d200a5]import[COLOR=#000000] gtk[/COLOR][/COLOR]
[COLOR=#d200a5]import[/COLOR] pygtk
[COLOR=#d200a5]import[/COLOR] webbrowser


window = gtk.Window()
window.set_title([COLOR=#e90000]"Portal"[/COLOR])
[COLOR=#e90000][COLOR=#000000]button = gtk.LinkButton([/COLOR]"http://example.iana.org/"[COLOR=#000000], label=[/COLOR]"Button001"[COLOR=#000000])[/COLOR][/COLOR]
window.add(button)
window.show_all()


[FONT=Menlo]gtk.main()[/FONT]
```

My problem is that whenever my app loads, I click on the button but get the error shown below.

```
PythonLinks.py:14: GtkWarning: Unable to show 'http://example.iana.org/': Operation not supported  gtk.main()

```

I have tried running my app on 3 different machines. One running debian, another running ubuntu and finally a macbook. All three systems seem to produce the same error for some reason ?? If anyone could help me with this that would be totally awesome. Thanks in advance.

---

### Post by oldfred on 2013-05-18
I have my own application with a database to scroll thru a bunch of pages and changed from gtk to qt.

But I have these links and think I had a working browser as in first example with gtk.
[http://ardoris.wordpress.com/2009/04/26/a-browser-in-14-lines-using-python-and-webkit](http://ardoris.wordpress.com/2009/04/26/a-browser-in-14-lines-using-python-and-webkit)
[http://www.aclevername.com/articles/python-webgui/](http://www.aclevername.com/articles/python-webgui/)

---

### Post by r-senior on 2013-05-18
Before progressing much further, you should reconsider the use of pygtk. You should be using GObject introspection to access GTK.

The last post on this thread explains it very well:

[http://ubuntuforums.org/showthread.php?t=2092094](http://ubuntuforums.org/showthread.php?t=2092094)

---

### Post by Fxy on 2013-05-18
> **oldfred said:**
> I have my own application with a database to scroll thru a bunch of pages and changed from gtk to qt.

But I have these links and think I had a working browser as in first example with gtk.
[http://ardoris.wordpress.com/2009/04/26/a-browser-in-14-lines-using-python-and-webkit](http://ardoris.wordpress.com/2009/04/26/a-browser-in-14-lines-using-python-and-webkit)
[http://www.aclevername.com/articles/python-webgui/](http://www.aclevername.com/articles/python-webgui/)

Thanks for your reply.

If I use "[COLOR=#E90000][FONT=Menlo][COLOR=#000000]webbrowser.open([/COLOR]"http://example.iana.org/"[COLOR=#000000])" it automatically loads my default web browser with the specified page so I know the web browser part is working ok.



> Before progressing much further, you should reconsider the use of pygtk. You should be using GObject introspection to access GTK.

The last post on this thread explains it very well:

[http://ubuntuforums.org/showthread.php?t=2092094](http://ubuntuforums.org/showthread.php?t=2092094)

What would you consider replacing "pygtk" with ?? Would it be better to go and use "qt" or should I stick with "gtk ?? Thanks for mentioning "gobject" I have that imported at the top of my code now.[/COLOR][/FONT][/COLOR]

---

### Post by MG&amp;TL on 2013-05-18
I've quickly edited this to use GObject, and it works just fine. If you replace:

```

import gtk
import pygtk
```

with:

```
from gi.repository import Gtk
```

And then replace all *gtk* references with *Gtk*, it works. I can post source code if you like, but I thought you'd prefer to figure this one out yourself. :)

---

### Post by Fxy on 2013-05-18
> **MG&TL said:**
> I've quickly edited this to use GObject, and it works just fine. If you replace:

```

import gtk
import pygtk
```

with:

```
from gi.repository import Gtk
```

And then replace all *gtk* references with *Gtk*, it works. I can post source code if you like, but I thought you'd prefer to figure this one out yourself. :)

Thank you for your quick reply.

I tried using your code "from gi.repository import Gtk" from what you mentioned above, but now I get an import error.
```
ImportError: No module named gi.repository
```

---

### Post by Fxy on 2013-05-18
Got everything working. Thanks for all the help. Your commands didn't work at first but they seem to be working now for some reason...

---

