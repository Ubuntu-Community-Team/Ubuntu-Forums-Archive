---
title: "Help releasing my new project"
date: 2009-08-22
forum: Packaging and Compiling Programs
---

### Post by tntcoda on 2009-08-22
Hey,

I'm after some help creating Ubuntu packages for my new project, its Qt based and my manual build process is as follows:

```

qmake
make
make install

```

I have absolutely no idea how to translate this into a .deb package, and from what ive read it seems more complex for Qt/qmake.

Would anyone be interested in helping me out with the packaging for the project? Or is there a simple procedure I can use to wrap qmake :confused:

Project is here: [http://piven.sourceforge.net](http://piven.sourceforge.net) its Usenet/NZB software.

Thanks very much for any advice.

Jack

---

### Post by Brandon Williams on 2009-08-23
[Here](http://www.debian.org/doc/maint-guide/) is the right place to start. It explains things step-by-step. The 'simple packaging example' in the appendix is a good place to start to get up and running quickly, though that example is easier to follow if you've read the whole guide already.

[Here](https://wiki.ubuntu.com/PackagingGuide/Complete) and [here](https://wiki.ubuntu.com/PackagingGuide/HandsOn) are some good Ubuntu-specific resources.

---

