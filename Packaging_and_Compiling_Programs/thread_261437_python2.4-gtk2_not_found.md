---
title: "python2.4-gtk2 not found"
date: 2006-09-20
forum: Packaging and Compiling Programs
---

### Post by subscr on 2006-09-20
Running Dapper 6.0.6

When running configure for a product compilation, I am getting the following error.

checking for python2.4-gtk2... Package python2.4-gtk2 was not found in the pkg-config search path. Perhaps you should add the directory containing `python2.4-gtk2.pc' to the PKG_CONFIG_PATH environment variable No package 'python2.4-gtk2' found
configure: error: Library requirements (python2.4-gtk2) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

Checking for Python-gtk, it appears to be installed. Any help would be appreciated.

# dpkg -l | grep python | grep gtk
ii  python-gtk-1.2                         0.6.12-4ubuntu1    GTK support module for Python
ii  python-gtk2                            2.8.6-0ubuntu1    Python bindings for the GTK+ widget set
ii  python-wxgtk2.6                        2.6.1.2ubuntu2    wxWidgets Cross-platform C++ GUI toolkit (wx
ii  python2.4-gtk2                         2.8.6-0ubuntu1    Python bindings for the GTK+ widget set

---

### Post by mlind on 2006-09-28
What are you trying to compile?

---

