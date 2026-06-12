---
title: "Missing emacs init file"
date: 2007-06-08
forum: Programming Talk
---

### Post by bramsundar on 2007-06-08
I can't find my .emacs file anywhere in my system. I've already looked in my home directory and it's nowhere to be found. Could somebody help me out?

---

### Post by jyba on 2007-06-09
There are two main versions of emacs - emacs and Xemacs and I don't think that either of them creates a .emacs file automatically - you have to create your own.

So what do you put in your .emacs? There are lots of examples of .emacs's that you can google for on the net, but here's one to start you off...
[http://www.dotemacs.de/dotfiles/sample.emacs.html](http://www.dotemacs.de/dotfiles/sample.emacs.html)
...just save it to .emacs in your home directory.

If you have Xemacs installed, they don't use a file called .emacs but create a directory called .xemacs. Inside that directory you create a file called custom.el and that functions as your .emacs.

Hmmmm, reading back over my message it looks as clear as mud. If you have any problems, post again. :p

---

### Post by bramsundar on 2007-06-11
Thanks a lot for the reply. I eventually managed to figure out that I was supposed to create my own .emacs file (although it took me forever, being the emacs noob that I am:)). Do you have any other hints about the .emacs file that could be useful?

---

