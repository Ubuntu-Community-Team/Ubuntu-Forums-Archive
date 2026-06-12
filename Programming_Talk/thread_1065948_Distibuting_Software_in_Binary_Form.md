---
title: "Distibuting Software in Binary Form"
date: 2009-02-10
forum: Programming Talk
---

### Post by MasterProg on 2009-02-10
I have written a program using GTK+ and GLib in C++. I want it to run on my subnotebook Acer Aspire One (it is running Linpus Linux). I copied binary executable and couldn't get it work, because it can't find libgio.so (as far as I know it's a part of GLib). I found out that there was an older version of GLib than on my Ubuntu box.

So, how do I make it work? How do I distribute software in binary form?

---

### Post by kknd on 2009-02-10
You do not =).

Well, to ensure library compatibility you should at least create a package for the system (if its a debian, create a .deb, etc) with the dependencies to let the user install then.

Don't ever think about statically-link all the libraries that a GTK+ 2 app needs.

* In my job, I have some clients using a pre-compiled binary, but I installed all the needed libraries, respecting the versions. It's a lot of work, specially if you can just delegate it to the package manager.

---

### Post by MasterProg on 2009-02-10
It's a Fedora-based distribution. I have almost no experience with it, but I still need my program to run on it.

---

### Post by jespdj on 2009-02-10
Is it really necessary to copy the binary? Can't you just copy the source and try to compile that on the Aspire One, using the version of the lib that's on there?

---

### Post by MasterProg on 2009-02-11
> **jespdj said:**
> Is it really necessary to copy the binary?
Well, not really. I thought that copying a binary file would be easier, but I was wrong.

I'll try to compile my program on the notebook. Probably, it's the best solution for now.

---

### Post by Simian Man on 2009-02-11
> **MasterProg said:**
> It's a Fedora-based distribution. I have almost no experience with it, but I still need my program to run on it.

The Right Way™ to do this would be to create an rpm package.  Then you could install it along with the dependencies automatically.  You could also try linking statically to the libraries it can't find, or install them manually under your notebook.

---

### Post by MasterProg on 2009-02-11
GTK is not intended to be linked statically, so it will be hard to do that if even possible.

---

### Post by MasterProg on 2009-02-11
After about an hour I finally could get it compiled, but it didn't work as expected. Then I found out that notebook's kernel was lacking *usbserial* module which I needed.

I really think installing new kernel is too much, I'm going to install Ubuntu.

Thanks to everyone who helped me out. :)

---

