---
title: "text editor"
date: 2007-10-17
forum: Programming Talk
---

### Post by xurios on 2007-10-17
I've been using TextWrangler and xcode on the mac, but I am often on a linux box as well, or using a kde environment on the mac (I often spend a lot of time doing stuff with xwindows, even on the mac). One feature that is enabled by default on both the xcode editor and TextWrangler is a drop down mini-menu listing all the functions in a source file. You mouse over and let up the button and you are magically transported to that part of your source file. I don't really want to use an IDE, but if I could find good docs for using custom make files in kdevelop or something, I suppose I would be open to using it. Though I think it just uses kate anyway and I haven't found this feature in kdevelop and I don't like all the overhead created by IDE's, i.e. a gazillion files and a complicated project directory.

So, the question:

Anyone know of an editor under x windows that does this? Is there a config for kate for this? Something I could put in my .emacs?

---

### Post by mjwood0 on 2007-10-17
I have a function in my XEmacs that does just that.  It's called Func-Menu and I'm really not sure where it came from.  I actually got it from a colleague but I believe it's available online.

It creates a menu along the top (to the left of the File menu) which is called functions and has everything you need.

One caveat though is that your functions must be left aligned (just the definition of the function).  I'm not sure why, but some people indent the whole function (definition and all).

---

### Post by pmasiar on 2007-10-17
Yup, this is one feature I miss from MultiEdit

---

### Post by ilautar on 2007-10-17
> **mjwood0 said:**
> I have a function in my XEmacs that does just that.  It's called Func-Menu and I'm really not sure where it came from.  I actually got it from a colleague but I believe it's available online.

It creates a menu along the top (to the left of the File menu) which is called functions and has everything you need.

One caveat though is that your functions must be left aligned (just the definition of the function).  I'm not sure why, but some people indent the whole function (definition and all).

func-menu?

[http://www.xemacs.org/Documentation/packages/html/edit-utils_41.html](http://www.xemacs.org/Documentation/packages/html/edit-utils_41.html)

---

### Post by mjwood0 on 2007-10-17
One of the servers I work on is still running xemacs v19.4...

Many of these new improvments were't around then :-)

---

### Post by xurios on 2007-10-17
thanks folks, I'll try this in my .emacs in the morning.

---

