---
title: "C++ questions"
date: 2006-11-19
forum: Programming Talk
---

### Post by Kiwinote on 2006-11-19
I've been using c++ for a while now, but still have a few questions:

**How can I create and edit a GUI that uses the standard theme of the user?**
I've tried googling this, but it keeps on resulting in visual c++ or gtkmm. Gtkmm looks reasonable, but is it possible to create a GUI in c++, without resorting to another language?

**How can I get a c++ program to issue commands(like bash)?**

If you know good tutorials about c++ written especially for g++, or good tutorials about creating deb's, please let me know.

Thanks,
Kiwinote

---

### Post by xtacocorex on 2006-11-19
Well gtkmm is the GTK+ library wrapper for C++ since all the GTK+ code is written in C. It's not a new language, it's a set of functions that will help with the creation of GUI's within C++.

---

### Post by Houman on 2006-11-19
Hi there,

As for your second question, you can execute commands by using system calls,
here is a good link: [http://www.cplusplus.com/ref/cstdlib/system.html]("http://www.cplusplus.com/ref/cstdlib/system.html")

regards

Houman

---

### Post by Kiwinote on 2006-11-20
> **Houman said:**
> Hi there,

As for your second question, you can execute commands by using system calls,
here is a good link: [http://www.cplusplus.com/ref/cstdlib/system.html]("http://www.cplusplus.com/ref/cstdlib/system.html")

regards

Houman

Thanks very much, just what I was looking for!

[quote=xtacocorex]Well gtkmm is the GTK+ library wrapper for C++ since all the GTK+ code is written in C. It's not a new language, it's a set of functions that will help with the creation of GUI's within C++.[/quote]

Will do some research in gtkmm once I have some free time then.

Thanks very much,
Kiwinote

---

### Post by hod139 on 2006-11-20
> **Kiwinote said:**
> I've been using c++ for a while now, but still have a few questions:

**How can I create and edit a GUI that uses the standard theme of the user?**
I've tried googling this, but it keeps on resulting in visual c++ or gtkmm. Gtkmm looks reasonable, but is it possible to create a GUI in c++, without resorting to another language?

There is [wx]("http://www.wxwidgets.org/"):
> 
Unlike other cross-platform toolkits, wxWidgets applications [B][I]look and feel native
[/I][/B]****

---

