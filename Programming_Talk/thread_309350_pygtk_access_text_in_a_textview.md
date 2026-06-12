---
title: "pygtk: access text in a textview"
date: 2006-11-29
forum: Programming Talk
---

### Post by Ubuntuud on 2006-11-29
Hi,
I'm creating a program with pygtk.
It's my first serious one. But I'm running into some problems with textview. I have the following code.

```
sw = gtk.ScrolledWindow();
		sw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC);
		textview = gtk.TextView();
		sw.add(textview);
```

Now I would like to access the text in the textview to save it.
And to open saved files.
How can I do that? I think I have to do something with textbuffers, but I don't know what.

Could anyone give an example? Thanks in advance!

---

### Post by bradleyd on 2006-11-29
you can look here [http://www.moeraki.com/pygtktutorial/pygtk2tutorial/ch-TextViewWidget.html]("http://www.moeraki.com/pygtktutorial/pygtk2tutorial/ch-TextViewWidget.html")
there is a textview example.

---

### Post by ohgod on 2006-11-29
I believe textview widgets have get_text() and set_text() functions to manipulate the text in the widget.

---

### Post by Ubuntuud on 2006-11-30
OK. Thanks to the both of you!

---

### Post by moephan on 2006-11-30
You'll notice in the tutorial that to manipulate text in a textview, you get the textbuffer for the textview:

buffer = textview.get_buffer()

and then you can do all sorts of stuff, particularly deleting and inserting text, etc...

buffer.insert_at_cursor(text)

Cheers, Rick

---

