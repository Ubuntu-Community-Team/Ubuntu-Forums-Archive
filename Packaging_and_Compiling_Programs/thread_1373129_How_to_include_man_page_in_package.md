---
title: "How to include man page in package"
date: 2010-01-05
forum: Packaging and Compiling Programs
---

### Post by Umang on 2010-01-05
Hi,
I'm pretty sure that this is a stupid question, so please do forgive me. I've written a man page (mypackage.1) and it is displayed as I want it to when I type $ man ./mypackage.1

I want to know how to make my package install this file. I've used this guide to package my python software: [https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)

Do I have to edit any of the control, rules, etc files?

Thanks.

Umang

---

### Post by andrewsomething on 2010-01-05
Hard to say exactly what you need to do without looking at your packaging, but generally:

The man page should go in: debian/mypackage.1

Then include a file named debian/mypackage.manpages whose contents include "debian/mypackage.1"

Or you can call "dh_installman debian/mypackage.1" from debian/rules.

---

### Post by Umang on 2010-01-05
Thanks! That works! Could I ask another small question?

If the package I am making is a game, does the man page have to be mygame.6 or mygame.1? The package is automatically renaming it to .6


EDIT: Silly question, I should have checked. It is mygame.6

---

### Post by Umang on 2010-01-06
Silly question again, and this time I'm not able to find the solution. Just the way you explained the manpage, could you explain the .desktop page also?

Thanks!

EDIT: Never mind. I'm going to ask on a new thread about the right method of doing this. Sorry for the confusion.

---

