---
title: "'if edited' with python"
date: 2009-02-07
forum: Programming Talk
---

### Post by cyclobs on 2009-02-07
hey guys,

trying to learn python here and i'm making a text editor. is there a way to make python see if the opened file was edited.

eg: user starts up the program with blank page and then types something

---

### Post by Tony Flury on 2009-02-07
I think your application will need to keep track of when the user makes any changes.

---

### Post by ssam on 2009-02-07
inotify lets your application ask to be notified when a file changes. there seems to be a pyinotify that you can use from python.

or maybe you just want to check modification times, you can use os.path.getmtime see [http://docs.python.org/library/os.path.html](http://docs.python.org/library/os.path.html)

---

### Post by cyclobs on 2009-02-07
thanks guys i got it sorted :)

---

