---
title: "Installing C++ GUI Library (FLTK?) on computer w/o root access"
date: 2007-12-18
forum: Programming Talk
---

### Post by veraction on 2007-12-18
I need to make a small, simple GUI in C++ for a project. I do not have root access to the system that I'll be compiling and running the app. This system doesn't seem to have any libraries already installed for C++ GUIs.

I've been looking at setting up FLTK (though I'm open to other libraries). I tried downloading the source and ./configure. However, I need the X11 development libraries. I downloaded the source for these, but these have many dependencies. I'm now like 12 layers deep in dependencies and it doesn't look like I'm getting out.

Now, if I had root access, I could just apt-get install libfltk1.1, which would resolve these dependencies for me.

How can I do this?

Thanks.

---

### Post by MG&amp;TL on 2011-07-10
As far as I know, you cannot install practically anything without access to sudo or whatever. I may be mistaken about this, but at the very least, it's difficult.

Sorry, stumbled across this on a web trawl.

---

### Post by MadCow108 on 2011-07-10
if the machine has fakechroot and fakeroot installed you could install your own little chroot where you have root.
if not you either have to install everything manually or, the obvious solution, ask the admin to install the software.

---

### Post by Bachstelze on 2011-08-01
Cool necro, bro. :o

---

