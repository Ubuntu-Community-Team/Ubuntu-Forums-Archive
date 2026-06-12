---
title: "[Python]displaying gzipped webpages stored locally"
date: 2010-03-30
forum: Programming Talk
---

### Post by Jordanwb on 2010-03-30
I want to clone a Windows app mainly to learn Python. This app has series of books and each book's chapters will be in its own html file (each book will have its own folder). But to save space I want to Gzip compress each HTML file. How would I go about embedding a web browser into my pygtk app and have it open the gzipped html files?

I found this: [http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html](http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html) but it's fairly out of date and refers to PyGtkMoz which is no longer maintained.

---

### Post by myrtle1908 on 2010-03-30
> **Jordanwb said:**
> I want to clone a Windows app mainly to learn Python. This app has series of books and each book's chapters will be in its own html file (each book will have its own folder). But to save space I want to Gzip compress each HTML file. How would I go about embedding a web browser into my pygtk app and have it open the gzipped html files?

I found this: [http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html](http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html) but it's fairly out of date and refers to PyGtkMoz which is no longer maintained.

There are most likely Python bindings for WebKit, maybe GTK or Qt.  Look around.

---

### Post by diesch on 2010-03-30
In [http://aciresnippets.wordpress.com/](http://aciresnippets.wordpress.com/) there's a snippet that creates a simple web brwoswer using Webkit/Gtk

But I don't know how to make it open gzipped HTML files.

---

