---
title: "Python : how to handle .deb files ?"
date: 2005-08-03
forum: Programming Talk
---

### Post by pef on 2005-08-03
Hello,

Does a module for python which handle .deb files exists ?

I'd like listing files, get the control file, etc from a deb file.

I've found python-apt and python-dpkg, but it doesn't suits me needs.


Thank you;)

---

### Post by LordHunter317 on 2005-08-03
What do you need to do that python-apt and python-dpkg don't do?

I suppose you could always call dpkg-deb directly.

---

### Post by pef on 2005-08-03
[QUOTE=LordHunter317]**What do you need to do that python-apt and python-dpkg don't do?**

I suppose you could always call dpkg-deb directly.[/QUOTE]

Listing files installed by the package like dpkg -c foo.deb

I know I can use popen or so, but I would like to know if a more "pythonic" way exists  ;-)

---

### Post by LordHunter317 on 2005-08-03
Well, like I said, you could always call dpkg-deb directly.  I don't know any better way if those two addons don't support that functionality.

---

### Post by Quest-Master on 2005-08-03
Or you could just use os.popen("dpkg something") and it would run the "dpkg something" command. If you needed to grab the output, just append a .read() onto it to make: os.poen("dpkg something").read()

---

### Post by LordHunter317 on 2005-08-03
That is what I'm telling him to do, in so many words.

---

