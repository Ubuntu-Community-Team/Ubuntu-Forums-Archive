---
title: "GUI or Web interface for stand-alone app?"
date: 2011-02-12
forum: Programming Talk
---

### Post by llanitedave on 2011-02-12
I'm developing an MVC simulation application in Python to be used by an individual, although distributable over the web.

The model and part of the controller portions are done, and it seems to be running -- it accepts input data (temporarily through a hard-coded "Entry Form" object), loops through its simulations, and spits out data.

What I need now is a sqlite database that stores selected bits of output, and a user interface that is relatively nice looking and will supply the input data as well as host routines for the display and analysis of the data, including graphs and formatted arrays.

This is where I'm pulling my hair out.  The design of my application *could* work well via a browser and a web server, and I've been thinking of developing a presentation system in Django to handle the database and user interface.

Alternatively, it is essentially a stand-alone application, and I should be able to implement it using Tkinter or wxPython or pyQt4 as well.

I'm thinking that Tkinter is easiest, as well as being Python3 ready, but I'm wondering if a web-based design might be more flexible and extensible.  I want to segue into creating some Django apps in the near future anyway.

I've been going back and forth in my mind, checking out the tutorials on both and trying to make a decision.  This is my most serious episode ever of "analysis paralysis".

So does it make sense to shift general-purpose application building efforts into a web-based model?  I guess the real question is, is the browser on track to serve as the GUI for general-purpose application development?

---

### Post by Some Penguin on 2011-02-12
Would every user of your application be expected to also be running a web server of their own?  (Or, alternately, connecting to servers that you've already set up)?

---

### Post by llanitedave on 2011-02-12
> **Some Penguin said:**
> Would every user of your application be expected to also be running a web server of their own?  (Or, alternately, connecting to servers that you've already set up)?

On Apple and Unix-ish systems that shouldn't be such a big deal, since Apache is installed by default on the Mac and web servers configurable for local use are common on *nix systems.  On Windows, might be more of a consideration.  Maybe something along the line's of Django's embedded development server would work for a non-shared standalone locally hosted application.

But considering the growing popularity of web apps, it does seem like it might be a good idea for computers to have local host servers available.

---

### Post by juancarlospaco on 2011-02-13
Apache is installed by default on the Mac ?, are you sure?

---

### Post by llanitedave on 2011-02-13
> **juancarlospaco said:**
> Apache is installed by default on the Mac ?, are you sure?

It was through 10.4, at least, when I last used it.  I haven't heard that it's changed.

---

