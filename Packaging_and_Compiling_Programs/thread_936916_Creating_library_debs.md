---
title: "Creating library debs"
date: 2008-10-03
forum: Packaging and Compiling Programs
---

### Post by SteelWo1f on 2008-10-03
So I'm trying to create a .deb out of a library. The steps I take are almost exactly the same as for a binary. I do:

dh_make (specifying library)
edit the stuff in debian/ accordingly
debuild

This does create the deb but there is nothing in it, just the changelog.

Am I doing something wrong?

Second questions: I want to run a script that does setup for a program the first time its installed. When you upgrade I dont want it to run the script again though. Where can I do this?

Thanks

---

### Post by Pro-reason on 2008-11-02
> **SteelWo1f said:**
> 
Second questions: I want to run a script that does setup for a program the first time its installed. When you upgrade I dont want it to run the script again though. Where can I do this?

Thanks

You should try to put only one question per thread.

You should probably run the script again.  What if the actions carried out by the script the first time have been reversed?  The user may be upgrading or re-installing in order to get it to work properly.  Just make it so that the script doesn't carry out any action if everything is already set up correctly.

For example, if you script adds a line to /etc/X11/xorg.conf, then it should include a function that checks to see whether the line is already there.

---

### Post by InfinityCircuit on 2008-11-03
Use debian/packagename.install files to specify which files to install and where.  man dh_install

---

### Post by SteelWo1f on 2008-11-03
Thanks for your reply. I did figure out how to do it. It was a combination of things. I needed to use dh_shlibdebs which by default isnt done. I needed to setup the .install files correctly as you say. Finally there was an issue with DESTDIR versus prefix.

It took a while but I think I understand pretty well most of whats going on now and Im creating packages left and right. I think this is just one of those things where you it would be nice to have someone point you in the general direction when you get lost. Actually the thing that helped the most was some tutorial recorded on IRC I found on a deb building site. It was hard to sort out but it did help. Some better docs would be nice.

---

