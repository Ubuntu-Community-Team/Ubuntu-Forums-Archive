---
title: "what is php5 gtk?"
date: 2009-12-03
forum: Programming Talk
---

### Post by kapi on 2009-12-03
Just read a thread and didn't want to hijack it, I've scoured the net (OK google) and have got a rough idea of what it does but am still a bit unclear.

are there any other links people could suggest.

[http://php-gtk.eu/](http://php-gtk.eu/)

seems the main site to look at - but I like peoples input

I am kind of excited that this exists (if it's as good as I hope)

what do you use php5 gtk for?

thanks for your time

---

### Post by wojox on 2009-12-03
It's an extension of php that hat implements language bindings for Gimp Tool Kit. Look at this site:

[http://gtk.php.net/](http://gtk.php.net/)

---

### Post by laceration on 2009-12-03
The idea is that PHP, being a hugely popular web programming language, could also be used as a language for desktop apps.  PHP-GTK makes this possible.   PHP-GTK never gained too much traction though.  I think it got usurped by the idea of a web app, where the browser itself is the ui. PHP is very naturally is suited to web apps, but I question whether being a good web language necessarily translates to the traditional desktop app.

---

### Post by nvteighen on 2009-12-03
GTK+ is the GUI toolkit library which was developed for the GNOME project. It is the one used in almost all GNOME applications, but it can be used in any other Desktop Environment. A GTK+ application can be used on KDE; the issue is that it will usually look really bad.

GTK+ is a C library, so it only can be used in C or languages that allow you interface with C code in some way. Usually, what you need is a wrapper around your language's "Foreign Function Interface" or "Native Interface" so the calls to GTK+ are "incorporated" into your language of choice in a way consistent with that language's ways. That's what's called a "binding"; and PHP5 GTK+ is one of them... but there are also several other bindings for GTK+ (PyGtk for Python, Gtk# for C#, Perl-GTK+, etc.)

---

