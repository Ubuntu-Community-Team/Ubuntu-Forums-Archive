---
title: "emacs 23.1"
date: 2009-01-24
forum: Programming Talk
---

### Post by perlsyntax on 2009-01-24
How can i install emacs 23.1 on unbuntu 8.10?

---

### Post by monkeyking on 2009-01-24
have you tried getting the sources  by cvs,
and then make and install it.

---

### Post by perlsyntax on 2009-01-24
how do i get it cvs?

---

### Post by shifty2 on 2009-01-24
I think (works on debian):
sudo apt-get install emacs-snapshot

---

### Post by monkeyking on 2009-01-28
Sorry for not getting back here earlier.
If you want cvs check out this webpage
[http://theblackdragon.wordpress.com/2006/04/27/installing-gnu-emacs-23-from-cvs/](http://theblackdragon.wordpress.com/2006/04/27/installing-gnu-emacs-23-from-cvs/)

If you install the snap shot from the repositories you'll get the
GNU Emacs 23.0.60.1
version.

But why do you want emacs 23?

---

### Post by nuclear-90 on 2009-07-31
emacs 23.1 has been released,where get .deb?

---

### Post by dusanyu on 2009-07-31
try Ubuntu PPA 
[https://launchpad.net/~ubuntu-elisp/+archive/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ppa)

there you will find the debs or a repository to temperately add and update your current emacs  version

---

### Post by bakom on 2009-07-31
> **dusanyu said:**
> try Ubuntu PPA 
[https://launchpad.net/~ubuntu-elisp/+archive/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ppa)

there you will find the debs or a repository to temperately add and update your current emacs  version

Hm, I don't see an emacs 23 package there?!

---

### Post by jpkotta on 2009-07-31
> **bakom said:**
> Hm, I don't see an emacs 23 package there?!

It's still called emacs-snapshot.

---

### Post by dbd on 2009-08-03
Thanks for the info, the snapshot seems to be working perfectly for me. 

The new version seems really nice so far. Unfortuntely the font it initially chose by default looked really ugly and blurry anti-aliased, so my first impression was pretty negative, but I've got myself a new monospace font now ([Inconsolata]("http://www.levien.com/type/myfonts/inconsolata.html")), and that looks niiiice :)

As for other changes the only really useful one I've noticed so far is the change to the behaviour of `C-l'. With a single press it does exactly what it used to, centres the window around the current line. But now when you press it again it moves the current line to the window centre, and a third press moves it to the bottom. I used to use `C-u 0 C-l' quite a lot to move the current line to the top, so being able to just double-tap `C-l' is really handy.

The new mode for viewing PDF and postscript files (Doc-view mode) would be really useful too, only it's far to slow at loading PDF files. Loading a 250 page PDF of text took over a minute (okular takes less than a second), and it takes that long every time I refresh it, even if only a couple of words have changed. I like to work with single, huge, files, so that renders the mode pretty much useless to me. 

Anyone else spotted any nice little changes? I bet there's a few more like the change to `C-l' which will be really useful, but impossible to discover otherwise, without a thorough reading of the changelog that is.

Edit: Actually, snapshot isn't 23.1, but the work in progress for version 23.2. Anyone found 23.1 in a repository somewhere?

Edit 2: I've ended up just compiling the source, which was pretty straightforward. Only problem is that there seems to be a bug when using AUCTeX mode in 23.1, which makes the window shrink whenever I use the minibuffer. But I've fixed that for now by disabling the tool-bar.

---

