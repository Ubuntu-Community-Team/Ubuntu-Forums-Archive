---
title: "Where are the Python info files?"
date: 2009-06-23
forum: Programming Talk
---

### Post by mrc23 on 2009-06-23
What's the easiest way to get Python's texinfo documentation into Ubuntu (/usr/share/info)?

Is there a package with the info files prebuilt? Or, should I apt-get sources python and build my own? Or are they just floating around somewhere ready to be downloaded?

(I've had no luck searching with google, on the Ubuntu wiki and forums, on python.org, even in likely places like emacswiki.)

/usr/share/python2.6/copyright implies texinfo files exist, but I can't find them.

---

### Post by ssam on 2009-06-23
does it have to be the info pages? if html is ok try the python-doc package. then start at /usr/share/doc/python2.6/html/index.html

if you need to read them from the command line use lynx or w3m. i prefer to use devhelp

---

### Post by mrc23 on 2009-06-23
Yup - it has to be info pages, so I can read it in emacs. I can find the html pages, but w3m (even w3m in emacs) is a lot less useful than info.

---

### Post by mrc23 on 2009-06-24
Answering my own question: It seems Python 2.6, when it switched to a new documentation format, dropped support for making info files out of the box.

I'm currently looking for alternatives, currently the most likely is using pandoc to convert the documentation from native rst format to texi. The version in the Jaunty repos is 0.46 from early 2008, but since 1.0 in September 2008 it's supported texi as an output format, then I can use makeinfo to take it from there.

---

### Post by Can+~ on 2009-06-24
> **mrc23 said:**
> Answering my own question: It seems Python 2.6, when it switched to a new documentation format, dropped support for making info files out of the box.

I'm currently looking for alternatives, currently the most likely is using pandoc to convert the documentation from native rst format to texi. The version in the Jaunty repos is 0.46 from early 2008, but since 1.0 in September 2008 it's supported texi as an output format, then I can use makeinfo to take it from there.

Python switched to [Sphinx]("http://sphinx.pocoo.org/") to handle it's documentation.

And I tried using sphinx and it's pretty nice, you can also generate LaTeX documents, maybe there's some plugin to create texi?

---

