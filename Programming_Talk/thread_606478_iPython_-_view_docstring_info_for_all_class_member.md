---
title: "iPython - view docstring info for all class members?"
date: 2007-11-08
forum: Programming Talk
---

### Post by chris.m.ball on 2007-11-08
I've been playing around with iPython and am loving some of the introspection features it offers.  However I'm finding one lacking feature.

Let's take the wxPython GUI Toolkit as an example.  Say we've just created a wx.Frame object and I'm curious about some of the member functions, properties, etc...I can obviously key in something like wx.Frame.<TAB> to get a nice list of all x hundred members of that class.  Likewise if I already know what I'm looking for, but need a bit more info, I might key in something like wx.Frame.SetStatusBar? or wx.Frame.SetStatusBar??.  But what if I wanted to get a listing of all the class members with their associated docstring info in one view?

I would like to be able to read the descriptions right next to each member for a given class.  

e.g.

>wx.Frame. *enters magic command here?*

SetStatusBar - Allows the user to associate the statusbar with the frame
SetMenuBar - Allows the user to associate the menubar with the frame
...

You get where I'm going with this I hope.  I'm trying to avoid having to "guess" at what members of a class I might make use of.

Thanks to all who can provide some insight here :popcorn:

---

### Post by ankursethi on 2007-11-08
In the terminal, type :
> pydoc <MODULE NAME>

:)

---

