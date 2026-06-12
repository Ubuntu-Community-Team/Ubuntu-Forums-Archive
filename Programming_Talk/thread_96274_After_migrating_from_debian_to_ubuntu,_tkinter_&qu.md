---
title: "After migrating from debian to ubuntu, tkinter &quot;hello world&quot; doesn't work"
date: 2005-11-28
forum: Programming Talk
---

### Post by zz_miguel on 2005-11-28
Hi

My python tkinter apps worked fine in debian linux (woody and sarge)
I moved to ubuntu 5.10

I follow the 'hello world' test as seen in
[http://wiki.python.org/moin/TkInter](http://wiki.python.org/moin/TkInter)


import _tkinter # with underscore, and lowercase 't'
import Tkinter # no underscore, uppercase 'T'
Tkinter._test() # note underscore in _test()

and at the third point I get:

  File "/usr/lib/python2.4/lib-tk/Tkinter.py", line 1569, in __init__
    self.tk = _tkinter.create(screenName, baseName, className,
interactive, wantobjects, useTk, sync, use)
_tkinter.TclError: this isn't a Tk applicationi


Some posts relate this error to locales, but I didn't change them

locale.getlocale()
('es_ES', 'iso-8859-15')

any help will be appreciated

Miguel

---

### Post by gord on 2005-11-28
seems to work fine for me, allthough i neeeeeeeever use Tkinter so its hard to diagnose. 
have you tryed removing python2.4-tk and reinstalling it?

did you just update to breezy via apt-get? iv heard about stability issues, it might be a good idea to reinstall ubuntu from a cd. having a seperate partition for /home is good for that, you can keep all you data intact and the like.

---

### Post by zz_miguel on 2005-12-01
It's a fresh instalation from a cd in a brand new laptop. I tried to
reinstall python2.4-tk and many other packeges  :-(

There are two errors
_tkinter.TclError: this isn't a Tk application
invalid color name "#efebe7 "

It is a tk problem. amsn (also based on tk) displays the same error.
Somebody in a post said that
aptitude install xrgb
solved it, but it didn't work for me.

It seems to be a problem of X window.
In a debian box, it works fine. But if I export the display to the
ubuntu
one, get same error. (Other apps export fine)
And even running it in the debian box, with a vnc display in the
ubuntu,
same error!   :-(( 

 The problem seems to be something very specific to my laptop and
x window.
I am using need  "855resolution"  , I'd like to know if it works for
somedy else with ubuntu and 855resolution.

thanks for your interest

---

