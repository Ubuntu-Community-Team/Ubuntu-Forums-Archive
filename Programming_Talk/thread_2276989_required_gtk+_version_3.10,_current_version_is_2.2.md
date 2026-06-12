---
title: "required gtk+ version 3.10, current version is 2.24"
date: 2015-05-06
forum: Programming Talk
---

### Post by ikki_72 on 2015-05-06
I have libgtk-3-0 but  python claims that I'm using version 2

```
$ python glade1.py 
Traceback (most recent call last):
  File "glade1.py", line 24, in <module>
    main = Buglump()
  File "glade1.py", line 18, in __init__
    self.builder.add_from_file(self.gladefile)
glib.GError: tutorial-1.glade: required gtk+ version 3.10, current version is 2.24

$ sudo dpkg --get-selections | grep libgtk-3
libgtk-3-0:amd64				install
libgtk-3-bin 					install
libgtk-3-common					install
libgtk-3-dev					install
libgtk-3-doc					install

$ sudo apt-cache show libgtk-3-0 | grep "Version:"
Version: 3.10.8-0ubuntu1.4
Version: 3.10.8-0ubuntu1
```

ubuntu 14.04 amd64

---

### Post by ofnuts on 2015-05-06
You likely have both versions of gtk, and your pygtk module is linked to gtk2. Try:
```

print pygtk._get_available_versions()

```

The [PyGTK page]("http://www.pygtk.org/") says that you have to use the PyGObject module instead of PyGTK is you want GTK3.

---

### Post by ikki_72 on 2015-05-06
where do I put that line?

```
$ print pygtk._get_available_versions()
bash: syntax error near unexpected token `('

$ python
Python 2.7.6 (default, Mar 22 2014, 22:59:56) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print pygtk._get_available_versions()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'pygtk' is not defined
>>>
```

I referred to article from [http://gnipsel.com/glade/glade01b.html](http://gnipsel.com/glade/glade01b.html) to learn GTK GUI

---

### Post by ofnuts on 2015-05-07
After an "import pygtk" :)

---

