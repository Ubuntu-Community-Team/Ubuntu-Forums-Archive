---
title: "Python syntax highlighting"
date: 2009-01-10
forum: Programming Talk
---

### Post by matmatmat on 2009-01-10
Is there a way to make text entries in a python gui toolkit highlight python syntax?

---

### Post by kostkon on 2009-01-10
Yes, I think you'll need to use a [*PyGtkSourceView*]("http://projects.gnome.org/gtksourceview/pygtksourceview.html") widget for that.

Here is [the reference manual]("http://www.pygtk.org/pygtksourceview/index.html"). 

The package you need to install is the [*python-gtksourceview2*]("http://packages.ubuntu.com/search?keywords=python-gtksourceview2&searchon=names&suite=all&section=all").

---

### Post by matmatmat on 2009-01-10
How do you use it?

---

### Post by kostkon on 2009-01-10
Oh, wait, I may have misunderstood your question. What do you want to do exactly?

Basically, I thought you mean that you are making a GUI application and you want a text widget that is able to highlight code.

---

### Post by matmatmat on 2009-01-10
I was thinking of making an editor that could highlight code (like in gedit strings are pink). But I wanted to make sure it was possible with mys (basic) programming skills - thanks for the response.

---

### Post by kostkon on 2009-01-10
> **matmatmat said:**
> I was thinking of making an editor that could highlight code (like in gedit strings are pink). But I wanted to make sure it was possible with mys (basic) programming skills - thanks for the response.
OK.

Eh, there aren't many resources on the net about this, I am afraid.

But for a start you could check [this short tutorial]("http://www.progbox.co.uk/wordpress/?p=300") to get an idea. Then combine it with the reference manual and try to make your own. I think with a little experimenting and some study of the manual you will be fine.

---

### Post by tomasd on 2009-01-10
I have similar problem (I think similar enough not to create another post)
I'm trying to enable python syntax highlight on gedit. I have python-gtksourceview2 installed on my laptop, if I go to gedit preferences there's no syntax highlight tab available. What do I need to do to enable syntax highlight on gedit?

---

### Post by tomasd on 2009-01-10
found gedit highlight on view -> highlight mode...

---

### Post by matmatmat on 2009-01-10
I found a gtksourceview example in:
```

/usr/share/doc/python-gtksourceview2/examples/

```

---

