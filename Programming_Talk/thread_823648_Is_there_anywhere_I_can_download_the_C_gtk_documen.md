---
title: "Is there anywhere I can download the C gtk documentation?"
date: 2008-06-09
forum: Programming Talk
---

### Post by days_of_ruin on 2008-06-09
I don't fell like reading online so is there a tarball somewhere I can download?I have googled and have still not found anything.

---

### Post by MicahCarrick on 2008-06-09
When you install the gtk2.0-doc package, then the GTK+ documentation is installed on your system to somewhere like /usr/share/doc.

However, a better method is to use Devhelp, the developer's help browser. You can search or browse and links to jump to the appropriate help manual page. It will allow you to browse all the APIs for packages with -doc suffix. So, try this;

```
sudo aptitude install devhelp libgtk2.0-doc libglib2.0-doc
```

You'll want to install the package-doc for any other libraries you are working with.

---

### Post by mike_g on 2008-06-09
Theres a good free GTK ebook here; [http://developer.gnome.org/doc/GGAD/](http://developer.gnome.org/doc/GGAD/)Theres a link with a tarball version at the bottom of the page.
The GTK reference manual is also handy for looking things up: [http://library.gnome.org/devel/gtk/unstable/index.html](http://library.gnome.org/devel/gtk/unstable/index.html)

---

