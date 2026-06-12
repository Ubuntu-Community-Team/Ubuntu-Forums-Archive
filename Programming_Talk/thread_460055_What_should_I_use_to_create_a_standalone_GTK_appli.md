---
title: "What should I use to create a standalone GTK application?"
date: 2007-05-31
forum: Programming Talk
---

### Post by PryGuy on 2007-05-31
Good day everyone!

I'm new to Linux programming so please forgive me for such a newbie question! ;)

I'm about to write an XML based GTK postinstaller tool that could parse XML file and perform installation using it's data. The question is, what language should I use to do it? One of the main requirements is that it should work with the out-of-the-box installation, so there would be no need to install extra packages to be able to run it. 

Thank you!

---

### Post by ankursethi on 2007-05-31
You can use Python. I think PyGTK works out of the box.

---

### Post by PryGuy on 2007-05-31
Are you sure because we install python after the base installation?

---

### Post by Tomosaur on 2007-05-31
Are you sure you really want to do this? There are very good reasons to use dependencies:

1) Stops system bloat.
2) Smaller downloads.
3) Easier system management.

---

### Post by PryGuy on 2007-05-31
Do what? Write a postinstall tool? ;)

---

### Post by ankursethi on 2007-06-01
Python works out of the box.

---

