---
title: "download manager in gtk+."
date: 2010-03-13
forum: Programming Talk
---

### Post by khatkarrohit on 2010-03-13
Hi, I am learning GTK+. I have to submit a project. I am thinking to make a simple download manager.
I would like to know what other libraries to use for http and ftp and some other type of help like a guidence to start working on it.
I have two months to make it. Is it possible to complete it in two months. Please help me.

---

### Post by BenAshton24 on 2010-03-13
> **khatkarrohit said:**
> Hi, I am learning GTK+. I have to submit a project. I am thinking to make a simple download manager.
I would like to know what other libraries to use for http and ftp and some other type of help like a guidence to start working on it.
I have two months to make it. Is it possible to complete it in two months. Please help me.

I would suggest that you go with libcurl ([http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/)) since it supports numerous protocols and is fairly simple to use. If it's not what you're looking for then there is a list of other libraries here:
[http://curl.haxx.se/libcurl/competitors.html](http://curl.haxx.se/libcurl/competitors.html)

You will also probably need a decent knowledge of threading but apart from that it should be relatively straight forward. If you are very new to GTK+ then I would recommend doing something a bit easier since it will get pretty confusing updating the GUI from your worker thread which will be especially difficult to manage if you are still getting used to things.

Good luck.
Ben.

---

### Post by khatkarrohit on 2010-09-03
thanks.......for the help..i made a little application.and my teacher was satisfied as it runs on linux...

---

### Post by SledgeHammer_999 on 2010-09-03
If you want to go a little bit low-level you could have a look at GIO's network capabilities(part of gtk)-->[http://library.gnome.org/devel/gio/stable/](http://library.gnome.org/devel/gio/stable/)
It's design makes it a little easier to NOT use multiple threads and update the main/gui thread.

---

