---
title: "I cannot create a project from existing sources in Anjuta 2"
date: 2009-11-30
forum: Programming Talk
---

### Post by Pepiko on 2009-11-30
Hello,

I have some C source code and I would like to create a new project with Anjuta from my existing source and I don't know exactly how to do that.

The reason is that the menu "New Project From Existing Sources" gives me an error that I have not a valid backend.

I have installed Anjuta 2.28.

Can anybody of you help me on creating a new project from existing files in Anjuta 2.

Any suggestions are welcomed.

---

### Post by Zugzwang on 2009-12-01
Please copy&paste the precise error message here. Also, please state which Ubuntu (Hardy/Jaunty/Karmic/etc.) you have installed.

---

### Post by Pepiko on 2009-12-01
Hi Zugzwang, ;)

The error that tells Anjuta is:

*Could not find a valid project backend for the directory given (/home/pepiko/project1). Please select a different directory, or try upgrading to a newer version of the Gnome Build Framework Anjuta.*

I was looking at the user manual of Anjuta and I have found that the functionallity of  importing a project from sources only works in existing projects that use **autoconf **or **automake** or for a limited number of plain Makefile files.

(Does it mean to have installed autotools package?)

I don't know exactly what does it means, but looking at the Internet I have found that the existing sources should have the following files with the sources:  *configure.ac* and *Makefile.am* .

See the following link for a Hello_world.c example [http://abhinavsingh.com/blog/2009/08/getting-started-with-autotools-gnu-build-system-on-debian/](http://abhinavsingh.com/blog/2009/08/getting-started-with-autotools-gnu-build-system-on-debian/)

Now, I don't know what to do because I only have the sources and a .glade file for the GUI and I don't know how should be my *configure.ac* and *Makefile.am* files if this is the way to import the project.

I will thank any comments,

---

### Post by Pepiko on 2009-12-01
Sorry I haven't told that I use karmic kubuntu and Anjuta 2.28.0.0, kernel 2.6.31-15-generic on a AMD 64

Thanks again,

---

### Post by MadCow108 on 2009-12-01
it may be outdated, but in the jaunty version (26 I think) import from existing project did not work at all.

And as your project was apparently not created by autotools you have little chance of getting it to work.
you'll probably have to create your project manually.

---

### Post by Pepiko on 2009-12-01
Hi MadCow108,

How can I create a project manually in Anjuta?

When I try to start creating a new project (GTK+ 2.0), Anjuta creates main.c, callbacks.c and a file with the extension .ui with the GUI based on GLADE.

I need to create a GTK+ project but with my existing main.c and an existing .glade file. Is it posible?

With [COLOR=#000000]Bloodshed Dev-C++ on Windows paltform you can create an empty project and after that add your sources. I don't know how to do that in Anjuta.

Thanks,
[/COLOR]

---

