---
title: "No gdk-2.0 and gthread-2.0 in repos"
date: 2012-08-23
forum: Repositories &amp; Backports
---

### Post by larzconwell on 2012-08-23
I'm checking out a go package called go-gtk [https://github.com/mattn/go-gtk](https://github.com/mattn/go-gtk)

That has bindings for GTK. But to install I need some gtk dev packages, I've found most of them but I can't find gdk-2.0 or gthread-2.0. I read somewhere that gthread is included with libglib-2.0, but it's still error-ing even though it's installed.

What are the packages name in the repos for gdk and gthread??

```

%:~ &#11607; go get github.com/mattn/go-gtk/gtk
# pkg-config --cflags gdk-2.0 gthread-2.0
Package gdk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gdk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gdk-2.0' found
exit status 1

```

---

### Post by MadCow108 on 2012-08-25
the pkgconfig files are, along with the headers, in the libgtk2.0-dev and libglib2.0-dev packages

---

### Post by larzconwell on 2012-08-25
Thanks so much! libgtk2.0-dev was the package I needed

---

