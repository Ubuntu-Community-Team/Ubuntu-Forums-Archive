---
title: "How do i create help files?"
date: 2011-01-30
forum: Programming Talk
---

### Post by dozy on 2011-01-30
Hi Everyone,

I'm just wondering if someone can point me to some info for creating my own help files.
I don't mean man pages, i mean HTML help.

1. What help system does Ubuntu use (when you press F1)?
2. What type of files does it use?
3. What program(s) can i use to create/compile this type of help file?

Thanks for your time!

---

### Post by SaintDanBert on 2011-01-30
Start by learning how to write good "man pages". open a terminal window (shell) and start with **man man** and then look at [http://www.schweikhardt.net/man_page_howto.html](http://www.schweikhardt.net/man_page_howto.html)

Next I'd read at the Linux Documentation Project
[http://tldp.org/manpages/man.html](http://tldp.org/manpages/man.html)

You can also find various per-package and per-distro and GNU-in-general guidelines for writing documentation.

I'm a technical writer and will help however I can.

Cheers,
~~~ 0;-Dan

---

### Post by hakermania on 2011-01-30
Without any knowledge, I think that these help files are under /usr/share/gnome/help/

---

### Post by Zugzwang on 2011-01-30
> **dozy said:**
> 1. What help system does Ubuntu use (when you press F1)?

The problem is that the answer to this question is not well-defined. Programs in Ubuntu can use any help system they like. Typically, GNOME programs use the gnome help system whereas QT programs use the one from QT. 

See here for QT stuff: [http://doc.qt.nokia.com/4.7/examples-helpsystem.html](http://doc.qt.nokia.com/4.7/examples-helpsystem.html)

See here for GNOME help: [http://library.gnome.org/users/user-guide/2.30/yelp](http://library.gnome.org/users/user-guide/2.30/yelp)

---

