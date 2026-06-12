---
title: "How to realise application? (both as soure code and binary deb)"
date: 2007-09-27
forum: Programming Talk
---

### Post by brynjarh on 2007-09-27
So I've programmed my first application, using python, and I'm wondering how to release the source code, for example when I download application Xs source code there come with it some tools to install it, like ./configure, make, make install. And everything falls into it's right place.

- What kind of "tool" or "system" is good to use with a program written in python? (./configure, make, make install)
- How can I know where to place each file of my application in the filesystem?
- And finally, how do I make a deb?

So I'm basically asking, what do I do with the application to make it ready for use, be it as released source code or binary deb?

*please don't kill me because of the deb question, I'm more interested in realising the source code anyway, at the moment*

---

### Post by slavik on 2007-09-27
#ubuntu-motu can help you with howtos and such. :)

---

### Post by pmasiar on 2007-09-28
You don't have to make debs - if it is just simple app from half a dozen files, don't bother with deb packaging at the beginning. Just release files for the dozen or so users. You can add .deb later when you have more users.

Start a project on some free project hosting sites, like SourceForge, Google Code, I found [comparision](http://www.pythonthreads.com/news/latest/google-code-hosting-vs-sourceforge.html). I believe license s/b GPL or BSD, but check it too.

---

