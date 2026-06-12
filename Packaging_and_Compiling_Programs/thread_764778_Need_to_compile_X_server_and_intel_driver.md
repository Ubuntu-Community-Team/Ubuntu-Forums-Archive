---
title: "Need to compile X server and intel driver"
date: 2008-04-24
forum: Packaging and Compiling Programs
---

### Post by aidan.dixon on 2008-04-24
I need to compile the Xserver for Gutsy (7.10) along with intel video driver since I have a multi-head issue I am trying to debug on my company's hardware.  

I've installed the source packages and got the source out of git too from freedesktop.org.  What next?  Anybody have a guide or refer me to a previous post on this?

Thanks...
-a.

---

### Post by Compyx on 2008-04-25
You're in for a lot of fun!

[This guide]("http://www.linuxfromscratch.org/blfs/view/svn/x/installing.html") (from the Beyond Linux From Scratch project) should help you get going. The guide is meant to be used for X.org 7.2, but it should give you some idea of how to go about building X.org from source.

I've built X.org 7.3 from source by tracking down dependencies to determine build order and then issuing a lot of './configure', 'make' and 'make install' commands.

It might be a good idea to use a prefix such as '/opt/X11' so when you screw up you can just 'rm -rfd /opt/X11/*' and start over.
When you do this you might have to create a few symbolic links and add some additional paths to PKGCONFIG_PATH and PATH. But that should all be explained in the guide I linked to.

---

### Post by aidan.dixon on 2008-05-02
Thanks!
-a.

---

